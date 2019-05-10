`    <td ``>Consider the types of users of your system. Do any users have only partial access to certain types of system data?`

</td>

`    <td ``>Attacker, who is an authorized system user, simply changes a parameter value that directly refers to a system object to another object the user isn’t authorized for. Is access granted?`

</td>

`    <td colspan=2  ``>Applications frequently use the actual name or key of an object when generating web pages. Applications don’t always verify the user is authorized for the target object. This results in an insecure direct object reference flaw. Testers can easily manipulate parameter values to detect such flaws and code analysis quickly shows whether authorization is properly verified.`

</td>

`    <td ``>Such flaws can compromise all the data that can be referenced by the parameter. Unless the name space is sparse, it’s easy for an attacker to access all available data of that type.`

</td>

`    <td ``>Consider the business value of the exposed data.`

`Also consider the business impact of public exposure of the vulnerability.`

</td>

The best way to find out if an application is vulnerable to insecure
direct object references is to verify that all object references have
appropriate defenses. To achieve this, consider:

1.  For **direct** references to **restricted** resources, the
    application needs to verify the user is authorized to access the
    exact resource they have requested.
2.  If the reference is an **indirect** reference, the mapping to the
    direct reference must be limited to values authorized for the
    current user.

Code review of the application can quickly verify whether either
approach is implemented safely. Testing is also effective for
identifying direct object references and whether they are safe.
Automated tools typically do not look for such flaws because they cannot
recognize what requires protection or what is safe or unsafe.
Preventing insecure direct object references requires selecting an
approach for protecting each user accessible object (e.g., object
number, filename):

1.  Use per user or session indirect object references. This prevents
    attackers from directly targeting unauthorized resources. For
    example, instead of using the resource’s database key, a drop down
    list of six resources authorized for the current user could use the
    numbers 1 to 6 to indicate which value the user selected. The
    application has to map the per-user indirect reference back to the
    actual database key on the server. OWASP’s
    [ESAPI](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Authenticator.html)
    includes both sequential and random access reference maps that
    developers can use to eliminate direct object references.
2.  Check access. Each use of a direct object reference from an
    untrusted source must include an access control check to ensure the
    user is authorized for the requested object.

The application uses unverified data in a SQL call that is accessing
account information: String query = "SELECT \* FROM accts WHERE account
= ?";
PreparedStatement pstmt = connection.prepareStatement(query , ... );
<span style="color:red">pstmt.setString( 1,
request.getParameter("acct"));</span>
ResultSet results = pstmt.executeQuery(); The attacker simply modifies
the ‘acct’ parameter in their browser to send whatever account number
they want. If not verified, the attacker can access any user’s account,
instead of only the intended customer’s account.
http://example.com/app/accountInfo?acct=notmyacct

  - [OWASP Top 10-2007 on Insecure Dir Object
    References](Top_10_2007-Insecure_Direct_Object_Reference "wikilink")
  - [ESAPI Access Reference
    Map](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessReferenceMap.html)
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
    (See isAuthorizedForData(), isAuthorizedForFile(),
    isAuthorizedForFunction() )

For additional access control requirements, see the [ASVS requirements
area for Access Control
(V4)](http://www.owasp.org/index.php/ASVS#tab=Downloads)

  - [CWE Entry 639 on Insecure Direct Object
    References](http://cwe.mitre.org/data/definitions/639.html)
  - [CWE Entry 22 on Path
    Traversal](http://cwe.mitre.org/data/definitions/22.html) (which is
    an example of a Direct Object Reference attack)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")