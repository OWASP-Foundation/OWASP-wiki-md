## The presentation

![Felipe_Moreno-Strauch.jpg](Felipe_Moreno-Strauch.jpg
"Felipe_Moreno-Strauch.jpg")This talk will suggest a new approach for
web application input validation testing and introduce Groundspeed, an
open-source Firefox extension that manipulates the interface of web
applications in order to make the life of the security tester easier.
Today, most of the manual parameter manipulation tests in web
applications are performed using tools that modify the raw HTTP requests
sent to the server. While this approach works best on simple
applications, it is often inappropriate for more complex applications.
Groundspeed is a Firefox extension that allows the security tester to
modify the application user interface by manipulating the forms and form
elements, eliminating annoying limitations and client-side controls.
Some of the practical uses of Groundspeed include changing all hidden
fields into text fields, removing size limitations on input fields and
modifying JavaScript event handlers to bypass client side validation
without actually removing it. The extension works by dynamically
modifying the Document Object Model (DOM) of the page after Firefox has
finished loading and rendering it. The changes take effect immediately
and, since it happens entirely on the client side without generating new
requests to the server, it is completely transparent to the application.
More information, including a link to download and install groundspeed
is available here: <http://groundspeed.wobot.org>.

## The speaker

Felipe Moreno is a manager at the Ernst & Young Advanced Security Center
(ASC), based in New York City. He has more than 8 years of information
security experience performing application security reviews and
penetration tests in addition to teaching secure coding classes to
Fortune 500 clients both in the US and Europe.

[Category:OWASP_AppSec_DC_09](Category:OWASP_AppSec_DC_09 "wikilink")
[Category:OWASP_Conference_Presentations](Category:OWASP_Conference_Presentations "wikilink")