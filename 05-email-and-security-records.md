# Email and security records

Beyond pointing a domain at a website, DNS carries the records that route email to your domain and that protect the domain from misuse. These are easy to overlook because the website can work fine without them, but missing or wrong email and security records cause real problems: mail that fails to deliver, mail from your domain treated as spam, and a domain more vulnerable to abuse.

## MX records route incoming mail

As the record-types page covered, MX records tell the world where to deliver email sent to your domain. If you use an email provider for addresses at your domain, setting their MX records is what makes mail actually arrive. This is separate from the website: a domain serves its site through A or CNAME records and routes its mail through MX records, independently. A common surprise is email not working after a domain change, because the MX records were not set or were lost; the website points correctly but mail has nowhere to go. Whenever a domain needs to receive email, the MX records from the mail provider are the piece that makes it happen.

## Email authentication: SPF, DKIM, DMARC

Sending email from your domain reliably requires a set of authentication records, published as TXT records in your DNS, that prove your mail is genuinely from you. SPF lists which servers are allowed to send as your domain. DKIM publishes a key that signs your mail so receivers can verify it. DMARC publishes a policy for what to do with mail that fails those checks. Together they are what keep your domain's mail out of spam folders and stop others from forging mail as your domain. These records live in DNS but the topic is large enough to have its own treatment; the dns-email-authentication reference and the email-deliverability reference in this portfolio cover them in depth. The point here is that they are DNS records, they matter whenever your domain sends mail, and skipping them is a common cause of mail landing in spam.

## CAA records limit certificate issuance

A CAA record, certification authority authorization, says which certificate authorities are allowed to issue security certificates for your domain. Without one, any authority might issue a certificate for your domain; with one, you restrict issuance to the authorities you actually use, which reduces the risk of an unauthorized certificate being issued for your domain. This is a small, set-once record that adds a layer of protection, and the security baseline in this portfolio recommends it. It does not affect day-to-day operation, but it closes a gap that is otherwise left open, and it is cheap to add once you know which authority issues your certificates.

## DNSSEC adds integrity to DNS itself

DNSSEC is a system that adds cryptographic signatures to your DNS records so that the answers to lookups can be verified as genuine and unaltered, protecting against certain attacks that forge DNS responses. Where your registrar and DNS provider support it, enabling DNSSEC strengthens the integrity of your domain's DNS. It is more involved than the other records and not every situation needs it, but the security baseline notes it as worth enabling where supported. The benefit is that systems can trust that the DNS answers for your domain are the real ones, not forged, which closes another avenue of attack against a domain.

## Protect the registrar account itself

Finally, the records are only as safe as the account that controls them. Whoever can log in to your registrar or DNS provider can change where your domain points, where its mail goes, and every record above, which makes that account a high-value target. The security baseline calls for the registrar account to have its own strong authentication, separate from other logins, because taking over that account means taking over the domain entirely. All the careful records in the world do not help if someone can log in and rewrite them. Securing the account that holds the DNS is the foundation that the email and security records sit on, and it is the one most often neglected.
