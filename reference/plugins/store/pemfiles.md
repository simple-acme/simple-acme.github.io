---
layout: plugin
plugin: e57c70e4-cd60-4ba6-80f6-a41703e21031
settings:
    - Store.PemFiles.DefaultPath
    - Store.PemFiles.DefaultPassword
    - Store.PemFiles.KeyFormat
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑pemfilespath C:\Certificates\] [‑‑pempassword ******] [‑‑pemfilesname mycert]' 
---
Designed for [Apache](/manual/advanced-use/examples/apache), nginx and other web servers. 
Exports a `.pem` file for the certificate and private key and places them a folder of your choice.

Files created are:
- `{name}-crt.pem` - certificate
- `{name}-key.pem` - private key
- `{name}-chain.pem` - certificate and intermediates (no root)
- `{name}-chain-full.pem` - certificate and full chain (including root)
- `{name}-chain-only.pem` - intermediates only (no certificate, no root)
- `{name}-chain-only-full.pem` - full chain only (no certificate, including root)

By default, `{name}` will be the common name of the certificate (i.e. the primary host 
name), but this may be overruled. If you choose to have the `-key.pem` file password 
protected, you should make sure that the software you intend to consume the key with 
supports this as well. 
