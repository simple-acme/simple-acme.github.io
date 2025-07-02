---
layout: plugin
plugin: 1c77b3a4-5310-4c46-92c6-00d866e84d6b
settings:
    - Validation.CleanupFolders
compatibility: All platforms
examples:
    -
        name: Path from IIS
        cmd: '‑‑validationsiteid 1'
    -
        name: Manual path
        cmd: '‑‑webroot c:\httpdocs\'
---
This plugin saves the validation challenge to a local or network path.

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>If you plan to use this plugin to serve files via <strong>IIS</strong>, consider using the default <a href="/reference/plugins/validation/http/selfhosting">self-hosting</a> instead, as self-hosting avoids many <a href="/manual/iis-configuration">configuration issues</a> that you might run into before IIS will properly serve validation files.</p>
    </div>
</div>

{% include validation-http-common.md %}