<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>This plugin requires to you use the <code>pluggable</code> release of the main executable. It will not work on the smaller <code>trimmed</code> releases.</p>
    </div>
</div>

<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>The plugin need to be unpacked into the folder where you also unpacked 
<code>wacs.exe</code> to able to use it. Note that after unpacking you may have to unblock all 
new .dll files before your device will trust them. You can do that from the Windows 
File Explorer by using the right mouse button and then checking the `Unblock` box 
on the General tab.<br>
<img src="/assets/unblock-dll.png"></p>
    </div>
</div>

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <p>If you are using simple-acme as a dotnet tool, you will have to unpack to <code>%userprofile%\.dotnet\tools\.store\simple-acme\{{ site.releasename }}\simple-acme\{{ site.releasename }}\tools\net8.0\any</code></p>
    </div>
</div>

<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>To verify that the plugin is properly installed you can start the main executable 
with <code>‑‑verbose</code> and it will print information about found and loaded plugins at 
start up. When the plugin is loaded, it manifests itself as extra menu choices and
command line parameters being made availalbe.</p>
    </div>
</div>
