---
client:
  - Client.ClientName
  - Client.ConfigurationPath
  - Client.LogPath
  - Client.VersionCheck
ui:
  - UI.DateFormat
  - UI.PageSize
  - UI.TextEncoding
  - UI.Color.Background
acme:
  - ACME.DefaultBaseUri
  - ACME.DefaultBaseUriTest
  - ACME.DefaultBaseUriImport
  - ACME.PostAsGet
  - ACME.ValidateServerCertificate
  - ACME.RetryCount
  - ACME.RetryInterval
  - ACME.PreferredIssuer
execution:
  - Execution.DefaultPreExecutionScript
  - Execution.DefaultPostExecutionScript
proxy:
  - Proxy.Url
  - Proxy.Username 
  - Proxy.Password
cache:
  - Cache.Path
  - Cache.ReuseDays 
  - Cache.DeleteStaleFiles 
  - Cache.DeleteStaleFileDays    
scheduledtask:
  - ScheduledTask.RenewalDays
  - ScheduledTask.RenewalDaysRange 
  - ScheduledTask.RenewalDisableServerSchedule 
  - ScheduledTask.RenewalMinimumValidDays    
  - ScheduledTask.StartBoundary    
  - ScheduledTask.ExecutionTimeLimit    
  - ScheduledTask.RandomDelay
notifications:
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
security:
  - Security.EncryptConfig
  - Security.FriendlyNameDateTimeStamp    
script:
  - Script.Timeout
  - Script.PowershellExecutablePath
source:
  - Source.DefaultSource
validation:
  - Validation.DefaultValidation  
  - Validation.DefaultValidationMode 
  - Validation.DisableMultiThreading  
  - Validation.ParallelBatchSize  
  - Validation.CleanupFolders  
  - Validation.PreValidateDns  
  - Validation.PreValidateDnsRetryCount  
  - Validation.PreValidateDnsRetryInterval 
  - Validation.AllowDnsSubstitution 
  - Validation.Ftp.UseGnuTls 
  - Validation.DnsServers
order:
  - Order.DefaultOrder
  - Order.DefaultValidDays
csr:
  - Csr.DefaultCsr
  - Csr.Rsa.KeyBits
  - Csr.Rsa.SignatureAlgorithm
  - Csr.Ec.CurveName
  - Csr.Ec.SignatureAlgorithm
store:
  - Store.DefaultStore
certificatestore:
  - Store.CertificateStore.DefaultStore
  - Store.CertificateStore.PrivateKeyExportable
  - Store.CertificateStore.UseNextGenerationCryptoApi
centralssl:
  - Store.CentralSsl.DefaultPath
  - Store.CentralSsl.DefaultPassword
pemfiles:
  - Store.PemFiles.DefaultPath
  - Store.PemFiles.DefaultPassword
pfxfile:
  - Store.PfxFile.DefaultPath
  - Store.PfxFile.DefaultPassword
installation:
  - Installation.DefaultInstallation
secrets:
  - Secrets.Json.FilePath
---
# Settings.json
Some of the applications' settings can be modified in a file called `settings.json`. 
If this file is not present when the program starts it will be automatically 
created on first run, copied from `settings_default.json`. This allows you to
<code>xcopy</code> new releases without worrying about overwriting your previously 
customized settings.

{% include settings.html settings=page.client title='Client' remove='Client' %}
{% include settings.html settings=page.ui title='UI' remove='UI' %}
{% include settings.html settings=page.acme title='ACME' remove='ACME' %}
{% include settings.html settings=page.execution title='Execution' remove='Execution' %}
{% include settings.html settings=page.proxy title='Proxy' remove='Proxy' %}
{% include settings.html settings=page.cache title='Cache' remove='Cache' %}
{% include settings.html settings=page.scheduledtask title='Scheduled task' remove='ScheduledTask' %}
{% include settings.html settings=page.notifications title='Notifications' remove='Notifications' %}
{% include settings.html settings=page.proxy title='Proxy' remove='Proxy' %}
{% include settings.html settings=page.script title='Script' remove='Script' %}
{% include settings.html settings=page.validation title='Validation' remove='Validation' %}
{% include settings.html settings=page.order title='Order' remove='Order' %}
{% include settings.html settings=page.csr title='CSR' remove='Csr' %}
{% include settings.html settings=page.store title='Store' remove='Store' %}
{% include settings.html settings=page.certificatestore title='Windows Certificate Store' remove='Store.CertificateStore' %}
{% include settings.html settings=page.centralssl title='IIS Central Certificate Store' remove='Store.CentralSsl' %}
{% include settings.html settings=page.pemfiles title='PEM files' remove='Store.PemFiles' %}
{% include settings.html settings=page.pfxfile title='PFX file' remove='Store.PfxFile' %}
{% include settings.html settings=page.installation title='Installation' remove='Installation' %}
{% include settings.html settings=page.secrets title='Secrets' remove='Secrets' %}