---
title: RSA
layout: plugin
plugin_type: csr
plugin_name: rsa
compatibility: Windows, Linux
default: Yes (all platforms)
id: b9060d4b-c2d3-49ac-b37f-962e7c3cbe9d
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
Generates 3072 bits RSA key pairs. The number of key bits can be configured in [settings.json](/reference/settings) but may not be less than 2048.