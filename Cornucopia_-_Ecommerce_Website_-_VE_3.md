![Cornucopia_-_Ecommerce_Website_VE_3.png](Cornucopia_-_Ecommerce_Website_VE_3.png
"Cornucopia_-_Ecommerce_Website_VE_3.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 3

### Description:

Robert can input malicious data because the allowed protocol format is
not being checked, or duplicates are accepted, or the structure is not
being verified, or the individual data elements are not being validated
for format, type, range, length and a whitelist of allowed characters or
formats.

### Technical Note:

A lack of input validation is often the root cause of many security
issues. Since the validation needs to be context specific, generic
sanitisation routines will not suffice and the developer needs to
understand how data are formatted/composed, why the data is being sent,
what it is used for and the meaning of the values. This input validation
should ensure that

  - Only the permitted inputs (field/parameter names) are supplied.
  - All the mandatory inputs are supplied.
  - The values associated with the field/parameter name are of the
    expected format, type, range, length, etc.

NB: This card relates to **generic input validation**. See [VE
4](Cornucopia_-_Ecommerce_Website_-_VE_4 "wikilink") for the similar
additional context-specific checks.

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

[8](OWASP_Secure_Coding_Practices_Checklist#8 "wikilink")

</td>

<td>

[5.4](OWASP_Application_Security_Verification_Standard#5.4 "wikilink")

</td>

<td>

[RE7](AppSensor_DetectionPoints#RE7 "wikilink")

</td>

<td>

[28](https://capec.mitre.org/data/definitions/28.html)

</td>

<td>

[3](SAFECode_Practical_Security_Stories#3 "wikilink")

</td>

</tr>

<tr>

<td>

[9](OWASP_Secure_Coding_Practices_Checklist#9 "wikilink")

</td>

<td>

[5.18](OWASP_Application_Security_Verification_Standard#5.18 "wikilink")

</td>

<td>

[RE8](AppSensor_DetectionPoints#RE8 "wikilink")

</td>

<td>

[48](https://capec.mitre.org/data/definitions/48.html)

</td>

<td>

[16](SAFECode_Practical_Security_Stories#16 "wikilink")

</td>

</tr>

<tr>

<td>

[11](OWASP_Secure_Coding_Practices_Checklist#11 "wikilink")

</td>

<td>

[11.2](OWASP_Application_Security_Verification_Standard#11.2 "wikilink")

</td>

<td>

[AE4](AppSensor_DetectionPoints#AE4 "wikilink")

</td>

<td>

[126](https://capec.mitre.org/data/definitions/126.html)

</td>

<td>

[24](SAFECode_Practical_Security_Stories#24 "wikilink")

</td>

</tr>

<tr>

<td>

[12](OWASP_Secure_Coding_Practices_Checklist#12 "wikilink")

</td>

<td>

[11.3](OWASP_Application_Security_Verification_Standard#11.3 "wikilink")

</td>

<td>

[AE7](AppSensor_DetectionPoints#AE7 "wikilink")

</td>

<td>

[165](https://capec.mitre.org/data/definitions/165.html)

</td>

<td>

[35](SAFECode_Practical_Security_Stories#35 "wikilink")

</td>

</tr>

<tr>

<td>

[13](OWASP_Secure_Coding_Practices_Checklist#13 "wikilink")

</td>

<td>

[11.6](OWASP_Application_Security_Verification_Standard#11.6 "wikilink")

</td>

<td>

[IE2](AppSensor_DetectionPoints#IE2 "wikilink")

</td>

<td>

[213](https://capec.mitre.org/data/definitions/213.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[14](OWASP_Secure_Coding_Practices_Checklist#14 "wikilink")

</td>

<td>

</td>

<td>

[IE3](AppSensor_DetectionPoints#IE3 "wikilink")

</td>

<td>

[220](https://capec.mitre.org/data/definitions/220.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[16](OWASP_Secure_Coding_Practices_Checklist#16 "wikilink")

</td>

<td>

</td>

<td>

[CIE1](AppSensor_DetectionPoints#CIE1 "wikilink")

</td>

<td>

[221](https://capec.mitre.org/data/definitions/221.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[159](OWASP_Secure_Coding_Practices_Checklist#159 "wikilink")

</td>

<td>

</td>

<td>

[CIE3](AppSensor_DetectionPoints#CIE3 "wikilink")

</td>

<td>

[257](https://capec.mitre.org/data/definitions/257.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[190](OWASP_Secure_Coding_Practices_Checklist#190 "wikilink")

</td>

<td>

</td>

<td>

[CIE4](AppSensor_DetectionPoints#CIE4 "wikilink")

</td>

<td>

[261](https://capec.mitre.org/data/definitions/261.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[191](OWASP_Secure_Coding_Practices_Checklist#191 "wikilink")

</td>

<td>

</td>

<td>

[HT1](AppSensor_DetectionPoints#HT1 "wikilink")

</td>

<td>

[271](https://capec.mitre.org/data/definitions/271.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

</td>

<td>

</td>

<td>

[HT2](AppSensor_DetectionPoints#HT2 "wikilink")

</td>

<td>

[272](https://capec.mitre.org/data/definitions/272.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

</td>

<td>

</td>

<td>

[HT3](AppSensor_DetectionPoints#HT3 "wikilink")

</td>

<td>

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_2 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_4 "wikilink")

</div>