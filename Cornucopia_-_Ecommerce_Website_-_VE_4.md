![Cornucopia_-_Ecommerce_Website_VE_4.png](Cornucopia_-_Ecommerce_Website_VE_4.png
"Cornucopia_-_Ecommerce_Website_VE_4.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 4

### Description:

Dave can input malicious field names or data because it is not being
checked within the context of the current user and process.

### Technical Note:

Malicious data can be introduced voluntarily (as part of an attack) or
involuntarily (e.g. XSS). Some input checks should be dependent upon the
function or user's context (e.g. the data is valid for one user but not
another). There are many alternatives to this kind of attack:

  - Tampering request types, URLs, cookies, session identifiers, fields
    or values that are not validated.
  - Adding, removing or duplicating request fields or values to exploit
    code behaviour (e.g. mass parameter assignment, parameter pollution,
    passing partial authentication data).
  - Sending requests that are processed independently of the user
    activities (stage, amount of requests, privileges).
  - Fuzzing a file input.

Depending of the target of the attack, the results of this type of input
varies widely:

  - Information disclosure (error logs, system responses, etc.).
  - Operations tampering (SQLi, eShoplifting).
  - Denial of Service.
  - Spoofing.
  - Code execution.

NB: This card relates to **context-specific input validation**. See [VE
3](Cornucopia_-_Ecommerce_Website_-_VE_3 "wikilink") for the similar
generic input validation checks.

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

[5.17](OWASP_Application_Security_Verification_Standard#5.17 "wikilink")

</td>

<td>

[RE3](AppSensor_DetectionPoints#RE3 "wikilink")

</td>

<td>

[28](https://capec.mitre.org/data/definitions/28.html)

</td>

<td>

[24](SAFECode_Practical_Security_Stories#24 "wikilink")

</td>

</tr>

<tr>

<td>

[10](OWASP_Secure_Coding_Practices_Checklist#10 "wikilink")

</td>

<td>

[15.2](OWASP_Application_Security_Verification_Standard#15.2 "wikilink")

</td>

<td>

[RE4](AppSensor_DetectionPoints#RE4 "wikilink")

</td>

<td>

[31](https://capec.mitre.org/data/definitions/31.html)

</td>

<td>

[35](SAFECode_Practical_Security_Stories#35 "wikilink")

</td>

</tr>

<tr>

<td>

[183](OWASP_Secure_Coding_Practices_Checklist#183 "wikilink")

</td>

<td>

[15.3](OWASP_Application_Security_Verification_Standard#15.3 "wikilink")

</td>

<td>

[RE5](AppSensor_DetectionPoints#RE5 "wikilink")

</td>

<td>

[48](https://capec.mitre.org/data/definitions/48.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

</td>

<td>

[15.10](OWASP_Application_Security_Verification_Standard#15.10 "wikilink")

</td>

<td>

[RE6](AppSensor_DetectionPoints#RE6 "wikilink")

</td>

<td>

[126](https://capec.mitre.org/data/definitions/126.html)

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

[AE8](AppSensor_DetectionPoints#AE8 "wikilink")

</td>

<td>

[162](https://capec.mitre.org/data/definitions/162.html)

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

[AE9](AppSensor_DetectionPoints#AE9 "wikilink")

</td>

<td>

[165](https://capec.mitre.org/data/definitions/165.html)

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

[AE10](AppSensor_DetectionPoints#AE10 "wikilink")

</td>

<td>

[213](https://capec.mitre.org/data/definitions/213.html)

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

[AE11](AppSensor_DetectionPoints#AE11 "wikilink")

</td>

<td>

[220](https://capec.mitre.org/data/definitions/220.html)

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

[SE1](AppSensor_DetectionPoints#SE1 "wikilink")

</td>

<td>

[221](https://capec.mitre.org/data/definitions/221.html)

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

[SE3](AppSensor_DetectionPoints#SE3 "wikilink")

</td>

<td>

[261](https://capec.mitre.org/data/definitions/261.html)

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

[SE4](AppSensor_DetectionPoints#SE4 "wikilink")

</td>

<td>

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

[SE5](AppSensor_DetectionPoints#SE5 "wikilink")

</td>

<td>

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

[SE6](AppSensor_DetectionPoints#SE6 "wikilink")

</td>

<td>

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

[IE2](AppSensor_DetectionPoints#IE2 "wikilink")

</td>

<td>

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

[IE3](AppSensor_DetectionPoints#IE3 "wikilink")

</td>

<td>

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

[IE4](AppSensor_DetectionPoints#IE4 "wikilink")

</td>

<td>

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

[HT1](AppSensor_DetectionPoints#HT1 "wikilink")

</td>

<td>

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_3 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_5 "wikilink")

</div>