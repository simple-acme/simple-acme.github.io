---
layout: plugin
plugin: 221310a3-14d8-4478-a0f1-3c6d90f2ea51
settings:
    - Store.P7bFile.DefaultPath
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑p7bfilepath C:\Certificates\] [‑‑p7bfilename mycert]' 
---
Exports a P7B archive file including the certificate and the chain, and places it in a folder of your choice. By default the 
file name will be the common name of the certificate (i.e. the primary host name), but this may be overruled.

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>This output format does not include a private key. It should only be used in combination with a <a href="/reference/plugins/source/csr">Custom CSR</a> or if you have another store method from where you access the private key.</p>
    </div>
</div>
