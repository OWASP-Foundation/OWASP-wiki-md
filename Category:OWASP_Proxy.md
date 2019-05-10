<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

## Overview

One of the priorities of this project is to allow developers to do
whatever they choose, without enforcing RFC compliance. This is
important for a security testing library, as often the most interesting
behavior manifests outside the RFCs\! Keep in mind that a lot of the
safety nets that exist in libraries that enforce RFC compliance do not
exist in this library, and that as the developer, you need to be
prepared to deal with the consequences\!

Another priority is to accurately deliver whatever is specified by the
client, and similarly, to accurately reflect whatever is returned by the
server, rather than coloured by the parsing and normalisation performed
by the library.

## Download

At the moment there is no packaged version of this library. Development
is done in a git repository, located
[here](http://dawes.za.net/gitweb.cgi?p=rogan/owasp-proxy/owasp-proxy.git;a=summary).

Interested parties can download a snapshot of the code at any point
using the snapshot link next to each revision, or clone the repository:

` $ git clone `<http://dawes.za.net/rogan/owasp-proxy/owasp-proxy.git/>

## Implementation details

In order to achieve byte for byte accuracy with what was sent by the
client, and received from the server, OWASP Proxy does the bare minimum
of message parsing. The basic storage of an HTTP message header is as an
array of byte (a byte for byte copy of what was read from the network),
rather than parsed out into convenient pieces. The library does provide
convenience methods for accessing interesting parts of the message, such
as headers, content, etc, but the message itself is represented as
either a byte\[\] for the header, and an InputStream for the content, or
a byte\[\] for the header, and a (possibly null) byte\[\] for the
message content.

The Request and Response objects that you may deal with also do not
decode the message bodies for you. If the message was sent using chunked
encoding, the message body will show the individual chunks that were
sent. Of course, again, there are also classes which allow you to obtain
the actual entity body, with appropriate decoding performed.

## Future development

As mentioned above, one objective is correctness. By this I mean
correctly handling whatever the major browsers send to it, and
successfully retrieving whichever resource was requested. Failure to do
so will be addressed as soon as possible.

Other than that, there is no intention to add major new features to the
library above those required to fulfill its purpose as a Listener and a
HTTP client implementation.

## Using the OWASP Proxy

### The Simplest Proxy

About the simplest proxy that you can write is as follows:

`RequestHandler requestHandler = new DefaultHttpRequestHandler();`
`ConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`InetSocketAddress listen = new InetSocketAddress("localhost", 8008);`
`Server proxy = new Server(listen, httpProxy);`
`proxy.start();`

A quick explanation of the classes referenced is warranted.

**Server** is a mostly trivial class that listens to an
**InetSocketAddress**, accepts connections and passes the accepted
**Socket** on to implementations of the **ConnectionHandler** interface.

**HttpProxyConnectionHandler** is a **ConnectionHandler** implementation
that implements an HTTP Proxy, reading HTTP requests from a client,
passes those on to an **HttpRequestHandler** to fetch the **Response**,
then relays that **Response** back to the client.

**DefaultHttpRequestHandler** is just a simple implementation of the
**HttpRequestHandler** interface, which makes use of the built-in custom
HTTP Client to send the **Request** to the server, and obtain the
**Response**.

Of course, it is not terribly useful. All it does is forward requests
and responses, without doing anything with them.

### The Message Object Model

Let's take a look at the message object model, before we try to do
something more complex.

`public interface MessageHeader {`
`    byte[] getHeader();`
`    String getStartLine() throws MessageFormatException;`
`    NamedValue[] getHeaders() throws MessageFormatException;`
`    String getHeader(String name) throws MessageFormatException;`
`}`

`public interface MutableMessageHeader {`
`    void setHeader(byte[] header);`
`    void setStartLine(String line) throws MessageFormatException;`
`    void setHeaders(NamedValue[] headers) throws MessageFormatException;`
`    void setHeader(String name, String value) throws MessageFormatException;`
`    void addHeader(String name, String value) throws MessageFormatException;`
`    String deleteHeader(String name) throws MessageFormatException;`
`}`

This shows the interface for a MessageHeader, and a mutable
MessageHeader. These are the foundations for the other message classes.
Everything is represented in a single byte\[\]. If you want to create a
message header that uses a plain CR as a line separator, go ahead and
construct a byte\[\] that has the lines separated by CR's, and call
setHeader(). Of course, the convenience methods are configured to expect
CRLF, and so if you call any of those methods, you should expect to
receive a MessageFormatException, and be prepared to parse the header
manually.

### Message Content

`public interface StreamingMessage extends MutableMessageHeader {`
`    InputStream getContent();`
`    InputStream getDecodedContent() throws MessageFormatException;`
`    void setContent(InputStream content);`
`    void setDecodedContent(InputStream content) throws MessageFormatException;`
`}`

`public interface BufferedMessage extends MessageHeader {`
`    byte[] getContent();`
`    byte[] getDecodedContent() throws MessageFormatException;`
`}`

`public interface MutableBufferedMessage extends BufferedMessage, MutableMessageHeader {`
`    void setContent(byte[] content);`
`    void setDecodedContent(byte[] content) throws MessageFormatException;`
`}`

The above interfaces represent the content of an HTTP message, either in
a streaming or buffered state. Streaming messages are useful if you only
really want to look at the message header, and not do anything with the
message body, or if you can process the message body in a streaming
fashion.

For example, you may want to compress a message transferred without gzip
encoding. Update the message header to reflect the new encoding, wrap
the content stream with a suitable GzipInputStream, and pass the message
on to the next layer.

Of course, if you want to do something complex with the message body,
you probably want to work with the buffered content. In that case, the
BufferedMessage and MutableBufferedMessage interfaces are appropriate.

Note: There is a distinction between BufferedMessage and
MutableBufferedMessage mainly as documentation indicating whether they
should be modified or not in a particular method. See
BufferedMessageInterceptor, for example.

### Requests and Responses

This is what a Request header looks like. Again, there are convenience
methods to obtain specific portions of the request, but underneath it
all is that byte\[\] containing the entire header.

`public interface RequestHeader extends MessageHeader {`
`    InetSocketAddress getTarget();`
`    boolean isSsl();`
`    String getMethod() throws MessageFormatException;`
`    String getResource() throws MessageFormatException;`
`    String getVersion() throws MessageFormatException;`
`}`

`public interface MutableRequestHeader extends RequestHeader, MutableMessageHeader {`
`    void setTarget(InetSocketAddress target);`
`    void setSsl(boolean ssl);`
`    void setMethod(String method) throws MessageFormatException;`
`    void setResource(String resource) throws MessageFormatException;`
`    void setVersion(String version) throws MessageFormatException;`
`}`

Note that the target server and whether the message should be encrypted
or not is external to the message header itself. In most cases, where no
upstream proxy is involved, sending the request is as simple as opening
a socket to the target InetSocketAddress, and calling
write(message.getHeader()); Again, the minimum of parsing is performed,
to allow for sending non-RFC compliant messages to a server.

There are similar interfaces for Responses, although they do not have an
associated target.

## Intercepting HTTP Messages

OWASP Proxy provides a BufferingHttpRequestHandler class which interacts
with implementations of the BufferedMessageInterceptor interface to
facilitate manipulation of the request and response.

This is what the BufferedMessageInterceptor interface looks like:

`public interface BufferedMessageInterceptor {`

`    enum Action { BUFFER, STREAM, IGNORE};`

`    Action directRequest(MutableRequestHeader request);`
`    void processRequest(MutableBufferedRequest request);`
`    void requestContentSizeExceeded(BufferedRequest request, int size);`
`    void requestStreamed(BufferedRequest request);`

`    Action directResponse(RequestHeader request, MutableResponseHeader response)`
`    void processResponse(RequestHeader request, MutableBufferedResponse response)`
`    void responseContentSizeExceeded(RequestHeader request, ResponseHeader response, int size);`
`    void responseStreamed(final RequestHeader request, BufferedResponse response);`

`}`

Note: BufferedMessageInterceptor is actually an abstract class, to save
implementation of methods that you have no interest in.

The first thing to do is decide which requests and responses your
implementation is interested in. The "directRequest()" method is called
first, with the RequestHeader as a parameter. Examine the request header
to determine if the request is "interesting" or not. If you want the
request content to be buffered, return Action.BUFFER. If you want the
request content to be streamed to the server, return Action.STREAM. If
you are not interested in any part of the request, you can return
Action.IGNORE, and no further methods will be called for that particular
Request/Response.

Note that the RequestHeader is actually Mutable, so if you are only
interested in the header, you can make any changes you like in this
method, and then return either Action.STREAM or Action.IGNORE, and
forget about it.

The methods that will be invoked next depend on the Action that was
returned.

If the Action was BUFFER, the processRequest(MutableBufferedRequest)
method will be called, with the buffered request as a parameter. You can
then modify it to suit, and when you return from this method, the
buffered request will be sent to the server.

If the action was STREAM, the requestStreamed(BufferedRequest) method
will be called. Note that this request is no longer mutable, as it is
only invoked AFTER the entire request body has been streamed to the
server.

Note: BufferingHttpRequestHandler takes a "max content size" parameter,
to avoid buffering excessively large messages, and potentially running
out of memory. If the limit is reached, the
requestContentSizeExceeded(BufferedRequest, size) method is invoked,
with the BufferedRequest containing the bytes buffered up to the size
limit, and the size parameter containing the ultimate size of the
message.

The same process is followed for the Response cycle. Determine if you
are interested in the response, return a suitable Action, and handle the
response in the appropriate methods thereafter.

## Putting an intercepting proxy together

`HttpRequestHandler requestHandler = new DefaultHttpRequestHandler();`
`BufferedMessageInterceptor interceptor = new BufferedMessageInterceptor() {`
`    public Action directResponse(RequestHeader request, MutableResponseHeader response) {`
`        return Action.BUFFER;`
`    }`

`    public void processResponse(RequestHeader request, MutableBufferedResponse response) {`
`        try {`
`            System.out.println(request.getResource() + " : " + response.getDecodedContent().length);`
`        } catch (MessageFormatException mfe) {`
`            mfe.printStackTrace();`
`        }`
`    }`
`};`
`int maxContentSize = 10240;`
`requestHandler = new BufferingHttpRequestHandler(requestHandler, interceptor, maxContentSize);`
`ConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`InetSocketAddress listen = new InetSocketAddress("localhost", 8008);`
`Server proxy = new Server(listen, httpProxy);`
`proxy.start();`

This constructs a very simple interceptor that just prints out the
resource path, and the size of the decoded content.

## Can we add SSL intercept?

Absolutely\!

`char[] password = "password".toCharArray();`
`HttpConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`SSLContextSelector contextSelector = new DefaultServerContextSelector("server.p12", password, password);`
`SSLConnectionHandler ssl = new SSLConnectionHandler(contextSelector, true, httpProxy);             // true -> autodetect SSL`
`httpProxy.setConnectHandler(ssl);`
`Server proxy = new Server(listen, httpProxy);`

This constructs an SSLConnectionHandler that automatically detects an
incoming SSL connection based on the first few bytes read from the
connection, negotiates an SSL Server connection with the client using
the supplied certificate in the "server.p12" PKCS\#12 file, then passes
the decrypted connection on to the HttpProxyConnectionHandler. It also
installs that same SSLConnectionHandler as the ConnectHandler of the
HttpProxyConnectionHandler. i.e. when the HTTP Proxy receives a CONNECT
request, after it is permitted, the raw byte stream is then passed back
to the SSLConnectionHandler.

### How can we avoid browser warnings about untrusted connections?

One problem with intercepting proxies that manifests when intercepting
SSL connections is that traditionally the browser will present a warning
to the user that the certificate used is invalid, and thus the
connection is untrusted. In many cases, this is easily worked around by
accepting the untrusted connection, and continuing, but for AJAX-y
connections, there is no opportunity to accept that warning, and the
site just ends up being non-functional.

OWASP Proxy includes a Sun JRE-specific class that uses Sun-internal
classes to generate and sign a CA keypair and certificate, and then uses
that to sign server-specific certificates. This means that if the CA
certificate is imported into the browser, any further certificates
signed by that CA certificate will automatically be trusted.

`SSLContextSelector contextSelector = new AutoGeneratingContextSelector("keystore", "JKS", password);`

## Constructing a reverse proxy

In essence, a proxy is just a server that already has a target. i.e. an
InetSocketAddress that is automatically associated with all requests
that it receives.

`TargetedConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`InetSocketAddress target = new InetSocketAddress("example.com", 80);`
`InetSocketAddress listen = new InetSocketAddress("localhost", 80);`
`Proxy proxy = new Proxy(listen, httpProxy, target);`

### and adding SSL

`ConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`SSLConnectionHandler ssl = new SSLConnectionHandler(contextSelector, true, httpProxy);`
`InetSocketAddress target = new InetSocketAddress("example.com", 80);`
`InetSocketAddress listen = new InetSocketAddress("localhost", 80);`
`Proxy proxy = new Proxy(listen, ssl, target);`

## SOCKS Proxies ROCK\!

While HTTP proxies are the most commonly encountered, SOCKS proxies are
better in many ways. For one, SOCKS proxies are expected to simply relay
data from client to server, and are not expected to understand the data
being proxied. This means that the client doesn't have to add any
proxy-specific message headers, and the behaviour of the client is
exactly the same as if there was no proxy involved at all. The server
should find a browser connecting through a SOCKS proxy indistinguishable
from one that is connecting directly without any proxy at all.

This all means that if we want to be as transparent as possible in our
interception, operating as a SOCKS proxy is the ideal approach. And it
is trivial to do so:

`ConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`ConnectionHandler socks = new SocksConnectionHandler(httpProxy, true); // true -> autodetect SOCKS`
`Server proxy = new Server(listen, socks);`

## Putting it all together

`ConnectionHandler httpProxy = new HttpProxyConnectionHandler(requestHandler);`
`SSLContextSelector contextSelector = new AutoGeneratingContextSelector("keystore", "JKS", password);`
`SSLConnectionHandler ssl = new SSLConnectionHandler(contextSelector, true, httpProxy);`
`httpProxy.setConnectHandler(ssl);`
`ConnectionHandler socks = new SocksConnectionHandler(ssl, true);`
`InetSocketAddress listen = new InetSocketAddress("localhost", 80);`
`Server proxy = new Server(listen, socks);`

This constructs a SOCKS server, that will autodetect the SOCKS protocol,
identify the target of the connection, autodetect an SSL connection,
generate a suitable X.509 keypair and certificate, read HTTP messages
from the client, relay them on to the targeted server, and return the
responses to the client.

All in just a few lines of code\! WOW\!

## Project Contributors

The OWASP Proxy project is run by Rogan Dawes. He can be contacted at
rogan AT dawes.za.net

[Proxy Project](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")