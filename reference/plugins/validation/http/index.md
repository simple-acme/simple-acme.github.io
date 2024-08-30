---
settings:
  - Execution.DefaultPreExecutionScript
  - Execution.DefaultPostExecutionScript
---
# HTTP validation
HTTP validation works as follows:
- For each domain (e.g. `sub.example.com`), the ACME server sends a 
challenge consisting of an `x` and `y` value. The truth is actually a little 
more complicated than that, but for the sake of this explanation it will suffice.
- The client has to make sure that when the ACME server makes a request 
to `http://sub.example.com/.well-known/acme-challenge/x`, the content of the HTTP 
response will be `y` with some specific headers set as well.
- The validation request is *always* made to port 80, that cannot be changed. 
- The ACME server **does** follow 301/302 redirects.
- There may be more than one validation request for the same token, e.g. from 
different geographic locations or different protocols (IPv4/IPv6).
- Let's Encrypt does **not** disclose the source locations of these requests, which 
effectively means that the domain has to be accessible for the public, 
at least for the duration of the validation. IF you need to temporarly open a firewall
for this purpose, check out the settings below.

{% include plugin-list.html type='validation' subtype='http' %}

## Warmup
Before allowing the ACME server to validate, the program will attempt to request
the validation file itself and note the result of that request in the log. A side 
effect of this is that it forces the application to start in case it's application pool
or equivalent went to sleep, warming up the caches etc. This reduces the chance of 
time-outs during validation.