---
layout: plugin
plugin: 7e191d0e-30d1-47b3-ae2e-442499d33e16
settings:
    - Validation.CleanupFolders
compatibility: All platforms
examples:
    -
        name: Typical
        cmd: '‑‑webroot webdav://example.com/path/ ‑‑username simple-acme ‑‑password *****'
---
This plugin pushes the validation challenge to a WebDav path.

{% include validation-http-common.md %}