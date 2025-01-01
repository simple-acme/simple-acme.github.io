---
layout: plugin
plugin: 3bb22c70-358d-4251-86bd-11858363d913
settings:
    - Script.PowershellExecutablePath
    - Script.Timeout
compatibility: All platforms
examples:
    - 
        name: Typical
        cmd: '‑‑script C:\script.bat [‑‑scriptparameters x]'
---

Runs an external script or executable after a successful renewal. This may be a `.bat` or `.exe` on Windows, `.sh` on Linux or `.ps1` on all platforms. You provide the program with the path to the script and it will run automatically.

## Example scripts
Many examples of `.ps1` scripts are included with the program in the `Scripts` folder included in the main distribution package, for example for Exchange, RDS and SQL Server. Please use these as a reference only.

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>Example scripts have been tested by their authors, but as always you should exercise <strong>extreme caution</strong> when running something that you find on the internet, because every environment is different. You may have a different system design or software versions, so always test thoroughly and create your own local copy to prevent future versions of the example from causing issues.</p>
    </div>
</div>

## Parameter replacement
The following variables can be provided from the program to the script as command line arguments.

<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <thead>
            <tr><th>Value</th><th>Replaced with</th></tr>
        </thead>
        <tbody>
            <tr><td><code>{0}</code> or <code>{CertCommonName}</code></td><td>Common name (primary domain name) of the newly issued certificate</td></tr>
            <tr><td><code>{1}</code> or <code>{CachePassword}</code></td><td>The <code>.pfx</code> password (generated randomly for each renewal)</td></tr>
            <tr><td><code>{2}</code> or <code>{CacheFile}</code></td><td>Full path of the cached <code>.pfx</code> file (*)</td></tr>
            <tr><td><code>{6}</code> or <code>{CacheFolder}</code></td><td>Directory containing the cached <code>.pfx</code> file (*)</td></tr>
            <tr><td><code>{4}</code> or <code>{CertFriendlyName}</code></td><td>Friendly name of the newly issued certificate</td></tr>
            <tr><td><code>{5}</code> or <code>{CertThumbprint}</code></td><td>Thumbprint of the newly issued certificate</td></tr>
            <tr><td><code>{7}</code> or <code>{RenewalId}</code></td><td>Id of the renewal i.e. <code>xxx</code> when renewing <code>xxx.renewal.json</code></td></tr>
            <tr><td><code>{3}</code> or <code>{StorePath}</code></td><td>Path or store name used by the (first) store plugin</td></tr>
            <tr><td><code>{StoreType}</code></td><td>Name of the (first) store plugin (e.g. <code>CentralSsl</code> or <code>PemFiles</code>)</td></tr>
            <tr><td><code>{OldCertCommonName}</code></td><td>Common name (primary domain name) of the previously issued certificate</td></tr>
            <tr><td><code>{OldCertFriendlyName}</code></td><td>Common name (primary domain name) of the previously issued certificate</td></tr>
            <tr><td><code>{OldCertThumbprint}</code></td><td>Common name (primary domain name) of the previously issued certificate</td></tr>
            <tr><td><code>{vault://json/mysecret}</code></td><td>Secret from the <a href="/manual/advanced-use/secret-management">secret vault</a></td></tr></tbody></table></div>
(*) This parameter will be empty if cache is disabled

#### Replacement example
If you need your scripts parameters to look something like this: `action=import file=C:\mydomain.pfx password=*****` Then your argument string should look like this: `action=import file={CacheFile} password={CachePassword}`

#### Parameter escaping
If you need to put double quotes around your parameters from the command line, you have to escape them with a slash, for example:

`‑‑scriptparameters "action=import file=\"{CacheFile}\" password=\"{CachePassword}\""`

For **Powershell** scripts, string parameters can also be delimited with single quotes, for example:

`‑‑scriptparameters "action=import file='{CacheFile}' password='{CachePassword}'"`
