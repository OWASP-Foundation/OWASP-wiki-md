This document is intended to explain how to configure WebScarab to chain
onto an upstream proxy.

I assume that you are familiar with the basic functionality of
WebScarab, and have managed to use it as a proxy to view and intercept
some conversations already. If not, I suggest reading the ["Getting
Started"](WebScarab_Getting_Started "wikilink") document first.

**[Stephen Venter](User:Stephen_Venter "wikilink")** 07:37, 16 March
2007 (EDT)

## Overview

In the case where you are browsing via a proxy server on your local
network, such as is often the case with corporate networks, you will
need to configure WebScarab to chain onto that proxy server if it is to
work correctly.

Some people refer to this as "Using WebScarab behind a firewall", since
it is the firewall that will be blocking all outgoing browser traffic,
other than the traffic which originates via the proxy server. But really
it is the proxy server that is the key to getting WebScarab working in
this circumstance.

## Outline of the setup for this example

To do this you obviously need to know that your proxy server’s IP
address (or its hostname that resolves on your LAN) together with the
port number that the proxy server listens on. For simplicity sake, let’s
assume I have a local LAN with network range 192.168.1.0 /24 (which
means it has a netmask of 255.255.255.0)and my proxy server is at IP
192.168.1.10 and it listens on port 8080.

If you are not sure what your proxy server’s IP address is and someone
else set up your browser such that it is correctly browsing via the
proxy, you may be able to view it within your browser’s configuration
settings (where it has been manually configured and is not being
automatically picked up by the browser – there are other ways of working
it out in that case, but I won’t go into that here).

Since I am using Microsoft Internet Explorer in this example, I see my
proxy settings here: Tools -\> Internet Options -\> Connections -\> LAN
settings -\> Use Proxy Server for your LAN -\> Address: 192.168.1.10
Port: 8080

I am running WebScarab locally on my PC, using the standard settings.
Thus it will be listening on the standard localhost IP address of
127.0.0.1 on port 8008. Some people like to use the name "localhost", I
prefer to use the IP address "127.0.0.1" – but they are interchangeable,
so it won’t matter which you use.

## Step One: Configuring WebScarab to point at my internal network proxy

Note: The port number "3128" is the default value included with the
WebScarab setting for chaining onto another proxy server (Tools -\>
Proxies). It does not necessarily mean that it is the correct port
number you should use for your network. In my example outline above, my
local network proxy is configured to listen on a port "8080". So that is
the value I have to use in WebScarab in: Tools -\> Proxies -\> \["Port"
box for both the "HTTP Proxy" and "HTTPS Proxy"\]

Once I have set that correctly, then WebScarab can make connections out
of my network via my local network proxy.

**CAUTION\!\!** Make sure that the proxy you specify via Tools -\>
Proxies does not point back to WebScarab's proxy port, otherwise you
will end up creating an infinite loop, since WebScarab will now try to
use itself as the upstream proxy and will simply run out of sockets or
available memory.

**Note:** If you are using WebScarab on Windows, and Internet Explorer
is correctly accessing the outside network through your designated
proxy, you may simply be able to access the WebScarab upstream proxy
setting via Tools -\> Proxies, and click the "Get IE Settings" button.
This only works for the "Installer" version of WebScarab, not the Java
WebStart or "selfcontained" versions, since it relies on a native
Windows library to read this information.

## Step Two: Configuring my web browser to send connections via WebScarab

This step is the usual one to use for getting WebScarab to work whether
or not I am setting it to chain onto another internal proxy.

The number "3128" is NOT the correct number to use in IE. Also, the
network proxy server IP is not what I want to use here either anymore
(unless I am connecting out to the internet directly without WebScarab
in-between).

As outlined above, I am running webscarab locally on the same PC as I am
browsing from. So in IE, I need to put the value "127.0.0.1" into the
"Address" box and "8008" into the "Port" box as follows: Tools -\>
Internet Options -\> Connections -\> LAN settings -\> Use Proxy Server
for your LAN -\> Address: 127.0.0.1 Port: 8008

Also, I suggest leaving the box for "Automatically detect settings"
un-checked / un-ticked. And same goes for the "Bypass proxy server for
local addresses" box. If you are intending to only use WebScarab when
making connections to sites outside your local network, it doesn't
matter. But if you then try to connect to a website on your local LAN,
that setting will result in IE connecting directly to that local web
server without proxying via WebScarab. So for safety sake, I suggest
keeping that box un-checked too.

Now I have:

  - my web browser forwarding connections via WebScarab, which is
    listening on 127.0.0.1:8008
  - and WebScarab forwarding connections out of my network via my
    network proxy on IP 192.168.1.10 and port number 8080 (a.k.a.
    WebScarab is chaining onto that proxy 192.168.1.10:8080).

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink")