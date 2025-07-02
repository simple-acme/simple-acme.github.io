---
layout: home
sidebar: home
---
# Features
- A simple text menu to get **free certificates from Let's Encrypt into IIS**.
- An advanced menu with options for many other use cases, including [Apache](/manual/advanced-use/examples/apache) and [Exchange](/manual/advanced-use/examples/exchange).
- Creates a scheduled task or cronjob to **automatically renew** when needed. 
- Supports wildcards (`*.example.com`) and international domains names (`证书.example.com`).
- Supports up to 4096 bit RSA keys, [Elliptic Curve](/reference/plugins/csr/ec) crypto (ECC) or bring-your-own-[CSR](/reference/plugins/source/csr).
- Handle HTTP challenges from a virtual or local folder, network share, [SFTP](/reference/plugins/validation/http/sftp), [FTPS](/reference/plugins/validation/http/ftps), [WebDav](/reference/plugins/validation/http/ftps) or [REST](/reference/plugins/validation/http/rest).
- Handle DNS challenges with **20+ plugins** for cloud providers, [acme-dns](/reference/plugins/validation/dns/acme-dns) or your own scripts.
- Store certificates in the 
	[Windows Store](/reference/plugins/store/certificatestore), 
	[IIS CCS](/reference/plugins/store/centralssl), 
	[PEM files](/reference/plugins/store/pemfiles), 
	[PFX/PKCS12 files](/reference/plugins/store/pfxfile),
	[P7B file](/reference/plugins/store/p7bfile) or 
	[Azure KeyVault](/reference/plugins/store/keyvault)
- Send notifications on success and/or failure.