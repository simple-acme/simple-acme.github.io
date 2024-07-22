---
title: Elliptic Curve
layout: plugin
plugin_type: csr
plugin_name: ec
compatibility: Windows, Linux
id: 9aadcf71-5241-4c4f-aee1-bfe3f6be3489
arguments:
    - 
        name: --ocsp-must-staple
        desc: Enable the OCSP Must Staple extension
    - 
        name: --reuse-privatekey
        desc: Use the same private key every time the certificate is replaced, which can be useful for example with <a href="https://en.wikipedia.org/wiki/DNS-based_Authentication_of_Named_Entities">DANE</a>.       
examples:
    - 
        name: Full
        cmd: '[--ocsp-must-staple] [--reuse-privatekey]'
 
---
Generates ECDSA keys based on the `secp384r1` curve. The curve to use can be 
configured in [settings.json](/reference/settings) but currently only 
SEC named curves are supported. The ACME server provider may have 
additional limitations.