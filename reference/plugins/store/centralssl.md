---
layout: plugin
plugin: af1f77b6-4e7b-4f96-bba5-c2eeb4d0dd42                                  
---

Designed for the [Central Certificate Store](https://blogs.msdn.microsoft.com/kaushal/2012/10/11/central-certificate-store-ccs-with-iis-8-windows-server-2012/) 
introduced in Windows 2012. Creates a separate copy of the `.pfx` file for each hostname and places it in the path provided. Using this store also triggers any created or updated IIS bindings to get the `CentralSSL` flag enabled. 