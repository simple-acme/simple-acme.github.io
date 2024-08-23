---
layout: plugin
plugin_type: store
plugin: keyvault
compatibility: All platforms
examples:
    - 
        name: Service Principal
        cmd: '‑‑azuretenantid xxx ‑‑azureclientid xxx ‑‑azuresecret ***** ‑‑vaultname MyVault ‑‑certificatename MyCertificate'
    -
        name: Managaged Identity
        cmd: '‑‑azureusemsi ‑‑vaultname MyVault ‑‑certificatename MyCertificate'   
---
Store the certificate in [Azure KeyVault](https://azure.microsoft.com/en-us/services/key-vault/).

{% include plugin-seperate.md %}
