---
layout: plugin
plugin: 8f1da72e-f727-49f0-8546-ef69e5ecec32
arguments:
    - validationmode
settings:
    - Script.PowershellExecutablePath
    - Script.Timeout
    - Validation.DisableMultiThreading
compatibility: All platforms
examples:
    -
        name: Prepare script only
        cmd: ‑‑validationpreparescript c:\create.ps1 [‑‑validationpreparescriptarguments {args}]
    -
        name: Separate prepare and cleanup scripts
        cmd: ‑‑validationpreparescript c:\create.ps1 ‑‑validationcleanupscript c:\delete.ps1 [‑‑validationpreparescriptarguments {args}] [‑‑validationcleanupscriptarguments {args}]
    - 
        name: Combined script
        cmd: ‑‑validationscript c:\create-and-delete.ps1 [‑‑validationpreparescriptarguments {args}] [‑‑validationcleanupscriptarguments {args}]
---
Run an external script or program to prepare for the validation challenge. Use this option to create TXT records at DNS providers that are not supported by native plugins (yet?) or to handle HTTP challenges in unconventional ways (e.g. calling into some API, starting a custom web server, etc.)

## General 
A preparation script is always required to prepare for the challenge answer. Providing a cleanup script to undo any changes made by the former is optional. You may also point to a single script to handle both tasks using different arguments. 

## Challenge type selection
For backwards compatibility, the script default to handling DNS challenges. To switch to HTTP challenges, you must provide the argument `--validationmode http-01` in unattended mode. In interactive mode this will simply be question asked during the setup process.

## Argument customization
The plugin has some hard-coded default argument templates which can be overruled according to your needs and preferences. Depending on the chosen challenge type, simple-acme will replace certain pre-defined tokens in the argument template to derive the actual arguments that will be passed to the script, thus enabling dynamic arguments to be passed. For example if your script handles DNS challenges and needs arguments like: `‑‑host _acme-challenge.example.com ‑‑token DGyRejmCefe7v4NfDGDKfA` then the argument template provided to simple-acme should look like this: `‑‑host {RecordName} ‑‑token {Token}`

## DNS challenge arguments
For DNS challenges following replacements are made to the arguments:

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

Default for preparation: `create {Identifier} {RecordName} {Token}`

Default for cleanup: `delete {Identifier} {RecordName} {Token}`

## HTTP challenge arguments
For HTTP challenges following replacements are made to the arguments:

<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <thead>
            <tr><th>Value</th><th>Replaced with</th></tr>
        </thead>
        <tbody>
            <tr><td><code>{Identifier}</code></td><td>Identifier that is being validated, e.g. <code>sub.example.com</code></td></tr>
            <tr><td><code>{Path}</code></td><td>Relative URI that will be requested (e.g. <code>/.well-known/acme-challenge/2fsdf2</code>)</td></tr>
            <tr><td><code>{FileName}</code></td><td>Name of the file that will be requested, e.g. <code>2fsdf2</code></td></tr>
            <tr><td><code>{Token}</code></td><td>Expected response content</td></tr>
            <tr><td><code>{vault://json/mysecret}</code></td><td>Secret from the <a href="/manual/advanced-use/secret-management">secret vault</a></td></tr>
            </tbody></table></div>

Default for preparation: `prepare {Identifier} {Path} {Token}`

Default for cleanup: `cleanup {Identifier} {Path} {Token}`

## Parallelism
You can use `‑‑validationscriptparallelism` to specify if your script supports parallelism. You may use the following values:

<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <thead>
            <tr><th>Value</th><th>Meaning</th></tr>
        </thead>
        <tbody>
            <tr><td><code>0</code></td><td>Serial, default serial behaviour</td></tr>
            <tr><td><code>1</code></td><td>Allow multiple validations to be prepared at the same time. Only do this when you are sure multiple instances of "prepare" running at the same time will not interfere with eachother. Typically difficult to achieve and therefor not recommended.</td></tr>
            <tr><td><code>2</code></td><td>Allow multiple validations to run at the same time. This is possible in theory with every method, but you must be sure that your script is non-destructive, e.g. it should not overwrite pre-existing records or files, nor delete more than what is specifically asked for</td></tr>
            <tr><td><code>3</code></td><td>Combination of 1 and 2</td></tr>
            </tbody></table></div>

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>This only has any effect when <code>DisableParallelism</code> is set to <code>false</code></p>
    </div>
</div>

## Reference scripts
Some reference scripts are available on [GitHub](https://github.com/simple-acme/reference-scripts/tree/main/Validation), including ones for EasyDNS, ZoneEdit, deSEC and Windows DNS.

## External resources
A lot of good reference scripts are available from the 
[POSH-ACME](https://github.com/rmbolger/Posh-ACME/tree/master/Posh-ACME/DnsPlugins)
project. Note that these scripts are **not compatible** with simple-acme. You will have
to make changes (e.g. in terms of accepted parameters and such) in order to use them.