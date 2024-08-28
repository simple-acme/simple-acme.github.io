---
layout: plugin
plugin_type: validation
plugin_subtype: http
plugin: sftp
---
# SFTP
This plugin uploads the validation challenge to a SSH FTP, also known as SFTP, server.

{% include validation-http-common.md %}

## Unattended 
`‑‑validation sftp ‑‑webroot ftps://x/ ‑‑username admin ‑‑password ******`