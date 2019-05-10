**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Arturo Busleiman (a.k.a Buanzo)

**Project coordinator**: Dinis Cruz

**Project Progress**: 70% Complete, [Progress
Page](SpoC_007_-_Enigform:_Firefox_Addon_for_OpenPGP_signing_of_HTTP_requests_-_Progress_Page "wikilink")

## Buanzo -Firefox Addon (Enigform) and Apache Module (mod_openpgp) to extend HTTP with OpenPGP capabilities

### Arturo "Buanzo" Busleiman

I am a 25 year old Independent security consultant from Buenos Aires,
Argentina, that has contributed to the world of information systems
security since 1994, when BBSes and Linux still lived together.

A quick search for buanzo on google
[1](http://www.google.com/search?hl=en&q=buanzo&btnG=Google+Search) will
provide all necessary details about my professional and community
background. For comprobable experience, you could also check my Rent a
Coder
profile.[2](http://www.rentacoder.com/RentACoder/SoftwareCoders/showBioInfo.asp?lngAuthorId=735204).

In my free time I like playing with my Punk-Pop band
[3](http://www.jamendo.com/es/artist/futurabanda/), Futurabanda.
[4](http://www.futurabanda.com.ar), and maintaining my Restaurants,
Wines and Recipes site. [5](http://www.vivamoslavida.com.ar). I have to
admit that my first priorities are my beloved son
[6](http://www.fotolog.com/buanzo) and my wonderful wife
[7](http://www.fotolog.com/buanzo).

### Accomplishments

I've contributed scripts, fixes and translations to the Nmap project.
I've also acted as Expert Contributor for SANS TOP-20 2004, 2005 and
2006. I've developed tools that can be found in Freshmeat, like mprl (a
getty enhancement to allow remote logins from the login: prompt of the
console). I've also written the Unix chapter of the OISSG's Information
Systems Security Assessment Framework, v0.1
[8](http://www.oissg.org/content/view/71/71/). I'm currently writing an
Internet Draft to be proposed for RFC named "OpenPGP Extensions to
HTTP".

### Community

I "run" the 2600 meetings site for Argentina
[9](http://www.2600.com/meetings/pages.html), I've been proposed, but I
refused, for President of the Argentinian Free Software group called
SOLAR \[www.solar.org.ar\]. I'm an active member of the FLOSS community
since 1996, having written articles in magazines
<http://www.net-security.org/dl/articles/Detecting_and_Understanding_rootkits.txt>,
made TV, radio and newspaper appearances
[10](http://codigoabierto.bitacoras.com/archivos/2005/04/01/buanzo-hacks)
and led different security research groups of Spain, Mexico and
Argentina. Currently I contribute time thorugh my sites, forums and
blogs, answering questions in mailing lists and helping coordinate some
local LUGs. I do also manager the Linux Counter for Argentina
[11](http://counter.li.org/reports/place.php?place=AR).

### My Project

Enigform [12](http://enigform.mozdev.org) is a Firefox extension that
enhances HTTP with OpenPGP functionality. It digitally signs and/or
encrypts outgoing HTTP requests so that a web server can authenticate
the identity and data of the incoming request. It is a Web Security tool
because it can, if correctly implemented as any OpenPGP based
technology, render man in the middle attacks useless. I think OpenPGP
already speaks for itself regarding eMail. Imagine the same benefits for
http and web applications. I think Enigform can fit into the OWASP
Validation Project
[13](http://www.owasp.org/index.php/Category:OWASP_Validation_Project).

Enigform is the reference implementation of the Internet Draft I'm
working on, in discussion with members of the IETF's OpenPGP Working
Group.

Some simple PHP code is enough to make a web application Enigform-aware
[14](http://enigformtest.buanzo.com.ar). The Smutty PHP MVC Framework
already supports Enigform [15](http://smutty.pu-gh.com/demo/enigform),
but the best approach is to use the Apache module I'm writing, called
mod_auth_openpgp (which will be renamed to mod_openpgp as it
evolves).

### Long Term

Have the Draft be proposed as a Standards Track RFC document, have
Enigform support directly in MS IIS, and port Enigform to other browsers
and/or programming languages, and also provide OpenPGP De/Encryption
support.

### Why should I be selected

I have the experience, security awareness and means to make this project
THE web security project of the decade. I am a respected member of the
international security community, and I firmly believe Enigform is my
greatest idea so far.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**