---
---
# Windows Certificate Store
Default plugin, saves certificates to the Windows Certificate store. Which store is used is based on the following priorities:

- Store configured for the specific renewal
- Global default is configured in [settings.json](/reference/settings)
- `WebHosting` store (if it exists, i.e. Windows 2012+ with IIS)
- The machine-level `My` store (better known as Personal)

## Compatibility
For improved compatiblitity, certificates with RSA keys are automatically converted to 
the `Microsoft RSA SChannel Cryptographic Provider` when stored to the Windows Certificate Store. 
This prevents problems with older versions of Exchange and allows exportable certificates (see next section) 
to be exported from the IIS Management Console (vs. only from the Computer Certificates snap-in). 
To disable this conversion step, set `UseNextGenerationCrypto` to `true` in [settings.json](/reference/settings).

## Private key export
By default the private keys are set to be *not* exportable. You can change this behaviour 
by setting `PrivateKeyExportable` to `true` in [settings.json](/reference/settings). 
The updated setting only takes effect after the next (uncached) renewal.

## Keep existing
The `‑‑keepexisting` switch can be used to prevent the program from deleting older 
versions of the certificate from the store.

## Private key ACL
The `‑‑acl-fullcontrol` and `‑‑acl-read` parameters can be used to grant principals other than the 
defaults for a specific store access to the private key. You can use principal names or well-known SIDs here.

## Unattended
`[‑‑store certificatestore] [‑‑certificatestore My] [‑‑keepexisting] [‑‑acl-fullcontrol "network service,administrators"] [‑‑acl-read "myapp"]`