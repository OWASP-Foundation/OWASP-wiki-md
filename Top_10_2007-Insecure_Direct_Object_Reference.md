A direct object reference occurs when a developer exposes a reference to
an internal implementation object, such as a file, directory, database
record, or key, as a URL or form parameter. An attacker can manipulate
direct object references to access other objects without authorization,
unless an access control check is in place.

For example, in Internet Banking applications, it is common to use the
account number as the primary key. Therefore, it is tempting to use the
account number directly in the web interface. Even if the developers
have used parameterized SQL queries to prevent SQL injection, if there
is no extra check that the user is the account holder and authorized to
see the account, an attacker tampering with the account number parameter
can see or change '''''all '''''accounts.

This type of attack occurred to the Australian Taxation Office’s *GST
Start Up Assistance* site in 2000, where a legitimate but hostile user
simply changed the ABN (a company tax id) present in the URL. The user
farmed around 17,000 company details from the system, and then e-mailed
each system. This was a major embarrassment to the Government of the
17,000 companies with details of his attack. This type of vulnerability
is very common, but is largely untested in current applications.

## Environments Affected

All web application frameworks are vulnerable to attacks on insecure
direct object references.

## Vulnerability

Many applications expose their internal object references to users.
Attackers use parameter tampering to change references and violate the
intended but unenforced access control policy. Frequently, these
references point to file systems and databases, but any exposed
application construct could be vulnerable.

For example, if code allows user input to specify filenames or paths, it
may allow attackers to jump out of the application’s directory, and
access other resources.

<select name="language"><option value="fr">`Français`</option></select>
`…`
`require_once ($_REQUEST['language’]."lang.php");`

Such code can be attacked using a string like
"../../../../etc/passwd%00" using [null byte
injection](Data_Validation "wikilink") (see the [OWASP Development
Guide](OWASP_Guide_Project "wikilink") for more information) to access
any file on the web server’s file system.

Similarly, references to database keys are frequently exposed. An
attacker can attack these parameters simply by guessing or searching for
another valid key. Often, these are sequential in nature. In the example
below, even if an application does not present any links to unauthorized
carts, and no SQL injection is possible, an attacker can still change
the cartID parameter to whatever cart they want.

`int cartID = Integer.parseInt( request.getParameter( "cartID" ) );`
`String query = "SELECT * FROM table WHERE cartID=" + cartID;`

## Verifying Security

The goal is to verify that the application does not allow direct object
references to be manipulated by an attacker.

Automated approaches: Vulnerability scanning tools will have difficulty
identifying which parameters are susceptible to manipulation or whether
the manipulation worked. Static analysis tools really cannot know which
parameters must have an access control check before use.

Manual approaches: Code review can trace critical parameters and
identify whether they are susceptible to manipulation in many cases.
Penetration testing can also verify that manipulation is possible.
However, both of these techniques are time-consuming and can be spotty.

## Protection

The best protection is to avoid exposing direct object references to
users by using an index, indirect reference map, or other indirect
method that is easy to validate. If a direct object reference must be
used, ensure that the user is authorized before using it.

Establishing a standard way of referring to application objects is
important:

  - **Avoid exposing your private object references to users** whenever
    possible, such as primary keys or filenames
  - **Validate any private object references** extensively with an
    "accept known good" approach
  - **Verify authorization to all referenced objects**

The best solution is to use an index value or a reference map to prevent
parameter manipulation attacks.

<http://www.example.com/application?file=1>

If you must expose direct references to database structures, ensure that
SQL statements and other database access methods only allow authorized
records to be shown:

`int cartID = Integer.parseInt( request.getParameter( "cartID" ) );`
`User user = (User)request.getSession().getAttribute( "user" );`
<code>`String query = "SELECT * FROM table WHERE `
`     cartID=" + cartID + " `**`AND``   ``userID="``   ``+``
 ``user.getID()`**`;`</code>

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0329>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4369>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-0229>
  - GST Assist attack details,
    <http://www.abc.net.au/7.30/stories/s146760.htm>

## References

  - CWE: [CWE-639 (Access Control Bypass Through User-Controlled
    Key)](http://cwe.mitre.org/data/definitions/639.html) - What OWASP
    refers to as an Insecure Direct Object Reference.
  - CWE: [CWE-22 (Path
    Traversal)](http://cwe.mitre.org/data/definitions/22.html) - An
    example of a direct object reference is a filename parameter, which
    the user could manipulate to access unauthorized files, even in
    completely different directories.
  - WASC Threat Classification:
    <http://www.webappsec.org/projects/threat/classes/abuse_of_functionality.shtml>,
    <http://www.webappsec.org/projects/threat/classes/insufficient_authorization.shtml>
  - OWASP Testing Guide, [Testing for Path
    Traversal](Testing_for_Path_Traversal_\(OWASP-AZ-001\) "wikilink")
  - OWASP [Access Control
    Vulnerability](:Category:Access_Control_Vulnerability "wikilink")

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")