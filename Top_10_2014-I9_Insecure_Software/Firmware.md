<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the device and/or the network the device resides on. Also consider anyone who could gain access to the update server.`

</td>

`    <td ``>Attacker uses multiple vectors such as capturing update files via unencrypted connections, the update file itself is not encrypted or they are able to perform their own malicious update via DNS hijacking. Depending on method of update and device configuration, attack could come from the local network or the internet.`

</td>

`    <td colspan=2  ``>The lack of ability for a device to be updated presents a security weakness on its own. Devices should have the ability to be updated when vulnerabilities are discovered and software/firmware updates can be insecure when the updated files themselves and the network connection they are delivered on are not protected. Software/Firmware can also be insecure if they contain hardcoded sensitive data such as credentials. Security issues with software/firmware are relatively easy to discover by simply inspecting the network traffic during the update to check for encryption or using a hex editor to inspect the update file itself for interesting information.`

</td>

`    <td ``>Insecure software/firmware could lead to compromise of user data, control over the device and attacks against other devices.`

</td>

`    <td ``>Consider the business impact if data can be stolen or modified and devices taken control of for the purpose of attacking other devices.  Could your customers be harmed? Could other users be harmed?`

</td>

  - Note - It is very important that devices first and foremost have the
    ability to update and perform updates regularly.

Checking for insecure software/firmware updates include:

  - Reviewing the update file itself for exposure of sensitive
    information in human readable format by someone using a hex edit
    tool
  - Reviewing the production file update for proper encryption using
    accepted algorithms
  - Reviewing the production file update to ensure it is properly signed
  - Reviewing the communication method used to transmit the update
  - Reviewing the cloud update server to ensure transport encryption
    methods are up to date and properly configured and that the server
    itself is not vulnerable
  - Reviewing the device for proper validation of signed update files

Securing software/firmware require:

1.  Ensuring the device has the ability to update (very important, need
    secure update mechanism)
2.  Ensuring the update file is encrypted using accepted encryption
    methods
3.  Ensuring the update file is transmitted via an encrypted connection
4.  Ensuring the update file does not expose sensitive data
5.  Ensuring the update is signed and verified before allowing the
    update to be uploaded and applied
6.  Ensuring the update server is secure
7.  Implement the secure boot if possible (chain of trust)

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)

**Scenario \#1:** Update file is transmitted via HTTP.

<span style="color:red;"> http://www.xyz.com/update.bin

</span> **Scenario \#2:** Update file is unencrypted and human readable
data can be viewed. <span style="color:red;">
�v�ñ\]��Ü��Qw�û\]��ˇ3DP�Ö�∂\]��ˇ3DPadmin.htmadvanced.htmalarms.htm

</span> In the cases above, the attacker is able to either capture the
update file or capture the file and view it's contents.