---
layout: plugin
plugin_type: csr
plugin: rsa
compatibility: All platforms
examples:
- 
    name: Full
    cmd: '[‑‑ocsp-must-staple] [‑‑reuse-privatekey]'
---
Generates RSA key pairs. The number of key bits can be configured in [settings.json](/reference/settings) but may not be less than 2048.