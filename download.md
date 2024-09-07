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
{% include plugin-download.html type='store' %}

### Validation
#### DNS
{% include plugin-download.html type='validation.dns' %}

#### HTTP
{% include plugin-download.html type='validation.http' %}

