---
layout: plugin
plugin: c7d5e050-9363-4ba1-b3a8-931b31c618b7
menu: Self-hosting
settings:
    - Execution.DefaultPreExecutionScript
    - Execution.DefaultPostExecutionScript
compatibility: All platforms
examples:
    -
        name: Typical
        cmd: '[‑‑validationport 8080] [‑‑validationprotocol https]'
---
This plugin launches a temporary built-in web listener that stores the validation 
response in memory. It can share port 80 with IIS and other (Microsoft) software 
so this doesn't interfere with regular traffic. Not all software supports this 
port sharing feature though. If you get errors telling you that the listener 
cannot be started, try to (temporarely) shut down other processes using the 
port, or look for another validation method.

## Non-default port
Even though Let's Encrypt will always send validation requests to port 80, 
you may internally proxy, NAT or redirect that to another port. Using the command 
line switch you can tell the plugin to listen to a specific port.

## Firewall exemption
Obviously, whichever port is used will have to be accessible from outside, meaning
your firewall(s) will have to permit access. Unfortunately due to the use of the
port sharing mechanism, it's not possible to configure the Windows Firewall with
a rule for a specific application (i.e. `wacs.exe`), so you will have to open the 
port to `System`. If you feel that is too generous, you could automate enabling/
disabling this rule by running a script before and after the validation starts, 
using the settings described below.

## User access
By default only adminstrators are allowed to create these kinds of listeners. On Windows
you can allow regular users to also do this by running 
`netsh http add urlacl url=http://+:80/.well-known/acme-challenge/ user=myuser`

## Errors
If the handler is unable to start you may first try to test which process is using
the port using Powershell `Get-Process -Id (Get-NetTCPConnection -LocalPort 80).OwningProcess`.
It's also possible that some software has blocked access, which can be diagnosed using 
the command `netsh http show urlacl`.