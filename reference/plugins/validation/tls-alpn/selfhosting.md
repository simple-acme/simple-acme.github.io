---
layout: plugin
plugin_type: validation
plugin_subtype: tls-alpn
plugin: selfhosting
---
This plugin launches a temporary built-in TCP listener that stores the validation details in memory. This requires exclusive access to the port, so it cannot be used while another application is handling connections.

## Non-default port
Even though the ACME server will always open the validation connection on port 443, you may forward that to another port within your internal 
infrastructure. Using the command line you can tell the plugin to listen to a specific port.
