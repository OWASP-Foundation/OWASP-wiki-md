#### Main

## New User Interface

As mentioned above, the user interface has changed quite a lot from the
old WebScarab. Apart from the new default Look\&Feel (JGoodies), you
will see that the conversation viewer has changed quite a lot. The old
"Raw" view is still there, but the Parsed version has changed quite
dramatically - for the better, I hope you'll agree\!

The Parsed view now shows the request and response details in a tree
form, rather than in individual text boxes. This makes the interface
look a lot cleaner, and more importantly, is a lot more compact. It also
makes it a lot easier to include features like automatically breaking
out URL parameters, and multiple cookies into their own nodes, where it
is a lot easier to view the individual parameters. We also show the
request and the response next to each other, rather than one above the
other, since most people seem to have more horizontal real-estate than
vertical. The split between request and response can easily be adjusted
by dragging, as can the split between the headers and the message
content.

![Image:WebScarab-NG-default.png](WebScarab-NG-default.png
"Image:WebScarab-NG-default.png")

## Current status

At this stage, WebScarab-NG primary feature is the intercepting proxy
that allows the operator to observe and modify requests from a browser
or other client passing through the proxy. A new feature is the Proxy
Control Bar, which is implemented as a "stays on top" tool bar that
floats above your browser or other thick client, and allows you to
quickly enable or disable request intercepts. It also allows you to
annotate or describe the requests as they pass through the proxy. If you
type some text into the annotation field, that text will be linked to
the next conversation that passes through the proxy, and can later be
viewed as part of the conversation history. this can be very helpful to
keep track of what you were doing in a multi-step procedure.

For example: Selecting a menu item, entering a value, submitting that
value, etc. Often sites are built in such a way that they can result in
dozens of conversations resulting from a single action. Annotating that
conversation that initiated all the rest makes it very easy to identify
them at a later stage.

![Image:WebScarab-NG-proxy-control-bar.png](WebScarab-NG-proxy-control-bar.png
"Image:WebScarab-NG-proxy-control-bar.png")

## Error feedback

One of the neat features provided by the Spring Rich Client Platform is
the ability to check that the inputs actually make sense, and to provide
automated "as you type" feedback to the user.

For example, look at the "Intercept Request" window:

![Image:WebScarab-NG-intercept-request-error.png](WebScarab-NG-intercept-request-error.png
"Image:WebScarab-NG-intercept-request-error.png")

We can see that the user tried to change the method from "POST" to
"PROST". WebScarab-NG has no idea how to execute a "PROST" method, and
so provides an error message to inform the user. Additionally, the OK
button is automatically disabled, until the error is corrected.

## Obtaining WebScarab-NG

WebScarab-NG is distributed via Google Code, and can be obtained
[here](https://code.google.com/p/webscarab-ng/downloads/list).

After extraction of files user need to run following command:

`java -jar WebScarab-ng-X.X.X.one-jar.jar`

where X.X.X is downloaded version or use one of scripts (start.sh for
Linux, start.bat for Windows).

## Technical information

Technical information for those interested in digging into it can be
found [here](OWASP_WebScarab_NG_Project_Technical_Info "wikilink").

This page lists the [differences between WebScarab Classic and WebScarab
NG](OWASP_WebScarab_Differences_%28Classic_vs_NG%29 "wikilink"),
including a ToDo list of work still to be done on WebScarab NG.

## Tips & Tricks

WebScarab NG already contains a lot of functionality but some of them
are well hidden beneath the GUI and nowhere documented. A list of such
functions can be found in the [Tips & Tricks of WebScarab
NG](OWASP_WebScarab_NG_Tips_&_Tricks "wikilink") section.

## Bugs

Any found bugs should be reported via [WebScarab NG Google Code issues
page](https://code.google.com/p/webscarab-ng/issues/list). Such
mechanism allows us to keep track of all found problems so we can
WebScarab-NG better.

## Feedback

If you have any comments or suggestions for WebScarab-NG, please feel
free to post them on [WebScarab NG Google Code issues
page](https://code.google.com/p/webscarab-ng/issues/list) or send them
to the [OWASP WebScarab mailing
list](http://lists.owasp.org/mailman/listinfo/owasp-webscarab)

Your feedback is much appreciated, and will be carefully considered for
future releases of WebScarab-NG.

## Project Contributors

The WebScarab-NG project is run by Daniel Brzozowski. He can be
contacted at ![<File:Db.png>](Db.png "File:Db.png").

#### Project About

__NOTOC__ <headertabs />

[WebScarab NG Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Download](Category:OWASP_Download "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")