Applications frequently fail to encrypt network traffic when it is
necessary to protect sensitive communications. Encryption (usually SSL)
must be used for all authenticated connections, especially
Internet-accessible web pages, but backend connections as well.
Otherwise, the application will expose an authentication or session
token. In addition, encryption should be used whenever sensitive data,
such as credit card or health information is transmitted. Applications
that fall back or can be forced out of an encrypting mode can be abused
by attackers.

The PCI standard requires that all credit card information being
transmitted over the internet be encrypted.

## Environments Affected

All web application frameworks are vulnerable to insecure
communications.

## Vulnerability

Failure to encrypt sensitive communications means that an attacker who
can sniff traffic from the network will be able to access the
conversation, including any credentials or sensitive information
transmitted. Consider that different networks will be more or less
susceptible to sniffing. However, it is important to realize that
eventually a host will be compromised on almost every network, and
attackers will quickly install a sniffer to capture the credentials of
other systems.

Using SSL for communications with end users is critical, as they are
very likely to be using insecure networks to access applications.
Because HTTP includes authentication credentials or a session token with
every single request, all authenticated traffic needs to go over SSL,
not just the actual login request.

Encrypting communications with backend servers is also important.
Although these networks are likely to be more secure, the information
and credentials they carry is more sensitive and more extensive.
Therefore using SSL on the backend is quite important.

Encrypting sensitive data, such as credit cards and social security
numbers, has become a privacy and financial regulation for many
organizations. Neglecting to use SSL for connections handling such data
creates a compliance risk.

## Verifying Security

The goal is to verify that the application properly encrypts all
authenticated and sensitive communications.

Automated approaches: Vulnerability scanning tools can verify that SSL
is used on the front end, and can find many SSL related flaws. However,
these tools do not have access to backend connections and cannot verify
that they are secure. Static analysis tools may be able to help with
analyzing some calls to backend systems, but probably will not
understand the custom logic required for all types of systems.

Manual approaches: Testing can verify that SSL is used and find many SSL
related flaws on the front end, but the automated approaches are
probably more efficient. Code review is quite efficient for verifying
the proper use of SSL for all backend connections.

## Protection

The most important protection is to use SSL on any authenticated
connection or whenever sensitive data is being transmitted. There are a
number of details involved with configuring SSL for web applications
properly, so understanding and analyzing your environment is important.
For example, IE 7.0 provides a green bar for high trust SSL
certificates, but this is not a suitable control to prove safe use of
cryptography alone.

  - Use SSL for all connections that are authenticated or transmitting
    sensitive or value data, such as credentials, credit card details,
    health and other private information
  - Ensure that communications between infrastructure elements, such as
    between web servers and database systems, are appropriately
    protected via the use of transport layer security or protocol level
    encryption for credentials and intrinsic value data
  - Under PCI Data Security Standard requirement 4, you must protect
    cardholder data in transit. PCI DSS compliance is mandatory by 2008
    for merchants and anyone else dealing with credit cards. In general,
    client, partner, staff and administrative online access to systems
    must be encrypted using SSL or similar. For more information, please
    see the PCI DSS Guidelines and implement controls as necessary

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6430>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-4704>
  - <http://www.schneier.com/blog/archives/2005/10/scandinavian_at_1.html>

## References

  - CWE: CWE-311 (Failure to encrypt data), CWE-326 (Weak Encryption),
    CWE-321 (Use of hard-coded cryptographic key), CWE-325 (Missing
    Required Cryptographic Step), others.
  - WASC Threat Classification: No explicit mapping
  - OWASP *Testing Guide*, [Testing for
    SSL-TLS](Testing_for_SSL-TLS_\(OWASP-CM-001\) "wikilink")
  - OWASP Development Guide,
    [Guide_to_Cryptography](Guide_to_Cryptography "wikilink")
  - Foundstone - SSL Digger,
    <http://www.foundstone.com/index.htm?subnav=services/navigation.htm&subcontent=/services/overview_s3i_des.htm>
  - NIST, SP 800-52 Guidelines for the selection and use of transport
    layer security (TLS) Implementations,
    <http://csrc.nist.gov/publications/nistpubs/800-52/SP800-52.pdf>
  - NIST SP 800-95 Guide to secure web services,
    [<http://csrc.nist.gov/publications/drafts.html#sp800-95>](http://csrc.nist.gov/publications/drafts.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")