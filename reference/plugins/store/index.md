---
settings:
    - Store.DefaultStore
arguments:
    - store
---
# Store plugins
Store plugins are responsible for storing issued certificates in their permanent 
location(s). The program will cache the certificate in a `.pfx` file in its cache 
but these files are protected by file system rights and random passwords to prevent 
local non-administrators from obtaining keys. Store plugins are responsible for 
making the certificates accessible to the application(s) that need them.

{% include plugin-list.html type='store' %}