![Cornucopia_-_Ecommerce_Website_VE_K.png](Cornucopia_-_Ecommerce_Website_VE_K.png
"Cornucopia_-_Ecommerce_Website_VE_K.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** K

### Description:

Gabe can inject data into an server-side interpreter (e.g. SQL, OS
commands, Xpath, Server JavaScript, SMTP) because a strongly typed
parameterised interface is not being used or has not been implemented
correctly.

### Technical Note:

Due a failure of server-side input or output validation, encoding or
sanitization, malicious code can be injected and treated as code rather
than data, leading to code execution in the server application.

NB: This relates to actual exploitation of an injection vulnerability on
the **server-side**. See [VE
Q](Cornucopia_-_Ecommerce_Website_-_VE_Q "wikilink") for the same attack
client-side, and other cards in this suit for individual data validation
and encoding issues (e.g. missing/by-passable/badly-implemented
input/output validation, encoding or sanitization).

### References:

<table class="wikitable" style="text-align:center;">

<tr>

<th>

OWASP SCP

</th>

<th>

OWASP ASVS

</th>

<th>

OWASP AppSensor

</th>

<th>

CAPEC

</th>

<th>

SAFECODE

</th>

</tr>

<tr>

<td>

[15](OWASP_Secure_Coding_Practices_Checklist#15 "wikilink")

</td>

<td>

[5.10](OWASP_Application_Security_Verification_Standard#5.10 "wikilink")

</td>

<td>

[CIE1](AppSensor_DetectionPoints#CIE1 "wikilink")

</td>

<td>

[23](https://capec.mitre.org/data/definitions/23.html)

</td>

<td>

[2](SAFECode_Practical_Security_Stories#2 "wikilink")

</td>

</tr>

<tr>

<td>

[19](OWASP_Secure_Coding_Practices_Checklist#19 "wikilink")

</td>

<td>

[5.11](OWASP_Application_Security_Verification_Standard#5.11 "wikilink")

</td>

<td>

[CIE2](AppSensor_DetectionPoints#CIE2 "wikilink")

</td>

<td>

[28](https://capec.mitre.org/data/definitions/28.html)

</td>

<td>

[19](SAFECode_Practical_Security_Stories#19 "wikilink")

</td>

</tr>

<tr>

<td>

[20](OWASP_Secure_Coding_Practices_Checklist#20 "wikilink")

</td>

<td>

[5.12](OWASP_Application_Security_Verification_Standard#5.12 "wikilink")

</td>

<td>

</td>

<td>

[76](https://capec.mitre.org/data/definitions/76.html)

</td>

<td>

[20](SAFECode_Practical_Security_Stories#20 "wikilink")

</td>

</tr>

<tr>

<td>

[21](OWASP_Secure_Coding_Practices_Checklist#21 "wikilink")

</td>

<td>

[5.13](OWASP_Application_Security_Verification_Standard#5.13 "wikilink")

</td>

<td>

</td>

<td>

[152](https://capec.mitre.org/data/definitions/152.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[22](OWASP_Secure_Coding_Practices_Checklist#22 "wikilink")

</td>

<td>

[5.14](OWASP_Application_Security_Verification_Standard#5.14 "wikilink")

</td>

<td>

</td>

<td>

[160](https://capec.mitre.org/data/definitions/160.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[167](OWASP_Secure_Coding_Practices_Checklist#167 "wikilink")

</td>

<td>

[5.16](OWASP_Application_Security_Verification_Standard#5.16 "wikilink")

</td>

<td>

</td>

<td>

[261](https://capec.mitre.org/data/definitions/261.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[180](OWASP_Secure_Coding_Practices_Checklist#180 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

</td>

</tr>

<tr>

<td>

[204](OWASP_Secure_Coding_Practices_Checklist#204 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

</td>

</tr>

<tr>

<td>

[211](OWASP_Secure_Coding_Practices_Checklist#211 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

</td>

</tr>

<tr>

<td>

[212](OWASP_Secure_Coding_Practices_Checklist#212 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_Q "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_A "wikilink")

</div>