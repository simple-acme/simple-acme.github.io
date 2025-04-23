---
arguments:
    - renew
    - cancel
    - revoke
    - id
    - friendlyname
settings:
    - Client.ConfigurationPath
---
# Renewal management
 This program is primarily used to create certificates, but the nature of ACME encourages certificates to be 
replaced regularly. We call a sequence of certificates, created with specific settings, a **renewal**. It's the 
basic unit of work that you manage with the program.

## Creation
- Creating a renewal can be done interactively from the main menu. The option `N` uses the easiest defaults for 
IIS users and the option `M` offers full options, for example for Apache, Exchange, wildcard certificates, etc. 
- Any certificate that can be created from the main menu, can also be created from the 
[command line](/reference/cli). 
The command line even offers some options that the menu does not, check out the documentation 
about [plugins](/reference/plugins/) to read all about it.
- It's also possible to add `.renewal.json` files to the folder yourself, either manually or using some clever tooling or scripting, to create a lightly coupled integration between your own management tools and simple-acme.

## Modification
Many users mistakenly try to modify their renewal by issuing commands like `‑‑renew ‑‑webroot C:\NewRoot` 
hoping that the configured webroot for their renewal will be changed. The reason this doesn't work is 
because a renew cycle checks **all** renewals, each of which can use any of the hundreds of possible 
combinations of [plugins](/reference/plugins/), so it's complex to figure out what the 
true intention of such a command should be. Therefore, modification and renewal are completely separate
functions.

Editing a renewal can be done through interactive mode using the menu `Manage renewals`, by selecting the
renewal that you would like to modify and then choosing `Edit renewal`. At that point you can either
fully reconfigure it, or change a single stage/plugin.

From the command line you can modify a renewal by re-creating it. If it turns out that a newly configured 
certificate has the same friendly name as a previously created one, then the older settings will be 
overwritten. When this happens in interactive mode the user is asked to confirm this, but in unattended 
mode the script or program calling simple-acme is assumed to know the consequences of its actions. If you
actually intend to create two very similar certificates, add the `‑‑id` parameter to make them unique 
and prevent overwrites based on the friendly name.

You can also edit the `.renewal.json` file using any text editor.

## Deleting/cancelling
To cancel a renewal means that the certificate will not be renewed anymore. The certificate, bindings 
and other configuration that is already in place will **not** be touched, so it's completely safe to do
this without disturbing your production applications. Only you will have to set up a new renewal or 
alternative certificate solution before the certificate reaches its natural expiration date. 
- You can cancel a renewal from the main menu. The program will then delete the `.renewal.json` file from 
disk and forget about it.
- You can cancel from the command line using the argument `‑‑cancel`. 
The effects are the same as above.
- You can delete the `.renewal.json` file yourself. The effects are the same as above.

## Revocation
Certificates can be revoked from the main menu with `Manage renewals` > `Revoke certificate`. You can also do it from the command line using the argument `‑‑revoke`.

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>Certificate should only be revoked when the private key is believed to have been compromised, not when simply replacing or cancelling it.</p>
    </div>
</div>

## Internals
Renewals are stored in the program's configuration path. Each file that fits the pattern `*.renewal.json` is considered to be a renewal. The files are randomly named by the program, but you are free to rename them if that suits you. The only requirement is that they must be unique, which is enforced by checking that the `"Id"` field in the JSON must match with the name of file. You can specify your own identifier at creation time with the `‑‑id` switch.

There is [JSON schema](/schema/renewal.json) published for the renewal files that helps guide users of supporting tools like Visual Studio Code in making modifications manually. Each file has three parts:
- Metadata, e.g. it's identifier, friendly name and the encrypted version of the password that is used for the cached `.pfx` archive.
- Plugin configuration, e.g. everything that the [plugins](/reference/plugins/) need to know 
to do their jobs, according to the command line arguments and menu choices that were given at creation time.
- History, i.e. a record of each successful and failed attempt to get a certificate based on the file.
