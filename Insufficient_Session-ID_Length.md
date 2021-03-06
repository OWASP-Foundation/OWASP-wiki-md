Last revision (mm/dd/yy): **//**

[Vulnerabilities Table of Contents](ASDR_TOC_Vulnerabilities "wikilink")

## Description

Session identifiers should be at least 128 bits long to prevent
brute-force session guessing attacks.

The WebLogic deployment descriptor should specify a session identifier
length of at least 128 bits. A shorter session identifier leaves the
application open to brute-force session guessing attacks. If an attacker
can guess an authenticated user's session identifier, he can take over
the user's session. The remainder of this explanation will detail a
back-of-the-envelope justification for a 128 bit session identifier.

The expected number of seconds required to guess a valid session
identifier is given by the equation:

[image:session_id_guessing.gif](image:session_id_guessing.gif "wikilink")

Where:

  - B is the number of bits of entropy in the session identifier
  - A is the number of guesses an attacker can try each second
  - S is the number of valid session identifiers that are valid and
    available to be guessed at any given time

The number of bits of entropy in the session identifier is always less
than the total number of bits in the session identifier. For example, if
session identifiers were provided in ascending order, there would be
close to zero bits of entropy in the session identifier no matter the
identifier's length. Assuming that the session identifiers are being
generated using a good source of random numbers, we will estimate the
number of bits of entropy in a session identifier to be half the total
number of bits in the session identifier. For realistic identifier
lengths this is possible, though perhaps optimistic.

If attackers use a botnet with hundreds or thousands of drone computers,
it is reasonable to assume that they could attempt tens of thousands of
guesses per second. If the web site in question is large and popular, a
high volume of guessing might go unnoticed for some time.

A lower bound on the number of valid session identifiers that are
available to be guessed is the number of users that are active on a site
at any given moment. However, any users that abandon their sessions
without logging out will increase this number. (This is one of many good
reasons to have a short inactive session timeout.)

With a 64 bit session identifier, assume 32 bits of entropy. For a large
web site, assume that the attacker can try 1,000 guesses per second and
that there are 10,000 valid session identifiers at any given moment.
Given these assumptions, the expected time for an attacker to
successfully guess a valid session identifier is about 7 minutes. (32bit
= 4294967296 / 10.000 = 429496. At 1000 attempts per second that is 429
seconds or 7.15 minutes.)

Now assume a 128 bit session identifier that provides 64 bits of
entropy. With a very large web site, an attacker might try 10,000
guesses per second with 100,000 valid session identifiers available to
be guessed. Given these assumptions, the expected time for an attacker
to successfully guess a valid session identifier is greater than 292
years.

## Risk Factors

  - Attackers that are try to obtain a valid session ID for [Session
    hijacking](Session_hijacking_attack "wikilink").

## Examples

### Short example name

  -
    A short example description, small picture, or sample code with
    [links](http://www.site.com)

### Short example name

  -
    A short example description, small picture, or sample code with
    [links](http://www.site.com)

## Related [Attacks](Attacks "wikilink")

  - [Brute force attack](Brute_force_attack "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

\[\[Category:FIXME|link doesn't exist

  - Insufficient cryptographic key length\]\]

## Related [Controls](Controls "wikilink")

  - [:Category:Session
    Management](:Category:Session_Management "wikilink")

## Related [Technical Impacts](Technical_Impacts "wikilink")

  - [Technical Impact 1](Technical_Impact_1 "wikilink")
  - [Technical Impact 2](Technical_Impact_2 "wikilink")

## References

TBD

__NOTOC__

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Deployment](Category:Deployment "wikilink")
[Category:Java](Category:Java "wikilink") [Category:Environmental
Vulnerability](Category:Environmental_Vulnerability "wikilink")
[Category:Session Management
Vulnerability](Category:Session_Management_Vulnerability "wikilink")
[Category:Cryptographic
Vulnerability](Category:Cryptographic_Vulnerability "wikilink") [link
doesn't exist](Category:FIXME "wikilink")
[Category:WebLogic](Category:WebLogic "wikilink")