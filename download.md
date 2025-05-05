---
---

# Downloads
Please check the [System Requirements](/manual/system-requirements) to see if your operating system is supported.

The current release on this page is **{{ site.data.build.releasename }}** (build {{ site.data.build.releasebuild }} / commit [{{ site.data.build.commit }}](https://github.com/simple-acme/simple-acme/tree/{{ site.data.build.commit }})). Release notes and downloads for older versions can be obtained from [GitHub](https://github.com/simple-acme/simple-acme/releases/). After downloading you can confirm integrity using the Powershell command `Get-FileHash` or the `sha265sum` command in Linux. All binaries except for the Linux executables are kindly signed by the [SignPath Foundation](https://signpath.org/). The "Product version" field in the file details should always reflect the build number and commit mentioned here.

---

### Windows

##### Full
The full builds are larger and support loading external plugins.
{% include downloads.html os='win' type='pluggable' %}


##### Trimmed
The trimmed builds are smaller but don't support plugins.
{% include downloads.html os='win' type='trimmed' %}

---

### Linux
Support for Linux is in beta at the moment.
##### Full
The full builds are larger and support loading external plugins.
{% include downloads.html os='linux' type='pluggable' %}


##### Trimmed
The trimmed builds are smaller but don't support plugins.
{% include downloads.html os='linux' type='trimmed' %}

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
