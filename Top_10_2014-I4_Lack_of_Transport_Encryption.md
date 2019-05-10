<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the network the device is connected to, including external and internal users.`

</td>

`    <td ``>Attacker uses the lack of transport encryption to view data being passed over the network. Attack could come from external or internal users.`

</td>

`    <td colspan=2  ``>Lack of transport encryption allows data to be viewed as it travels over local networks or the internet. Lack of transport encryption is prevalent on local networks as it is easy to assume that local network traffic will not be widely visible, however in the case of a local wireless network, misconfiguration of that wireless network can make traffic visible to anyone within range of that wireless network. Many Issues with transport encryption are easy to discover simply by viewing network traffic and searching for readable data. Automated tools can also look for proper implementation of common transport encryption such as SSL and TLS.`

</td>

`    <td ``>Lack of transport encryption can result in data loss and depending on the data exposed, could lead to complete compromise of the device or user accounts.`

</td>

`    <td ``>Consider the business impact of exposed data as it travels across various networks. Data could be stolen or modified.  Could your users be harmed by having their data exposed?`

</td>

Checking for Lack of Transport Encryption includes:

  - Reviewing network traffic of the device, its mobile application and
    any cloud connections to determine if any information is passed in
    clear text
  - Reviewing the use of SSL or TLS to ensure it is up to date and
    properly implemented
  - Reviewing the use of any encryption protocols to ensure they are
    recommended and accepted

Sufficient transport encryption requires:

1.  Ensuring data is encrypted using protocols such as SSL and TLS while
    transiting networks.
2.  Ensuring other industry standard encryption techniques are utilized
    to protect data during transport if SSL or TLS are not available.
3.  Ensuring only accepted encryption standards are used and avoid using
    proprietary encryption protocols
4.  Ensuring the message payload encryption
5.  Ensuring the secure encryption key handshaking
6.  Ensuring received data integrity verification

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** The cloud interface uses only HTTP.

<span style="color:red;"> http://www.xyzcloudsite.com

</span> **Scenario \#2:** Username and password are transmitted in the
clear over the network. <span style="color:red;">
http://www.xyzcloud.com/login.php?userid=3\&password=1234

</span> In the cases above, the attacker has the ability to view
sensitive data in the clear due to lack of transport encryption.

[Top 10 2013-A6-Sensitive Data
Exposure](https://www.owasp.org/index.php/Top_10_2013-A6-Sensitive_Data_Exposure)