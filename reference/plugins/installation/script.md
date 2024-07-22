---
title: Script
layout: plugin
plugin_type: installation
plugin_name: script
compatibility: Windows, Linux
id: 3bb22c70-358d-4251-86bd-11858363d913
arguments:
    - 
        name: --script
        desc: Path to script file to run after retrieving the certificate. This may be an executable file or a Powershell (.ps1) script.
    -
        name: --scriptparameters
        desc: Parameters for the script to run after retrieving the certificate.    
examples:
    - 
        name: Full
        cmd: '--script C:\script.bat [--scriptparameters x]'
 
---

Runs an external script or executable after a succesful renewal. This may be a `.bat` or `.exe` on Windows, `.sh` on Linux or `.ps1` on all platforms. You provide the program with the path to the script and it will run automatically.

### Parameter replacement
The following variables can be provided from the program to the script as command line arguments.

| Value          |  Replaced with |
|----------------|----------------|
| `{0}` or `{CertCommonName}` | Common name (primary domain name) of the newly issued certificate          |
| `{1}` or `{CachePassword}` | The `.pfx` password (generated randomly for each renewal)  |
| `{2}` or `{CacheFile}`       | Full path of the cached `.pfx` file (*)                                 |
| `{6}` or `{CacheFolder}`       | Directory containing the cached `.pfx` file (*)                                 |
| `{4}` or `{CertFriendlyName}`       |  Friendly name of the newly issued certificate                               |
| `{5}` or `{CertThumbprint}`      | Thumbprint of the newly issued certificate                             |
| `{7}` or `{RenewalId}`       | Id of the renewal                                    |
| `{3}` or `{StorePath}`      | Path or store name used by the (first) store plugin   |
| `{StoreType}`        |  Name of the (first) store plugin (e.g. CentralSsl or PemFiles)                                    |
| `{OldCertCommonName}`        |  Common name (primary domain name) of the previously issued certificate |
| `{OldCertFriendlyName}`        |  Friendly name of the previously issued certificate |
| `{OldCertThumbprint}`        |  Thumbprint of the previously issued certificate |
| `{vault://json/mysecret}`        |  Secret from the [vault](https://www.simple-acme.com/manual/advanced-use/secret-management) |


*) Will be empty if cache is disabled

### Example
If you need your scripts parameters to look something like this:

`action=import file=C:\mydomain.pfx password=*****`

Then your argument string should look like this:

`action=import file={CacheFile} password={CachePassword}`

### Parameter escaping
If you need to put double quotes around your parameters from the command line, you have to escape them with a slash, for example:

`--scriptparameters "action=import file=\"{CacheFile}\" password=\"{CachePassword}\""`

For **Powershell** scripts, string parameters can also be delimited with single quotes, for example:

`--scriptparameters "action=import file='{CacheFile}' password='{CachePassword}'"`