---
layout: plugin
plugin_type: store
plugin: certificatestore                                   
---
Saves certificates to the Windows Certificate store. This will always import to the `Computer` store. Refer to the [User Store](/reference/plugins/store/userstore) plugin if you want to have a certificate in the `User` store.

## Compatibility
For best compatiblitity with legacy applications, the program attempts to store certificates with RSA keys using the `Microsoft RSA SChannel Cryptographic Provider`. If you require a more modern approach to key storage, refer to the setting listed below.

## Private key export
By default the private keys *not* exportable. This can be changed globally via the settings, but generally we recommend not doing this, because 99% of use cases should be manageable by using another (additional) store step. If you're looking to move the certificate to another server, read more about [migration to another server](/manual/migration).