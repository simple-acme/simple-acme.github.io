---
layout: plugin
plugin: bc27d719-dcf2-41ff-bf08-54db7ea49c48
menu: FTP(S)
settings:
   - Validation.CleanupFolders
   - Validation.Ftp.UseGnuTls 
compatibility: All platforms
examples:
   -
      name: Typical
      cmd: ‑‑webroot ftps://ftp.example.com:990/path/ ‑‑username simpleacme ‑‑password *****
---
This plugin uploads the validation challenge to a (secure) FTP server.

{% include validation-http-common.md %}

## Microsoft TLS vs. GnuTLS
If you experience connection issues when running simple-acme on Windows while connecting to a Unix FTPS server, using the GnuTLS library
instead of Microsofts native TLS might solve the problem. [This page](https://github.com/robinrodricks/FluentFTP/wiki/FTPS-Connection-using-GnuTLS) 
by the FluentFTP project explains the reasons behind and limitations of this method.

Using this requires:
   - A change in `settings.config`, `Validation.Ftp.UseGnuTls` should be set to `true`.
   - The pluggable **x64** release of simple-acme (it is not available for x86 or ARM due to limitations of the upstream package, and also doesn't work on the trimmed build) 
   - Download and extract the additonal build artifact <a href="https://github.com/simple-acme/simple-acme/releases/download/{{ site.data.build.releasetag }}/gnutls.v{{ site.data.build.releasebuild }}.x64.zip">gnutls.v{{ site.data.build.releasebuild }}.x64.zip</a> for the current release (or find older versions on GitHub).