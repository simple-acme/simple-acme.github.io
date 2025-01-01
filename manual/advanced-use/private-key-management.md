---
settings:
    - Cache.Path
    - Cache.ReuseDays
    - Store.CertificateStore.PrivateKeyExportable
    - Store.CertificateStore.UseNextGenerationCryptoApi
arguments:
    - reuse-privatekey
---
# Private keys

ACME is all about automation and certificates are typically considered to 
be disposable and easily replacable. There are scenarios though where you
want to manually handle a certificate and its private key.

## Always-accessible private keys
The best way to access the private keys is to configure your renewals to 
save the certificate in an easily transferrable way, e.g. by using the 
[PFX file](/reference/plugins/store/pfxfile) store plugin. 

If you're using 
the default [Windows Certificate Store](/reference/plugins/store/certificatestore)
plugin you can set `PrivateKeyExportable` to `true` to enable certificates to be exported with their keys included. The best tools for exporting are Powershell and the "Manage Computer Certificates" MMC snap-in, because when `UseNextGenerationCryptoApi` is enabled, even exportable certificates cannot be exported by the IIS Manager.

## Disaster recovery
The `PrivateKeyExportable` setting only works for future certificates, 
so if you're in a hurry you can force the renewals using `‑‑renew ‑‑force` 
or from the interactive menu to get new certificates with exportable keys.

When renewal is not an option and you need to get the current certificate,
you can find a `.pfx` file in the `{Client.CertificatePath}`. You can access the 
passwords for these cache files from the main menu (`Manage Renewals` > `Show details`) 
or you can [decrypt](/manual/advanced-use/encryption) the `.renewal.json` files and 
subsequently find the passwords in plain text.

## Reuse private keys
If you don't want your private key to change for each renewal, you can use the option 
`‑‑reuse-privatekey` when setting up the renewal. This can 

## Private key cache
By default simple-acme retains a copy of the private key in its certificate cache. These files are both encrypted and protected by access control lists in the file system. You can disable this feature by setting `Cache.ReuseDays` to `0` There will still be `.pfx` files written to disk containing the certificates (this is used for various other purposes, like detecting source changes, revocation, etc.), but they will not contain any private key information.
