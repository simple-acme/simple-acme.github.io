---
---
# IIS configuration

<div class="callout-block callout-block-danger pb-1 mt-3">
    <div class="content">
        <p>All of the following should <strong>only</strong> be applied to the <code>/.well-known/acme-challenge/</code> path. Don't do any of this at the root of the server or the website, because it might break your application(s).</p>
    </div>
</div>

## Relevant settings
### CMS
Your CMS might intercept the request and redirect the user to an (error) page. The solution is to configure your CMS to allow unlimited access to the challenge path.

### Handlers
IIS might not be configured to serve static extensionless files. Go to "Handler Mappings" > "View Ordered List" and move <code>StaticFile</code> above the various <code>ExtensionlessUrlHandler</code>s.</p>
<p><img src="/assets/staticfile.png" /></p>

### MIME types
IIS should serve extensionless files with the MIME type <code>text/plain</code>.

### Request filtering
Unlisted file extensions and high bit characters should be allowed.

### Authentication
Your website might require NTLM, client certificates or other authentication methods. Enable anonymous authentication to allow access from the ACME server.

### SSL
Your website might be configured to exclusively accept HTTPS traffic, while the validation request comes in on port 80. Disable the "Require SSL" setting to fix that.

### IP/Domain Restrictions
Your website might use IP Address and Domain Restrictions to provide extra security. The ACME server will have to bypass though. (Let's Encrypt does not publish a list of IP addresses that they can use for validation.)

### URL Rewrite:
If you are using <a href="https://www.iis.net/downloads/microsoft/url-rewrite">URL Rewrite</a> 
the validation request might get caught up in that, so you may need to make an exception for 
the challenge path. For example like so: 

```XML
<rule name="ACME validation" stopProcessing="true">
    <match url="^\.well-known.*$" />
    <action type="None" />
</rule>
```

### MVC 
For MVC sites you might need the following:

```XML
<configuration>
    <system.webServer>
        <staticContent>
            <clear/>
            <mimeMap fileExtension = ".*" mimeType="text/json" />
        </staticContent>
        <handlers>
            <clear />
            <add name="StaticFile" 
			path="*" 
			verb="*" 
			type="" 
			modules="StaticFileModule,
			         DefaultDocumentModule,
					 DirectoryListingModule" 
			scriptProcessor="" 
			resourceType="Either"
			requireAccess="Read" 
			allowPathInfo="false" 
			preCondition="" 
			responseBufferLimit="4194304" />
        </handlers>
    </system.webServer>
</configuration>
```

## Testing
Use `--test` mode and external servers like https://letsdebug.net/ to verify your configuration.