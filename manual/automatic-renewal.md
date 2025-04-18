---
arguments:
    - renew
    - force
    - nocache
settings:
    - ScheduledTask.RenewalDays
    - ScheduledTask.RenewalDaysRange
    - ScheduledTask.RenewalDisableServerSchedule
    - ScheduledTask.RenewalMinimumValidDays
    - ScheduledTask.StartBoundary
    - ScheduledTask.ExecutionTimeLimit
    - ScheduledTask.RandomDelay
    - Cache.ReuseDays
---
# Automatic renewal

## Scheduled task
A single scheduled task or cronjob is responsible to renew *all* certificates created by the program, but will only do so when it's actually necessary. The task is created by the program itself after successfully creating the first certificate. The task runs once every day and checks five conditions to determine if it should renew:

- The certificate is getting too old. This is based on the known history and validity dates, recorded in the internal certificate cache and `*.renewal.json` files. Certificates are considered due for renewal when it's been issued more than `ScheduledTask.RenewalDays` days in the past, *or* it is valid for less than `ScheduledTask.RenewalMinimumValidDays` days in the future.
- The source (list of domains) has changed, e.g. an extra binding has been added to an IIS site.
- The server tells the client that a renewal should happen, e.g. due to a security incident or because of anticipated load peaks. This mechanism is called ACME Renewal Information (ARI) and is a [draft specification](https://datatracker.ietf.org/doc/draft-ietf-acme-ari/04/).
- The certificate has been revoked by the user.
- The certificate has not been successfully installed yet.

### Customization
Some properties for the scheduled task can be changed in [settings.json](/reference/settings#scheduled-task) or the Task Scheduler, as long as its name is left unmodified. By default, it runs randomly between 9:00am and 11:00am (to help spread load at the server) using the `SYSTEM` account.

### Health checks
The health of the scheduled task is checked each time the program is run manually. It can also be (re)created from the menu (`More options...` > `(Re)create scheduled task`).

### Monitoring
The renewal process can be monitored from the Windows Event Viewer and log files 
written to `%programdata%\simple-acme\$baseuri$\Log`. Logs are retained for 120 days by default. You can also set up [notifications](/manual/notifications) to be informed about any problems that the program encounters.

## Testing and troubleshooting
To test or troubleshoot the renewal process, renewals can be triggered manually from the menu or the command line with `‑‑renew ‑‑force` switches. We recommend doing so while running with the `‑‑verbose` parameter to get maximum log visibility. When listing the details for a renewal, the program will show any errors that have been recorded during previous runs.

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>The program's built in certificate cache protects users from running into rate limits while debugging the renewal process. On a cache hit, the program still goes through all the steps, but doesn't actually request a new certificate from the server. To bypass the cache, the argument <code>‑‑nocache</code> or the setting <code>Cache.ReuseDays</code> can be used.</p>
    </div>
</div>
