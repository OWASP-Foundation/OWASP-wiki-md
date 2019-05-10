<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the device via a network connection, including external and internal users.`

</td>

`    <td ``>Attacker uses vulnerable network services to attack the device itself or bounce attacks off the device. Attack could come from external or internal users.`

</td>

`    <td colspan=2  ``>Insecure network services may be susceptible to buffer overflow attacks or attacks that create a denial of service condition leaving the device inaccessible to the user. Denial of service attacks against other users may also be facilitated when insecure network services are available. Insecure network services can often be detected by automated tools such as port scanners and fuzzers.`

</td>

`    <td ``>Insecure network services can result in data loss or corruption, denial of service or facilitation of attacks on other devices.`

</td>

`    <td ``>Consider the business impact of devices which have been rendered useless from a denial of service attack or the device is used to facilitate attacks against other devices and networks. Could your customers or other users be harmed?`

</td>

Checking for Insecure Network Services includes:

  - Determining if insecure network services exist by reviewing your
    device for open ports using a port scanner
  - As open ports are identified, each can be tested using any number of
    automated tools that look for DoS vulnerabilities, vulnerabilities
    related to UDP services and vulnerabilities related to buffer
    overflow and fuzzing attacks
  - Reviewing network ports to ensure they are absolutely necessary and
    if there are any ports being exposed to the internet using UPnP.

Securing network services requires:

1.  Ensuring only necessary ports are exposed and available.
2.  Ensuring services are not vulnerable to buffer overflow and fuzzing
    attacks.
3.  Ensuring services are not vulnerable to DoS attacks which can affect
    the device itself or other devices and/or users on the local network
    or other networks.
4.  Ensuring network ports or services are not exposed to the internet
    via UPnP for example
5.  The abnormal service request traffic should be detected and blocked
    on service gateway layer

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** Fuzzing attack causes network service and device to
crash.

<span style="color:red;"> GET %s%s%s%s%s%s%s%s%s%s%s%s%s%s%s HTTP/1.0

</span> **Scenario \#2:** Ports open to the internet possibly without
the user's knowledge via UPnP. <span style="color:red;"> Port 80 and 443
exposed to the internet via a home router.

</span> In the cases above, the attacker is able to disable the device
completely with an HTTP GET or access the device via the internet over
port 80 and/or port 443.