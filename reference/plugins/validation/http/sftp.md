---
layout: plugin
plugin: 048aa2e7-2bce-4d3e-b731-6e0ed8b8170d
settings:
    - Validation.CleanupFolders
compatibility: All platforms
examples:
    -
        name: Typical
        cmd: '‑‑webroot sftp://example.com/path/ ‑‑username simple-acme ‑‑password *****'
---
This plugin uploads the validation challenge via SSH-FTP, also known as SFTP.

{% include validation-http-common.md %}