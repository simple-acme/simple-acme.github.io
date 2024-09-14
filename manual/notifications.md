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
You can receive notifications about failed (and optionally successful) renewals via email by configuring the required SMTP server details in settings.json. You can test these notifications from the menu (`More options...` > `Test notification`).

## Plugins
It is possible to implement additional forms of notification (i.e. Slack, Discord) using C# by implementing the `INotificationTarget` interface. Contributions in this area are most welcome!