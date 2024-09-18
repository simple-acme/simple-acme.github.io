---
arguments:
    - source
    - order
    - csr
    - validation
    - store
    - installation
settings:
    - Source.DefaultSource
    - Order.DefaultOrder
    - Csr.DefaultCsr
    - Validation.DefaultValidation
    - Store.DefaultStore
    - Installation.DefaultInstallation
---
# Plugins

Conceptually simple-acme works by chaining together five components also known as plugins, which can be 
mixed and matched to support many use cases. Using the "default settings" mode of the UI, the default 
for each plugin will be chosen for you. These defaults can be changed in [settings.json](/reference/settings). 

In "full options" mode, you will be asked to pick each of these plugins. 

From the command line you can also rely on the configured defaults or explicitly provide which 
one(s) you want. Check the [command line reference](/reference/cli) to see how.

- A [source plugin](/reference/plugins/source/) determines which domains to include in the renewal.
- An [order plugin](/reference/plugins/order/) divides these domains over one or more certificates to be ordered.
- A [CSR plugin](/reference/plugins/csr/) determines the (type of) private key and extensions to use for the certificate(s).
- A [validation plugin](/reference/plugins/validation/) provides the ACME server with proof that you own the domain(s).
- One or more [store plugins](/reference/plugins/store/) place the certificate(s) in a specific location and format.
- One or more [installation plugins](/reference/plugins/installation/) make changes to your application(s) configuration.

There are two other types of plugins that may be interesting to developers of custom solutions:

- A [notification](/manual/notifications) target can be used to send success or error messages to your favorite channel, instead of (or in addition to) the built in emails.
- A [secret store](/manual/advanced-use/secret-management) can be used to get and set secrets like passwords and API keys from your favorite management tool, instead of (or in addition to) the built in encrypted JSON file.

Currently there are no alternative implementations for these last two interfaces available as part of this project, but we welcome contributions in these areas.

## Pluggable vs. Trimmed releases

A lot of plugins are built-in, but some plugins are distributed as optional extra downloads. 
When using one of the extra downloads, it's required to use the "pluggable" releases of the 
main program. Otherwise you may use the "trimmed" releases to save disk space and network bandwidth.