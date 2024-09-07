---
layout: plugin
plugin: c49a7a9a-f8c9-494a-a6a4-c6b9daae7d9d
compatibility: All platforms
examples:
    -
        name: Inline key
        cmd: ‑‑transip-login mylogin ‑‑transip-privatekey "---- BEGIN PRIVATE KEY ---- **** ---- END PRIVATE KEY ----"
    -
        name: Key on disk
        cmd: ‑‑transip-login mylogin ‑‑transip-privatekeyfile C:\transip.key
---
Create the record at [TransIP](https://www.transip.nl/). Note that this provider is not very fast updating its records after their API has accepted the changes, so it's highly recommended to roughly double either `PreValidateDnsRetryCount` and/or `PreValidateDnsRetryInterval` when using DNS validation through them.

## Setup
This requires you to activate the API in the "my account" section of the control panel and to create a key pair for simple-acme.