---
layout: plugin
plugin_type: csr
plugin: ec
compatibility: All platforms
examples:
- 
    name: Full
    cmd: '[‑‑ocsp-must-staple] [‑‑reuse-privatekey]'
---
Generates ECDSA keys. Only SEC named curves are supported by this client. The ACME server may have additional limitations.