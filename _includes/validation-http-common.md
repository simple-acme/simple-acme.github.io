## web.config
Optionally this plugin can place a `web.config` next to the validation file, to 
help IIS properly serve the response. This automatically fixes *some* of the issues mentioned in 
<a href="/manual/iis-configuration">IIS configuration</a>. In interactive mode the program 
will ask you if you want to do this. In unattended mode you can request it using the 
command line toggle `--manualtargetisiis` (if the source is IIS, this is automatically applied). 
The web.config that will be copied lives in the root of the program directory with the
 name `web_config.xml`. You can modify it to fit your needs. Let us know if you could use a similar feature for uploading an `.htaccess`!