<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>Plugins needs to be unpacked into a folder called <code>%programdata%\simple-acme\plugins</code>. Depending on how you downloaded the file, you may have to unblock the <code>.dll</code> files before your computer will trust them. You can do that from the File Explorer by using the right mouse button and then checking the `Unblock` box on the General tab.<br><br>
<img src="/assets/unblock-dll.png"></p>
        <p>To verify that the plugin is properly installed you can start the main executable 
with <code>‑‑verbose</code> and it will print information about found and loaded plugins at 
start up. When the plugin is loaded, it manifests itself as extra menu choices and
command line parameters being made available.</p>
    <div class="callout-block callout-block-warning pb-1 mt-3">
        <div class="content">
            <p>All releases published to third party package managers like Chocolatey and NuGet support plugins, but if you download simple-acme manually, you must choose a <code>pluggable</code> version instead of the <code>trimmed</code> one to use it.</p>
        </div>
    </div>
    </div>
</div>