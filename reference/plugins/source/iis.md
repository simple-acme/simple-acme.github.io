---
layout: plugin
plugin_type: source
plugin: iis
compatibility: Windows (admin only)
examples:
    - 
        name: Single binding
        cmd: '‑‑host example.com [‑‑siteid 1]'
    - 
        name: Multiple bindings
        cmd: '‑‑host example.com,www.example.com [‑‑siteid 1,2,3] [‑‑commonname common.example.com]'
    - 
        name: All bindings of a site
        cmd: '‑‑siteid 1 [‑‑commonname common.example.com] [‑‑excludebindings exclude.example.com]'
    - 
        name: All bindings of multiple sites
        cmd: '‑‑siteid 1,2,3 [‑‑commonname common.example.com] [‑‑excludebindings exclude.example.com]'
    - 
        name: All bindings of all sites
        cmd: '‑‑siteid s [‑‑commonname common.example.com] [‑‑excludebindings exclude.example.com]'
    - 
        name: Binding pattern
        cmd: '‑‑host-pattern *.example.??? [‑‑siteid 1,2,3] [‑‑commonname common.example.com] [‑‑excludebindings exclude.example.com]'
    - 
        name: Binging regex
        cmd: '‑‑host-regex [a-z]{3}\.example(\.com|\.net) [‑‑siteid 1,2,3] [‑‑commonname common.example.com] [‑‑excludebindings exclude.example.com]'                                                    
---

Create source based on bindings configured in IIS. 
- Automatically updates webroot path (useful for [FileSystem validation](/reference/plugins/validation/http/filesystem))

# Filtering bindings
While it's possible to create a certificate for all bindings in all sites, typically you will want to select some 
specific bindings to create a certificate for. There are several filters available, that in some cases can also be
combined with eachother.

## Site filters
You can choose to limit the certificate to specific websites by specifying a site identifier, or a comma separated list 
of them. The magic value `s` will dynamically include all current and future websites created on the server. To also include FTP 
sites, set `‑‑host-type` to `http,ftp`

## Binding filters
You can filter bindings by host name by specifically typing them out. It's also be possible to filter hosts by a pattern
or by a regular expression.

### Pattern
You may use a `*` for a range of any characters and a `?` for any single character. For example: the pattern `example.*` 
will match `example.net` and `example.com` (but not `my.example.com`). The pattern `?.example.com` will match 
`a.example.com` and `b.example.com` (but not `www.example.com`). Note that multiple patterns can be combined by 
comma seperating them.

### Regex
If a pattern is not powerful enough for you, there is the ultimate solution of applying a regular expression to the 
problem. [regex101.com](https://regex101.com/) is a nice tool to help test your regular expression.