---
layout: plugin
plugin: b7c331d4-d875-453e-b83a-2b537ca12535
compatibility: All platforms
---
Generates an order/certificate for each registerable domain found in the source. For example when there are five hosts in the source:

- sub.example.com
- another.sub.example.com
- sub.contoso.net
- *.contoso.net
- *.contoso.co.uk

Three certificates will be generated: 
- Certicate A for two `example.com` hosts, 
- Certicate B for two `contoso.net` hosts
- Certicate C for one `contoso.co.uk` host

Not compatible with the [custom CSR](/reference/plugins/source/csr) source.