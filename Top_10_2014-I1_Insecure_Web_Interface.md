<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the web interface including internal and external users.`

</td>

`    <td ``>Attacker uses weak credentials, captures plain-text credentials or enumerates accounts to access the web interface. Attack could come from external or internal users.`

</td>

`    <td colspan=2  ``>An insecure web interface can be present when issues such as account enumeration, lack of account lockout or weak credenitals are present. Insecure web interfaces are prevalent as the intent is to have these interfaces exposed only on internal networks, however threats from the internal users can be just as significant as threats from external users. Issues with the web interface are easy to discover when examining the interface manually along with automated testing tools to identify other issues such as cross-site scripting.`

</td>

`    <td ``>Insecure web interfaces can result in data loss or corruption, lack of accountability, or denial of access and can lead to complete device takeover.`

</td>

`    <td ``>Consider the business impact of poorly secured web interfaces that could lead to compromised devices along with compromised customers. Could your customers be harmed? Could your brand be harmed?`

</td>

Checking for an Insecure Web Interface includes:

  - Determining if the default username and password can be changed
    during initial product setup
  - Determining if a specific user account is locked out after 3 - 5
    failed login attempts
  - Determining if valid accounts can be identified using password
    recovery mechanisms or new user pages
  - Reviewing the interface for issues such as cross-site scripting,
    cross-site request forgery and sql injection.

A secure web interface requires:

1.  Default passwords and ideally default usernames to be changed during
    initial setup
2.  Ensuring password recovery mechanisms are robust and do not supply
    an attacker with information indicating a valid account
3.  Ensuring web interface is not susceptible to XSS, SQLi or CSRF
4.  Ensuring credentials are not exposed in internal or external network
    traffic
5.  Ensuring weak passwords are not allowed
6.  Ensuring account lockout after 3 -5 failed login attempts

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** The web interface presents "Forgot Password"
functionality which upon entering an invalid account informs the
attacker that the account does not exist. Once valid accounts are
identified, password guessing can begin for an indefinite amount of time
if no account lockout controls exist.

<span style="color:red;"> Account john@doe.com does not exist.

</span> **Scenario \#2:** Web interface is susceptible to cross-site
scripting. <span style="color:red;">
http://xyz.com/index.php?user=\<script\>alert(123)\</script\> ...
Response from browser is an alert popup. </span> In the cases above, the
attacker is able to easily determine if an account is valid or not and
is also able to determine that the site is susceptible to cross-site
scripting (XSS).

  - [Top 10 2013-A1-Injection](https://www.owasp.org/index.php/Top_10_2013-A1-Injection)
  - [Top 10 2013-A3-Cross-Site
    Scripting](https://www.owasp.org/index.php/Top_10_2013-A3-Cross-Site_Scripting_\(XSS\))
  - [Top 10 2013-A8-Cross-Site Request Forgery
    (CSRF)](https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_\(CSRF\))