

**Reflected File Download** is an attack combining [URL path
segments](http://stackoverflow.com/questions/2163803/what-is-the-semicolon-reserved-for-in-urls)
(now deprecated) with pages that reflects user inputs in the response.
Generally web services vulnerable to [JSONP
Injection](https://securitycafe.ro/2017/01/18/practical-jsonp-injection/)
are used to deliver malware to end users.

Let's assume we have a vulnerable API that reflects whatever we send to
it (the URL was real apparently, now fixed):

`   `<hxxps://google.com/s?q=rfd%22>

| |calc | |

`   {"results":["q", "rfd\"||calc||","I love rfd"]}`

Now, this is normally harmless in a browser as it's JSON so it's not
going to be rendered but the browser will rather offer to download the
response as a file. Now here's the path segments come to help the
attacker:

`   `<hxxps://google.com/s;/setup.bat>`;?q=rfd%22`

| |calc | |

Everything between semicolons (\`;/setup.bat;\`) will be not sent to the
web service, but instead the browser will interpret it as the file
name... to save the API response. Now, a file called setup.bat will be
downloaded and run without asking about dangers of running files
downloaded from Internet (because it contains the word "setup" in its
name). The contents will be interpreted as Windows batch file, and the
\`calc.exe\` command will be run.

Prevention:

  - sanitize your API's input (in this case they should just allow
    alphanumerics); escaping is not sufficient
  - add \`Content-Disposition: attachment; filename="whatever.txt"\` on
    APIs that are not going to be rendered; Google was missing the
    filename part which actually made the attack easier
  - add \`X-Content-Type-Options: nosniff\` header to API responses

References:

  - [Oren Hafif "Reflected File Download A New Web Attack Vector",
    BlackHat
    EU 2014](https://www.blackhat.com/docs/eu-14/materials/eu-14-Hafif-Reflected-File-Download-A-New-Web-Attack-Vector.pdf)

Last revision (mm/dd/yy): **//**

__NOTOC__

## Overview

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Security Focus Area](Category:Security_Focus_Area "wikilink")