Last updated 4 Aug 11

<center>

**Course Title: OWASP Top 10 Threats and Mitigation**

</center>

<center>

</center>

<center>

**Exam Questions - Single Select**

</center>

1\) Which of the following consequences is most likely to occur due to
an injection attack?

1.  Spoofing
2.  Cross-site request forgery
3.  Denial of service **Correct**
4.  Insecure direct object references

2\) Your application is created using a language that does not support a
clear distinction between code and data. Which vulnerability is most
likely to occur in your application?

1.  Injection **Correct**
2.  Insecure direct object references
3.  Failure to restrict URL access
4.  Insufficient transport layer protection

3\) Which of the following scenarios is most likely to cause an
injection attack?

1.  Unvalidated input is embedded in an instruction stream. **Correct**
2.  Unvalidated input can be distinguished from valid instructions.
3.  A Web application does not validate a client’s access to a resource.
4.  A Web action performs an operation on behalf of the user without
    checking a shared secret.

4\) A user is able to pass malicious input that invokes control codes in
your Web application. Which vulnerability is most likely to occur in
your Web application?

1.  Injection **Correct**
2.  Insecure direct object references
3.  Failure to restrict URL access
4.  Insufficient transport layer protection

5\) Which of the following is the best way to protect against injection
attacks?

1.  SQL queries based on user input
2.  Input validation using an allow list **Correct**
3.  Memory size checks
4.  Validate integer values before referencing arrays

6\) Which of the following is most vulnerable to injection attacks?

1.  Session IDs
2.  Registry keys
3.  Regular expressions **Correct**
4.  Server configuration files

7\) Which character is most likely to be used for an SQL injection
attack?

1.  Single quote (') **Correct**
2.  Null (\\0) byte
3.  Less than sign(\<)
4.  Greater than sign(\>)

8\) Which mitigation technique can help you strictly define valid input?

1.  Allow list **Correct**
2.  Memory size checks
3.  Table indirection
4.  Escaping

9\) Which of the following architecture-level techniques are the best
approaches to prevent attacks based on malicious input?

1.  Allow list
2.  Table indirection **Correct**
3.  Escaping
4.  Memory size checks

10\) Which mitigation technique helps you tell the parser that a
specific character is a literal and not a control character?

1.  Table indirection
2.  Allow list
3.  Escaping **Correct**
4.  Block list

11\) State whether the following statement is True or False. You should
use a blacklist wherever possible; use whitelists only as a secondary
defense.

1.  True
2.  False **Correct**

12\) Which of the following is the best way to define disallowed inputs?

1.  Allow list
2.  Block list **Correct**
3.  Table indirection
4.  Escaping

13\) Which of the following are injection attacks?

1.  Cross-site scripting **Correct**
2.  Cross-site request forgery
3.  Insecure direct object references
4.  Broken authentication and session management

14\) Which of the following languages are the primary targets of
cross-site scripting?

1.  HTML **Correct**
2.  SQL
3.  XSLT
4.  XPath

15\) Which of the following attacks occurs when a malicious user
convinces a victim to send a request to a server with malicious input
and the server echoes the input back to client?

1.  Reflected XSS **Correct**
2.  Persistent XSS
3.  Insecure direct object references
4.  Failure to restrict URL access

16\) Which of the following is the best way to prevent a DOM-based XSS
attack?

1.  Set the HttpOnly flag in cookies
2.  Ensure that session IDs are not exposed in a URL
3.  Ensure that a different nonce is created for each request
4.  Validate any input that comes from another Web site **Correct**

17\) How does malicious input flow in a DOM-based XSS?

1.  From server to client
2.  From client to itself **Correct**
3.  From attacker to server
4.  From victim to server

18\) Which of the following is the best way to prevent malicious input
exploiting your application?

1.  Input validation using an allow List **Correct**
2.  Using encryption
3.  Using table indirection
4.  Using GET/POST parameters

19\) You should set the HttpOnly flag in a cookie to ensure that:

1.  The cookie is not available to client scripts. **Correct**
2.  The cookie is deleted when the user closes the browser.
3.  The cookie is sent over an encrypted channel.
4.  The cookie is a persistent cookie.

20\) You should set a secure flag in a cookie to ensure that:

1.  The cookie is a persistent cookie.
2.  The cookie is not available to client script.
3.  The cookie is sent over an encrypted channel. **Correct**
4.  The cookie is deleted when the user closes the browser.

21\) An attacker submits data to the server and the data is stored on
the server. Which type of vulnerability is most likely to occur in your
application?

1.  DOM-based XSS
2.  Reflected XSS
3.  Persistent XSS **Correct**
4.  Cross-site request forgery

22\) Which of the following input sources can be directly controlled by
a malicious user?

1.  GET/POST parameters **Correct**
2.  Server configuration files
3.  Ports
4.  Server code

23\) Which of the following scenarios is most likely to result in broken
authentication and session management vulnerabilities?

1.  Poorly implemented custom code is used. **Correct**
2.  Session-based indirection is used.
3.  Unused and unnecessary services, code, and DLLs are disabled.
4.  The HttpOnly flag is set in cookies.

24\) Which of the following actions should you take before implementing
a custom authentication and session management system?

1.  Find out if the HttpOnly flag is set in cookies.
2.  Find out if you can use a small extension to an existing component
    to implement the system. **Correct**
3.  Find out if form variables are available to store data.
4.  Find out if you need to use session-based indirection.

25\) State whether the following statement is True or False. When
implementing an authentication or session system, you should ensure that
new session IDs are not created at login.

1.  True
2.  False **Correct**

26\) Which of the following functionalities should you include in an
authentication and session management system?

1.  Logout functionality **Correct**
2.  Regular expressions
3.  Escaping functionality
4.  Forwarding system functionality

27\) Why should you use CAPTCHA?

1.  To create cryptographically random session IDs
2.  To protect credentials by using encryption or cryptographic salt and
    hash
3.  To protect authentication systems from automated or brute-force
    attacks **Correct**
4.  To ensure that authentication systems implement inactivity timeout
    functionality

28\) What should you do before passing credentials over the network?

1.  Replace the credentials with a cryptographic salt and hash.
    **Correct**
2.  Accept session IDs from URLs.
3.  Share the credentials with the client.
4.  Use persistent cookies to manage session IDs.

29\) Which location should you ideally use to store a session ID?

1.  URLs
2.  Form variables
3.  Persistent cookies
4.  Non-persistent cookies **Correct**

30\) Which of the following is the best way to ensure that JavaScript
cannot be used to access a cookie?

1.  Set the secure flag in the cookie
2.  Set the HttpOnly flag in the cookie **Correct**
3.  Use the CAPTCHA system
4.  Use non-persistent cookies

31\) Which of the following is an authentication system mandatory
requirement?

1.  Form variables are used for managing session IDs.
2.  Use a GOTCHA to prevent automated attacks.
3.  User logout and session inactivity controls. **Correct**
4.  Session IDs are only accepted from cookies and parameter variables.

32\) A session-based system authenticates a user to a Web site to
provide access to restricted resources. To increase security in this
scenario, an authentication token should meet which of the following
requirements?

1.  It should identify returning users to the site.
2.  It should be public information.
3.  It should always use a persistent cookie.
4.  It should always use a non-persistent cookie. **Correct**

33\) State whether the following statement is True or False. An
identification token is a replacement for a user’s credentials and
should allow access to restricted resources of a Web site.

1.  True
2.  False **Correct**

34\) Which of the following tasks is performed by a session-based
system?

1.  Identifying returning users **Correct**
2.  Using form variables for managing session IDs
3.  Using the HTTP protocol
4.  Sending successful logins to a well-known location

35\) Which threat is most likely to occur when a Web application fails
to validate a client's access to a resource?

1.  Injection
2.  Cross-site scripting
3.  Insecure direct object reference **Correct**
4.  Cross-site request forgery

36\) Which of the following objects is most susceptible to an insecure
direct object reference attack?

1.  Nonpersistent cookies
2.  Registry keys **Correct**
3.  Conditional constructs
4.  GET/POST parameters

37\) Which of the following vulnerabilities is most likely to occur due
to an insecure direct object reference attack?

1.  Executing commands on the server.
2.  Impersonating any user on the system.
3.  Modifying SQL data pointed to by the query.
4.  Accessing a resource without authorization. **Correct**

38\) Which of the following is the best way to mitigate the threat of an
insecure direct object reference attack?

1.  Use session-based indirection. **Correct**
2.  Use POST parameters instead of GET parameters.
3.  Use a regular expression.
4.  Send successful logins to a well-known location instead of automatic
    redirection.

39\) State whether the following statement is True or False. Time of
Check Time of Use (TOCTOU) occurs if the authorization check is
performed on one page of a Web site and the resource is used on a
different page.

1.  True **Correct**
2.  False

40\) Your Web application stores information about many accounts. Which
threat is your Web application susceptible to if you can manipulate the
URL of an account page to access all accounts?

1.  Cross-site request forgery
2.  Insecure direct object reference **Correct**
3.  Cross-site scripting
4.  Injection

41\) Which of the following threats is most likely to be caused by poor
input validation?

1.  Enabling of IPSec
2.  Insecure direct object reference **Correct**
3.  Insecure cryptographic storage
4.  Insufficient transport layer protection

42\) Which threat is most likely to occur when a POST parameter performs
an operation on behalf of a user without checking a shared secret?

1.  Cross-site request forgery **Correct**
2.  Insecure direct object reference
3.  Cross-site scripting
4.  Injection

43\) Which of the following is the most common result of a cross-site
request forgery?

1.  Elevation of privilege **Correct**
2.  Disabled security features
3.  Enabling of IPSec
4.  Misconfigured security features

44\) An attacker lures a victim to malicious content on a Web site. A
request is automatically sent to the vulnerable site which includes
victim’s credentials. Which attack is most likely to occur in this
scenario?

1.  Injection
2.  Cross-site scripting
3.  Insecure direct object reference
4.  Cross-site request forgery **Correct**

45\) State whether the following statement is True or False. The
downside of a nonce is that it needs to be stored on the client.

1.  True
2.  False **Correct**

46\) What should you add to an HMAC to ensure that the secret value is
unique for each request?

1.  Salt
2.  Nonce
3.  Session ID
4.  Timestamp **Correct**

47\) Which of the following practices should you observe in order to
implement defense-in-depth techniques against CSRF attacks?

1.  Use GET parameters
2.  Use automatic redirection.
3.  Don’t include secrets in the URL. **Correct**
4.  Resubmit POST parameters during redirection.

48\) State whether the following statement is True or False. HTTP GET
parameters limit the types of manipulation a malicious user can perform
on the victim to forge a request.

1.  True
2.  False **Correct**

49\) Which of the following mistakes is most often associated with a
security misconfiguration threat?

1.  Cross-site request forgery
2.  Failure to disable default accounts **Correct**
3.  Bad cryptography
4.  Unsafe key storage

50\) You have not yet applied some recent service packs and updates to
your Web application. Which of the following threats is your Web server
susceptible to?

1.  Injection
2.  Security misconfiguration **Correct**
3.  Insecure cryptographic storage
4.  Cross-site request forgery

51\) Which of the following is the best way to reevaluate your
environment and address new threats?

1.  Add or remove network segments. **Correct**
2.  Use the white-list validation of allowed input technique.
3.  Use custom cryptographic algorithms.
4.  Use your browser to forge unauthorized requests.

52\) Which of the following procedures are involved in the hardening
process?

1.  Disable unnecessary features. **Correct**
2.  Resubmit POST parameters during redirection.
3.  Repeat the process at random intervals.
4.  Update the environment with changes only when needed.

53\) Which of the following consequence is most likely to result if your
production environment does not match your development, testing, and
staging environments?

1.  Your application may not work as expected. **Correct**
2.  Testing your application may take a long time.
3.  Your application may be expensive to administer.
4.  Your application may have too many configuration files.

54\) Which of the following can result in insecure cryptography?

1.  Unsalted hash **Correct**
2.  Unused services
3.  Default accounts
4.  Rotating keys frequently

55\) Which of the following is most likely to result in insecure
cryptography?

1.  Unused services
2.  Unsalted hash **Correct**
3.  New products
4.  Missing patches

56\) Which of the following may result in cryptographic weakness?

1.  Failure to restrict URL access
2.  Insufficient cryptographic protocols **Correct**
3.  Missing patches
4.  Unnecessary/unused services or features

57\) Which of the following protocols is a network layer encryption
protocol?

1.  HTTP
2.  EFS
3.  IPSec **Correct**
4.  Kerberos

58\) Which of the following factors helps you secure keys?

1.  Complexity **Correct**
2.  Session-based indirection
3.  Escaping
4.  Encryption

59\) Which of the following combines public-key cryptography with a
cryptographic hash?

1.  Nonce
2.  Digital signature **Correct**
3.  SSL
4.  Salt

60\) hich of the following depicts the typical impact of failure to
restrict URL access?

1.  Attackers perform man-in-the-middle attacks.
2.  Attackers impersonate any user on the system.
3.  Attackers invoke functions and services they have no authorization
    for. **Correct**
4.  Attackers perform all actions that the victims themselves have
    permission to perform.

61\) Which of the following actions should you take to test the security
of your Web application?

1.  Use policy mechanisms.
2.  Use a simple and positive model at every layer.
3.  Set the secure flag on session ID cookies.
4.  Use your browser to forge unauthorized requests. **Correct**

62\) Which of the following should you use to protect the connections
between the physical tiers of your application?

1.  EFS
2.  SSL **Correct**
3.  HTTP
4.  Kerberos

63\) Which of the following is the best way to implement transport layer
protection?

1.  Install IDS
2.  Enable SSL **Correct**
3.  Set the HttpOnly flag on session ID cookies
4.  Perform client-side validation.

64\) Which of the following is most likely to result from unvalidated
redirects and forwards?

1.  Brute force attack
2.  Network sniffing
3.  Man-in-the-middle attack
4.  Bypassed authorization checks **Correct**

65\) Which of the following is the best way to protect a Web application
from unvalidated redirects and forwards?

1.  Validate the referrer header. **Correct**
2.  Use extended validation certificates.
3.  Use the escaping technique.
4.  Disallow requests to unauthorized file types.

66\) Which of the following is the best way to detect unvalidated
redirects and forwards?

1.  Use internal transfers without authorizing the user for target URL
2.  Use your browser to forge unauthorized requests
3.  Use weblogs to identify redirects and forwards **Correct**
4.  Use policy mechanisms

67\) State whether the following statement is True or False. Most
security issues are related to input and a user’s ability to interact
with and control input.

1.  True **Correct**
2.  False

68\) State whether the following statement is True or False. If user
input can be confused for instructions in the language or the way the
language is applied, then the language is vulnerable to an injection
attack.

1.  True **Correct**
2.  False

69\) In which of the following scenarios should you use the escaping
technique?

1.  When user input is echoed back to the user in HTML **Correct**
2.  When you need to validate any input as valid input
3.  When you are trying to protect against regular expression injection
4.  When you need to tell the interpreter that input is code

70\) Which of the following is the best way to prevent unvalidated
redirect and forwards vulnerabilities?

1.  Use an allow list, such as table indirection. **Correct**
2.  Use client-side validation.
3.  Allow only absolute redirects.
4.  Use session-based indirection.