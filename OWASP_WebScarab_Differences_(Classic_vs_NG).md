**This page is intended to document the differences between WebScarab
Classic and WebScarab Next Generation**

The objective is to list the major features that one has over the other,
with the intent to track the porting of desirable features from Classic
to NG.

## Framework functionality

NG has no concept of the shared cookie jar, which is used in Classic to
allow plugins such as the Spider and Manual Request plugins to use the
most current cookies for a particular URL. This could/should be replaced
by an Identity module, which can provide the most current identifiers
for a particular identity (cookies, Basic auth, etc).

NG now also has the Transcoder functionality, implemented as a non-modal
dialog. It is intended to also implement "right-click" menus to perform
various transcoding operations "in-place" in arbitrary text fields.

## Plugins

NG has significantly fewer plugins than Classic. The only plugins
currently implemented in NG are the Proxy, Manual Request and
WebServices plugins.

This leaves the following plugins to be implemented:

  - Spider
  - Extensions
  - XSSCRLF
  - SessionIDAnalysis
  - Scripting
  - Fragments
  - Compare
  - Search

### Proxy

Features that remain to be ported:

  - BeanShell scripts for programmatic modification of
    requests/responses
  - Miscellaneous proxy plugins - Reveal hidden fields, prevent caching
    of responses
  - Ability to modify Internet Explorer proxy settings automatically on
    startup and exit

### Manual Request

Features that remain to be ported:

  - Ability to convert a request from a GET to a POST or multipart POST,
    and vice versa.

### WebServices

Partially completed. Currently it is sufficient to access the WebGoat
web service.

Features that remain to be ported:

  - Support for complex types (This functionality could easily be added
    if desired)

## HTTP Protocol support

WebScarab-classic has support for authentication to servers using SSL
client certificates (including those stored on a smart card), as well as
using NTLM. NG does not currently support SSL client certificates at
all. NTLM should be supported through the Apache HTTPClient library, but
this has not been tested.

## Porting suggestions

For people interested in contributing to this project by porting one of
the above plugins, here are some suggestions:

  - SessionID analysis

The current session id analysis plugin, while looking cool is actually
very misleading. Anyone wanting to implement this feature for NG would
be advised to take a look at Michal Zalewski's stompy to see how it can
be done better.

  - Search, Compare

These plugins are very clunky to use. It actually makes a lot more sense
to make those features available as part of the primary interface,
rather than relegating them to a backwater. Search should provide a
simple interface where the operator can type some text and click Go,
rather than having to write code.

## Execution

WebScarab NG is distributed using the Maven onejar plugin, which
packages all the required jars into a subdirectory of the "onejar", and
provides a specialised classloader to allow Java to access the contents
of those jars. To start WebScarab NG use following command in jar
directory

`java -jar WebScarab-ng-X.X.X.one-jar.jar`

where X.X.X is downloaded version or use one of scripts (start.sh for
Linux, start.bat for Windows) provided in WebScarab NG zip file (which
can be found
[here](https://code.google.com/p/webscarab-ng/downloads/list)).

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink") [Category:OWASP
WebScarab NG Project](Category:OWASP_WebScarab_NG_Project "wikilink")