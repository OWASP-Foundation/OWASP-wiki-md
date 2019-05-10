## Summary

A JavaScript Injection vulnerability is a subtype of Cross Site
Scripting (XSS) that involves the ability to inject arbitrary JavaScript
code that is executed by the application inside the victim's browser.
This vulnerability can have many consequences, like disclosure of a
user's session cookies that could be used to impersonate the victim, or,
more generally, it can allow the attacker to modify the page content
seen by the victims or the application behavior.

## How to Test

Such a vulnerability occurs when the application lacks proper user
supplied input and output validation. JavaScript is used to dynamically
populate web pages, this injection occurs during this content processing
phase and consequently affects the victim.

When trying to exploit this kind of issues, consider that some
characters are treated differently by different browsers. For reference
see the DOM XSS Wiki.

The following script does not perform any validation of the variable rr
that contains the user supplied input via the query string and
additionally does not apply any form of encoding:

    var rr = location.search.substring(1);
    if(rr)
      window.location=decodeURIComponent(rr);

This implies that an attacker could inject JavaScript code simply by
submitting the following query string:
''www.victim.com/?javascript:alert(1)''.

### Black Box testing

Black box testing for JavaScript Execution is not usually performed
since access to the source code is always available as it needs to be
sent to the client to be executed.

### Gray Box testing

**Testing for JavaScript Execution vulnerabilities:**

For example, looking at the following URL:
<http://www.domxss.com/domxss/01_Basics/04_eval.html>

The page contains the following scripts:

    <script>
    function loadObj(){
     var cc=eval('('+aMess+')');
     document.getElementById('mess').textContent=cc.message;
    }

    if(window.location.hash.indexOf('message')==-1)
      var aMess="({\"message\":\"Hello User!\"})";
    else
      var aMess=location.hash.substr(window.location.hash.indexOf('message=')+8);
    </script>

The above code contains a source 'location.hash' that is controlled by
the attacker that can inject directly in the 'message' value a
JavaScript Code to take the control of the user browser.

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