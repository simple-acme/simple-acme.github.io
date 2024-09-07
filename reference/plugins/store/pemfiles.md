---
layout: plugin
plugin: e57c70e4-cd60-4ba6-80f6-a41703e21031
settings:
    - Store.PemFiles.DefaultPath
    - Store.PemFiles.DefaultPassword
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑pemfilespath C:\Certificates\] [‑‑pempassword ******] [‑‑pemfilesname mycert]' 
---
Designed for [Apache](/manual/advanced-use/examples/apache), nginx and other web servers. 
Exports a `.pem` file for the certificate and private key and places them a folder of your choice.

Files created are:
- `{name}-crt.pem` (certificate)
- `{name}-key.pem` (private key)
- `{name}-chain.pem` (certificate plus chain)
- `{name}-chain-only.pem` (chain without certificate)

By default `{name}` will be the common name of the certificate (i.e. the primary host 
name), but this may be overruled. If you choose to have the `-key.pem` file password 
protected, you should make sure that the software you intend to consume the key with 
supports this as well.