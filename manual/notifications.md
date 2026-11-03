---
settings:
    - Notification.ComputerName
    - Notification.Email.SmtpServer
    - Notification.Email.SmtpPort
    - Notification.Email.SmtpUser
    - Notification.Email.SmtpPassword
    - Notification.Email.SmtpSecure
    - Notification.Email.SmtpSecureMode
    - Notification.Email.SenderName
    - Notification.Email.SenderAddress
    - Notification.Email.ReceiverAddresses
    - Notification.Email.NotifyOnSuccess
    - Notification.Script.Path
    - Notification.Script.Parameters
    - Notification.Script.NotifyOnSuccess
    - Notification.Webhook.Url
    - Notification.Webhook.Format
    - Notification.Webhook.TemplatePath
    - Notification.Webhook.Headers
    - Notification.Webhook.IncludeLog
    - Notification.Webhook.NotifyOnSuccess
---
# Notifications
## Email
You can receive notifications about failed (and optionally successful) renewals via email by configuring the required SMTP server details in `settings.json`. You can test these notifications from the menu (`More options...` > `Test notification`). 

## Script
You can also configure a script to run to send you notifications, enabling more direct integration with third party communication or monitoring platforms. Examples of such scripts may be available in the [reference scripts](https://github.com/simple-acme/reference-scripts) repository. Contributions are most welcome!

## Webhooks
Notifications can also be sent as an HTTP `POST` request to a webhook, for example to post a message in Slack, to start a workflow in Zapier or n8n, or to report the status to a monitoring system.

### Events
Failures, renewals that succeeded with errors and cancelled renewals are always sent. Created and renewed certificates are only sent when `NotifyOnSuccess` is enabled.

| Event | Severity | Status | Sent |
|---|---|---|---|
| `created` | `info` | `up` | When `NotifyOnSuccess` is enabled |
| `success` | `info` | `up` | When `NotifyOnSuccess` is enabled |
| `success-with-errors` | `warning` | `down` | Always |
| `failure` | `error` | `down` | Always |
| `cancel` | `info` | `up` | Always |
| `test` | `info` | `up` | From the menu (`More options...` > `Test notification`) |

### Slack, Discord and Mattermost
Set `Format` to `slack` to send a message with the title, the message and, when known, the hosts of the certificate. This format also works for Slack-compatible services like Mattermost and Discord (add `/slack` to the Discord webhook URL). Because webhook URLs contain a secret, it is recommended to store the URL in the [secret vault](/manual/advanced-use/secret-management) and only refer to it in `settings.json`:

```json
"Notification": {
    "Webhook": {
        "Url": "vault://json/slackWebhook",
        "Format": "slack",
        "NotifyOnSuccess": true
    }
}
```

### Standard event
With the default format `json`, each notification is sent as a JSON object like the one below. The fields are added explicitly, so secrets like the PFX password or plugin options are never included. The log is only included when `IncludeLog` is enabled, and then contains at most 100 lines.

```json
{
    "schemaVersion": 1,
    "id": "0b6a3c1e-5f0d-4b6e-9a51-3f2b7c8d9e10",
    "type": "failure",
    "timestamp": "2026-11-01T02:00:03Z",
    "data": {
        "severity": "error",
        "status": "down",
        "title": "Renewal for example.com failed",
        "message": "Renewal for example.com on web01 failed, will retry on next run. Errors: ...",
        "computerName": "web01",
        "client": "simple-acme",
        "clientVersion": "2.x.x",
        "renewalId": "aBcDeFgHiJk",
        "friendlyName": "example.com",
        "hosts": [ "example.com", "www.example.com" ],
        "plugins": {
            "source": "IIS",
            "validation": "SelfHosting",
            "order": "Single",
            "csr": "RSA",
            "store": [ "CertificateStore" ],
            "installation": [ "IIS" ]
        },
        "expiresAt": "2026-12-20T10:00:00Z",
        "nextDueAt": "2026-11-28T10:00:00Z",
        "thumbprints": [ "0123456789ABCDEF0123456789ABCDEF01234567" ],
        "errors": [ "..." ],
        "log": null
    }
}
```

### Templates
When the receiver expects a different body, you can use `TemplatePath` to point to a JSON file of your own. Tokens like `{FriendlyName}` are replaced in each string value of the template, so the result is always valid JSON, even when a value contains quotes or line breaks. A value that consists of only `{Hosts}` or `{Errors}` becomes an array, and a value that consists of only `{ExitCode}` becomes a number (`0` when the status is `up`, otherwise `1`).

```json
{
    "summary": "{Title}",
    "details": "{Message}",
    "source": "{ComputerName}",
    "hosts": "{Hosts}",
    "errors": "{Errors}",
    "exitCode": "{ExitCode}"
}
```

The available tokens are `{EventId}`, `{EventType}`, `{Timestamp}`, `{Severity}`, `{Status}`, `{ExitCode}`, `{Title}`, `{Message}`, `{RenewalId}`, `{FriendlyName}`, `{ComputerName}`, `{Hosts}`, `{Errors}`, `{ExpiresAt}` and `{NextDueAt}`. Dates are in UTC, in the format `2026-12-20T10:00:00Z`.

### URL tokens and headers
The URL may contain the same tokens, which are URL-encoded. This is useful for health check services that read the status from the URL, for example [Healthchecks.io](https://healthchecks.io/docs/http_api/):

```json
"Webhook": {
    "Url": "https://hc-ping.com/your-uuid/{ExitCode}",
    "NotifyOnSuccess": true
}
```

Extra headers, for example for authentication, are configured in the form `Name: value`. The value may also refer to the secret vault:

```json
"Webhook": {
    "Url": "https://example.com/hooks/certificates",
    "Headers": [ "Authorization: vault://json/webhookAuthorization" ]
}
```

### Delivery
Each attempt has a timeout of 15 seconds. Network errors, timeouts and responses with status `429` or `5xx` are retried, with at most three attempts in total, respecting a `Retry-After` header of up to 30 seconds. Other responses are not retried. A redirect that changes the `POST` into a `GET` is reported as an error, because the body would not be delivered, so make sure to configure the final URL.

A failed webhook is logged, but never causes the renewal itself to fail. Because the URL and headers may contain secrets, only the host of the webhook is logged, also in verbose mode.

<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>Many services can be reached with a webhook and a template. When that is not enough, it is possible to implement additional forms of notification (e.g. Teams, Jira, ...) using C# by implementing the <a href="https://github.com/simple-acme/simple-acme/blob/main/src/main.lib/Services/Interfaces/INotificationTarget.cs">INotificationTarget</a> interface. Contributions in this area are most welcome!</p>
    </div>
</div>
