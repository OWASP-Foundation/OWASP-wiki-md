## Objective

To make repetitive modifications to either requests or responses (or
both) as they pass through the proxy

## Approach

Write a script to make the modifications as desired. Scripts can be
written in the Proxy-\>BeanShell plugin, or attached to Hooks in the
ScriptManager interface. Depending on which you choose, the script
itself changes a little.

## What methods exist to manipulate the request and response?

The request and response are instances of the Request and Response
classes, respectively. These classes both extend the Message class which
provides functionality common to both.

The Message class provides the following methods, which are common to
both the Request and Response classes:

`  String[] getHeaderNames()`
`  String getHeader(String name)`
`  void setHeader(String name, String value)`
`  void addHeader(String name, String value)`
`  void deleteHeader(String name)`
`  NamedValue[] getHeaders()`
`  void setheaders(NamedValue[] headers)`
`  byte[] getContent()`
`  void setContent(byte[] content)`

The Request class adds the following methods:

`  String getMethod()`
`  void setMethod(String method)`
`  HttpUrl getURL()`
`  void setURL(HttpUrl url)`
`  void setURL(String url) throws MalformedURLException`
`  String getVersion()`
`  void setVersion(String version)`

The Response class adds the following methods:

`  String getVersion();`
`  void setVersion(String version);`
`  String getStatus();`
`  void setStatus(String status);`
`  String getMessage();`
`  void setMessage(String message);`
`  String getStatusLine();`

## Using the Proxy-\>BeanShell plugin

The Proxy-\>BeanShell plugin comes supplied with a very simple script to
show you how to get access to the request and response objects.
Unfortunately, it doesn't provide much assistance on how to go forward
from there. Here is an example, showing you how to reject all requests
for Flash content:

`  import org.owasp.webscarab.model.HttpUrl;`
`  import org.owasp.webscarab.model.Request;`
`  import org.owasp.webscarab.model.Response;`
`  import org.owasp.webscarab.httpclient.HTTPClient;`
`  import java.io.IOException;`
`  `
`  public Response fetchResponse(HTTPClient nextPlugin, Request request) throws IOException {`
`     HttpUrl url = request.getURL();`
`     if (url.toString().endsWith(".swf"))`
`         throw new IOException("No flash content allowed");`
`     response = nextPlugin.fetchResponse(request);`
`     return response;`
`  }`

Here's an example showing how to replace a particular string in a
JavaScript response:

`  import org.owasp.webscarab.model.Request;`
`  import org.owasp.webscarab.model.Response;`
`  import org.owasp.webscarab.httpclient.HTTPClient;`
`  import java.io.IOException;`
`  `
`  public Response fetchResponse(HTTPClient nextPlugin, Request request) throws IOException {`
`     response = nextPlugin.fetchResponse(request);`
`     String cType = response.getHeader("Content-Type");`
`     if (cType != null && cType.endsWith("javascript")) {`
`        byte[] bytes = response.getContent();`
`        if (bytes != null) {`
`           String content = new String(bytes);`
`           content = content.replace("my search string", "my replacement");`
`           response.setContent(content.getBytes());`
`        }`
`     }`
`     return response;`
`  }`

## So, what's with the ScriptManager?

The ScriptManager is intended to provide a more generic interface to
scripting throughout WebScarab. Each plugin can provide Hooks that can
have scripts attached to them. Each Hook provides a brief explanation of
how to use it. The Proxy provides 3 hooks:

  - Allow Connection

Called when a new connection is received from a browser Use
connection.getAddress() and connection.closeConnection() to decide and
react

This hook is intended to provide a measure of security in installations
where WebScarab is allowing connections from non-localhost interfaces.
Here is an example of how it may be used:

`  import java.net.InetAddress;`
`  `
`  InetAddress from = connection.getAddress();`
`  if (! from.getHostAddress().startsWith("192.168.1.")) `
`     connection.closeConnection();`

This script rejects all connections from hosts outside the 192.168.1
subnet.

  - Intercept Request

Called when a new request has been submitted by the browser Use
connection.getRequest() and connection.setRequest(request) to perform
changes

Here is an example, corresponding to the one shown above:

`  import org.owasp.webscarab.model.Request;`
`  import org.owasp.webscarab.model.HttpUrl;`
`  `
`  Request request = connection.getRequest();`
`  HttpUrl url = request.getURL();`
`  if (url.toString().endsWith(".swf"))`
`      throw new IOException("No flash content allowed");`

  - Intercept Response

Called when the request has been submitted to the server, and the
response has been received. Use connection.getResponse() and
connection.setResponse(response) to perform changes

Here is an example, again corresponding to the one shown above:

`  import org.owasp.webscarab.model.Response;`
`  `
`  Response response = connection.getResponse();`
`  String cType = response.getHeader("Content-Type");`
`  if (cType != null && cType.endsWith("javascript")) {`
`     byte[] bytes = response.getContent();`
`     if (bytes != null) {`
`        String content = new String(bytes);`
`        content = content.replace("my search string", "my replacement");`
`        response.setContent(content.getBytes());`
`        connection.setResponse(response);`
`     }`
`  }`

Note that to actually make your changes take effect, you have to call
setResponse(response), since the object you have been modifying is only
a copy, not the actual response object.

[Category:How To](Category:How_To "wikilink") [Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink") [Category:Session
Management](Category:Session_Management "wikilink") [Category:OWASP
Testing Project](Category:OWASP_Testing_Project "wikilink")