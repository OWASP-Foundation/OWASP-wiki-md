`    <td ``>Consider anyone who can monitor the network traffic of your users. If the application is on the internet, who knows how your users access it. Don’t forget back end connections.`

</td>

`    <td ``>Monitoring users’ network traffic can be difficult, but is sometimes easy. The primary difficulty lies in monitoring the proper network’s traffic while users are accessing the vulnerable site.`

</td>

`    <td colspan=2  ``>Applications frequently do not protect network traffic. They may use SSL/TLS during authentication, but not elsewhere, exposing data and session IDs to interception. Expired or improperly configured certificates may also be used.`

`Detecting basic flaws is easy. Just observe the site’s network traffic. More subtle flaws require inspecting the design of the application and the server configuration.`

</td>

`    <td ``>Such flaws expose individual users’ data and can lead to account theft. If an admin account was compromised, the entire site could be exposed. Poor SSL setup can also facilitate phishing and MITM attacks.`

</td>

`    <td ``>Consider the business value of the data exposed on the communications channel in terms of its confidentiality and integrity needs, and the need to authenticate both participants.`

</td>

The best way to find out if an application has sufficient transport
layer protection is to verify that:

1.  SSL is used to protect all authentication related traffic.
2.  SSL is used for all resources on all private pages and services.
    This protects all data and session tokens that are exchanged. Mixed
    SSL on a page should be avoided since it causes user warnings in the
    browser, and may expose the user’s session ID.
3.  Only strong algorithms are supported.
4.  All session cookies have their ‘secure’ flag set so the browser
    never transmits them in the clear.
5.  The server certificate is legitimate and properly configured for
    that server. This includes being issued by an authorized issuer, not
    expired, has not been revoked, and it matches all domains the site
    uses.

Providing proper transport layer protection can affect the site design.
It’s easiest to require SSL for the entire site. For performance
reasons, some sites use SSL only on private pages. Others use SSL only
on ‘critical’ pages, but this can expose session IDs and other sensitive
data. At a minimum, do all of the following:

1.  Require SSL for all sensitive pages. Non-SSL requests to these pages
    should be redirected to the SSL page.
2.  Set the ‘secure’ flag on all sensitive cookies.
3.  Configure your SSL provider to only support strong (e.g., FIPS 140-2
    compliant) algorithms.
4.  Ensure your certificate is valid, not expired, not revoked, and
    matches all domains used by the site.
5.  Backend and other connections should also use SSL or other
    encryption technologies.

<u>Scenario \#1</u>: A site simply doesn’t use SSL for all pages that
require authentication. Attacker simply monitors network traffic (like
an open wireless or their neighborhood cable modem network), and
observes an authenticated victim’s session cookie. Attacker then replays
this cookie and takes over the user’s session.

<u>Scenario \#2</u>: A site has improperly configured SSL certificate
which causes browser warnings for its users. Users have to accept such
warnings and continue, in order to use the site. This causes users to
get accustomed to such warnings. Phishing attack against the site’s
customers lures them to a lookalike site which doesn’t have a valid
certificate, which generates similar browser warnings. Since victims are
accustomed to such warnings, they proceed on and use the phishing site,
giving away passwords or other private data.

<u>Scenario \#3</u>: A site simply uses standard ODBC/JDBC for the
database connection, not realizing all traffic is in the clear.

For a more complete set of requirements and problems to avoid in this
area, see the [ASVS requirements on Communications Security
(V10)](http://www.owasp.org/index.php/ASVS#tab=Downloads).

  - [OWASP Transport Layer Protection Cheat
    Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")
  - [OWASP Top 10-2007 on Insecure
    Communications](Top_10_2007-Insecure_Communications "wikilink")
  - [OWASP Development Guide: Chapter on
    Cryptography](http://www.owasp.org/index.php/Guide_to_Cryptography#Insecure_transmission_of_secrets)
  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](Testing_for_SSL-TLS "wikilink")

<!-- end list -->

  - [CWE Entry 319 on Cleartext Transmission of Sensitive
    Information](http://cwe.mitre.org/data/definitions/319.html)
  - [SSL Labs Server Test](https://www.ssllabs.com/ssldb/index.html)
  - [Definition of FIPS 140-2 Cryptographic
    Standard](http://csrc.nist.gov/publications/fips/fips140-2/fips1402.pdf)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")