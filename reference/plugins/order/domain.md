---
title: Domain
layout: plugin
plugin_type: order
plugin_name: domain
compatibility: Windows, Linux
id: b7c331d4-d875-453e-b83a-2b537ca12535
---
Generates an order/certificate for each registerable domain found in the source. 
For example when there are five hosts in the source:

- sub.example.com
- another.sub.example.com
- sub.contoso.net
- *.contoso.net
- *.contoso.co.uk

Three certificates will be generated: one for all `example.com` bindings, one for `contoso.net` bindings and one for `contoso.co.uk` bindings.

Not compatible with the [custom CSR](/reference/plugins/source/csr) source.