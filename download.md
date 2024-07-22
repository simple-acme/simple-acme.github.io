---
---

# Downloads
Please check the [System Requirements](/manual/system-requirements) to see if your operating system is supported.

The current release on this page is **{{ site.releasename }}** (build {{ site.releasetag }}). Release notes and downloads for older versions can be obtained from [GitHub](https://github.com/simple-acme/simple-acme/releases/).

---

### Windows
##### Full
The full builds are larger (~35MB compressed) and support loading external plugins.
- [x64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-x64.pluggable.zip) - modern Intel/AMD platforms, most likely to work if you're unsure
- [x86](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-x86.pluggable.zip) - legacy 32 bit systems
- [ARM64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-arm64.pluggable.zip) - ARM based platforms

##### Trimmed
The trimmed builds are smaller (~10MB compressed) but don't support plugins.
- [x64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-x64.trimmed.zip) - modern Intel/AMD platforms, most likely to work if you're unsure
- [x86](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-x86.trimmed.zip) - legacy 32 bit systems
- [ARM64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.win-arm64.trimmed.zip) - ARM based platforms

---

### Linux
Support for Linux is in beta at the moment.
##### Full
The full builds are larger (~35MB compressed) and support loading external plugins.
- [x64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.linux-x64.pluggable.zip) - modern Intel/AMD platforms, most likely to work if you're unsure
- [ARM64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.linux-arm64.pluggable.zip) - ARM based platforms

##### Trimmed
The trimmed builds are smaller (~10MB compressed) but don't support plugins.
- [x64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.linux-x64.trimmed.zip) - modern Intel/AMD platforms, most likely to work if you're unsure
- [ARM64](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/simple-acme.v{{ site.releasebuild }}.linux-arm64.trimmed.zip) - ARM based platforms

---

## Plugins
Plugins only work with the full build of the program. It is recommended to upgrade plugins and the main program at the same time, though generally they are forwards and backwards compatible within a major release series (e.g. all 2.3.x builds).

### Store
- [Azure KeyVault](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.store.keyvault.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/store/keyvault))
- [UserStore](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.store.userstore.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/store/userstore))

### Validation
#### DNS
- [acme-dns](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.acme.v{{ site.releasebuild }}.zip) (built-in, [documentation](/reference/plugins/validation/dns/acme-dns))
- [Alibaba Cloud / Aliyun](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.aliyun.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/alibaba))
- [Azure DNS (Microsoft)](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.azure.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/azure))
- [Cloudflare](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.cloudflare.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/cloudflare))
- [DigitalOcean](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.digitalocean.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/digitalocean))
- [DNSEXIT](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.dnsexit.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/dnsexit))
- [DNS Made Easy](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.dnsmadeeasy.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/dnsmadeeasy))
- [Domainname.shop](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.domeneshop.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/domene))
- [DreamHost](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.dreamhost.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/dreamhost))
- [GoDaddy](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.godaddy.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/godaddy))
- [Google Cloud DNS](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.googledns.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/clouddns))
- [Hetzner](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.hetzner.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/hetzner))
- [InfoManiak](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.infomaniak.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/infomaniak))
- [Linode (Akamai)](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.linode.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/linode))
- [LuaDNS](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.luadns.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/lua))
- [NS1](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.ns1.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/ns1))
- [RFC2136](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.rfc2136.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/rfc2136))
- [Route53 (Amazon AWS)](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.route53.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/route53))
- [Simply.com](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.simply.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/simply))
- [Tencent Cloud](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.tencent.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/tencent))
- [TransIP](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.dns.transip.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/dns/transip))

#### HTTP
- [FTP(S)](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.http.ftp.v{{ site.releasebuild }}.zip) (built-in, [documentation](/reference/plugins/validation/http/ftps))
- [REST](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.http.rest.v{{ site.releasebuild }}.zip) ([documentation](/reference/plugins/validation/http/rest))
- [SFTP](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.http.sftp.v{{ site.releasebuild }}.zip) (built-in, [documentation](/reference/plugins/validation/http/sftp))
- [WebDav](https://github.com/simple-acme/simple-acme/releases/download/v{{ site.releasetag }}/plugin.validation.http.webdav.v{{ site.releasebuild }}.zip) (built-in, [documentation](/reference/plugins/validation/http/webdav))

