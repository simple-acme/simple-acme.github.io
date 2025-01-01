---
---
# ACME
This page is a short summary of the development of the ACME protocol, mainly meant for IT types to help convince security/policy types to embrace the standard into their organisations.

## The Bad Old Days
Before ACME, managing TLS/SSL certificate renewals was an operational pain. Certificates could be valid for up to 5 years, which meant that by the time one expired, people often forgot that it existed at all, or who was supposed to be responsible for it. Furthermore, there was often no up-to-date documentation describing where it was installed or how to install it.

Even for organisations that managed to avoid these pitfalls, the manual processes required were still time-consuming and often inherently insecure - involving emails and random temporary folders. For every organisation that painstakingly got certificate management (mostly) right, ten more started securing their connections and fell into the same traps.

## Let's Encrypt
The Let's Encrypt project was started in 2012 by people at Mozilla, the EFF and the University of Michigan with the goal of encrypting the whole internet. It set out to solve the management problem by fully automating the process of ordering and replacing certificates. They adopted the common philosophy in software engineering that if something is difficult, you should strive to do it more frequently. Hence, they decided to issue certificates that were valid for only 90 days, forcing at least 4 renewals per year.

The other thing that Let's Encrypt did was equally revolutionary: they made their certificates available for free. Predictably, this annoyed traditional commercial issuers who charged up to $80 per year for the same service, and quite a lot of FUD was spread to try and slow down the phenomenal growth the project saw after its launch in 2016. Often still echoed is that Let's Encrypt certificates are somehow less secure. [That is mostly nonsense](/manual/about/domain-validated).

## The New Standard
Regardless of your opinion on Let's Encrypt or Domain Validated (DV) certificates, the Automatic Certificate Management Environment (ACME) protocol is now standardized by the IETF in [RFC8555](https://datatracker.ietf.org/doc/html/rfc8555/) and been adopted by the most of the ecosystem of public and private certificate issuers, including traditional names like [Sectigo](https://www.sectigo.com/) and [Digicert](https://www.digicert.com/). Others like [ZeroSSL](https://zerossl.com/) and [Buypass](https://www.buypass.com/) even joined the "free certificates" party.

The protocol will only become more relevant in the future, because the maximum permitted certificate lifetime is ever shortening. The [CA/Browser Forum](https://cabforum.org/) initially agreed on a maximum age of 60 months back in 2011, but changed it to 27 months in 2018 and to its current limit of 13 months in 2020. Recently, Google has been pushing hard to reduce it to 90 days.

In our humble opinion, that will not be the last reduction either. The long term strategy of the industry is to take humans out of the loop by increasing the workload for manual renewals, while normalizing automation as a viable alternative. Once that is done even 7 days could seem like a reasonable upper limit, with some choosing daily or even hourly renewals. That's in fact what some of the current "zero trust" products out there already do for peer validation.

Short-lived certificates improve security because leaked keys lose their value quickly and domain ownership is verified more frequently, greatly reducing the potential impact of momentary lapses in security.
