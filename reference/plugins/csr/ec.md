---
layout: plugin
plugin_type: csr
plugin: ec
compatibility: All platforms
examples:
- 
    name: Full
    cmd: '[--ocsp-must-staple] [--reuse-privatekey]'
---
Generates ECDSA keys based on the `secp384r1` curve. The curve to use can be 
configured in [settings.json](/reference/settings) but currently only 
SEC named curves are supported. The ACME server provider may have 
additional limitations.