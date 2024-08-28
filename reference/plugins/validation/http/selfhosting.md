---
layout: plugin
plugin_type: validation
plugin_subtype: http
plugin: selfhosting
---
# Self-hosting
This plugin launches a temporary built-in web listener that stores the validation 
response in memory. It can share port 80 with IIS and other (Microsoft) software 
so this doesn't interfere with regular traffic. Not all software supports this 
port sharing feature though. If you get errors telling you that the listener 
cannot be started, try to (temporarely) shut down other processes  using the 
port, or look for another validation method.

## Non-default port
Even though Let's Encrypt will always send validation requests to port 80, 
you may internally proxy, NAT or redirect that to another port. Using the 
`‑‑validationport` switch you can tell the plugin to listen to a specific port.

## Firewall exemption
Obviously, whichever port is used will have to be accessible from outside, meaning
your firewall(s) will have to permit access. Unfortunately due to the use of the
port sharing mechanism, it's not possible to configure the Windows Firewall with
a rule for a specific application (i.e. `wacs.exe`), so you will have to open the 
port to `System`. If you feel that is too generous, you could automate enabling/
disabling this rule by running a script before and after `wacs.exe`. Make sure to
also add that script as steps in the scheduled task.

## Errors
If the handler is unable to start you may first try to test which process is using
the port using Powershell `Get-Process -Id (Get-NetTCPConnection -LocalPort 80).OwningProcess`.
It's also possible that some software has blocked access, which can be diagnosed using 
the command `netsh http show urlacl`.

## Unattended 
`[‑‑validation selfhosting] [‑‑validationport 8080]`