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
'slow motion'. This will run against the Let's Encrypt staging server, so you don't risk 
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
Let's Encrypt does not support more than 100 domain names per certificate, or 25 if you 
select the `tlsserver` profile.

### Non-public domains
Let's Encrypt can only be used to issue certificates for domains living on the
public internet. Internal domains or Active Directory host names are therefore not
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

### IIS issues
Note that it's recommended to use the default [self-hosting](/reference/plugins/validation/http/selfhosting) validation plugin in combination with IIS. The [other HTTP plugins](/reference/plugins/validation/http/) are great for web servers such as [Apache](/manual/advanced-use/examples/apache), but using them in combination with IIS leads to many potentials issues, highlighted on [this page](/manual/iis-configuration).

## DNS validation issues
The ACME server may query all of your name servers, so they will have to be in sync before submitting the challenge. The program will perform a pre-validation
'dry run' to allow the DNS changes to be processed. Please check the page on [DNS validation plugins](/reference/plugins/validation/dns/) for fine-tuning options if the pre-validation fails.
