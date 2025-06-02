---
---
# Settings.json
Some of the applications' settings can be modified in a file called `settings.json`. 
If this file is not present when the program starts it will be automatically 
created on first run, copied from `settings_default.json`. This allows you to
<code>xcopy</code> new releases without worrying about overwriting your previously 
customized settings.

{% include settings.html settings=site.data.settings2.client title='Client' remove='Client' %}
{% include settings.html settings=site.data.settings2.ui title='UI' remove='UI' %}
{% include settings.html settings=site.data.settings2.acme title='ACME' remove='Acme' %}
{% include settings.html settings=site.data.settings2.execution title='Execution' remove='Execution' %}
{% include settings.html settings=site.data.settings2.proxy title='Proxy' remove='Proxy' %}
{% include settings.html settings=site.data.settings2.cache title='Cache' remove='Cache' %}
{% include settings.html settings=site.data.settings2.scheduledtask title='Scheduled task' remove='ScheduledTask' %}
{% include settings.html settings=site.data.settings2.notification title='Notifications' remove='Notification' %}
{% include settings.html settings=site.data.settings2.security title='Security' remove='Security' %}
{% include settings.html settings=site.data.settings2.proxy title='Proxy' remove='Proxy' %}
{% include settings.html settings=site.data.settings2.script title='Script' remove='Script' %}
{% include settings.html settings=site.data.settings2.validation title='Validation' remove='Validation' %}
{% include settings.html settings=site.data.settings2.order title='Order' remove='Order' %}
{% include settings.html settings=site.data.settings2.csr title='CSR' remove='Csr' %}
{% include settings.html settings=site.data.settings2.store title='Store' remove='Store' %}
{% include settings.html settings=site.data.settings2.certificatestore title='Windows Certificate Store' remove='Store.CertificateStore' %}
{% include settings.html settings=site.data.settings2.centralssl title='IIS Central Certificate Store' remove='Store.CentralSsl' %}
{% include settings.html settings=site.data.settings2.pemfiles title='PEM files' remove='Store.PemFiles' %}
{% include settings.html settings=site.data.settings2.pfxfile title='PFX file' remove='Store.PfxFile' %}
{% include settings.html settings=site.data.settings2.p7bfile title='P7B file' remove='Store.P7bFile' %}
{% include settings.html settings=site.data.settings2.installation title='Installation' remove='Installation' %}
{% include settings.html settings=site.data.settings2.secrets title='Secrets' remove='Secrets' %}