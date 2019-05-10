[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink") __TOC__

There are a number of tools to aid the wily application security
assessor. By far the most relevant to this type of security assessment
are local proxies and web/application spiders. To complete the full set
of WebGoat lessons a web-proxy will be required.

## Application Assessment Proxy

A normal web-proxy typically receives, processes and forwards HTTP and
HTTPS traffic between the client and server. This is normally to provide
a single point through which all web traffic passes – for example to
monitor usage, improve performance through caching or apply security
policies.

An application proxy tool is designed to intercept all HTTP and HTTPS
communication between the local client browser and the server-side. It
acts as a man-in-the-middle where all interaction may be monitored,
reviewed and (importantly) modified.

Through such a tool, the assessor can determine exactly what data is
passed between the Client and Server. Furthermore, they may analyze and
modify the data in order to test the impact of the application.

Another important reason to use an HTTP Proxy is WebGoat requiring Basic
Authentication. When automated tools are used to access WebGoat, they
might not have the functionality to authenticate to WebGoat. By using a
proxy like WebScarab, the tester can set the basic authentication
credentials that will be transparently passed to WebGoat when requested.

It is essential for many of the lessons within WebGoat that an
application assessment proxy, or software with equivalent functionality
be used.

The following are recommended:

  - WebScarab: <u>[WebScarab
    Project](:Category:OWASP_WebScarab_Project "wikilink")</u>
  - BurpProxy- <http://portswigger.net/>
  - ParosProxy - <http://parosproxy.org>

## Application Spider

Spidering or crawling a site should identify and follow all of the
intended pages and links within a web site & application, and optionally
store a local copy.

The results can then be analyzed to define a comprehensive list of
target scripts, forms, pages and fields within the application for use
in later testing.

Mirrored content can also be analyzed for relevant information far more
quickly than through a manual or ‘on the wire’ analysis.

The following are recommended:

  - WebScarab – [WebScarab
    Project](:Category:OWASP_WebScarab_Project "wikilink")
  - BurpSpider - <http://portswigger.net>
  - ParosProxy - <http://parosproxy.org>

[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")

[Category:OWASP WebGoat
Project](Category:OWASP_WebGoat_Project "wikilink")