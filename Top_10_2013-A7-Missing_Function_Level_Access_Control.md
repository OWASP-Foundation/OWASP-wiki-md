`    <td ``>`

Anyone with network access can send your application a request. Could
anonymous users access private functionality or regular users a
privileged function?

</td>

`    <td ``>`

Attacker, who is an authorized system user, simply changes the URL or a
parameter to a privileged function. Is access granted? Anonymous users
could access private functions that aren’t protected.

</td>

`    <td colspan=2  ``>`

Applications do not always protect application functions properly.
Sometimes, function level protection is managed via configuration, and
the system is misconfigured. Sometimes, developers must include the
proper code checks, and they forget.

Detecting such flaws is easy. The hardest part is identifying which
pages (URLs) or functions exist to attack.

</td>

`    <td ``>`

Such flaws allow attackers to access unauthorized functionality.
Administrative functions are key targets for this type of attack.

</td>

`    <td ``>`

Consider the business value of the exposed functions and the data they
process.

Also consider the impact to your reputation if this vulnerability became
public.

</td>

The best way to find out if an application has failed to properly
restrict function level access is to verify every application function:

1.  Does the UI show navigation to unauthorized functions?
2.  Are server side authentication or authorization checks missing?
3.  Are server side checks done that solely rely on information provided
    by the attacker?

Using a proxy, browse your application with a privileged role. Then
revisit restricted pages using a less privileged role. If the server
responses are alike, you're probably vulnerable. Some testing proxies
directly support this type of analysis.

You can also check the access control implementation in the code. Try
following a single privileged request through the code and verifying the
authorization pattern. Then search the codebase to find where that
pattern is not being followed.

Automated tools are unlikely to find these problems.

Your application should have a consistent and easy to analyze
authorization module that is invoked from all of your business
functions. Frequently, such protection is provided by one or more
components external to the application code.

1.  Think about the process for managing entitlements and ensure you can
    update and audit easily. Don’t hard code.
2.  The enforcement mechanism(s) should deny all access by default,
    requiring explicit grants to specific roles for access to every
    function.
3.  If the function is involved in a workflow, check to make sure the
    conditions are in the proper state to allow access.

NOTE: Most web applications don’t display links and buttons to
unauthorized functions, but this “presentation layer access control”
doesn’t actually provide protection. You must <u>also</u> implement
checks in the controller or business logic.

**Scenario \#1:** The attacker simply force browses to target URLs. The
following URLs require authentication. Admin rights are also required
for access to the <u>admin_getappInfo</u> page.

http://example.com/app/getappInfo
http://example.com/app/admin_getappInfo  If an unauthenticated user can
access either page, that’s a flaw. If an authenticated, non-admin, user
is allowed to access the <u>admin_getappInfo</u> page, this is also a
flaw, and may lead the attacker to more improperly protected admin
pages.

**Scenario \#2:** A page provides an 'action' parameter to specify the
function being invoked, and different actions require different roles.
If these roles aren’t enforced, that’s a flaw.

  - [OWASP Top 10-2007 on Failure to Restrict URL
    Access](https://www.owasp.org/index.php/Top_10_2007-Failure_to_Restrict_URL_Access)
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
  - [OWASP Development Guide: Chapter on
    Authorization](https://www.owasp.org/index.php/Guide_to_Authorization)
  - [OWASP Testing Guide: Testing for Path
    Traversal](https://www.owasp.org/index.php/Testing_for_Path_Traversal)
  - [OWASP Article on Forced
    Browsing](https://www.owasp.org/index.php/Forced_browsing)

For additional access control requirements, see the [ASVS requirements
area for Access Control (V4)](https://www.owasp.org/index.php/ASVS).

  - [CWE Entry 285 on Improper Access Control
    (Authorization)](http://cwe.mitre.org/data/definitions/285.html)