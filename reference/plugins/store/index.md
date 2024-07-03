---
---
# Store plugins
Store plugins are responsible for storing issued certificates in their permanent 
location(s). The program will cache the certificate in a `.pfx` file in its 
CertificatePath (which defaults to `%programdata%\win-acme\$baseuri$\certificates`) but 
these files are protected by random passwords to prevent local non-administrators 
from obtaining keys. Store plugins are responsible for making the certificates 
accessible to the application(s) that need them.

## Multiple
More than one plugin can run by choosing them in order of execution. In interactive 
mode you will be asked, for unattended mode you can provide a comma separated list, 
e.g. `--store certificatestore,pemfiles`

## Default
The default is the [Windows Certificate Store](/reference/plugins/store/certificatestore).
This can be changed in [settings.json](/reference/settings).

## None
To instruct the program not to use any store, for example when your installation 
script handles it, you may specify `--store none`. 