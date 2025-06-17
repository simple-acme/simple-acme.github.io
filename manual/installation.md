---
---
# Installation

## Manual
- [Download](/download) the latest version of the program from this website and unpack the contents of the `.zip` archive to a folder, for example `%programfiles%\simple-acme`.
- Run `wacs.exe` (or just `wacs` on Linux) as an administrator/superuser. While running under a privileged context is not required for *all* operations, it will be necessary to set up a scheduled task (or cronjob), manage IIS bindings and handle validation requests internally, i.e. the most common use cases.
- To update from a previous version, simply unpack the contents of the archive in the same folder, overwriting all files already there. 

## Chocolatey
There is an official [Chocolatey package](https://community.chocolatey.org/packages/simple-acme/) available, which can be installed using `choco install simple-acme` and upgraded to the latest version using `choco upgrade simple-acme`. Note that due to the manual moderation process in use by the Chocolatey community, these versions may sometimes be older than the ones published on this site.

## dotnet tool
This is an alternative method to install and update the program. This requires [.NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0) to be pre-installed on the system.
- Open a command prompt as an administrator (running for the local user only is not supported). 
- Run `dotnet tool install simple-acme ‑‑global`
- Run `wacs`
- To update from a previous version, run `dotnet tool update simple-acme ‑‑global`
