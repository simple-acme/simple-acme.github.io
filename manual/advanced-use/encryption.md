---
settings:
    - Security.EncryptConfig
---
# Encryption
The program uses Microsoft Data Protection API to add a layer of security to sensitive information that is stored in the `ConfigPath`. Encryption is turned on by default, but may be turned off at will, for example when you want to [migrate](/manual/migration) to another machine or want to [load balance](/manual/advanced-use/load-balancing).

## Encryping or decrypting the files
Save the desired encryption setting in [settings.json](/reference/settings).

- In the main menu pick `More options...` > `Encrypt/decrypt configuration`

Or 

- Run `wacs.exe ‑‑encrypt`