---
arguments:
    - test
    - verbose
    - baseuri
---
# Validation problems
Validation is an important aspect of the ACME and Let's Encrypt, but there are many subtle ways 
that it can fail. This page is meant for people who run into problems to help figure out what 
the issue might be.

## Testing 
Run `wacs.exe` with the `‑‑test` and `‑‑verbose` parameters to watch your validation unfold in 
'slow motion'. This will run against the Let's Encrypt staging server so you don't risk 
running into any rate limits. If you want to test against the production endpoint, include the
parameter `‑‑baseuri https://acme-v02.api.letsencrypt.org/` as well.

## General validation issues

### DNSSEC
ACME providers will typically validate your DNSSEC configuration. If there is anything suspicious 
about it, your browser might not complain, but you will not be able to get a certificate. A useful 
tool to check your (provider's) DNSSEC configuration from the perspective of a strict external
observer is the [Unbound DNS checker](https://unboundtest.com/).

### CAA records
ACME providers will check for the existence and validity of a 
[CAA record](https://support.dnsimple.com/articles/caa-record/) for your domain. You may have to add
a record like `example.com. CAA 0 issue "letsencrypt.org" to your DNS server in order to allow the
provider to issue certificates for your domain. This can be checked using 
[Let's Debug](https://letsdebug.net/).

### Protocols and cipher suites
Tools like [IISCrypto](https://www.nartac.com/Products/IISCrypto) are often used configure the 
[cipher suites](http://letsencrypt.readthedocs.io/en/latest/ciphers.html) of Windows systems 
according to the latest best practices. Changing these settings always brings some risk of 
breaking compatibility between two parties though. Too restrictive cipher suites have been known 
to hamper the ability to communicate with the ACME API endpoint and its validation servers. If 
that happens try more conservative settings. Test if the 
[API endpoint](https://acme-v02.api.letsencrypt.org) is accessible from a web browser on 
your server.

## Let's Encrypt limitations
The following limitations apply to Let's Encrypt and may not be true for every ACME 
service provider.

### Domain count limit
Let's Encrypt does not support more than 100 domain names per certificate.

### Non-public domains
Let's Encrypt can only be used to issue certificates for domains living on the
public internet. Interal domains or Active Directory host names are therefor not
possible to use.

## HTTP validation issues

### Firewall
HTTP validation happens on port 80, so it will have to open on your firewall(s). Let's Encrypt 
doesn't disclose IP address range(s) for their validation servers, meaning port 80 will have 
to be accessible from *any* origin, at least for the duration of the validation. Looking to temporarily open the firewall? See some options [here](/reference/plugins/validation/http/).

### IPv6 configuration 
Let's Encrypt will check IPv6 access to your site if `AAAA` records are configured. Many browsers
and networks don't use IPv6 yet or automatically fallback to IPv4 when an error occurs, so 
it might not be immediately obvious that your site is unreachable on IPv6. You can test 
it [here](http://ipv6-test.com/validate.php).

### Issues with IIS
Note that it's recommended to use the default [self-hosting](/reference/plugins/validation/http/selfhosting) validation plugin in combination with IIS. The [other HTTP plugins](/reference/plugins/validation/http/) are great for web servers such as [Apache](/manual/advanced-use/examples/apache), but using them in combination with IIS leads to many potentials issues, highlighted below.

<div class="callout-block callout-block-warning pb-1 mt-3">
    <div class="content">
        <div class="callout-block callout-block-danger pb-1 mt-3">
            <div class="content">
                <p>All of the following should <strong>only</strong> be applied to the <code>/.well-known/acme-challenge/</code> path. Don't do any of this at the root of the server or the website, because it might break your application(s).</p>
            </div>
        </div>
        <p>
        <strong>CMS:</strong>
        Your CMS might intercept the request and redirect the user to an (error) page. The solution 
        is to configure your CMS to allow unlimited access to the challenge path.
        </p>
        <p>
        <strong>Handlers:</strong>
        IIS might not be configured to serve static extensionless files. Go to "Handler Mappings" > "View Ordered List" and move <code>StaticFile</code> above the various <code>ExtensionlessUrlHandler</code>s.</p>
        <p><img src="/assets/staticfile.png" /></p>
        <p><strong>Authentication:</strong>
        Your website might require NTLM, client certificates or other authentication methods. Enable anonymous authentication to allow access from the ACME server.</p>
        <p><strong>SSL:</strong>
        Your website might be configured to exclusively accept HTTPS traffic, while the validation request comes in on port 80. Disable the "Require SSL" setting to fix that.</p>
        <p><strong>IP/Domain Restrictions:</strong>
        Your website might use IP Address and Domain Restrictions to provide extra security. 
        The ACME server will have to bypass though. (Let's Encrypt does not publish a list of 
        IP addresses that they can use for validation.)
        </p>
        <p>
        <strong>URL Rewrite:</strong>
        If you are using <a href="https://www.iis.net/downloads/microsoft/url-rewrite">URL Rewrite</a> 
        the validation request might get caught up in that, so you may need to make an exception for 
        the challenge path. For example like so: <code>
            &lt;rule name=&quot;ACME validation&quot; stopProcessing=&quot;true&quot;&gt;
                &lt;match url=&quot;^\.well-known/acme-challenge/.*$&quot; /&gt;
                &lt;action type=&quot;None&quot; /&gt;
            &lt;/rule&gt;
        </code>
        </p>
    </div>
</div>

## DNS validation issues
The ACME server may query all of your name servers, so they will have to be in sync before submitting the challenge. The program will perform a pre-validation
'dry run' to allow the DNS changes to be processed. Please check the page on [DNS validation plugins](/reference/plugins/validation/http/) for finetuning options if the pre-validation fails.