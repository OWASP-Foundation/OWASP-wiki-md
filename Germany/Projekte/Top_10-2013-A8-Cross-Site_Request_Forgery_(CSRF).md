`    <td ``>`

Consider anyone who can load content into your users’ browsers, and thus
force them to submit a request to your website. Any website or other
HTML feed that your users access could do this.

</td>

`    <td ``>`

Attacker creates forged HTTP requests and tricks a victim into
submitting them via image tags, XSS, or numerous other techniques. <u>If
the user is authenticated</u>, the attack succeeds.

</td>

`    <td colspan=2  ``>`[`CSRF`](https://www.owasp.org/index.php/CSRF)` takes advantage the fact that most web apps allow atof tackers to predict all the details of a particular action.`

Because browsers send credentials like session cookies automatically,
attackers can create malicious web pages which generate forged requests
that are indistinguishable from legitimate ones.

Detection of CSRF flaws is fairly easy via penetration testing or code
analysis.

</td>

`    <td ``>`

Attackers can trick victims into performing any state changing operation
the victim is authorized to perform, e.g., updating account details,
making purchases, logout and even login.

</td>

`    <td ``>`

Consider the business value of the affected data or application
functions. Imagine not being sure if users intended to take these
actions.

Consider the impact to your reputation.

</td>

To check whether an application is vulnerable, see if any links and
forms lack an unpredictable CSRF token. Without such a token, attackers
can forge malicious requests. An alternate defense is to require the
user to prove they intended to submit the request, either through
reauthentication, or some other proof they are a real user (e.g., a
CAPTCHA).

Focus on the links and forms that invoke state-changing functions, since
those are the most important CSRF targets.

You should check multistep transactions, as they are not inherently
immune. Attackers can easily forge a series of requests by using
multiple tags or possibly JavaScript.

Note that session cookies, source IP addresses, and other information
automatically sent by the browser don’t provide any defense against CSRF
since this information is also included in forged requests.

OWASP’s [CSRF Tester](https://www.owasp.org/index.php/CSRFTester) tool
can help generate test cases to demonstrate the dangers of CSRF flaws.

Preventing CSRF usually requires the inclusion of an unpredictable token
in each HTTP request. Such tokens should, at a minimum, be unique per
user session.

1.  The preferred option is to include the unique token in a hidden
    field. This causes the value to be sent in the body of the HTTP
    request, avoiding its inclusion in the URL, which is more prone to
    exposure.
2.  The unique token can also be included in the URL itself, or a URL
    parameter. However, such placement runs a greater risk that the URL
    will be exposed to an attacker, thus compromising the secret token.

OWASP’s [CSRF Guard](https://www.owasp.org/index.php/CSRFGuard) can
automatically include such tokens in Java EE, .NET, or PHP apps. OWASP’s
[ESAPI](https://www.owasp.org/index.php/ESAPI) includes methods
developers can use to prevent CSRF vulnerabilities. Requiring the user
to reauthenticate, or prove they are a user (e.g., via a CAPTCHA) can
also protect against CSRF.  The application allows a user to submit a
state changing request that does not include anything secret. For
example:
http://example.com/app/transferFunds?amount=1500\&destinationAccount=4673243243
 So, the attacker constructs a request that will transfer money from the
victim’s account to the attacker’s account, and then embeds this attack
in an image request or iframe stored on various sites under the
attacker’s control:  \<img
src="<span style="color: red;">http://example.com/app/transferFunds?amount=1500\&destinationAccount=attackersAcct\#</span>"
width="0" height="0" /\>  If the victim visits any of the attacker’s
sites while already authenticated to example.com, these forged requests
will automatically include the user’s session info, authorizing the
attacker’s request.

  - [OWASP CSRF Article](https://www.owasp.org/index.php/CSRFGuard)
  - [OWASP CSRF Prevention Cheat
    Sheet](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet)
  - [OWASP CSRFGuard - CSRF Defense
    Tool](https://www.owasp.org/index.php/CSRFGuard)
  - ESAPI [Project](https://www.owasp.org/index.php/ESAPI)Home Page
  - [ESAPI HTTPUtilities Class with AntiCSRF
    Tokens](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/HTTPUtilities.html)
  - [OWASP Testing Guide: Chapter on CSRF
    Testing](https://www.owasp.org/index.php/Testing_for_CSRF_\(OWASP-SM-005\))
  - [OWASP CSRFTester - CSRF Testing
    Tool](https://www.owasp.org/index.php/CSRFTester)

<!-- end list -->

  - CWE [Entry](http://cwe.mitre.org/data/definitions/352.html)352 on
    CSRF