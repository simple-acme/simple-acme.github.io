---
layout: plugin
plugin: b9060d4b-c2d3-49ac-b37f-962e7c3cbe9d
settings:
    - Csr.Rsa.KeyBits
    - Csr.Rsa.SignatureAlgorithm
compatibility: All platforms
examples:
    - 
      name: Typical
      cmd: '[‑‑ocsp-must-staple] [‑‑reuse-privatekey]'
---
Generates RSA key pairs. The number of key bits can be configured in [settings.json](/reference/settings) but may not be less than 2048.