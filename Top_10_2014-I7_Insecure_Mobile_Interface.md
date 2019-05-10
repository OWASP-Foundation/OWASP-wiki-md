<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the mobile application.`

</td>

`    <td ``>Attacker uses multiple vectors such as insufficient authentication, lack of transport encryption and account enumeration to access data or controls via the mobile interface.`

</td>

`    <td colspan=2  ``>An insecure mobile interface is present when easy to guess credentials are used or account enumeration is possible. Insecure mobile interfaces are easy to discover by simply reviewing the connection to the wireless networks and identifying if SSL is in use or by using the password reset mechanism to identify valid accounts which can lead to account enumeration.`

</td>

`    <td ``>An insecure mobile interface could lead to compromise of user data and control over the device.`

</td>

`    <td ``>Consider the business impact of an insecure mobile interface. Data could be stolen or modified and control over devices assumed. Could your customers be harmed? Could your brand be harmed?`

</td>

Checking for an Insecure Mobile Interface includes:

  - Determining if the default username and password can be changed
    during initial product setup
  - Determining if a specific user account is locked out after 3 - 5
    failed login attempts
  - Determining if valid accounts can be identified using password
    recovery mechanisms or new user pages
  - Reviewing whether credentials are exposed while connected to
    wireless networks
  - Reviewing whether two factor authentication options are available

A secure mobile interface requires:

1.  Default passwords and ideally default usernames to be changed during
    initial setup
2.  Ensuring user accounts can not be enumerated using functionality
    such as password reset mechanisms
3.  Ensuring account lockout after an 3 - 5 failed login attempts
4.  Ensuring credentials are not exposed while connected to wireless
    networks
5.  Implementing two factor authentication if possible
6.  Apply mobile app obfuscation techinque
7.  Implement mbile app anti-tempering mechanism
8.  Ensuring the mobile app's memory hacking is possible
9.  Restric the mobile app's execution on tempered OS environment

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** Password reset indicates whether account exist or
not.

<span style="color:red;"> Password Reset "That account does not exist."

</span> **Scenario \#2:** Username and password are poorly protected
when transmitted over the network. <span style="color:red;">
Authorization: Basic S2ZjSDFzYkF4ZzoxMjM0NTY3

</span> In the cases above, the attacker is able to either determine a
valid user account or is able to capture the credentials as they cross
the network and decode them since the credentials are only protected
using Base64 Encoding.

[OWASP Top Ten Mobile
Risks](https://www.owasp.org/index.php/Projects/OWASP_Mobile_Security_Project_-_Top_Ten_Mobile_Risks)