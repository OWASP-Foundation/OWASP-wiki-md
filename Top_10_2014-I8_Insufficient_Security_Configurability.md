<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the device.`

</td>

`    <td ``>Attacker uses the lack of granular permissions to access data or controls on the device. The attacker could also us the lack of encryption options and lack of password options to perform other attacks which lead to compromise of the device and/or data. Attack could potentially come from any user of the device whether intentional or accidental.`

</td>

`    <td colspan=2  ``>Insufficient security configurability is present when users of the device have limited or no ability to alter its security controls. Insufficient security configurability is apparent when the web interface of the device has no options for creating granular user permissions or for example, forcing the use of strong passwords. Manual review of the web interface and its available options will reveal these deficiencies. `

</td>

`    <td ``>Insufficient security configurability could lead to compromise of the device whether intentional or accidental and/or data loss.`

</td>

`    <td ``>Consider the business impact if data can be stolen or modified and control over the device assumed. Could your customers be harmed?`

</td>

Checking for Insufficient Security Configurability includes:

  - Reviewing the administrative interface of the device for options to
    strengthen security such as forcing the creation of strong passwords
  - Reviewing the administrative interface for the ability to separate
    admin users from normal users
  - Reviewing the administrative interface for encryption options
  - Reviewing the administrative interface for options to enable secure
    logging of various security events
  - Reviewing the administrative interface for options to enable alerts
    and notifications to the end user for security events

Sufficient security configurability requires:

1.  Ensuring the ability to separate normal users from administrative
    users
2.  Ensuring the ability to encrypt data at rest or in transit
3.  Ensuring the ability to force strong password policies
4.  Ensuring the ability to enable logging of security events
5.  Ensuring the ability to notify end users of security events

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** No ability to enforce strong password policies.

<span style="color:red;"> Admins and users are allowed to create
passwords for their accounts.

</span> **Scenario \#2:** No ability to enable encryption of data at
rest. <span style="color:red;"> Password or other sensitive data stored
on the device may not be encrypted.

</span> In the cases above, the attacker is able to use the lack of
these controls to get access to user accounts with weak passwords or
access data at rest which has protection.