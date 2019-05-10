![Cornucopia_-_Ecommerce_Website_VE_9.png](Cornucopia_-_Ecommerce_Website_VE_9.png
"Cornucopia_-_Ecommerce_Website_VE_9.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 9

### Description:

Shamun can bypass input validation or output validation checks because
validation failures are not rejected and/or sanitized.

### Technical Note:

Extensive checks and validations can be made of inputs and outputs, but
proper actions following the results is what provides security. Data
sanitization is a good approach for outputs, as this data is already
accepted by the system. Failing input validation always needs to result
in rejection. It is also useful to log (associated with the user's
identity if possible) and flag these as probably malicious activity for
further analysis, or as input for application intrusion detection
systems.

NB: Unlike [other cards in this
suit](Cornucopia_-_Ecommerce_Website_-_VE "wikilink"), VE 9 assumes that
input and output validation checks are in place, however they do not
correctly respond to incorrect input.

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

[6](OWASP_Secure_Coding_Practices_Checklist#6 "wikilink")

</td>

<td>

[5.3](OWASP_Application_Security_Verification_Standard#5.3 "wikilink")

</td>

<td>

[IE2](AppSensor_DetectionPoints#IE2 "wikilink")

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

[21](OWASP_Secure_Coding_Practices_Checklist#21 "wikilink")

</td>

<td>

</td>

<td>

[IE3](AppSensor_DetectionPoints#IE3 "wikilink")

</td>

<td>

</td>

<td>

[16](SAFECode_Practical_Security_Stories#16 "wikilink")

</td>

</tr>

<tr>

<td>

[22](OWASP_Secure_Coding_Practices_Checklist#22 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

[24](SAFECode_Practical_Security_Stories#24 "wikilink")

</td>

</tr>

<tr>

<td>

[168](OWASP_Secure_Coding_Practices_Checklist#168 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_8 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_10 "wikilink")

</div>