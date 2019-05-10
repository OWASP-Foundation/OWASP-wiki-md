`    <td ``>Consider anyone who can trick your users into submitting a request to your website. Any website or other HTML feed that your users access could do this.`

</td>

`    <td ``>Attacker creates forged HTTP requests and tricks a victim into submitting them via image tags, XSS, or numerous other techniques. If the `<u>`user is authenticated`</u>`, the attack succeeds.`

</td>

`    <td colspan=2  ``>`[`CSRF`](CSRF "wikilink")` takes advantage of web applications that allow attackers to predict all the details of a particular action.`

`Since browsers send credentials like session cookies automatically, attackers can create malicious web pages which generate forged requests that are indistinguishable from legitimate ones.`

`Detection of CSRF flaws is fairly easy via penetration testing or code analysis.`

</td>

`    <td ``>Attackers can cause victims to change any data the victim is allowed to change or perform any function the victim is authorized to use`

</td>

`    <td ``>Consider the business value of the affected data or application functions. Imagine not being sure if users intended to take these actions.`

`Consider the impact to your reputation.`

</td>

The easiest way to check whether an application is vulnerable is to see
if each link and form contains an unpredictable token for each user.
Without such an unpredictable token, attackers can forge malicious
requests. Focus on the links and forms that invoke state-changing
functions, since those are the most important CSRF targets.

You should check multi-step transactions, as they are not inherently
immune. Attackers can easily forge a series of requests by using
multiple tags or possibly JavaScript.

Note that session cookies, source IP addresses, and other information
that is automatically sent by the browser doesn’t count since this
information is also included in forged requests.

OWASP’s [CSRF Tester](CSRFTester "wikilink") tool can help generate test
cases to demonstrate the dangers of CSRF flaws.  Preventing CSRF
requires the inclusion of an unpredictable token in the body or URL of
each HTTP request. Such tokens should at a minimum be unique per user
session, but can also be unique per request.

1.  The preferred option is to include the unique token in a hidden
    field. This causes the value to be sent in the body of the HTTP
    request, avoiding its inclusion in the URL, which is subject to
    exposure.
2.  The unique token can also be included in the URL itself, or a URL
    parameter. However, such placement runs the risk that the URL will
    be exposed to an attacker, thus compromising the secret token.

OWASP’s [CSRF Guard](CSRFGuard "wikilink") can be used to automatically
include such tokens in your Java EE, .NET, or PHP application. OWASP’s
[ESAPI](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/HTTPUtilities.html)
includes token generators and validators that developers can use to
protect their transactions.  The application allows a user to submit a
state changing request that does not include anything secret. Like so:
http://example.com/app/transferFunds?amount=1500\&destinationAccount=4673243243
So, the attacker constructs a request that will transfer money from the
victim’s account to their account, and then embeds this attack in an
image request or iframe stored on various sites under the attacker’s
control. \<img
src="http://example.com/app/transferFunds?amount=1500\&destinationAccount=attackersAcct\#"
width="0" height="0" /\> If the victim visits any of these sites while
already authenticated to example.com, any forged requests will include
the user’s session info, inadvertently authorizing the request.

  - [OWASP CSRF Article](CSRF "wikilink")
  - [OWASP CSRF Prevention Cheat
    Sheet](Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP CSRFGuard - CSRF Defense Tool](CSRFGuard "wikilink")
  - [ESAPI Project Home Page](ESAPI "wikilink")
  - [ESAPI HTTPUtilities Class with AntiCSRF
    Tokens](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/HTTPUtilities.html)
  - [OWASP Testing Guide: Chapter on CSRF
    Testing](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")
  - [OWASP CSRFTester - CSRF Testing Tool](CSRFTester "wikilink")

<!-- end list -->

  - [CWE Entry 352 on
    CSRF](http://cwe.mitre.org/data/definitions/352.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")