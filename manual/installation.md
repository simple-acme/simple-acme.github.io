---
---
# Installation

## Manual
- [Download](/download) the latest version of the program from this website and unpack the contents of the `.zip` archive to a folder, for example `%programfiles%\simple-acme`.
- Run `wacs.exe` (or just `wacs` on Linux) as an administrator/superuser. While running under a priviledged context is not required for *all* operations, it will be necessary to set up a scheduled task (or cronjob), manage IIS bindings and handle validation requests internally, i.e. the most common use cases.
- To update from a previous version, simply unpack the contents of the archive in the same folder, overwriting all files already there. 

## dotnet
This is an alternative method to install and update the program. While more convenient than a manual installation, it has two downsides. First it requires [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) to be pre-installed on the system and second it makes installing [plugins](/reference/plugins/) more cumbersome.
- Open a command prompt as an administrator (running for the local user only is not supported). 
- Run `dotnet tool install simple-acme ‑‑global`
- Run `wacs`
- To update from a previous version, run `dotnet tool update simple-acme ‑‑global`