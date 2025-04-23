---
layout: plugin
plugin: e45d62b9-f9a8-441e-b95f-c5ee0dcd8040
compatibility: All platforms
---
The client will show the record that is supposed to be created on screen and you will create it manually by whatever means necessary.

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>It will not be possible to automatically renew certificates created using this method. Use this for proof of concept only.</p>
    </div>
</div>

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>Are you looking into this method because there is no <a href="/reference/plugins/validation/dns/">plugin</a> available for your preferred DNS provider? You have three options in increasing level of complexity to do better than manual updates:</p>
<ul>
    <li><code>CNAME</code> the validation record to one of the supported providers and automate the updates there (a technique called <a href="/reference/plugins/validation/dns">substitution</a> or aliasing)</li>
    <li>Hack together a script to do DNS updates and use the <a href="/reference/plugins/validation/dns/script">script</a> plugin to call it.</li>
    <li>Build your own plugin for simple-acme in C#. Optionally contribute it to GitHub for eternal fame!</li></ul></div></div>