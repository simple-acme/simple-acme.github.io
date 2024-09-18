---
---
# Getting started

<div class="callout-block callout-block-info">                    
    <div class="content">
        <h4 class="callout-title">
            <span class="callout-icon-holder me-1">
                <svg class="svg-inline--fa fa-circle-info" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="circle-info" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M256 512A256 256 0 1 0 256 0a256 256 0 1 0 0 512zM216 336h24V272H216c-13.3 0-24-10.7-24-24s10.7-24 24-24h48c13.3 0 24 10.7 24 24v88h8c13.3 0 24 10.7 24 24s-10.7 24-24 24H216c-13.3 0-24-10.7-24-24s10.7-24 24-24zm40-208a32 32 0 1 1 0 64 32 32 0 1 1 0-64z"></path></svg><!-- <i class="fas fa-info-circle"></i> Font Awesome fontawesome.com -->
            </span><!--//icon-holder-->
            Note
        </h4>
The default settings are for users looking to install a regular (non-wildcard) certificate for an IIS web server running on the same machine. For any other scenario you should skip straight to the section on advanced use.
    </div><!--//content-->
</div>


- [Install](/manual/installation) simple-acme on your web server using any method.
- Choose `N` in the main menu to create a new certificate with default settings.
- Choose the website(s) and binding(s) that you want to create a certificate for.
- You may get a popup from your firewall requesting permission for the program to listen to incoming requests on port 80 and 443. This is required for the default validation method. If you refuse, you can pick another validation method instead.
- An [account](/manual/account-management) is created at the ACME server (which is [Let's Encrypt](https://letsencrypt.org/) by default). You will be asked to agree to the terms of service and to (optionally) provide an email address that the administrators can use to contact you.
- The program negotiates with the server to try and prove your ownership of the domain(s) that you want to create the certificate for. By default the [HTTP validation](/reference/plugins/validation/http/) mode is used, handled by our [self-hosting](/reference/plugins/validation/http/selfhosting) plugin. Getting validation right is often the most tricky part of getting an ACME certificate. If there are problems please check out some [common issues](/manual/validation-problems).
- After the proof has been provided, the program downloads the new certificate from the server, installs it into the [Windows Certificate Store](/reference/plugins/store/certificatestore) and updates or creates [IIS bindings](/reference/plugins/installation/iis) as required. Note that the program is deliberately conservative in creating new bindings, so the first time you may need to add additional ones manually, e.g. if you're running the same host name on multiple ports.
- The program remembers all choices that you made while creating the certificate and applies them for each subsequent [renewal](/manual/automatic-renewal). It also recognizes when an ACME certificate has been manually added to any other web or ftp site and updates those automatically upon replacement.
- A scheduled task is created in the Windows Task Scheduler, which will run the program every day. Every day the task runs, [several methods](/manual/automatic-renewal) are used to determine whether one ore more certificates managed by the program are supposed to be renewed on that particular day.