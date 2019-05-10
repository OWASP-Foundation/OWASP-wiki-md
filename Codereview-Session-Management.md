__TOC__

## Description

Session management from a code review perspective should focus on the
creation, renewal, and destruction of a user’s session throughout the
application. The code review process should ensure the following:

**Session ID**
Authenticated users should have a robust and cryptographically secure
association with their session. The session identifier (Session ID)
should not be predictable, and generation of such should be left to the
underlying framework. The development effort to produce a session with
sufficient entropy is subject to errors, and best left to tried and
trusted methods.

**Authorization**

  - Applications should check if the session is valid prior to servicing
    any user requests. The user's session object may also hold
    authorization data.
  - Session ID should be applied to a new user upon successful
    authentication.
  - Reviewing the code to identify where sessions are created and
    invalidated is important. A user should be assigned a new unique
    session once authenticated to mitigate session fixation attacks.
  - Sessions may need to be terminated upon authorization failures. If a
    logical condition exists which is not possible, unless the state
    transition is circumvented or an obvious attempt to escalate
    privileges, a session should be terminated.

**Session Transport**
Applications avoid or prevent common web attacks, such as replay,
request forging, and man-in-the-middle.

  - Session identifiers should be passed to the user in a secure manner
    such as not using HTTP GET with the session ID being placed in the
    query string. Such data (query string) is logged in web server logs.
  - Cookie transport should be performed over a secure channel. Review
    the code in relation to cookie manipulation. Verify if the secure
    flag is set. This prevents the cookie being transported over a
    non-secure channel.

**Session Lifecycle**

  - Session Timeout - Sessions should have a defined inactivity timeout
    and also in some cases a session hard-limit. The code review should
    examine such session settings. They may be defined in configuration
    files or in the code itself. Hard limits shall kill a session
    regardless of session activity.
  - The log-out commands must do more that simply kill the browser.
    Review the code to verify that log-out commands invalidate the
    session on the server. Upon the logout request, be it a parameter or
    URL, one must review the code to ensure the session is invalidated.

**Example for Session Invalidate:**

`import java.io.*;`
`import javax.servlet.*;`
`import javax.servlet.http.*;`
`import java.sql.*;`
`public class `<font color="red">`doLogout`</font>` extends HttpServlet`
`    {`
`         public void doGet(HttpServletRequest req,HttpServletResponse res)throws ServletException,IOException`
`         {`
`              res.setContentType("text/html");`
`              HttpSession ses =req.getSession();   `
`              ses.removeValue("Login");`
`              ses.removeValue("password");`
`              ses.invalidate();                     `
`              res.sendRedirect("`<http://company.com/servlets/login.html>`");          `
`         } `
`    }`

### Related Vulnerabilities

  - [Reviewing Code for Data
    Validation](Reviewing_Code_for_Data_Validation "wikilink")
  - [Reviewing code for XSS
    issues](Reviewing_code_for_XSS_issues "wikilink")
  - [Reviewing Code for Authorization
    Issues](Reviewing_Code_for_Authorization_Issues "wikilink")
  - [Reviewing Code for
    Authentication](Reviewing_Code_for_Authentication "wikilink")
  - [Reviewing Code for Session Integrity
    issues](Reviewing_Code_for_Session_Integrity_issues "wikilink")

## Related Security Activities

### Description of Session Management Vulnerabilities

See the OWASP articles on [Session Management
Vulnerabilities](:Category:Session_Management_Vulnerability "wikilink").

### Description of Session Management Countermeasures

See the OWASP articles on [Session Management
Countermeasures](:Category:Session_Management "wikilink").

### How to Avoid Session Management Vulnerabilities

See the [OWASP Development
Guide](:Category:OWASP_Guide_Project "wikilink") article on how to
[Avoid Session Management](Session_Management "wikilink")
Vulnerabilities.

### How to Test for Session Management Vulnerabilities

See the [OWASP Testing
Guide](:Category:OWASP_Testing_Project "wikilink") article on how to
[Test for Session Management](Testing_for_Session_Management "wikilink")
Vulnerabilities.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")