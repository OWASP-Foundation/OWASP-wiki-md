## Planning the new OWASP Testing Guide v3

**3rd October 2007: Startup v3**
The OWASP Testing Guide v2 was a great success, with thousand download
and many many Companies that have adopted it as standard for a Web
Application Penetration Testing.
Now we would like to begin a new project that is based on v2 but improve
it and complete it.

In the OWASP Testing Guide v2 we have split the set of tests in 8
sub-categories:

  - Information Gathering
  - Business Logic Testing
  - Authentication Testing
  - Session Management Testing
  - Data Validation Testing
  - Denial of Service Testing
  - Web Services Testing
  - AJAX Testing

The following are my thoughts about the new OWASP Testing Guide v3:

1\) Authorization testing missing. As Jeff and Dave said many time
before it's important to create a new category.
\* This should include things which were in v1 but dropped from v2,
like: OWASP-AC-003 : Authorization Parameter Manipulation, OWASP-AC-004
: Authorized pages/functions 2) Information gathering is not a set of
vulnerabilities --\> not in report --\> new category: Passive mode
3\) Business logic testing --\> not in report --\> Passive mode
4\) Infrastructural test --\> new category
5\) Web Services section needs improvement
6\) AJAX Testing section needs improvement
7\) New category: Client side Testing. AJAX and Flash Testing

This [document](http://www.owasp.org/index.php/Image:Planning_OTGv3.doc)
analyzes the OWASP Testing Guide v2 vulnerabilities and a plan for
create the new v3.

The following clarifications/considerations also need to be made in
preparation for v3:
1\) Are "OWASP-AUTHN-001 : Authentication endpoint request should be
HTTPS" and "OWASP-AUTHN-003 : Credentials transport over an encrypted
channel" as they were in v1 fully covered by "OWASP-IG-005 : SSL/TLS
Testing"? **--\> no, we need to create a new test in authentication
testing**
2\) Are "OWASP-AUTHN-009 : Password Structure" and "OWASP-AUTHN-010 :
Blank Passwords" as they were in v1 fully covered by OWASP-AT-003 &
OWASP-AT-001? **--\> Yes**
3\) Are all 5 AUTHSM references as they were in v1 fully covered by
"OWASP-SM-001 : Session Management Schema"?
4\) What does "OWASP-DP-001 : Sensitive Data in HTML" fall under in
v2/v3?
5\) Are all the SSL Data protection references (DP-003 through DP-007)
from v1 fall under "OWASP-IG-005 : SSL/TLS Testing"?
6\) Is "OWASP-DS-001 : Locking Customer Accounts" a subset of AUTHN-008
in v1 or AT-006 in v2 or is it really an item on it's own?
7\) Are "OWASP-EH-002 : User Error Messages" and "OWASP-EH-001 :
Application Error Messages" as they were in v1 meant to fall under
"OWASP-IG-004 : Analysis of Error Codes"? If so where would things like
overly specific authentication errors appear in the report? (If I
understand correctly Information gathering isn't going to be reported)
\[This would be things like errors messages which actually specify
"invalid username" or "invalid password" instead of "Error: the
credentials provided are invalid" or similar generic messaging.\] **--\>
yes**