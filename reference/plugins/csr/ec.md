---
layout: plugin
plugin: 9aadcf71-5241-4c4f-aee1-bfe3f6be3489
settings:
    - Csr.Ec.CurveName
    - Csr.Ec.SignatureAlgorithm
compatibility: All platforms
examples:
    - 
      name: Typical
      cmd: '[‑‑ocsp-must-staple] [‑‑reuse-privatekey]'
---
Generates ECDSA keys. Only SEC named curves are supported by this client. The ACME server may have additional limitations.