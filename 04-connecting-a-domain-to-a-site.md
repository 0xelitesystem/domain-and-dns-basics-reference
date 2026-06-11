# Connecting a domain to a site

The most common reason to touch DNS is to point a domain at the place hosting your website, so that visiting the domain reaches your site. How you do it depends on what your host gives you, an address or a name to point at, and on whether you are pointing the bare domain or a subdomain. The mechanics are a few records, but a couple of quirks trip people up.

## Pointing at an address versus a name

Hosts and platforms tell you to connect your domain in one of two ways. Some give you a numeric address to point at, in which case you use an A record, and an AAAA record too if they provide an address in the newer format. Others give you one of their names to point at, in which case you use a CNAME record aliasing your name to theirs, and they manage the underlying address. Either way, you are telling DNS that your domain leads to their server. Follow whichever instruction your specific host gives, since they know how their platform expects to receive your domain, and using the wrong record type, or the wrong target, is the usual reason a connection fails.

## The bare domain versus the www subdomain

A recurring wrinkle is the difference between the bare domain, the name with nothing in front, and the www subdomain. As the record-types page noted, the bare domain often cannot be a CNAME, while a subdomain can be. This is why hosts sometimes give different instructions for the two: an A record or a special arrangement for the bare domain, and a CNAME for www, or the reverse. The common goal is that both the bare domain and the www version reach your site, usually with one redirecting to the other so you have a single canonical address. Setting up both, and a redirect from one to the other, avoids the situation where the site works at one but not the other.

## Subdomains point wherever you choose

A subdomain, a name in front of your domain, is just another DNS entry you can point independently. You might point the main domain at your website and a subdomain at a different service, a help center, a blog, an app, each with its own record. Subdomains are how you run several things under one domain, each pointing where it needs to. Creating one is simply adding a record for that subdomain name, pointing it at the relevant address or name. This flexibility is part of why owning a domain is useful: it is not one destination but a namespace you can route in pieces.

## Verifying ownership and adding the certificate

Connecting a domain to a modern host usually involves two things beyond pointing the records: proving you own the domain, and getting a security certificate so the site serves over HTTPS. Ownership is often proven by adding a TXT record the host specifies, as the record-types page described. The certificate is frequently issued and managed automatically by the host once the domain points at them, which connects to the HTTPS reference in this portfolio; the practical point is that after the DNS points correctly, the host typically handles the certificate so the site can serve securely. If HTTPS is not working after connecting, it is often because the domain is not yet pointing correctly or the certificate has not finished being issued.

## Confirming it worked

After setting the records, confirm the connection actually works, allowing for the caching delay from the propagation page. Visit both the bare domain and the www version and check they reach your site and serve over HTTPS. If they do not, the usual causes are the records still being cached, the wrong record type or target for what your host expected, or editing at a provider other than the one your nameservers point to. Working through those, and giving caching time to clear, resolves most connection problems. Once both versions of the domain reach the site securely, the connection is done, and the DNS for the website part of your domain rarely needs touching again unless you move hosts.
