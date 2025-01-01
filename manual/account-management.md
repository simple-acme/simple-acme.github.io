---
settings:
    - Acme.DefaultBaseUri
arguments:
    - accepttos
    - emailaddress
    - eab-key-identifier
    - eab-key
    - eab-algorithm
    - account
    - baseuri
    - register
---
# Account management
To use an ACME server, you need to create an account first. There are two types of accounts: (semi)anonymous ones that can be created by anyone at any time, or so called "externally bound" accounts, that typically require you to sign up for a service through a manual process before being allowed to use the ACME endpoint. The latter is a more common progress for commercial services that need payment information.

## Creating an account
The client automatically initiates the account creation progress when you create your first certificate with a specific server. If you want to create an account without also creating a certificate, you can do so from the interactive menu or through the command line.

### Anonymous account
To create an anonymous account you will typically only be asked to agree with some terms of service. The standard dictates that clients cannot automatically agree on behalf of their users, so simple-acme will download these to your disk and offer you a yes/no question to confirm. Alternatively, you can provide an additional command line switch the first time you're using a specific server to agree. Also, the server will ask you for an email address to be able to send you notifications about any potential issues. Note that this is entirely separate from the [notifications](/manual/notifications) sent by the client. The "More options" menu contains an option to update your contact information later on.

Example: `--accepttos --emailaddress acme@example.com`

### Externally bound account
To link to an external account, you will be asked for an EAB key identifier and the corresponding EAB key. The client will ask for this in interactive mode, but you can also specify them on the command line. You don't need to agree with terms or service or provide any other information, because the server will already have all of this from you. As the program is configured to use Let's Encrypt by default, you should either update this in `settings.json` or provide the `--baseuri` parameter on the command line as well.

Example: `[--baseuri https://commercialca.com/acme/] --eab-key-identifier mykey --eab-key *****`

## Multiple accounts
The program supports using multiple accounts per server, should you need it. This feature is only available from the command line, but it allows different renewals to use different accounts with the same server.

## Deleting accounts
There's no built-in function to delete an account, but it can be done by navigating to the configuration path and deleting the files `Registration_v2` and `Signer_v2` from disk. This won't affect any renewals or certificates: a new account can simply be created instead.
