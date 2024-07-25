---
settings:
    - Installation.DefaultInstallation
---
# Installation plugins
Installation plugins are responsible for making the necessary changes to your 
application(s) after successfully creating or renewing a certificate. Currently 
there are two of these plugins.

## Multiple
More than one plugin can run by choosing them in order of execution. In interactive 
mode you will be asked, for unattended mode you can provide a comma separated list, 
e.g. `--installation script,iis`

## Default
In interactive mode the default installation plugin is [IIS](/reference/plugins/installation/iis). 
This can be changed in [settings.json](/reference/settings).  

In unattended mode, using `--source iis` will also imply `--installation iis`, which
can be counter-acted by explicitly providing `--installation none`. When using another
source (e.g. `--source manual`), there is **no** default installation step, 
so `--installation iis` has to be explicitly provided in such cases. The default 
installation steps can be changed in [settings.json](/reference/settings).