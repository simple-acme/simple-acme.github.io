---
settings:
- Secrets.Json.FilePath
- Secrets.Script.Get
- Secrets.Script.GetArguments
---
# Secrets

Some plugins require authentication information such as a password or API key to be able to work, e.g. to login to an FTP server or an API key needed to update a DNS record. These secrets are historically saved in [encrypted](/manual/advanced-use/encryption) form in the [.renewal.json](/manual/advanced-use/renewal-management) files in the configuration folder.

There are also some global secrets, like the proxy server password and the SMTP server password, that are stored in [settings.json](/reference/settings).

## Central Management

Version 2.1.17 introduced the secret manager to make it easier to re-use and manage
secrets for renewals. Also, it makes it possible to protect those aforementioned global 
secrets. The secret manager can be accessed from the main menu by going to 
`More options...` > `Manage secrets`. There you will be presented with a list of currently 
known secrets (if any) to update/delete them, and an option to add a new one. Each secret 
has a unique URI like `vault://json/mysecret` which you can use in various places like 
configuration files, command line arguments or script installation parameters.

## Multiple backends

Currently, there are three backends for the secret manager shipped with the program:

- `json` works with an encrypted file in the configuration folder. It does not offer additional security over normal way of storing secrets, but makes them more convenient to manage. The location of that file may be modified through [settings.json](/reference/settings), for example if you want to share it between different ACME endpoints. 
- `script` calls a script configurable in `settings.json` to retrieve a secret and is intended as a bridge to connect to third party secret management solutions that do not have native plugin available (yet). This is a read-only vault.
- `environment` vault looks at environment variables and is intended for servers that are under configuration management. This is a read-only vault.

In the future the idea is to support more backends like Azure KeyVault and HashiCorp. Implementation of a new backend is fairly straightforward for 
someone with C# experience, it just requires an assembly that implements [ISecretProvider](https://github.com/simple-acme/simple-acme/blob/main/src/main.lib/Services/Interfaces/ISecretService.cs). Contributions in this area are most welcome!
