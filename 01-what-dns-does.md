# What DNS does

DNS, the domain name system, turns a name people can remember into the information machines need to connect. People type a domain like a website's name; computers route traffic using numeric addresses. DNS is the system that translates between the two, so that a human-friendly name reaches the right server. Every time someone visits a site, sends email to a domain, or connects to a service by name, a DNS lookup happens first to find where that name actually points.

## The address-book analogy

The common way to describe DNS is as the address book or phone book of the internet. You know a name; DNS looks up the address that name corresponds to. Without it, you would have to know the numeric address of every server you wanted to reach, which is impractical, the way memorizing phone numbers instead of using contacts would be. DNS lets the whole internet run on memorable names while the machines underneath use the addresses those names resolve to. When you own a domain, you control its entries in this address book, deciding what each name under your domain points to.

## The lookup that happens every time

When someone goes to your domain, their device asks the DNS system, what address does this name point to, and the system returns the answer, after which the device connects to that address. This lookup is fast and mostly invisible, but it is happening constantly, before every connection by name. The answer comes from the DNS records you have set for your domain, which is why those records are the control surface: change where a record points, and you change where traffic for that name goes. Understanding DNS is mostly understanding that you are editing the answers the world gets when it looks up your domain.

## What you control with DNS

Owning a domain gives you control over its DNS records, and through them you decide several things. You point the domain, and names under it, at the server or platform hosting your website. You route email sent to your domain to the right mail provider. You publish records that prove you own the domain or that authenticate your email. You can create subdomains, distinct names under your domain, each pointing wherever you choose. All of this is done by adding and editing DNS records, which is the practical work of managing a domain once you own it.

## Why it matters to get right

DNS sits in front of everything your domain does, so mistakes are visible and disruptive. A wrong record can take your site offline, send your email into a black hole, or break a service, and because of how DNS caching works, covered later, fixing it is not always instant. Conversely, correct DNS records are what make a domain actually do its job: serve the site, deliver the mail, pass the checks. The records are not many and they are not complex once the types make sense, which is what the next page covers. The goal of this reference is that you can read and set your own domain's records with confidence rather than guessing.
