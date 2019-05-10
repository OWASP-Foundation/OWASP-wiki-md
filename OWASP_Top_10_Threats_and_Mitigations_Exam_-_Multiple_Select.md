Last updated 4 Aug 11

<center>

**Course Title: OWASP Top 10 Threats and Mitigation**

</center>

<center>

</center>

<center>

**Exam Questions - Multiple Select**

</center>

1\) Which of the following consequences are most likely to occur due to
an injection attack? (Choose two.)

1.  Spoofing
2.  Data loss **Correct**
3.  Denial of service **Correct**
4.  Insecure direct object references

3\) Which of the following scenarios are most likely to cause an
injection attack? (Choose two.)

1.  Unvalidated input is embedded in an instruction stream. **Correct**
2.  Unvalidated input cannot be distinguished from valid instructions.
    **Correct**
3.  A Web application does not validate a client’s access to a resource.
4.  A Web action performs an operation on behalf of the user without
    checking a shared secret.

5\) Which of the following are the best ways to protect against
injection attacks? (Choose three.)

1.  Block list **Correct**
2.  Allow list **Correct**
3.  Escaping **Correct**
4.  Memory size checks
5.  Validate integer values before referencing arrays

6\) Which of the following are most vulnerable to injection attacks?
(Choose two.)

1.  Session IDs
2.  Registry keys
3.  Regular expressions **Correct**
4.  SQL queries based on user input **Correct**

8\) Which mitigation techniques when used in combination can help you
strictly define valid input? (Choose two.)

1.  Allow list **Correct**
2.  Block list **Correct**
3.  Table indirection
4.  Escaping

9\) Which of the following architecture-level techniques are the best
approaches to prevent attacks based on malicious input? (Choose two.)

1.  Allow list
2.  Table indirection **Correct**
3.  Escaping
4.  Object class for user input **Correct**

14\) Which of the following languages are the primary targets of
cross-site scripting? (Choose two.)

1.  HTML **Correct**
2.  SQL
3.  XSLT
4.  JavaScript **Correct**

18\) Which of the following are the best ways to prevent malicious input
exploiting your application? (Choose three.)

1.  Using allow List **Correct**
2.  Using block list **Correct**
3.  Using escaping **Correct**
4.  Using encryption
5.  Using table indirection

22\) Which of the following input sources can be directly controlled by
a malicious user? (Choose two.)

1.  Window.location **Correct**
2.  GET/POST parameters **Correct**
3.  Server configuration files
4.  Ports and network resources

23\) Which of the following scenarios are most likely to result in
broken authentication and session management vulnerabilities? (Choose
two.)

1.  Poorly implemented custom code is used. **Correct**
2.  Misconfigured off-the-shelf code is used. **Correct**
3.  Unused and unnecessary services, code, and DLLs are disabled.
4.  The HttpOnly flag is set in cookies.

24\) Which of the following actions should you take before implementing
a custom authentication and session management system? (Choose two.)

1.  Find out if a suitable framework component already exists.
    **Correct**
2.  Find out if you can use a small extension to an existing component
    to implement the system. **Correct**
3.  Find out if form variables are available to store data.
4.  Find out if you need to use session-based indirection.

26\) Which of the following functionalities should you include in an
authentication and session management system? (Choose two.)

1.  Logout functionality **Correct**
2.  Inactivity timeout functionality **Correct**
3.  Escaping functionality
4.  Forwarding system functionality

31\) Which of the following are authentication system mandatory
requirements? (Choose three.)

1.  Strong passwords are required. **Correct**
2.  Use a GOTCHA to prevent automated attacks.
3.  User logout and session inactivity are required. **Correct**
4.  Session IDs are only accepted from cookies and parameter variables.
5.  Credentials are always protected with encryption or cryptographic
    salting and hashing. **Correct**

32\) A session-based system authenticates a user to a Web site to
provide access to restricted resources. To increase security in this
scenario, an authentication token should meet which of the following
requirements? (Choose two.)

1.  It should identify returning users to the site.
2.  It should be used as a replacement for a user's credentials.
    **Correct**
3.  It should always use a persistent cookie.
4.  It should always use a non-persistent cookie. **Correct**

34\) Which of the following tasks are performed by a session-based
system? (Choose two.)

1.  Identifying returning users **Correct**
2.  Providing access to restricted resources **Correct**
3.  Using the HTTP protocol
4.  Sending successful logins to a well-known location

36\) Which of the following objects are most susceptible to an insecure
direct object reference attack? (Choose two.)

1.  Files **Correct**
2.  Registry keys **Correct**
3.  Conditional constructs
4.  GET/POST parameters

37\) Which of the following vulnerabilities are most likely to occur due
to an insecure direct object reference attack? (Choose two.)

1.  Executing commands on the server.
2.  Impersonating any user on the system.
3.  Modifying SQL data pointed to by the query.
4.  Modifying data without authorization. **Correct**
5.  Accessing a resource without authorization. **Correct**

38\) Which of the following are the best ways to mitigate the threat of
an insecure direct object reference attack? (Choose two.)

1.  Use session-based indirection. **Correct**
2.  Use POST parameters instead of GET parameters.
3.  Perform an access check each time a resource identifier arrives as
    input. **Correct**
4.  Send successful logins to a well-known location instead of automatic
    redirection.

41\) Which of the following threats are most likely to be caused by poor
input validation? (Choose three.)

1.  Injection **Correct**
2.  Cross-site scripting **Correct**
3.  Insecure direct object reference **Correct**
4.  Insecure cryptographic storage
5.  Insufficient transport layer protection

43\) Which of the following are the most common results of a cross-site
request forgery? (Choose three.)

1.  Elevation of privilege **Correct**
2.  Denial of service **Correct**
3.  Spoofing and tampering **Correct**
4.  Enabling of IPSec
5.  Misconfigured or disabled security features

49\) Which of the following are most often associated with a security
misconfiguration threat? (Choose two.)

1.  Unused services **Correct**
2.  Default accounts **Correct**
3.  Bad cryptography
4.  Unsafe key storage

51\) Which of the following are the best ways to reevaluate your
environment and address new threats? (Choose two.)

1.  Add or remove network segments. **Correct**
2.  Apply the latest service packs, patches, hotfixes, and updates.
    **Correct**
3.  Use custom cryptographic algorithms.
4.  Use your browser to forge unauthorized requests.

52\) Which of the following procedures are involved in the hardening
process? (Choose two.)

1.  Disable unnecessary features. **Correct**
2.  Review all settings/configurations. **Correct**
3.  Repeat the process at random intervals.
4.  Update the environment with changes only when needed.

53\) Which of the following consequences are most likely to result if
your production environment does not match your development, testing,
and staging environments? (Choose two.)

1.  Your application may not work as expected. **Correct**
2.  Your application may not authenticate users as expected. **Correct**
3.  Your application may be expensive to administer.
4.  Your application may have too many configuration files.

54\) Which of the following can result in insecure cryptography? (Choose
two.)

1.  Unsalted hash **Correct**
2.  Unused services
3.  Default accounts
4.  Failure to rotate keys **Correct**

55\) Which of the following are most likely to result in insecure
cryptography? (Choose two.)

1.  Custom cryptographic algorithms **Correct**
2.  Unsalted hash **Correct**
3.  New products
4.  Missing patches

56\) Which of the following may result in cryptographic weakness?
(Choose three.)

1.  Poor/weak algorithm choice **Correct**
2.  Custom cryptographic algorithms **Correct**
3.  Insufficient cryptographic protocols **Correct**
4.  Missing patches
5.  Unnecessary/unused services or features

57\) Which of the following protocols are network layer encryption
protocols? (Choose two.)

1.  SSL **Correct**
2.  EFS
3.  IPSec **Correct**
4.  Kerberos

58\) Which of the following factors help you secure keys? (Choose
three.)

1.  Complexity **Correct**
2.  Rotation **Correct**
3.  Randomness **Correct**
4.  Encryption

60\) Which of the following depict the typical impact of failure to
restrict URL access? (Choose two.)

1.  Attackers access other users’ accounts and data. **Correct**
2.  Attackers impersonate any user on the system.
3.  Attackers invoke functions and services they have no authorization
    for. **Correct**
4.  Attackers perform all actions that the victims themselves have
    permission to perform.

61\) Which of the following actions should you take to verify the
implementation of your Web application? (Choose two.)

1.  Use policy mechanisms.
2.  Use a simple and positive model at every layer.
3.  Verify that each URL in your application is appropriately protected.
    **Correct**
4.  Use your browser to forge unauthorized requests. **Correct**

62\) Which of the following should you use to protect the connections
between the physical tiers of your application? (Choose two.)

1.  EFS
2.  SSL **Correct**
3.  IPSec **Correct**
4.  Kerberos

63\) Which of the following are the best ways to implement transport
layer protection? (Choose two.)

1.  Install IDS
2.  Enable SSL **Correct**
3.  Set the HttpOnly flag on session ID cookies
4.  Enable IPSec **Correct**

65\) Which of the following are the best ways to protect a Web
application from unvalidated redirects and forwards? (Choose two.)

1.  Validate the referrer header **Correct**
2.  Use extended validation certificates
3.  Validate all input from the client **Correct**
4.  Disallow requests to unauthorized file types

69\) In which of the following scenarios should you use the escaping
technique? (Choose two.)

1.  When user input is echoed back to the user in HTML **Correct**
2.  When you need to validate any input as valid input
3.  When you are trying to protect against regular expression injection
4.  When you need to tell the interpreter that input is data and not
    code **Correct**

70\) Which of the following are the best ways to prevent unvalidated
redirect and forwards vulnerabilities? (Choose two.)

1.  Use an allow list, such as table indirection. **Correct**
2.  Use client-side validation.
3.  Allow only relative redirects. **Correct**
4.  Use session-based indirection.