---
settings:
    - Notifications.SmtpServer
    - Notifications.SmtpPort
    - Notifications.SmtpUser
    - Notifications.SmtpPassword
    - Notifications.SmtpSecure
    - Notifications.SmtpSecureMode
    - Notifications.SmtpSenderName
    - Notifications.SenderAddress
    - Notifications.ReceiverAddresses
    - Notifications.EmailOnSuccess
    - Notifications.ComputerName
---
# Notifications
You can receive notifications about failed (and optionally successful) renewals via email by configuring the required SMTP server details in `settings.json`. You can test these notifications from the menu (`More options...` > `Test notification`).

<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>It is possible to implement additional forms of notification (i.e. Slack, Discord, Teams, Jira, ...) using C# by implementing the <a href="https://github.com/simple-acme/simple-acme/blob/master/src/main.lib/Services/Interfaces/INotificationTarget.cs">INotificationTarget</a> interface. Contributions in this area are most welcome!</p>
    </div>
</div>