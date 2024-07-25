---
settings:
    - Csr.DefaultCsr
---
# CSR plugins

CSR plugins are responsible for generating a [Certificate Signing Request](https://en.wikipedia.org/wiki/Certificate_signing_request) 
that the ACME server can fulfill in the final stage of the order process. They determine key properties such as the private key, 
applications and extensions. When a custom CSR is used as [source](/reference/plugins/source/csr), no CSR plugin can be chosen. 
The third party application that generated the custom CSR is expected to take care of the private key and extensions 
instead.

## Default
The default is an [RSA](/reference/plugins/csr/rsa) private key. This can be changed in [settings.json](/reference/settings).