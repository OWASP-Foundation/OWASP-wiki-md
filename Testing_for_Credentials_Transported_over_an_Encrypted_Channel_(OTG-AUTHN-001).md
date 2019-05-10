## Summary

Testing for credentials transport means verifying that the user's
authentication data are transferred via an encrypted channel to avoid
being intercepted by malicious users. The analysis focuses simply on
trying to understand if the data travels unencrypted from the web
browser to the server, or if the web application takes the appropriate
security measures using a protocol like HTTPS. The HTTPS protocol is
built on TLS/SSL to encrypt the data that is transmitted and to ensure
that user is being sent towards the desired site.

Clearly, the fact that traffic is encrypted does not necessarily mean
that it's completely safe. The security also depends on the encryption
algorithm used and the robustness of the keys that the application is
using, but this particular topic will not be addressed in this section.

For a more detailed discussion on testing the safety of TLS/SSL channels
refer to the chapter [Testing for Weak
SSL/TLS](Testing_for_Weak_SSL/TSL_Ciphers,_Insufficient_Transport_Layer_Protection_\(OWASP-EN-002\) "wikilink").
Here, the tester will just try to understand if the data that users put
in to web forms in order to log in to a web site, are transmitted using
secure protocols that protect them from an attacker.

Nowadays, the most common example of this issue is the log in page of a
web application. The tester should verify that user's credentials are
transmitted via an encrypted channel. In order to log in to a web site,
the user usually has to fill a simple form that transmits the inserted
data to the web application with the POST method. What is less obvious
is that this data can be passed using the HTTP protocol, which transmits
the data in a non-secure, clear text form, or using the HTTPS protocol,
which encrypts the data during the transmission. To further complicate
things, there is the possibility that the site has the login page
accessible via HTTP (making us believe that the transmission is
insecure), but then it actually sends data via HTTPS. This test is done
to be sure that an attacker cannot retrieve sensitive information by
simply sniffing the network with a sniffer tool.

## How to Test

### Black Box testing

In the following examples we will use WebScarab in order to capture
packet headers and to inspect them. You can use any web proxy that you
prefer.

#### Example 1: Sending data with POST method through HTTP

Suppose that the login page presents a form with fields User, Pass, and
the Submit button to authenticate and give access to the application. If
we look at the headers of our request with WebScarab, we can get
something like this:

    POST http://www.example.com/AuthenticationServlet HTTP/1.1
    Host: www.example.com
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.8.1.14) Gecko/20080404
    Accept: text/xml,application/xml,application/xhtml+xml
    Accept-Language: it-it,it;q=0.8,en-us;q=0.5,en;q=0.3
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: http://www.example.com/index.jsp
    Cookie: JSESSIONID=LVrRRQQXgwyWpW7QMnS49vtW1yBdqn98CGlkP4jTvVCGdyPkmn3S!
    Content-Type: application/x-www-form-urlencoded
    Content-length: 64

    delegated_service=218&User=test&Pass=test&Submit=SUBMIT

From this example the tester can understand that the POST request sends
the data to the page *www.example.com/AuthenticationServlet* using HTTP.
Sothe data is transmitted without encryption and a malicious user could
intercept the username and password by simply sniffing the network with
a tool like Wireshark.

#### Example 2: Sending data with POST method through HTTPS

Suppose that our web application uses the HTTPS protocol to encrypt the
data we are sending (or at least for transmitting sensitive data like
credentials). In this case, when logging on to the web application the
header of our POST request would be similar to the following:

    POST https://www.example.com:443/cgi-bin/login.cgi HTTP/1.1
    Host: www.example.com
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.8.1.14) Gecko/20080404
    Accept: text/xml,application/xml,application/xhtml+xml,text/html
    Accept-Language: it-it,it;q=0.8,en-us;q=0.5,en;q=0.3
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: https://www.example.com/cgi-bin/login.cgi
    Cookie: language=English;
    Content-Type: application/x-www-form-urlencoded
    Content-length: 50

    Command=Login&User=test&Pass=test

We can see that the request is addressed to
*www.example.com:443/cgi-bin/login.cgi* using the HTTPS protocol. This
ensures that our credentials are sent using an encrypted channel and
that the credentials are not readable by a malicious user using a
sniffer.

#### Example 3: sending data with POST method via HTTPS on a page reachable via HTTP

Now, imagine having a web page reachable via HTTP and that only data
sent from the authentication form are transmitted via HTTPS. This
situation occurs, for example, when we are on a portal of a big company
that offers various information and services that are publicly
available, without identification, but the site also has a private
section accessible from the home page when users log in. So when we try
to log in, the header of our request will look like the following
example:

    POST http://www.example.com/homepage.do
    Host: http://www.example.com/homepage.do
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.8.1.14) Gecko/20080404
    Accept: text/xml,application/xml,application/xhtml+xml,text/html
    Accept-Language: it-it,it;q=0.8,en-us;q=0.5,en;q=0.3
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: http://www.example.com/homepage.do
    Cookie: SERVTIMSESSIONID=s2JyLkvDJ9ZhX3yr5BJ3DFLkdphH0QNSJ3VQB6pLhjkW6F
    Content-Type: application/x-www-form-urlencoded
    Content-length: 45

    User=test&Pass=test&portal=ExamplePortal

We can see that our request is addressed to
*www.example.com:443/login.do* using HTTPS. But if we have a look at the
Referer-header (the page from which we came), it is
*www.example.com/homepage.do* and is accessible via simple HTTP.
Although we are sending data via HTTPS, this deployment can allow
[SSLStrip](http://www.thoughtcrime.org/software/sslstrip/) attacks (a
type of
[Man-in-the-middle](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)
attack)

#### Example 4: Sending data with GET method through HTTPS

In this last example, suppose that the application transfers data using
the GET method. This method should never be used in a form that
transmits sensitive data such as username and password, because the data
is displayed in clear text in the URL and this causes a whole set of
security issues. For example, the URL that is requested is easily
available from the server logs or from your browser history, which makes
your sensitive data retrievable for unauthorized persons. So this
example is purely demonstrative, but, in reality, it is strongly
suggested to use the POST method instead.

    GET https://www.example.com/success.html?user=test&pass=test HTTP/1.1
    Host: www.example.com
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.8.1.14) Gecko/20080404
    Accept: text/xml,application/xml,application/xhtml+xml,text/html
    Accept-Language: it-it,it;q=0.8,en-us;q=0.5,en;q=0.3
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: https://www.example.com/form.html
    If-Modified-Since: Mon, 30 Jun 2008 07:55:11 GMT
    If-None-Match: "43a01-5b-4868915f"

You can see that the data is transferred in clear text in the URL and
not in the body of the request as before. But we must consider that
SSL/TLS is a level 5 protocol, a lower level than HTTP, so the whole
HTTP packet is still encrypted making the URL unreadable to a malicious
user using a sniffer. Nevertheless as stated before, it is not a good
practice to use the GET method to send sensitive data to a web
application, because the information contained in the URL can be stored
in many locations such as proxy and web server logs.

### Gray Box testing

Speak with the developers of the web application and try to understand
if they are aware of the differences between HTTP and HTTPS protocols
and why they should use HTTPS for transmitting sensitive information.
Then, check with them if HTTPS is used in every sensitive request, like
those in log in pages, to prevent unauthorized users to intercept the
data.

## Tools

  - [WebScarab](OWASP_WebScarab_Project "wikilink")
  - [OWASP Zed Attack Proxy
    (ZAP)](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)

## References

**Whitepapers**
\* HTTP/1.1: Security Considerations -
<http://www.w3.org/Protocols/rfc2616/rfc2616-sec15.html>

  - [SSL is not about
    encryption](http://www.troyhunt.com/2011/01/ssl-is-not-about-encryption.html)