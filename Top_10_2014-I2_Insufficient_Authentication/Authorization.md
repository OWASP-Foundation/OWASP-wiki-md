<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the web interface, mobile interface or cloud interface including internal and external users.`

</td>

`    <td ``>Attacker uses weak passwords, insecure password recovery mechanisms, poorly protected credentials or lack of granular access control to access a particular interface. Attack could come from external or internal users.`

</td>

`    <td colspan=2  ``>Authentication may not be sufficient when weak passwords are used or are poorly protected. Insufficient authentication/authorization is prevalent as it is assumed that interfaces will only be exposed to users on internal networks and not to external users on other networks. Deficiencies are often found to be present across all interfaces. Many Issues with authentication/authorization are easy to discover when examining the interface manually and can also be discovered via automated testing.`

</td>

`    <td ``>Insufficient authentication/authorization can result in data loss or corruption, lack of accountability, or denial of access and can lead to complete compromise of the device and/or user accounts.`

</td>

`    <td ``>Consider the business impact of compromised user accounts and possibly devices. All data could be stolen, modified, or deleted.  Could your customers be harmed?`

</td>

Checking for Insufficient Authentication includes:

  - Attempting to use simple passwords such as "1234" is a fast and easy
    way to determine if the password policy is sufficient across all
    interfaces
  - Reviewing network traffic to determine if credentials are being
    transmitted in clear text
  - Reviewing requirements around password controls such as password
    complexity, password history check, password expiration and forced
    password reset for new users
  - Reviewing whether re-authentication is required for sensitive
    features

Checking for Insufficient Authorization includes:

  - Reviewing the various interfaces to determine whether the interfaces
    allow for separation of roles. For example, all features will be
    accessible to administrators, but users will have a more limited set
    of features available.
  - Reviewing access controls and testing for privilege escalation

Sufficient authentication/authorization requires:

1.  Ensuring that the strong passwords are required
2.  Ensuring granular access control is in place when necessary
3.  Ensuring credentials are properly protected
4.  Implement two factor authentication where possible
5.  Ensuring that password recovery mechanisms are secure
6.  Ensuring re-authentication is required for sensitive features
7.  Ensuring options are available for configuring password controls
8.  Ensuring credential can be revoked
9.  The app authentication is required
10. The device authentication is required
11. The server authentication is required
12. Manage authenicated user id(credential info.) and the user's device
    id, the user's app id mapping table in the authentication server
13. Ensuring that the authentication token/session key issuing to client
    is always different
14. Ensuring that the user id, app id, device id is universally unique

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** The interface only requires simple passwords.

<span style="color:red;"> Username = Bob; Password = 1234

</span> **Scenario \#2:** Username and password are poorly protected
when transmitted over the network. <span style="color:red;">
Authorization: Basic YWRtaW46MTIzNA==

</span> In the cases above, the attacker is able to either easily guess
the password or is able to capture the credentials as they cross the
network and decode it since the credentials are only protected using
Base64 Encoding.

[Top 10 2013-A2-Broken Authentication and Session
Management](https://www.owasp.org/index.php/Top_10_2013-A2-Broken_Authentication_and_Session_Management)