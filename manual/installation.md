---
---
# Installation
There are five methods to obtain the program.

## WinGet
There is an official [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/) package available. 
- Run `winget install simple-acme` to install the latest version
- Run `winget upgrade simple-acme` to upgrade to the latest version
- Run `winget show simple-acme --versions` to list all available versions
- Run `winget install simple-acme --version 2.3.5.2195` to install a specific version
  
Note that WinGet is only available on Windows 10 version 1809 and later or on Windows Server 2025 or later.

## Manual
Manual downloads hosted at GitHub and linked on this website on the [download page](/download) unpack the contents of the `.zip` archive to a folder, for example `%programfiles%\simple-acme`. The website lists SHA256 hashes for manual integrity validation. If you need an older release, go to the [release page](https://github.com/simple-acme/simple-acme/releases) on GitHub and you'll find it there.

To update from a previous version, simply unpack the contents of the archive to the same folder as the previous version, overwriting all files already there. Settings and renewals will be preserved!

## Chocolatey
There is an official [Chocolatey package](https://community.chocolatey.org/packages/simple-acme/) available.
- Install [Chocolatey](https://chocolatey.org/)
- Run `choco install simple-acme` to install the program
- Run `choco upgrade simple-acme` to upgrade to the latest version
- Run `choco search --exact simple-acme --all` to list available versions
- Run `choco install simple-acme --version 2.3.5` to install a specific version

Note that due to the manual moderation process in use by the Chocolatey community, there may be couple of days delay.

## dotnet tool
There is an official [NuGet package](https://www.nuget.org/packages/simple-acme) available which can be used as a [.NET tool](https://learn.microsoft.com/en-us/dotnet/core/tools/global-tools). 
- Install [.NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0) on the system.
- Run `dotnet tool install simple-acme --global` to install the program
- Run `dotnet tool update simple-acme --global` to upgrade to the latest version
- Run `dotnet package search simple-acme --exact-match` to list available versions
- Run `dotnet tool install simple-acme --global --version 2.3.5.2195` to install a specific version

## Build it yourself!
You can clone the repo using `git clone https://github.com/simple-acme/simple-acme` and create your own build using the script `.\build\appveyor-local.ps1`. This requires at least [git](https://git-scm.com/) and the [.NET 9.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/9.0).

# Starting
Run `wacs.exe` (or just `wacs` on Linux) as an administrator/superuser. While running under a privileged context is not required for *all* operations, it will be necessary to set up a scheduled task (or cronjob), manage IIS bindings and handle validation requests internally, i.e. the most common use cases.
