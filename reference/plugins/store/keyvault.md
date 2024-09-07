---
layout: plugin
plugin: dbfa91e2-28c0-4b37-857c-df6575dbb388
compatibility: All platforms
examples:
    - 
        name: Service Principal
        cmd: '‑‑azuretenantid 8a947dda-3ed2-40dc-8058-d7b212322ed2 ‑‑azureclientid e02a0517-412e-4e0a-996b-2693458a9232 ‑‑azuresecret ***** ‑‑vaultname MyVault ‑‑certificatename MyCertificate'
    -
        name: Managaged Identity
        cmd: '‑‑azureusemsi ‑‑vaultname MyVault ‑‑certificatename MyCertificate'
---
Store the certificate in [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/).