---
layout: plugin
plugin: e30adc8e-d756-4e16-a6f2-450f784b1a97
settings:
    - Store.CertificateStore.DefaultStore
    - Store.CertificateStore.PrivateKeyExportable
    - Store.CertificateStore.UseNextGenerationCryptoApi
compatibility: Windows
examples:
    - 
        name: Typical
        cmd: '[‑‑certificatestore My] [‑‑keepexisting] [‑‑acl-fullcontrol "network service,administrators"] [‑‑acl-read "myapp"]'  
---
Saves certificates to the Windows Certificate store. This will always import to the `Computer` store. Refer to the [User Store](/reference/plugins/store/userstore) plugin if you want to have a certificate in the `User` store.

## Compatibility
For best compatiblitity with legacy applications, the program attempts to store certificates with RSA keys using the `Microsoft RSA SChannel Cryptographic Provider`. If you require a more modern approach to key storage, refer to the setting listed below.

## Private key export
By default the private keys *not* exportable. This can be changed globally via the settings, but generally we recommend not doing this, because 99% of use cases should be manageable by using another (additional) store step. If you're looking to move the certificate to another server, read more about [migration to another server](/manual/migration).