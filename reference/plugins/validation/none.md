---
layout: plugin
plugin: a37b41dc-b45a-42fe-8d81-82ca409a5491
compatibility: All platforms
---
The client will not perform any validation. This is mainly useful to request certificates for pre-authorized domains without having to go through the 'trouble' of setting up a validation method. Particulary, a DNS validation method that is normally required for wildcard domains.

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>You cannot bypass mandatory validation by selecting this option. The certificate order will fail if the server issues a challenge.</p>
    </div>
</div>
