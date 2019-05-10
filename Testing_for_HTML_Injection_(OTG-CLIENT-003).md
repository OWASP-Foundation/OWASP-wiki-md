## Summary

HTML injection is a type of injection issue that occurs when a user is
able to control an input point and is able to inject arbitrary HTML code
into a vulnerable web page. This vulnerability can have many
consequences, like disclosure of a user's session cookies that could be
used to impersonate the victim, or, more generally, it can allow the
attacker to modify the page content seen by the victims.

## How to Test

This vulnerability occurs when the user input is not correctly sanitized
and the output is not encoded. An injection allows the attacker to send
a malicious HTML page to a victim. The targeted browser will not be able
to distinguish (trust) the legit from the malicious parts and
consequently will parse and execute all as legit in the victim context.

There is a wide range of methods and attributes that could be used to
render HTML content. If these methods are provided with an untrusted
input, then there is an high risk of XSS, specifically an HTML injection
one. Malicious HTML code could be injected for example via innerHTML,
that is used to render user inserted HTML code. If strings are not
correctly sanitized the problem could lead to XSS based HTML injection.
Another method could be document.write()

When trying to exploit this kind of issues, consider that some
characters are treated differently by different browsers. For reference
see the DOM XSS Wiki.

The innerHTML property sets or returns the inner HTML of an element. An
improper usage of this property, that means lack of sanitization from
untrusted input and missing output encoding, could allow an attacker to
inject malicious HTML code.

Example of Vulnerable Code: The following example shows a snippet of
vulnerable code that allows an unvalidated input to be used to create
dynamic html in the page context:

    var userposition=location.href.indexOf("user=");
    var user=location.href.substring(userposition+5);
    document.getElementById("Welcome").innerHTML=" Hello, "+user;

In the same way, the following example shows a vulnerable code using the
document.write() function:

    var userposition=location.href.indexOf("user=");
    var user=location.href.substring(userposition+5);
    document.write("<h1>Hello, " + user +"</h1>");

In both examples, an input like the following:

<http://vulnerable.site/page.html?user=>`<img%20src='aaa'%20onerror=alert(1)>`

will add to the page the image tag that will execute an arbitrary
JavaScript code inserted by the malicious user in the HTML context.

### Black Box testing

Black box testing for HTML Injection is not usually performed since
access to the source code is always available as it needs to be sent to
the client to be executed.

### Gray Box testing

**Testing for HTML Injection vulnerabilities:**
For example, looking at the following URL:

<http://www.domxss.com/domxss/01_Basics/06_jquery_old_html.html>

The HTML code will contains the following script:

    <script src="../js/jquery-1.7.1.js"></script>
    <script>
    function setMessage(){
     var t=location.hash.slice(1);
     $("div[id="+t+"]").text("The DOM is now loaded and can be manipulated.");
    }
    $(document).ready(setMessage  );
    $(window).bind("hashchange",setMessage)
    </script>
    <body><script src="../js/embed.js"></script>
    <span><a href="#message" > Show Here</a><div id="message">Showing Message1</div></span>
    <span><a href="#message1" > Show Here</a><div id="message1">Showing Message2</div>
    <span><a href="#message2" > Show Here</a><div id="message2">Showing Message3</div>
    </body>

It is possible to inject HTML code.

## References

**OWASP Resources**

  - [DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - DOMXSS.com - <http://www.domxss.com>

**Whitepapers**
\* Browser location/document URI/URL Sources -
<https://code.google.com/p/domxsswiki/wiki/LocationSources>

  -   - i.e., what is returned when the user asks the browser for things
        like document.URL, document.baseURI, location, location.href,
        etc.