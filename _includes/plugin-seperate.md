<div class="callout-block callout-block-success pb-1 mt-3">
    <div class="content">
        <p>The plugin need to be unpacked into the folder where you also unpacked 
<code>wacs.exe</code> to able to use it. Depending on how you downloaded the file, 
you may have to unblock all new <code>.dll</code> files before your computer will trust 
them. You can do that from the Windows File Explorer by using the right mouse button 
and then checking the `Unblock` box on the General tab.<br><br>
<img src="/assets/unblock-dll.png"></p>
        <div class="callout-block callout-block-warning pb-1 mt-3">
            <div class="content">
                <p>If you are using simple-acme as a dotnet tool, the folder will be <code>%userprofile%\.dotnet\tools\.store\simple-acme\{{ site.data.build.releasebuild }}\simple-acme\{{ site.data.build.releasebuild }}\tools\net9.0\any</code></p>
            </div>
        </div>
        <p>To verify that the plugin is properly installed you can start the main executable 
with <code>‑‑verbose</code> and it will print information about found and loaded plugins at 
start up. When the plugin is loaded, it manifests itself as extra menu choices and
command line parameters being made availalbe.</p>
    <div class="callout-block callout-block-warning pb-1 mt-3">
        <div class="content">
            <p>This plugin requires to you use the <code>pluggable</code> release of the main executable. It will not work on the smaller <code>trimmed</code> releases.</p>
        </div>
    </div>
    </div>
</div>