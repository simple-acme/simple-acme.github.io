---
settings:
    - Validation.DefaultValidation
    - Validation.DefaultValidationMode
---
# Validation plugins

A validation plugin is responsible for providing the ACME server with proof that you own the identifiers 
(host names) that you want to create a certificate for. The 
[ACMEv2 protocol](https://tools.ietf.org/html/draft-ietf-acme-acme-18) defines different 
challenge types, three of which are supported by simple-acme. For wildcard identifiers, only DNS-01 validation is accepted by Let's Encrypt.

## Supported challenge types
The following challenge types are supported by simple-acme. Various plugins exist to automate handling the challenge. E.g. the file required for HTTP-01 validation may be placed on the local filesystem or uploaded via FTP, and the DNS record required for DNS-01 validation may be created at different providers.
<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <tbody>
            <tr>
                <td><a href="/reference/plugins/validation/http/">HTTP-01</a></td>
                <td>Serve a text file on port 80</td>
                <td></td>
            </tr>
            <tr>
                <td><a href="/reference/plugins/validation/dns/">DNS-01</a></td>
                <td>Create a TXT record in the DNS</td>
                <td></td>
            </tr>
            <tr>
                <td><a href="/reference/plugins/validation/tls-alpns/">TLS-ALPN-01</a></td>
                <td>Present self-siged certificate on port 443</td>
                <td></td>
            </tr>
        </tbody>
    </table>
</div>

## Special purpose tools
{% include plugin-list.html type='validation' %}

## Unsupported challenge types
<div class="table-responsive my-4 me-5 pe-5">
    <table class="table table-striped">
        <tbody>
            <tr>
                <td>TLS-SNI-01/-02</td>
                <td>Deprecated and removed</td>
                <td></td>
            </tr>
            <tr>
                <td>PROOFOFPOSSESSION-01</td>
                <td>Unsupported</td>
                <td></td>
            </tr>
        </tbody>
    </table>
</div>