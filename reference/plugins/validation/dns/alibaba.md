---
---
# Alibaba Cloud / Aliyun 
Create the record at [Alibaba Cloud](https://www.alibabacloud.com/). This requires an API key.

[Download the plugin](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.aliyun.v{{ site.releasebuild }}.zip)

{% include plugin-seperate.md %}

## Unattended 
`‑‑validation aliyun ‑‑aliyunapiid xx ‑‑aliyunapisecret xx [‑‑aliyunserver xx]`

If `‑‑aliyunserver` is not specified then the default value is `dns.aliyuncs.com`, for more possible options see [this list](https://api.aliyun.com/product/Alidns).
