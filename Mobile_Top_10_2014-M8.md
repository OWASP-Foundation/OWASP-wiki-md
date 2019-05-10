<center>

[Back To The Mobile Top Ten Main
Page](https://www.owasp.org/index.php/Projects/OWASP_Mobile_Security_Project_-_Top_Ten_Mobile_Risks)

</center>

`    <td ``>Threat Agents include entities that can pass untrusted inputs to the sensitive method calls. Examples of such entities include, but are not limited to, users, malware and vulnerable apps.`

</td>

`    <td ``> Exploitability of this vulnerability remains easy. `
` An attacker with access to app can intercept intermediate calls and manipulate results via parameter tampering. `

</td>

`    <td colspan=2  ``>Developers generally use hidden fields and values or any hidden functionality to distinguish higher level users from lower level users. An attacker can intercept the calls (IPC or web service calls) and temper with such sensitive parameters. Weak implementation of such functionalities leads to improper behavior of an app and even granting higher level permissions to an attacker.This can easily be exploited through hooking functionality. `

</td>

`    <td ``>This vulnerability may lead to privilege escalation providing access of higher authorities and functionalities to an attacker. It can even bypass security mechanisms implemented by the app leading to loss of confidentiality and integrity. `

</td>

`    <td ``>This vulnerability leads to loss of reputation. `
`At the same time, impacting and harming the integrity and confidentiality. `

</td>

Your mobile application can accept data from all kinds of sources. In
most cases this will be an Inter Process Communication (IPC) mechanism.
In general try and adhere to the following IPC design patterns:

  - If there is a business requirement for IPC communication, the mobile
    application should restrict access to a white-list of trusted
    applications
  - Sensitive actions which are triggered through IPC entry points
    should require user interaction before performing the action
  - All input received from IPC entry points must undergo stringent
    input validation in order to prevent input driven attacks
  - Do not pass any sensitive information through IPC mechanisms, as it
    may be susceptible to being read by third party applications under
    certain scenarios

iOS Specific Examples:

  - Do not use the deprecated handleOpenURL method to handle URL Scheme
    calls. This method does not contain an argument containing the
    BundleID of the source application.
      - Instead use the openURL:sourceApplication:annotation method and
        validation the sourceApplication argument against a white-list
        of trusted applications
  - Do not use the iOS Pasteboard for IPC communications, as it is
    susceptible to being set or read by all third party apps on the
    device.

Android Specific Examples

  -
Example Scenarios  References

[An In Depth Introduction to the Android Permissions Modeland How to
Secure MultiComponent
Applications](https://www.owasp.org/images/c/ca/ASDC12-An_InDepth_Introduction_to_the_Android_Permissions_Modeland_How_to_Secure_MultiComponent_Applications.pdf)