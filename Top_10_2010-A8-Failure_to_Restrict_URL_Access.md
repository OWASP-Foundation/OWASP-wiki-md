`    <td ``>Anyone with network access can send your application a request. Could anonymous users access a private page or regular users a privileged page?`

</td>

`    <td ``>Attacker, who is an authorized system user, simply changes the URL to a privileged page. Is access granted? Anonymous users could access private pages that aren’t protected.`

</td>

`    <td colspan=2  ``>Applications are not always protecting page requests properly. Sometimes, URL protection is managed via configuration, and the system is misconfigured. Sometimes, developers must include the proper code checks, and they forget.`

`Detecting such flaws is easy. The hardest part is identifying which pages (URLs) exist to attack.`

</td>

`    <td ``>Such flaws may allow some or even all accounts to be attacked. Once successful, the attacker can do anything the victim could do. Privileged accounts are frequently targeted.`

</td>

`    <td ``>Consider the business value of the exposed functions and the data they process.`

`Also consider the impact to your reputation if this vulnerability became public.`

</td>

The best way to find out if an application has failed to properly
restrict URL access is to verify **every** page. Consider for each page,
is the page supposed to be public or private. If a private page:

1.  Is authentication required to access that page?
2.  Is it supposed to be accessible to ANY authenticated user? If not,
    is an authorization check made to ensure the user has permission to
    access that page?

External security mechanisms frequently provide authentication and
authorization checks for page access. Verify they are properly
configured for every page. If code level protection is used, verify that
code level protection is in place for every required page. Penetration
testing can also verify whether proper protection is in place.
Preventing unauthorized URL access requires selecting an approach for
requiring proper authentication and proper authorization for each page.
Frequently, such protection is provided by one or more components
external to the application code. Regardless of the mechanism(s), all of
the following are recommended:

1.  The authentication and authorization policies be role based, to
    minimize the effort required to maintain these policies.
2.  The policies should be highly configurable, in order to minimize any
    hard coded aspects of the policy.
3.  The enforcement mechanism(s) should deny all access by default,
    requiring explicit grants to specific users and roles for access to
    every page.
4.  If the page is involved in a workflow, check to make sure the
    conditions are in the proper state to allow access.

The attacker simply force browses to target URLs. Consider the following
URLs which are both supposed to require authentication. Admin rights are
also required for access to the “admin_getappInfo” page.
http://example.com/app/getappInfo
http://example.com/app/admin_getappInfo If the attacker is not
authenticated, and access to either page is granted, then unauthorized
access was allowed. If an authenticated, non-admin, user is allowed to
access the “admin_getappInfo” page, this is a flaw, and may lead the
attacker to more improperly protected admin pages.

Such flaws are frequently introduced when links and buttons are simply
not displayed to unauthorized users, but the application fails to
protect the pages they target.

  - [OWASP Top 10-2007 on Failure to Restrict URL
    Access](Top_10_2007-Failure_to_Restrict_URL_Access "wikilink")
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
  - [OWASP Development Guide: Chapter on
    Authorization](Guide_to_Authorization "wikilink")
  - [OWASP Testing Guide: Testing for Path
    Traversal](Testing_for_Path_Traversal "wikilink")
  - [OWASP Article on Forced Browsing](Forced_browsing "wikilink")

For additional access control requirements, see the [ASVS requirements
area for Access Control
(V4)](http://www.owasp.org/index.php/ASVS#tab=Downloads)

  - [CWE Entry 285 on Improper Access Control
    (Authorization)](http://cwe.mitre.org/data/definitions/285.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")