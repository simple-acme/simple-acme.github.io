---
layout: plugin
plugin: 11ba2994-ea59-4f2f-b9eb-0eaa2fa3cbfa
compatibility: All platforms
examples:
    -
        name: Typical
        cmd: '‑‑rest-securitytoken ***** [‑‑rest-usehttps]'
---
Publish the challenge answer using a REST API. You will need a third party or custom server component for this validation method to work. The reference implementation can be found [here](https://github.com/marcoskirchner/AcmeChallengeResponder).