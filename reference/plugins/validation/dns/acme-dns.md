---
layout: plugin
plugin: c13acc1b-7571-432b-9652-7a68a5f506c5
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑acmednsserver https://acme-dns.example.com/]'   
---
Use an [acme-dns](https://github.com/joohoi/acme-dns) server to handle the validation records. The plugin will ask you to choose an endpoint to use. 

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>For testing the <a href="https://auth.acme-dns.io/">https://auth.acme-dns.io/</a> endpoint is useful, but it is a security concern. As the readme of that project clearly states: "You are encouraged to run your own acme-dns instance."</p>
    </div>
</div>

It's possible to use basic authentication for your acme-dns service by specifying a url with the format `https://user:password@acme-dns.example.com/`

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>Unattended creation of certificates using this plugin has limited support. It only works if there are pre-existing acme-dns registrations for all the included domains. The reason for this is that acme-dns requires you to create CNAME records. In the future this might be scripted the same way we can script DNS validation itself, but so far there hasn't been enough demand for that feature to make it worth developing.</p>
    </div>
</div>