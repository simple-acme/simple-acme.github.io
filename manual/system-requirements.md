---
---
# System requirements
## Windows
Officially, Microsoft only supports Windows Server 2012 and higher
for .NET 9.0, which this program builds and depends on. If you're stuck 
on an older version of Windows (sorry), consider running the latest 
version of simple-acme on a different machine and transfering the certificates 
over to the older machine using an installation script.

If you absolutely must run on the older machine, you can use an older
release of the software and accept all known bugs and limitations, because
they are not supported anymore.

- .NET8 (should work on Windows 2012): version [2.3.0.1826](https://github.com/simple-acme/simple-acme/releases/tag/v2.3.0.1826])
- .NET7 (should work on Windows 2012): version [2.2.9.1](https://github.com/win-acme/win-acme/releases/tag/v2.2.9.1701])
- .NET6 (should work on Windows 2012): version [2.1.23](https://github.com/win-acme/win-acme/releases/tag/v2.1.23.1315])
- .NET5 (should work on Windows 2008): version [2.1.20](https://github.com/win-acme/win-acme/releases/tag/v2.1.20])
- .NET4 (backup if above fails to run): version [2.0.12.1](https://github.com/win-acme/win-acme/releases/tag/v2.0.11.705)

### Startup problems
If simple-acme fails to start, you can try the following:
- You may need to install [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685)
- If you run into an error about `api-ms-win-crt-runtime-l1-1-0.dll` you may need [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows).
- If you run into an error about `hostfxr.dll` you may need [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot).
- If you run into an error like `Failure processing application bundle`, perhaps [this thread](https://github.com/win-acme/win-acme/issues/1632) might provide a solution.
- If the program doesn't seem to start but an error like `Microsoft.Windows.Apprep.ChxApp_cw5n1h2txyewy:App.AppXc99k5qnnsvxj5szemm7fp3g7y08we5vm.mca` appears in the Event Viewer [this thread](https://github.com/win-acme/win-acme/issues/1491) might provide a solution. 

### IIS limitations
Not all features of this program can work on older versions of IIS.

#### Server Name Indication
Server Name Indication (SNI) is supported from IIS 8.0 (Windows Server 2012) and above. This feature allows you to have multiple HTTPS certificates on the same IP address. Without it, you can only configure a single certificate per IP address. If you want to have SSL for multiple sites with multiple domains with IIS 7.5 or lower all bound to the same IP address your choices are to either create a single certificate for all sites, or to use a wildcard certificate.

#### Configuring the IP address
When simple-acme creates the binding for a new certificate, it will bind the wildcard (*) IP address by default. In other words, incoming connections on all network interfaces will handeled using the certificate. You can customize this with the `‑‑sslipaddress` switch from the command line, or manually after simple-acme created the binding. On renewal, the program will preserve whatever setting is configured in IIS.

#### Wildcard bindings
Wildcard bindings are only supported on IIS 10 (Windows Server 2016+). Wildcard 
certificates can be created with older versions of IIS but their bindings will have 
to be configured manually.

#### FTPS bindings
Updating FTPS binding is only supported for IIS 7.5 (Windows 2008 R2) and above.

## Linux
Support for Linux should be considered in beta and has so far only been tested on Ubuntu 24.04.