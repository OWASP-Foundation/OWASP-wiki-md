## Summary

This kind of test focuses on verifying how the authorization schema has
been implemented for each role or privilege to get access to reserved
functions and resources.

For every specific role the tester holds during the assessment, for
every function and request that the application executes during the
post-authentication phase, it is necessary to verify:

  - Is it possible to access that resource even if the user is not
    authenticated?
  - Is it possible to access that resource after the log-out?
  - Is it possible to access functions and resources that should be
    accessible to a user that holds a different role or privilege?

Try to access the application as an administrative user and track all
the administrative functions.

  - Is it possible to access administrative functions also if the tester
    is logged as a user with standard privileges?
  - Is it possible to use these administrative functions as a user with
    a different role and for whom that action should be denied?

## How to test

**Testing for access to administrative functions**
For example, suppose that the 'AddUser.jsp' function is part of the
administrative menu of the application, and it is possible to access it
by requesting the following URL:

` `<https://www.example.com/admin/addUser.jsp>` `

Then, the following HTTP request is generated when calling the AddUser
function:

    POST /admin/addUser.jsp HTTP/1.1
    Host: www.example.com
    [other HTTP headers]

    userID=fakeuser&role=3&group=grp001

What happens if a non-administrative user tries to execute that request?
Will the user be created? If so, can the new user use their privileges?

**Testing for access to resources assigned to a different role**
For example analyze an application that uses a shared directory to store
temporary PDF files for different users. Suppose that documentABC.pdf
should be accessible only by the user test1 with roleA. Verify if user
test2 with roleB can access that resource.


## Tools

  - OWASP WebScarab: [OWASP WebScarab
    Project](OWASP_WebScarab_Project "wikilink")
  - [OWASP Zed Attack Proxy
    (ZAP)](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)