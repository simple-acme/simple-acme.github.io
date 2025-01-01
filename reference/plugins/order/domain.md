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
- Certificate A for two `example.com` hosts, 
- Certificate B for two `contoso.net` hosts
- Certificate C for one `contoso.co.uk` host

Not compatible with the [custom CSR](/reference/plugins/source/csr) source.
