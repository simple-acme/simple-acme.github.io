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

{% include validation-http-common.md %}