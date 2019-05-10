[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink") __TOC__

Phishing attacks are one of the highest visibility problems for banking
and e-commerce sites, with the potential to destroy a customer’s
livelihood and credit rating. There are a few precautions that
application writers can follow to reduce the risk, but most phishing
controls are procedural and user education.

Phishing is a completely different approach from most scams. In most
scams, there is misrepresentation and the victim is clearly
identifiable. In phishing, the lines are blurred:

  - The identify theft victim is a victim. And they will be repeatedly
    victimized for years. Simply draining their bank account is not the
    end. Like all types of identity theft, the damage is never
    completely resolved. Just when the person thinks that everything has
    finally been cleaned up, the information is used again.

<!-- end list -->

  - Banks, ISPs, stores, and other phishing targets are victimized –
    they suffer a huge loss of reputation and trust by consumers. If you
    received a legitimate email from Citibank today, would you trust it?

## What is Phishing?

Phishing is misrepresentation where the criminal uses social engineering
to appear as a trusted identity. They leverage the trust to gain
valuable information; usually details of accounts, or enough information
to open accounts, obtain loans, or buy goods through e-commerce sites.

Up to 5% of users seem to be lured into these attacks, so it can be
quite profitable for scammers – many of whom send millions of scam
e-mails a day.

The basic phishing attack follows one or more of these patterns:

  - Delivery via web site, e-mail or instant message, the attack asks
    users to click on a link to “re-validate” or “re-activate” their
    account. The link displays a believable facsimile of your site and
    brand to con users into submitting private details.

<!-- end list -->

  - Sends a threatening e-mail to users telling them that the user has
    attacked the sender. There’s a link in the e-mail which asks users
    to provide personal details.

<!-- end list -->

  - Installs spyware that watches for certain bank URLs to be typed, and
    when typed, up pops a believable form that asks the users for their
    private details.

<!-- end list -->

  - Installs spyware (such as Berbew) that watches for POST data, such
    as usernames and passwords, which is then sent onto a third party
    system.

<!-- end list -->

  - Installs spyware (such as AgoBot) that dredges the host PC for
    information from caches and cookies.

<!-- end list -->

  - “Urgent” messages that the user’s account has been compromised, and
    they need to take some sort of action to “clear it up”.

<!-- end list -->

  - Messages from the “Security” section asking the victim to check
    their account as someone illegally accessed it on this date. Just
    click this trusty link…

Worms have been known to send phishing e-mails, such as MiMail, so
delivery mechanisms constantly evolve. Phishing gangs (aka organized
crime) often use malicious software like Sasser or SubSeven to install
and control zombie PCs to hide their actions, provide many hosts to
receive phishing information, and evade the shutdown of one or two
hosts.

Sites that are not phished today are not immune from phishing tomorrow.
Phishers have a variety of uses for stolen accounts -- any kind of
e-commerce is usable. For example:

  - Bank accounts: Steal money. But other uses: Money laundering. If
    they cannot convert the money to cash, then just keep it moving.
    Just because you don't have anything of value sitting in the account
    does not mean that the account has no value. Many bank accounts are
    linked. So compromising one will likely compromise many others. Bank
    accounts can lead to social security numbers and other account
    numbers. (Do you pay bills using an auto-pay system? Those account
    numbers are also accessible. Same with direct deposit.)

<!-- end list -->

  - PayPal: All the benefits of a bank without being a bank. No FDIC
    paper trail.

<!-- end list -->

  - eBay: Laundering.

<!-- end list -->

  - Western Union: "Cashing out". Converting stolen money to cash.

<!-- end list -->

  - Online music and other e-commerce stores. Laundering. Sometimes
    goods (e.g., music) are more desirable than money. Cashing out takes
    significant resources. Just getting music (downloadable, instant,
    non-returnable) is easy. And easy is sometimes desirable.

<!-- end list -->

  - ISP accounts. Spamming, compromising web servers, virus
    distribution, etc. Could also lead to bank accounts. For example, if
    you use auto-pay from your bank to your ISP, then the ISP account
    usually leads to the bank account number.

<!-- end list -->

  - Physical utilities (phone, gas, electricity, water) directly lead to
    identity theft.

<!-- end list -->

  - And the list goes on.

It is not enough to not trust emails from banks. You need to question
emails from all sources.

## Deploy SPF, DKIM, DMARC

SPF - Sender Policy Framework - <http://www.openspf.org/> - is a simple
addition you can make to your DNS servers to alow recipients to
authenticate email messages you send. After you're SPF-Enabled, any
phishing emails that attempt to spoof your legitimate email domain will
be erased by all good anti-spam software, thus preventing victims from
ever receiving the phish emails. DKIM - DomainKeys Identified Mail -
<http://www.dkim.org/> - is another similar system, albeit more resource
intensive. And finally, there is [DMARC](https://www.dmarc.org)
(Domain-based Message Authentication, Reporting & Conformance), which is
an email authentication, policy, and reporting protocol. It builds on
the widely deployed SPF and DKIM protocols, adding linkage to the author
(“From:”) domain name, published policies for recipient handling of
authentication failures, and reporting from receivers to senders, to
improve and monitor protection of the domain from fraudulent email.

## User Education

Users are the primary attack vector for phishing attacks. Without
training your users to be wary of phishing attempts, they will fall
victim to phishing attacks sooner or later. It is insufficient to say
that users shouldn’t have to worry about this issue, but unfortunately,
there are few effective technical security controls that work against
phishing attempts as attackers are constantly working on new and
interesting methods to defraud users. Users are the first, and often the
last, lines of defense, and therefore any workable solution must include
them.

Create a policy detailing exactly what you will and will not do.
Regularly communicate the policy in easy to understand terms (as in “My
Mom will understand this”) to users. Make sure they can see your
policies on your web site.

From time to time, ask your users to confirm that they have installed
anti-virus software, anti-spyware, keep it up to date, scanned recently,
and have updated their computer with patches recently. This keeps basic
computer hygiene in the users’ minds, and they know they shouldn’t
ignore it. Consider teaming with anti-virus firms to offer special deals
to your users to provide low cost protection for them (and you).

However, be aware that user education is difficult. Users have been
lulled into “learned helplessness”, and actively ignore privacy
policies, security policies, license agreements, and help pages. Do not
expect them to read anything you communicate with them.

## Make it easy for your users to report scams

Monitor <u>abuse@yourdomain.com</u> and consider setting up a feedback
form. Users are often your first line of defense, and can alert you far
sooner than simply waiting for the first scam victims to come forward.
Every minute of a phishing scam counts.

## Communicating with customers via e-mail

Customer relationship management (CRM) is a huge business, so it’s
highly improbable that you can prevent your business from sending
customers marketing materials. However, it is vital to communicate with
users in a safe way:

  - Education - Tell users every single time you communicate with them,
    that:
      - they must type your URL into their browser to access your site
      - you don’t provide links for them to click
      - you will never ask them for their secrets
      - and if they receive any such messages, they should immediately
        report any such e-mail to you, and you will forward that on to
        their local law enforcement agencies

<!-- end list -->

  - Consistent branding – don’t send e-mail that references another
    company or domain. If your domain is “example.com”, then all links,
    URLs, and email addresses should strictly reference “example.com”.
    Using mixed brands and multiple domains – even when your company
    owns the multiple domain names – generates user confusion and
    permits attackers to impersonate your company.

<!-- end list -->

  - Reduce Risk - don’t send e-mail at all. Communicate with your users
    using your website rather than e-mail. The advantages are many: the
    content can be in HTML, it’s more secure (as the content cannot be
    easily spoofed by phishers), it is much cheaper than mass mailing,
    doesn’t involve spamming the Internet, and your customers are aware
    that you never send e-mail, so any e-mail received from “you” is
    fraudulent.

<!-- end list -->

  - Reduce Risk - don’t send HTML e-mail. If you must send HTML e-mail,
    don’t allow URLs to be clickable and always send well-formed
    multi-part MIME e-mails with a readable text part. HTML content
    should never contain JavaScript, submission forms, or ask for user
    information.

<!-- end list -->

  - Reduce Risk - be careful of using “short” obfuscated URLs (like
    <u><http://redir.example.com/f45jgk></u>) for users to type in, as
    scammers may be able to work out how to use your obfuscation process
    to redirect users to a scam site. In general, be wary of redirection
    facilities – nearly all of them are vulnerable to
    [XSS](Cross-site_Scripting_\(XSS\) "wikilink").

<!-- end list -->

  - Increase trust - Many large organizations outsource customer
    communications to third parties. Work with these organizations to
    make all e-mail communications appear to come from your organization
    (i.e., crm.example.com where example.com is your domain, rather than
    smtp34.massmailer.com or even worse, just an IP address). This goes
    for any image providers that are used in the main body.

<!-- end list -->

  - Increase trust - set up a Sender Policy Framework (SPF) record in
    your DNS to validate your SMTP servers. Phishing e-mails not sent
    from servers listed in your SPF records will be rejected by SPF
    aware MTAs. If that fails, scam messages will be flagged by newer
    MUAs like Outlook 2003 (with recent product updates applied),
    Thunderbird, and Eudora. Over time, this control will become more
    and more effective as ISPs, users and organizations upgrade to
    versions of software that has SPF enabled by default

<!-- end list -->

  - Increase trust - consider using S/MIME to digitally sign your
    communications

<!-- end list -->

  - Incident Response - Don’t send users e-mail notification that their
    account has been locked or fraud has occurred – if that has
    happened, just lock their accounts and provide a telephone number or
    e-mail address for them to contact you

## Never ask your customers for their secrets

Scammers will often ask your users to provide their credit card number,
password or PIN to “reactivate” their accounts. Often the scammers will
present part of a credit card number or some other verifier (such as
mother’s maiden name – which is obtainable via public records), which
makes the phish more believable.

Make sure your processes never need users’ secrets; even partial secrets
like the last four digits of a credit card, or rely on easily available
“secrets” that are obtainable from public records or credit history
transcripts.

Tell the users you will not ask them for secrets, and to notify you if
they receive an e-mail or visit a web page that looks like you and
requires them to type in their secrets.

## Fix all your XSS issues

Do not expose any code that has [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink") issues, particularly
unauthenticated code. Phishers often target vulnerable code, such as
redirectors, search fields, and other forms on your website to push the
user to their attack sites in a believable way.

For more information on XSS prevention, please see the User Agent
Injection section of the Interpreter Injection chapter.

## Do not use pop-ups

Pop-ups are a common technique used by scammers to make it seem like
they are coming from your domain. If you don’t use them, it makes it
much more difficult for scammers to take over a user’s session without
being detected.

Tell your users you do not use pop-ups and to report any examples to you
immediately.

## Don’t be framed

As pop-ups are now blocked by default by most browsers, phishers have
started to use iframes and frames to host malicious content whilst
hosting your actual application. They can then use bugs or features of
the DOM model to discover secrets in your application.

Use the TARGET directive to create a new window, which will usually
break out of IFRAME and other JavaScript jails. This usually means using
something like:

    <A HREF=”<u>http://www.example.com/login</u>” TARGET=”_top”>

to open a new page in the same window, but without using a pop-up.

Your application should regularly check the DOM model to inspect your
client’s environment for what you expect to see, and reject access
attempts that contain any additional frames.

This doesn’t help with Browser Helper Objects (BHO’s) or spyware
toolbars, but it can help close down many scams.

## Move your application one link away from your front page

It is possible to diminish native phishing attacks:

  - Make the authenticator for your application on a separate page.

<!-- end list -->

  - Consider implementing a simple referrer check. In section 11.11, we
    show that referrer fields are easily spoofed by motivated attackers,
    so this control doesn’t really work that well against even
    moderately skilled attackers, but closes off links in e-mails as
    being an attack vector.

<!-- end list -->

  - Encourage your users to type your URL or simply don’t provide a link
    for them to click.

Referrer checks are effective against indirect attackers such as
phishers – a hostile site cannot force a user’s browser to send forged
referrer headers.

## Enforce local referrers for images and other resources

Scammers will try to use actual images from your web site, or from
partner web sites (such as loyalty programs or edge caching partners
providing faster, nearby versions of images).

Make the scammers use their own saved copies as this increases the
chances that they will get it wrong, or the images will have changed by
the time the attack is launched.

The feature is typically called “anti-leeching”, and is implemented in
most of the common web servers but disabled by default in most. Akamai,
which calls this feature “Request Based Blocking”, and hopefully all
edge caching businesses, can provide this service to their customers.

Consider using watermarked images, so you can determine when the image
was obtained so you can trace the original spider. It may not be
possible to do this for busy websites, but it may be useful to watermark
an image once per day in such cases.

Investigate all accesses that enumerate your entire website or only
access images – you can spider your own website to see what it looks
like and to capture a sequence of access entries that can be used to
identify such activity. Often the scammers are using their own PCs to do
this activity, so you may be able to provide law enforcement with
probable IP addresses to chase down.

## Keep the address bar, use SSL, do not use IP addresses

Many web sites try to stop users seeing the address bar in a weak
attempt to prevent the user tampering with data, prevent users from book
marking your site, or pressing back, or some other feature. All of these
excuses do not help users avoid phishing attacks.

Data that is user sensitive should be moved to the session object or –
at worst – tamperproof, hidden fields. Book marking does not work if
authorization enforces login requirements. Pressing back can be defeated
in two ways – JavaScript hacks and sequence cookies.

Users should always be able to see your domain name – not IP addresses.
This means you will need to register all your hosts rather than push
them to IP addresses.

## Don’t be the source of identity theft

If you hold a great deal of data about a user, as a bank or government
institution might, do not allow applications to present this data to end
users.

For example, Internet Banking solutions may allow users to update their
physical address records. There is no point in displaying the current
address within the application, so the Internet Banking solution’s
database doesn’t need to hold address data – only back end systems do.

In general, minimize the amount of data held by the application. If it’s
not there to be pharmed, the application is safer for your users.

## Implement safe-guards within your application

Consider implementing:

  - If you’re an ISP or DNS registrar, make the registrant wait 24 hours
    for access to their domain; often scammers will register and dump a
    domain within the first 24 hours as the scam is found out.

<!-- end list -->

  - If an account is opened, but not used for a period of time (say a
    week or a month), disable it.

<!-- end list -->

  - Does all the registration info check out? For example, does the ZIP
    code mean California, but the phone number come from New York? If it
    doesn’t, don’t enable the account.

<!-- end list -->

  - Daily limits, particularly for unverified customers.

<!-- end list -->

  - Settlement periods for offsite transactions to allow users time to
    repudiate transactions.

<!-- end list -->

  - Only deliver goods to the customer’s home country and address as per
    their billing information (i.e., don’t ship a camera to Fiji if the
    customer lives in Noumea)

<!-- end list -->

  - Only deliver goods to verified customers (or consider a limit for
    such transactions).

<!-- end list -->

  - If your application allows updates to e-mail addresses or physical
    addresses, send a notification to both the new and old addresses
    when the key contact details change. This allows fraudulent changes
    to be detected by the user.

<!-- end list -->

  - Do not send existing or permanent passwords via e-mails or physical
    mail. Use one time, time limited verifiers instead. Send
    notification to the user that their password has been changed using
    this mechanism.

<!-- end list -->

  - Implement SMS or e-mail notification of account activities,
    particularly those involving transfers and change of address or
    phone details.

<!-- end list -->

  - Prevent too many transactions from the same user being performed in
    a certain period of time – this slows down automated attacks.

<!-- end list -->

  - Two factor authentication for highly sensitive or high value
    transactional accounts.

## Monitor unusual account activity

Use heuristics and other business logic to determine if users are likely
to act on a certain sequence of events, such as:

  - Clearing out their accounts

<!-- end list -->

  - Conducting many small transactions to get under your daily limits or
    other monitoring schemes

<!-- end list -->

  - If orders from multiple accounts are being delivered to the same
    shipping address.

<!-- end list -->

  - If the same transactions are being performed quickly from the same
    IP address

Prevent pharming - Consider staggering transaction delays using resource
monitors or add a delay. Each transaction will increase the delay by a
random, but increasing, amount so that by the 3rd or certainly by the
10th transaction, the delay is significant (3 minutes or more between
pages).

## Get the phishing target servers offline pronto

Work with law enforcement agencies, banking regulators, ISPs and so on
to get the phishing victim server (or servers) offline from the Internet
as quickly as possible. This does not mean destroy\!

These systems contain a significant amount of information about the
phisher, so never destroy the system – if the world was a perfect place,
it should be forensically imaged and examined by a competent computer
forensic examiner. Any new malicious software identified should be
handed over to as many anti-virus and anti-spyware companies as
possible.

Zombie and phishing server victims are usually unaware that their host
has been compromised and they’ll be grateful that you’ve spotted it, so
don’t try for a dawn raid with the local SWAT team.

If you think the server is under the direct control of a scammer, you
should let the law enforcement agencies handle the issue, as you should
never deal with the scammer directly for safety reasons.

If you represent an ISP, it’s important to understand that simply wiping
and re-imaging the server, whilst good for business, practically
guarantees that your systems will be repeatedly violated by the same
organized crime gangs. Of all the phishing victims, ISPs need to take
the most care in finding and resolving these cases, and work with local
and international law enforcement.

## Take control of the fraudulent domain name

Many scammers try to use homographs and similar or mis-spelt domain
names to spoof your web site. For example, if a user sees
<u><http://www.example.com></u>, but the x in example is a homograph
from another character set, or the user sees misspellings such as
<u><http://www.exmaple.com/></u> or <u><http://www.evample.com/></u> the
average user will not notice the difference.

It is important to use the dispute resolution process of the domain
registrar to take control of this domain as quickly as possible. Once
it’s in your control, it cannot be re-used by attackers in the future.
Once you have control, lock the domain so it cannot be transferred away
from you without signed permission.

Limitations with this approach include

  - There are an awful lot of domains variations, so costs can mount up

<!-- end list -->

  - It can be slow, particularly with some DRP policies – disputes can
    take many months and a lawyer’s picnic of cash to resolve

<!-- end list -->

  - Monitoring a TLD like .COM is nearly impossible – particularly in
    competitive regimes

<!-- end list -->

  - Some disputes cannot be won if you don’t hold a trademark or
    registration mark for your name, and even then…

<!-- end list -->

  - Organized crime is organized – some even own their own registrars or
    work so closely with them as to be indistinguishable from them.

## Work with law enforcement

The only way to get rid of the problem is to put the perpetrators away.
Work with your law enforcement agencies – help them make it easier to
report the crime, handle the evidence properly, and prosecute. Don’t
forward every e-mail or ask your users to do this, as it’s the same
crime. Collate evidence from your users, report it once, and make it
obvious that you take fraud seriously.

Help your users sue the scammers for civil damages. For example, advise
clients of their rights and whether class action lawsuits are possible
against the scammers.

Unfortunately, many scammers come from countries with weak or
non-existent criminal laws against fraud and phishing. In addition, many
scammers belong to (or act on behalf of) organized crime. It is
dangerous to contact these criminals directly, so always heed the
warnings of your law enforcement agencies and work through them.

## When an attack happens

Be nice to your users – they are the unwitting victims. If you want to
retain a customer for life, this is the time to be nice to them. Help
them every step of the way.

Have a phishing incident management policy ready and tested. Ensure that
everyone knows their role to restrict the damage caused by the attacks.

If you are a credit reporting agency or work with a regulatory body,
make it possible for legitimate victims to move credit identities. This
will allow the user’s prior actual history to be retained, but flag any
new access as pure fraud.

## Further Reading

  - Anti-phishing working group

<u><http://www.antiphishing.org/></u>

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Security Focus Area](Category:Security_Focus_Area "wikilink")