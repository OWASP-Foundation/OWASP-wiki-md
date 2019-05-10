[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")__TOC__

The features within WebGoat for revealing the workings of the
application also need to be supplemented with the assessor’s application
assessment proxy of choice.

This enables further analysis and modification of the client-server
interaction, and data in transit.

Use and configuration will be unique to each tool, but the basic
concepts are as follows:

  - The application assessment proxy must sit *between* the client
    browser and the remote server.
  - It should allow the display and modification of all HTTP data in
    transit.

Typically, the tool will either plug directly into the browser, or
listen on another local port. When it plugs in directly, a special URL
may need to be entered in the browser. When the tool listens on a port,
the browser will probably need to be configured to use the proxy. In
Microsoft Internet Explorer this can be done from the tool menu by
choosing:

1.  Choose the “Tools/Internet Options” menu item.
2.  Choose the “Connections” tab
3.  Hit the “LAN Settings…” button.
4.  On the Local Area Network Settings dialog check the Proxy server
    checkbox.
5.  Uncheck the “bypass proxy server” box
6.  Enter the address and port where the proxy tool will be listening.
    The default listening port for WebScarab is 8008.

![Figure 7: LAN Settings](WebGoat_LAN_Settings.gif
"Figure 7: LAN Settings")

Now, when receiving or sending data from the client browser it is
possible to intercept, analyze and modify HTTP requests to test the
application for security flaws in the target.

For a tutorial on setting up and running WebScarab see: [WebScarab
Tutorial](WebScarab_Tutorial "wikilink")

  - In using proxies of this kind, a number of capabilities become
    available to the assessor, including:
  - All GET/POST parameters are available for modification, regardless
    of their hidden status
  - Cookies, both persistent and non-persistent may be modified when
    entering or leaving the browser
  - All client-side data validation can be bypassed, as the parameters
    can be modified immediately before being sent to the server
  - Information regarding the caching of data (e.g. Pragma: no-cache) is
    exposed for analysis
  - Server: and other headers are revealed, which may be useful for
    enumeration of the remote web-server and application-server
    technologies

[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")

[Category:OWASP WebGoat
Project](Category:OWASP_WebGoat_Project "wikilink")