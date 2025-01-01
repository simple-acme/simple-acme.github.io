---
---
# Domain validated
Sometimes it's claimed that using Let's Encrypt is somehow "less secure" than paid alternatives. That's mostly nonsense designed to keep risk-averse organisations paying up.

The fact is that Let's Encrypt has always been fully compliant and accountable to the [CA/Browser Forum](https://cabforum.org/), just like any other issuer that hopes to become trusted by mainstream operating systems and browsers. Members like Google, Apple and Microsoft take the rules of this game *very* seriously. If there were genuine concerns about Let's Encrypt, this forum (which also includes their competitors) would be all over them and demand explanations and improvements. Of course there have been some incidents, but generally they've been in good standing within this community of experts for almost a decade.

### Domain Validated 
Let's Encrypt provides only domain validated (DV) certificates. This means that they will put their hand in the fire for the fact that whomever is issued one of their certificates has sufficiently demonstrated control of the included domain(s) to them. 

Here is the crux though: being in control of a domain is not always the same as being its legitimate owner. Hackers can target a website and/or its infrastructure, which if successful could potentially allow them to issue a certificate using Let's Encrypt without the owners' permission - and without leaving a paper trail.

Commercial providers "solve" this problem by also offering Organisation Validation (OV) certificates. This is the "more secure" and more expensive product that Let's Encrypt lacks and what most of the arguments against it boil down to. 

OV certificates are technically identical to DV certificates - i.e. they offer same level of encryption - but they include additional meta data fields incidating who payed for them, guaranteed to be correct by the issuer. Theoretically this allows end users to make more informed decisions on whether to trust them or not. 

The problem is that the number of users actually doing that rounds down to zero, because these extra fields don't show up anywhere near the regular browsing experience; users often need to click through multiple popups to get to it.

Even more damning is that every new connection could be potentially be set up using a new certificate. You'd have to monitor every single request to notice possible deviation from the expected values. 

Blocking Let's Encrypt wholesale might stop hackers from issuing rogue certificates after they've gained access to your domain. And of course, defence-in-depth is generally a sound principe to go by, but the case is aguably very thin here, because they are two scenarios:

1. The hacker does *not* gain control over your DNS servers, so your [CAA policy](https://en.wikipedia.org/wiki/DNS_Certification_Authority_Authorization) remains in effect to protect you against rogue certificates being issued. (Unless you don't have this in place, *or* your regular trusted provider is happy to sell the hacker a DV certificate.)
2. The hacker is able to gain control of your DNS servers. This is game over no matter what you've put in place. 

### Staying in control
The rational thing to do as a security policy maker is to accept that Let's Encrypt is here to stay. It's become the biggest issuer on the internet, with over 300 million domains using it, so it can practically not be blanket distrusted anymore. Average users certainly won't notice the difference between Let's Encrypt and other certificates, nor will attackers trying to snoop in on network traffic.

Even if your organisation prefers OV over DV for some applications, you still don't have to ban Let's Encrypt outright. You can exercise very fine-grained control for each of your (sub)domains by using [CAA policy](https://en.wikipedia.org/wiki/DNS_Certification_Authority_Authorization) records. Originally you either had to allow Let's Encrypt or not, but since 2019 you can limit issuance to specific accounts and validation methods, further reducing the attack surface.

And if you're still concerned about rogue certificates with a solid CAA in place, please take a look at the [Certificate Transparancy](https://certificate.transparency.dev/) ecosystem, which provides tools to monitor for them, even allowing you to detect incidents after you've lost control over your DNS, or third parties abusing the trust you've granted them. 

These tools combined form a much stronger defence-in-depth posture than banning Let's Encrypt from your organisation.
