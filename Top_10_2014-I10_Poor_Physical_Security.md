<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has physical access to the device.`

</td>

`    <td ``>Attacker uses vectors such as USB ports, SD cards or other storage means to access the Operating System and potentially any data stored on the device.`

</td>

`    <td colspan=2  ``>Physical security weaknesses are present when an attacker can disassemble a device to easily access the storage medium and any data stored on that medium. Weaknesses are also present when USB ports or other external ports can be used to access the device using features intended for configuration or maintenance.`

</td>

`    <td ``>Insufficient physical security could lead to compromise of the device itself and any data stored on that device.`

</td>

`    <td ``>Data could be stolen or modified and the device taken control of for purposes other than what was originally intended. Could your customers be harmed? Could your brand be harmed?`

</td>

Checking for Poor Physical Security includes:

  - Reviewing how easily a device can be disassembled and data storage
    mediums accessed or removed
  - Reviewing the use of external ports such as USB to determine if data
    can be accessed on the device without disassembling the device.
  - Reviewing the number of physical external ports to determine if all
    are required for proper device function
  - Reviewing the administrative interface to determine if external
    ports such as USB can be deactivated
  - Reviewing the administrative interface to determine if
    administrative capabilities can be limited to local access only

Adequate physical security requires:

1.  Ensuring data storage medium can not be easily removed.
2.  Ensuring stored data is encrypted at rest.
3.  Ensuring USB ports or other external ports can not be used to
    maliciously access the device.
4.  Ensuring device can not be easily disassembled.
5.  Ensuring only required external ports such as USB are required for
    the product to funtion
6.  Ensuring the product has the ability to limit administrative
    capabilities

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)

**Scenario \#1:** The device can be easily disassembled and storage
medium is an unencrypted SD card.

<span style="color:red;"> SD card can be removed and inserted into a
card reader to be modified or copied.

</span> **Scenario \#2:** USB ports are present on the device.
<span style="color:red;"> Custom software could be written to take
advantage of features such as updating via the USB port to modify the
original device software.

</span> In both cases, an attacker is able to access the original device
software and make modifications or simply copy specific target data.