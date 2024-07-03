---
---
# Windows Certificate Store
Default plugin, saves certificates to the Windows Certificate store. Which store is used is based on the following priorities:

- Store configured for the specific renewal
- Global default is configured in [settings.json](/reference/settings)
- `WebHosting` store (if it exists, i.e. Windows 2012+ with IIS)
- The machine-level `My` store (better known as Personal)

## Private key export
By default the private keys are not set to be exportable. You can change this behaviour 
by setting `PrivateKeyExportable` to `true` in [settings.json](/reference/settings). 

## Keep existing
The `--keepexisting` switch can be used to prevent the program from deleting older 
versions of the certificate from the store.

## Private key ACL
The `--acl-fullcontrol` parameter can be used to grant principals other than the 
defaults for a specific store full control access to the private key. 

## Unattended
`[--store certificatestore] [--certificatestore My] [--keepexisting] [--acl-fullcontrol "network service,administrators"]`