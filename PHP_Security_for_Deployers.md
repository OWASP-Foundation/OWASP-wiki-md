## PHP Security for Deployers

### If you're a Developer

[READ THIS](http://www.owasp.org/index.php/PHP_Top_5) and then work with
your SysAdmins to step through any and all the layers of security
designed to protect your apps.

Example:

1.  1.  Traffic must first pass through a SPI firewall (ensure that ONLY
        necessary ports/protocols are permitted; ensure that EGRESS
        BLOCKING is in place so that if your system IS compromised it
        will be very difficult for the attacker to send data back or
        attack someone else via the Network Layer. (Need reference;
        "traditional" SPI-based firewall security).
    2.  Traffic may then pass through an in-line IPS (Intrusion
        Prevention System) to filter out network-based attacks against
        the OS, web platform, or PHP framework itself
    3.  Traffic may then pass through a WAF (Web Application Firewall)
        such as [ModSecurity](http://www.modsecurity.org/) or a
        commercial WAF to defeat basic script-based attacks
    4.  Traffic may then pass through an additional layer of security
        such as [PHP-IDS](http://php-ids.org/) to identify other attacks
        or concerns.
    5.  By the time traffic has passed through all the layers above,
        you've achieved a significant measure of mitigation HOWEVER you
        still need to follow all the best practices to "harden" PHP,
        perhaps by using
        [suhosin](http://www.hardened-php.net/suhosin.127.html).
    6.  Ditto for all other layers. Your SysAdmin should ensure that the
        OS and web server (iis, apache) are also hardened. See the NSA's
        [security configuration
        guides](http://www.nsa.gov/ia/guidance/security_configuration_guides/)
        to get started.
    7.  The rest is up to you, the developer. [Write secure
        code](http://icanhascheezburger.com/2007/11/27/meh-security-system-let-me-showz-u-him/).
        How difficult could
        [THAT](http://icanhascheezburger.com/2008/10/06/funny-pictures-doin-it-rathr-well-akshully/)
        be? All it takes is a little
        [work](http://icanhascheezburger.com/2007/07/18/i-is-workin-wat-u-want/)...

### If you're a Tester

1.  Note that [PHP-IDS](http://php-ids.org/) and
    [ModSecurity](http://www.modsecurity.org/)can also be useful tools
    for testing/discovering vulnerabilities in your code. See [Ryan
    Barnett's excellent
    presentation](https://www.owasp.org/images/f/fd/OWASP_Dynamic_Vulnerability_Identification_RyanBarnett200804.pdf)
    to the [Boulder OWASP
    chapter](http://www.owasp.org/index.php/Boulder) regarding using
    ModSecurity to identify app vulns on an ongoing basis.
2.  Grab the OWASP LiveCD
    [here(owasp.org)](http://www.owasp.org/index.php/Category:OWASP_Live_CD_Project)
    or [here(appseclive.org)](http://www.appseclive.org/) and review the
    great information in the [OWASP Testing
    Project](http://www.owasp.org/index.php/Category:OWASP_Testing_Project)

### If you're a SysAdmin

1.  BE PATIENT. NOBODY was born with a visceral understanding of how to
    write secure code, any more than YOU were born with the knowledge of
    how to harden YOUR components.
2.  Help out with all the items above.
3.  Have the developers buy you your favorite libation when you've
    completed all of the above items the first time. There's a pretty
    strong posibility that they are making better wages than you.

[Category:PHP](Category:PHP "wikilink")