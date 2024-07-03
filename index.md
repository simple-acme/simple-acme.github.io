---
layout: home
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
	[PFX/PKCS12 files](/reference/plugins/store/pfxfile) or
	[Azure KeyVault](/reference/plugins/store/keyvault)
- Send notifications on success or failure.

# Compatibility
- Free initiatives like [Let's Encrypt](https://letsencrypt.org/) and [ZeroSSL](https://zerossl.com/).
- Commercial providers like [DigiCert](https://www.digicert.com/), [Sectigo](https://sectigo.com/) and [Buypass](https://www.buypass.com/).
- Private servers like [Smallstep](https://smallstep.com/product/) and [Keyfactor](https://www.keyfactor.com/).
- Implements ACMEv2 ([RFC8555](https://datatracker.ietf.org/doc/html/rfc8555)).
- Implements [ARI draft-4](https://datatracker.ietf.org/doc/draft-ietf-acme-ari/) for early renewal on server compromise.
- Implements dynamic DNS updates ([RFC2136](https://www.rfc-editor.org/rfc/rfc2136)).
- Supports DANE ([RFC6698](https://datatracker.ietf.org/doc/html/rfc6698)) through [re-use](/reference/plugins/csr/rsa) of keys. 
- Implements TLS-ALPN-01 validation ([RFC8737](https://datatracker.ietf.org/doc/html/rfc8737)).
- Supports [OCSP Must Staple](/reference/plugins/csr/rsa) extension ([RFC7633](https://datatracker.ietf.org/doc/html/rfc7633)).
- Support alternate chain selection.
- Runs on Windows 2012+ and Linux (beta).
- Runs on x86, x64 and ARM.

# Automation
- Completely unattended operation from the command line.
- `xcopy` installation and upgrade process.
- Available on NuGet.org as a dotnet tool.
- Secret management allowing central rotation of API keys (protected by Windows DPAPI). 
- Manipulate `.renewal.json` files to manage renewals outside of the tool.
- Write your own Powershell `.ps1` scripts to handle installation and validation.
- Build your own plugins with C#.