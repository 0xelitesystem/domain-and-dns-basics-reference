# The common record types

DNS records come in several types, each holding a different kind of answer, but a handful cover almost everything an indie operator needs. Knowing what each type does, and when to use which, is most of what makes DNS manageable. The common ones are A, AAAA, CNAME, MX, TXT, and NS.

## A and AAAA: pointing a name at an address

An A record points a name at a numeric address, the kind used by the current and most common addressing scheme. It is the workhorse: when you want a domain or subdomain to lead to a particular server, an A record holding that server's address is usually how. An AAAA record does the same job for the newer addressing scheme, which uses a longer address format; it points a name at an address in that scheme. In practice, A and AAAA records are how you say this name lives at this server. If your host gives you a numeric address to point your domain at, you put it in an A record, and an AAAA record if they also give you one in the newer format.

## CNAME: pointing a name at another name

A CNAME record points one name at another name, rather than at an address. Instead of saying this name is at this address, it says this name is an alias for that other name, and the address is whatever that other name resolves to. CNAMEs are common when a platform tells you to point your subdomain at one of their names; the platform manages the underlying address, and your CNAME just follows their name wherever it leads. A practical rule worth knowing is that a CNAME cannot coexist with certain other records on the exact same name, and the root of a domain often cannot be a CNAME, which is why platforms sometimes give different instructions for the bare domain versus a subdomain.

## MX: routing email

An MX record, for mail exchange, tells the world where to deliver email addressed to your domain. When someone sends mail to an address at your domain, the sending system looks up your MX records to find which mail servers should receive it. If you use an email provider, they give you the MX records to set, and putting them in is what makes mail to your domain actually arrive at that provider. Without correct MX records, email to your domain has nowhere to go. MX records are separate from where your website lives; a domain can serve a site from one place and route its email to another, because A or CNAME records handle the web and MX records handle the mail.

## TXT: text records for verification and policy

A TXT record holds arbitrary text, and it is used for a range of purposes that mostly come down to proving something or publishing a policy. Services often ask you to add a TXT record with a specific value to prove you own the domain before they will work with it. The email authentication records, covered later, are TXT records that publish your mail-sending policy. Because TXT records just hold text that other systems read, they are the catch-all for publishing information about your domain that machines need to check. When a service says add this verification string to your DNS, it almost always means a TXT record.

## NS: which nameservers are authoritative

An NS record, for nameserver, says which servers hold the authoritative records for your domain, the ones that give the real answers to lookups. This connects to the next page's distinction between your registrar and your nameservers. The NS records determine which DNS service actually answers for your domain, and changing them moves control of your domain's DNS to a different provider. You usually do not edit NS records often, but knowing they exist explains how a domain bought in one place can have its DNS managed in another: the NS records point to whichever nameservers you have chosen to be authoritative.
