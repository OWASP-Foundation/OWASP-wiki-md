<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the internet.`

</td>

`    <td ``>Attacker uses multiple vectors such as insufficient authentication, lack of transport encryption and account enumeration to access data or controls via the cloud website. Attack will most likely come from the internet.`

</td>

`    <td colspan=2  ``>An insecure cloud interface is present when easy to guess credentials are used or account enumeration is possible. Insecure cloud interfaces are easy to discover by simply reviewing the connection to the cloud interface and identifying if SSL is in use or by using the password reset mechanism to identify valid accounts which can lead to account enumeration.`

</td>

`    <td ``>An insecure cloud interface could lead to compromise of user data and control over the device.`

</td>

`    <td ``>Consider the business impact of an insecure cloud interface. Data could be stolen or modified and control over devices assumed.  Could your customers be harmed? Could your brand be harmed?`

</td>

Checking for a Insecure Cloud Interface includes:

  - Determining if the default username and password can be changed
    during initial product setup
  - Determining if a specific user account is locked out after 3 - 5
    failed login attempts
  - Determining if valid accounts can be identified using password
    recovery mechanisms or new user pages
  - Reviewing the interface for issues such as cross-site scripting,
    cross-site request forgery and sql injection.
  - Reviewing all cloud interfaces for vulnerabilities (API interfaces
    and cloud-based web interfaces)

A secure cloud interface requires:

1.  Default passwords and ideally default usernames to be changed during
    initial setup
2.  Ensuring user accounts can not be enumerated using functionality
    such as password reset mechanisms
3.  Ensuring account lockout after 3- 5 failed login attempts
4.  Ensuring the cloud-based web interface is not susceptible to XSS,
    SQLi or CSRF
5.  Ensuring credentials are not exposed over the internet
6.  Implement two factor authentication if possible
7.  Detect or block the abnormal reqests/attempts

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** Password reset indicates whether account is valid.

<span style="color:red;"> Password Reset "That account does not exist."

</span> **Scenario \#2:** Username and password are poorly protected
when transmitted over the network. <span style="color:red;">
Authorization: Basic S2ZjSDFzYkF4ZzoxMjM0NTY3

</span> In the cases above, the attacker is able to either determine a
valid user account or is able to capture the credentials as they cross
the network and decode them since the credentials are only protected
using Base64 Encoding.

  - [Top 10 2013-A1-Injection](https://www.owasp.org/index.php/Top_10_2013-A1-Injection)
  - [Top 10 2013-A3-Cross-Site
    Scripting](https://www.owasp.org/index.php/Top_10_2013-A3-Cross-Site_Scripting_\(XSS\))
  - [Top 10 2013-A8-Cross-Site Request Forgery
    (CSRF)](https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_\(CSRF\))