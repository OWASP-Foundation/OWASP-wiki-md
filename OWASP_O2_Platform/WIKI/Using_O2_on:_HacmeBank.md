Note: HacmeBank is about to become an OWASP Project: see
[HacmeBank](HacmeBank "wikilink")

This page contains information about HacmeBank and O2 can be used to
find, exploit and mitigate its vulnerabilities

## Links

  - original version of
    HacmeBank:<http://www.foundstone.com/us/resources/proddesc/hacmebank.htm>
  - updated version of HacmeBank (O2's website):
    <http://www.o2-ounceopen.com/technical-info/2008/12/8/updated-version-of-hacmebank.html>
      - download: HacmeBank_v2.0 (Dinis version - 7 Dec 08).zip
      - video:
        <http://www.o2-ounceopen.com/storage/videos/HacmeBank%20-%20Features.wmv>
      - video:
        <http://www.o2-ounceopen.com/storage/videos/HacmeBank-%20Using%20the%20SQL%20Injection%20Database%20Explorer.wmv>
  - google query on HackmeBank :
    <http://www.google.com/search?q=hacmebank>

## Notes:

**Removing 'OnlyAllowLocalAccess' restriction**

By default (to prevent accidental exploitation) non-local requests are
not allowed (i.e. only <http://127.0.0.1> will work).

To allow such accesses, edit the Hacme Bank's website web.config (in
HacmeBank_v2_Website folder) and comment out the
HttpModule_onlyAllowLocalAccess line in the <httpModules> section.

To also access (and 'unprotect') the Webservices, remove the same line
from the web.config file that is in the HacmeBank_v2_WS folder

**Installing on non-US English systems**

The [Hacme Bank
v2](http://www.foundstone.com/us/resources/proddesc/hacmebank.htm)
available from Foundstone/McAfee only works on systems where the
regional settings are set to the United States. Although, it at first
appears to work, lots of the application interactions and database calls
fail with ugly error messages. The easiest fix is to build a dedicated
server using US English settings from the ground-up.

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")