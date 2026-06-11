# Registrar, nameservers, and propagation

Three things confuse people new to DNS: the difference between where you bought the domain and where its DNS is managed, what nameservers are, and why DNS changes do not take effect instantly. Understanding these removes most of the mystery and the frustration around DNS changes that seem not to work.

## Registrar versus DNS host

The registrar is the company you bought the domain from, the one that registers your ownership of the name. The DNS host, or nameserver provider, is whoever holds and answers your domain's DNS records. These are often the same company, since registrars usually offer DNS management, but they do not have to be. You can buy a domain from one company and have its DNS managed by another, by pointing the domain's nameservers at the second company. This separation explains a common confusion: you bought the domain in one place but are told to manage records somewhere else, because the DNS is hosted by a different provider than the registrar. Knowing which company actually holds your DNS records tells you where to go to edit them.

## What nameservers are

Nameservers are the servers that hold your domain's DNS records and answer lookups for it. When the world wants to know what a name under your domain points to, it ultimately asks your domain's nameservers, which give the authoritative answer from the records you have set. Your domain has NS records, as the previous page noted, that say which nameservers are authoritative for it. Choosing a DNS provider means pointing your domain at that provider's nameservers, after which their system answers for your domain and you edit your records in their control panel. If you change nameservers, you move where your domain's DNS is answered, which is how you switch DNS providers.

## Why changes take time: caching and TTL

DNS changes do not take effect instantly, and the reason is caching. To avoid asking your nameservers for the same answer constantly, systems across the internet cache DNS answers for a while, and they keep serving the cached answer until it expires. How long they cache is governed by a value attached to each record called the TTL, time to live, which says how long the answer may be cached before it should be looked up again. When you change a record, systems that cached the old answer keep using it until their cache expires according to the TTL, which is why a change can take anywhere from minutes to many hours to be seen everywhere. This delay is often called propagation, though it is really caches expiring rather than the change physically spreading.

## Working with TTL

Because TTL controls how long old answers linger, you can plan changes around it. If you know you are going to change a record soon, lowering its TTL ahead of time means systems will cache the new answer for a shorter period, so when you make the actual change it takes effect faster everywhere. After the change has settled, you can raise the TTL again to reduce lookups. For a stable record, a longer TTL is fine and efficient; before a planned move, a shorter TTL reduces the window where some visitors see the old answer and some see the new. Understanding TTL turns propagation from a mysterious wait into something you can anticipate and shorten.

## Why a change might seem not to work

The caching behavior explains the most common DNS frustration: you changed a record, it looks right in your DNS panel, but the site or service still behaves as before. Usually this is caching, your own device or network is still holding the old answer, and it will resolve once the cache expires per the TTL. Sometimes it is editing the records at the wrong provider, because the domain's nameservers point somewhere other than where you are editing. Checking that you are editing at the provider your nameservers actually point to, and then allowing for the TTL before concluding something is wrong, resolves most of these. The change is usually correct; the delay is the cache, and the occasional real error is editing in the wrong place.
