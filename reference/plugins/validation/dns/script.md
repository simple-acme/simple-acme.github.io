---
layout: plugin
plugin: 8f1da72e-f727-49f0-8546-ef69e5ecec32
settings:
    - Script.PowershellExecutablePath
    - Script.Timeout
    - Validation.DisableMultiThreading
compatibility: All platforms
examples:
    -
        name: Create script only
        cmd: ‑‑dnscreatescript c:\create.ps1 [‑‑dnscreatescriptarguments {args}]
    -
        name: Separate create and delete scripts
        cmd: ‑‑dnscreatescript c:\create.ps1 ‑‑dnsdeletescript c:\delete.ps1 [‑‑dnscreatescriptarguments {args}] [‑‑dnsdeletescriptarguments {args}]
    - 
        name: Combined script
        cmd: ‑‑dnsscript c:\create-and-delete.ps1 [‑‑dnscreatescriptarguments {args}] [‑‑dnsdeletescriptarguments {args}]
---
Run an external script or program to create or update the validation records.

## Create
A script that creates a DNS TXT record at your provider must be provided. The argument template 
passed to the script will be `create {Identifier} {RecordName} {Token}` by default, with the following 
replacements made by simple-acme:

<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <thead>
            <tr><th>Value</th><th>Replaced with</th></tr>
        </thead>
        <tbody>
            <tr><td><code>{Identifier}</code></td><td>Host name that's being validated, e.g. <code>sub.example.com</code></td></tr>
            <tr><td><code>{RecordName}</code></td><td>Full name of the TXT record that will be queried, e.g. <code>_acme-challenge.sub.example.com</code></td></tr>
            <tr><td><code>{ZoneName}</code></td><td>Registerable domain, e.g. <code>example.com</code></td></tr>
            <tr><td><code>{NodeName}</code></td><td>Relative record name, e.g. <code>_acme-challenge.sub</code></td></tr>
            <tr><td><code>{Token}</code></td><td>Content of the TXT record, e.g. <code>DGyRejmCefe7v4NfDGDKfA</code></td></tr>
            <tr><td><code>{vault://json/mysecret}</code></td><td>Secret from the <a href="/manual/advanced-use/secret-management">secret vault</a></td></tr>
            </tbody></table></div>

The order and format of arguments may be customized by providing a diffent argument template. For example if your script needs arguments like: `‑‑host _acme-challenge.example.com ‑‑token DGyRejmCefe7v4NfDGDKfA` then the argument template string provided to simple-acme should look like this: `‑‑host {RecordName} ‑‑token {Token}`

## Delete
Optionally, another script may be provided to delete the record after validation. The arguments template for that
script is `delete {Identifier} {RecordName} {Token}` by default. The order and format of arguments may be 
customized by providing a diffent argument template, just like for the create script. 

## Combined
You can also choose to use the same script for create and delete, with each their own argument string.

## Parallelism
You can use `‑‑dnsscriptparallelism` to specify if your script supports parallelism. You may use the following values:

<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <thead>
            <tr><th>Value</th><th>Meaning</th></tr>
        </thead>
        <tbody>
            <tr><td>0</td><td>Serial, default serial behaviour</td></tr>
            <tr><td>1</td><td>Allow multiple new records to created as the same time. Only do this when you are sure multiple instances of "create" running at the same time will not interfere with eachother. Typically difficult to achieve and therefor not recommended.</td></tr>
            <tr><td>2</td><td>Allow multiple validations to run at the same time. This is possible in theory with any DNS provider, but you must be sure that your script is non-destructive, e.g. it should not overwrite pre-existing TXT records, nor delete more than the one specifically asked for</td></tr>
            <tr><td>3</td><td>Combination of 1 and 2</td></tr>
            </tbody></table></div>

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>This only has any effect when <code>DisableParallelism</code> is set to <code>false</code></p>
    </div>
</div>

## External esources
A lot of good reference scripts are available from the 
[POSH-ACME](https://github.com/rmbolger/Posh-ACME/tree/master/Posh-ACME/DnsPlugins)
project. Note that these scripts are **not compatible** with simple-acme. You will have
to make changes (e.g. in terms of accepted parameter and such) in order to use them.