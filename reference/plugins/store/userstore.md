---
layout: plugin
plugin: 95ee94e7-c8e2-40e6-a26f-c9fc3afa9fa5
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '[‑‑keepexisting]' 
---
Like the built-in [certificate store](/reference/plugins/store/certificatestore) plugin, 
this one places the certificate in the Windows Certificate Store. However, instead of 
using the `LocalSystem` location, it employes the `CurrentUser` location. This means the certificate will only be available to whichever user is running the simple-acme executable. The advantage of this is that you don't need administrator rights to be able to use this plugin, as is required for the built-in one.

The disadvantage is that you will need to carefully manage which user(s) run the program, both
initially and for future renewals. When running the scheduled task as `SYSTEM` (which is the 
default) this plugin will refuse to run, because it will most likely be a mistake to do so.