`    <td ``>Consider anyone who can trick your users into submitting a request to your website. Any website or other HTML feed that your users use could do this.`

</td>

`    <td ``>Attacker links to unvalidated redirect and tricks victims into clicking it. Victims are more likely to click on it, since the link is to a valid site. Attacker targets unsafe forward to bypass security checks.`

</td>

`    <td colspan=2  ``>Applications frequently redirect users to other pages, or use internal forwards in a similar manner. Sometimes the target page is specified in an unvalidated parameter, allowing attackers to choose the destination page.`

</td>

`    <td ``>Such redirects may attempt to install malware or trick victims into disclosing passwords or other sensitive information. Unsafe forwards may allow access control bypass.`

</td>

`    <td ``>Consider the business value of retaining your users’ trust.`

`What if they get owned by malware?`

`What if attackers can access internal only functions?`

</td>

The best way to find out if an application has any unvalidated redirects
or forwards is to:

1.  Review the code for all uses of redirect or forward (called a
    transfer in .NET). For each use, identify if the target URL is
    included in any parameter values. If so, verify the parameter(s) are
    validated to contain only an allowed destination, or element of a
    destination.
2.  Also, spider the site to see if it generates any redirects (HTTP
    response codes 300-307, typically 302). Look at the parameters
    supplied prior to the redirect to see if they appear to be a target
    URL or a piece of such a URL. If so, change the URL target and
    observe whether the site redirects to the new target.
3.  If code is unavailable, check all parameters to see if they look
    like part of a redirect or forward URL destination and test those
    that do.

Safe use of redirects and forwards can be done in a number of ways:

1.  Simply avoid using redirects and forwards.
2.  If used, don’t involve user parameters in calculating the
    destination. This can usually be done.
3.  If destination parameters can’t be avoided, ensure that the supplied
    **value** is valid, and **authorized** for the user.

It is recommended that any such destination parameters be a mapping
value, rather than the actual URL or portion of the URL, and that server
side code translate this mapping to the target URL.

Applications can use ESAPI to override the
\[<http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/filters/SecurityWrapperResponse.html#sendRedirect(java.lang.String>)
sendRedirect()\] method to make sure all redirect destinations are safe.

Avoiding such flaws is extremely important as they are a favorite target
of phishers trying to gain the user’s trust.  Scenario \#1: The
application has a page called “redirect.jsp” which takes a single
parameter named “url”. The attacker crafts a malicious URL that
redirects users to a malicious site that performs phishing and installs
malware.

http://www.example.com/redirect.jsp?url=evil.com

Scenario \#2:The application uses forward to route requests between
different parts of the site. To facilitate this, some pages use a
parameter to indicate where the user should be sent if a transaction is
successful. In this case, the attacker crafts a URL that will pass the
application’s access control check and then forward the attacker to an
administrative function that she would not normally be able to access.

http://www.example.com/boring.jsp?fwd=admin.jsp

  - [OWASP Article on Open Redirects](Open_redirect "wikilink")
  - \[<http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/filters/SecurityWrapperResponse.html#sendRedirect(java.lang.String>)
    ESAPI SecurityWrapperResponse.sendRedirect() method\]

<!-- end list -->

  - [CWE Entry 601 on Open
    Redirects](http://cwe.mitre.org/data/definitions/601.html)
  - [WASC Article on URL Redirector
    Abuse](http://projects.webappsec.org/URL-Redirector-Abuse)
  - [Google blog article on the dangers of open
    redirects](http://googlewebmastercentral.blogspot.com/2009/01/open-redirect-urls-is-your-site-being.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")