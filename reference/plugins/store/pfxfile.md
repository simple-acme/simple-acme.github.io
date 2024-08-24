---
layout: plugin
plugin_type: store
plugin: pfxfile
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑pfxpassword *****] [‑‑pfxfilepath C:\Certificates\] [‑‑pfxfilename mycert]' 
---
Exports a PKCS12 archive (on Windows often called a PFX archive) including the certificate, 
its private key and the chain, and places it in a folder of your choice. By default the 
file name will be the common name of the certificate (i.e. the primary host name), but 
this may be overruled.
