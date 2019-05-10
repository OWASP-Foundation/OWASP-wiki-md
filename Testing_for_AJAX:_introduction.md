**4.11 AJAX Testing**

-----

AJAX, an acronym for Asynchronous JavaScript and XML, is a web
development technique used to create more responsive web applications.
It uses a combination of technologies in order to provide an experience
that is more like using a desktop application. This is accomplished by
using the XMLHttpRequest object and JavaScript to make asynchronous
requests to the web server, parsing the responses and then updating the
page DOM HTML and CSS.

Utilizing AJAX techniques can have tremendous usability benefits for web
applications. From a security standpoint, however, AJAX applications
have a greater attack surface than normal web applications, and they are
often developed with a focus on what can be done rather than what should
be done. Also, AJAX applications are more complicated because processing
is done on both the client side and the server side. The use of
frameworks to hide this complexity can help to reduce development
headaches, but can also result in situations where developers do not
fully understand where the code they are writing will execute. This can
lead to situations where it is difficult to properly assess the risk
associated with particular applications or features.

AJAX applications are vulnerable to the full range of traditional web
application vulnerabilities. Insecure coding practices can lead to SQL
injection vulnerabilities, misplaced trust in user-supplied input can
lead to parameter tampering vulnerabilities, and a failure to require
proper authentication and authorization can lead to problems with
confidentiality and integrity. In addition, AJAX applications can be
vulnerable to new classes of attack such as Cross Site Request Forgery
(XSRF).

Testing AJAX applications can be challenging because developers are
given a tremendous amount of freedom in how they communicate between the
client and the server. In traditional web applications, standard HTML
forms submitted via GET or POST requests have an easy-to-understand
format, and it is therefore easy to modify or create new well-formed
requests. AJAX applications often use different encoding or
serialization schemes to submit POST data making it difficult for
testing tools to reliably create automated test requests. The use of web
proxy tools is extremely valuable for observing behind-the-scenes
asynchronous traffic and for ultimately modifying this traffic to
properly test the AJAX-enabled application.
In this section, we will visit these topics:
[4.11.1 AJAX Vulnerabilities
(OWASP-AJ-001)](Testing_for_AJAX_Vulnerabilities_\(OWASP-AJ-001\) "wikilink")
[4.11.2 How to test AJAX
(OWASP-AJ-002)](Testing_for_AJAX_\(OWASP-AJ-002\) "wikilink")