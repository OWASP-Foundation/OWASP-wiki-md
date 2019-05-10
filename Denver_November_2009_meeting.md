## Wednesday 18 November 2009, 6pm @ [Raytheon Polar Services](http://maps.google.com/maps?f=q&hl=en&q=7400%20S%20Tucson%20Way%2C%20Englewood%2C%20CO)

### Anton Rager: "The Evils of XSS: Its not just for cookies anymore"

Many security professionals, security administrators and developers are
aware of Cross-Site Scripting (XSS) vulnerabilities, but disregard them
as a significant risk to an organization. Traditionally XSS attacks have
either involved nuisance re-direction of a client or leakage of client
cookies/state information to an attacker. They are almost always a
one-shot XSS exploit against a vulnerable server and dont have the
ability to execute multiple transactions against an XSS vulnerable site.

This presentation briefly outlines current XSS attacks, then discusses
and demonstrates methods to create multi-transaction XSS attacks or
persistent XSS based browser hi-jacking. Browser hi-jacking uses the
victim browser to leverage existing trust that a browser may have with
an XSS vulnerable site, and performs an arbitrary number of transactions
from the victim browser against the vulnerable site. This means that the
attacker can use the victims browser to attack a site that is behind a
firewall, requires client-side certificates, filters IP addresses, or
has a cached authentication with the victim browser this is way beyond
cookie theft as an attacker is actually using the victims browser to
access the site. Attack modes can include transparent site traversal
thru victim browser (read and/or write to server with access of victim
from remote attack console), passive monitoring of victim interaction
with target site, or active MITM content modification of information
to/from victim browser.

A custom tool (XSS-Proxy) will be demonstrated that demonstrates the
ability for a remote attacker to perform these XSS based attacks. XSS
persistence and commands are controlled from a Perl based HTTP attack
server with victim/XSS target content forwarded to the same server. This
does not rely on any new vulnerability in browsers and currently works
in modern JavaScript enabled IE and Mozilla/Firefox based browsers.

Presenter: **Anton Rager**

Anton Rager is an independent security researcher focused on
vulnerability exploitation, VPN security and wireless security. He is
currently a programmer with an undisclosed network storage startup where
he focuses on application development, Linux network magic, and Linux
kernel/driver hacking.

He is best known for his work with 802.11 wireless WEP security and
associated testing/analysis tools. In 2001 he released WEPCrack, the
first open-source, public domain utility to validate the WEP/RC4 attack
discovered by Fluhrer, Mantin and Shamir. Anton was also a Contributing
Technical Editor to the book Maximum Wireless Security. In 2003 he
continued researching 802.11/WEP and developed an injection attack and
open-source tool (WEPWedgie) that allows network scanning attacks of WEP
encrypted networks without knowledge of WEP keys. This tool/attack is
mentioned in the book WI-FOO: The Secrets of Wireless Hacking as well as
multiple online articles.

Anton has also focused heavily on IPSec VPN security issues and in 2001
implemented the first open-source utility to allow password attacks
against IKE based IPSec VPN connections (IKECrack). Follow-on IPSec
research resulted in an IKE protocol testing tool (IKEProber) that
highlighted multiple vulnerabilities in common IPSec client/gateway
implementations.

More recently he has been working with web application security issues
and in 2005 devised a novel Cross-Site-Scripting (XSS) attack method and
open-source tool (XSS-Proxy) to allow browser hijacking with XSS
vulnerable sites. This tool/attack is also highlighted in Phishing
Exposed book and as well as the book XSS-Attacks that he co-authored
with other leading XSS researchers.

Anton has presented at well-known security conferences and has conducted
many security training and security awareness primers with industry and
government sectors. He currently resides and works near Denver,
Colorado. In addition to an addictive computer security hobby, Anton is
also an extreme mountain biker, snowboarder, naturalist, guitarist and
philosopher hack.

### Agenda

  - 6pm: Pizza & pop @ [Raytheon Polar
    Services](http://maps.google.com/maps?f=q&hl=en&q=7400%20S%20Tucson%20Way%2C%20Englewood%2C%20CO),
    courtesy of [Accuvant](http://www.accuvant.com/)
  - 6:30pm: Introduction and Chapter business
  - 6:45pm --\> 8pm: Presentation

[Back to OWASP Denver](https://www.owasp.org/index.php/Denver)