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
---
# Notifications
You can receive notifications about failed (and optionally successful) renewals via email by configuring the required SMTP server details in `settings.json`. You can test these notifications from the menu (`More options...` > `Test notification`). 

You can also configure a script to run to send you notifications, enabling more direct integration with third party communication or monitoring platforms. Examples of such scripts may be available in the [reference scripts](https://github.com/simple-acme/reference-scripts) repository. Contributions are most welcome!

<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>It is possible to implement additional forms of notification (i.e. Slack, Discord, Teams, Jira, ...) using C# by implementing the <a href="https://github.com/simple-acme/simple-acme/blob/master/src/main.lib/Services/Interfaces/INotificationTarget.cs">INotificationTarget</a> interface. Contributions in this area are most welcome!</p>
    </div>
</div>
