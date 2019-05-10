<center>

[Back To The Internet of Things
Top 10](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Top_10_IoT_Vulnerabilities__282014_29)

</center>

`    <td ``>Consider anyone who has access to the device itself, the network the device is connected to, the mobile application and the cloud connection including external and internal users.`

</td>

`    <td ``>Attacker uses multiple vectors such as insufficient authentication, lack of transport encryption or insecure network services to view personal data which is not being properly protected or is being collected unnecessarily. Attack could come from external or internal users.`

</td>

`    <td colspan=2  ``>Privacy concerns generated by the collection of personal data in addition to the lack of proper protection of that data is prevalent. Privacy concerns are easy to discover by simply reviewing the data that is being collected as the user sets up and activates the device. Automated tools can also look for specific patterns of data that may indicate collection of personal data or other sensitive data.`

</td>

`    <td ``>Collection of personal data along with a lack of protection of that data can lead to compromise of a user's personal data.`

</td>

`    <td ``>Consider the business impact of personal data that is collected unnecessarily or isn't protected properly. Data could be stolen.  Could your customers be harmed by having this personal data exposed?`

</td>

Checking for Privacy Concerns includes:

  - Identifying all data types that are being collected by the device,
    its mobile application and any cloud interfaces
  - The device and it's various components should only collect what is
    necessary to perform its function
  - Personally identifiable information can be exposed when not properly
    encrypted while at rest on storage mediums and during transit over
    networks
  - Reviewing who has access to personal information that is collected
  - Determining if data collected can be de-identified or anonymized
  - Determining if data collected is beyond what is needed for proper
    operation of the device (Does the end-user have a choice for this
    data collection?)
  - Determining if a data retention policy is in place

Minimizing privacy concerns requires:

1.  Ensuring only data critical to the functionality of the device is
    collected
2.  Ensuring that any data collected is of a less sensitive nature
    (i.e., try not to collect sensitive data)
3.  Ensuring that any data collected is de-identified or anonymized
4.  Ensuring any data collected is properly protected with encryption
5.  Ensuring the device and all of its components properly protect
    personal information
6.  Ensuring only authorized individuals have access to collected
    personal information
7.  Ensuring that retention limits are set for collected data
8.  Ensuring that end-users are provided with "Notice and Choice" if
    data collected is more than what would be expected from the product
9.  Ensuring the role based access control/authorization to the
    collected data/analyzed data is applied
10. Ensuring that the analyzed data is de-identified

Please review the following tabs for more detail based on whether you
are a
[Manufacturer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Manufacturers),
[Developer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Developers)
or
[Consumer](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Top_Ten_Project#tab=Consumers)
 **Scenario \#1:** Collection of personal data.

<span style="color:red;"> Date of birth, home address, phone number,
etc.

</span> **Scenario \#2:** Collection of financial and/or health
information. <span style="color:red;"> Credit card data and bank account
information.

</span> In the cases above, exposure of any of the data examples could
lead to identity theft or compromise of accounts.

[Top 10 2013-A6-Sensitive Data
Exposure](https://www.owasp.org/index.php/Top_10_2013-A6-Sensitive_Data_Exposure)
[Top 10 Privacy Risks
Project](https://www.owasp.org/index.php/OWASP_Top_10_Privacy_Risks_Project)


[FTC: Careful Connections: Building Security in the Internet of
Things](https://www.ftc.gov/tips-advice/business-center/guidance/careful-connections-building-security-internet-things)
[FTC: Internet of Things, Privacy & Security in a Connected
World](https://www.ftc.gov/system/files/documents/reports/federal-trade-commission-staff-report-november-2013-workshop-entitled-internet-things-privacy/150127iotrpt.pdf)