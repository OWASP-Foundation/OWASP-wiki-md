![Cornucopia_-_Ecommerce_Website_VE_7.png](Cornucopia_-_Ecommerce_Website_VE_7.png
"Cornucopia_-_Ecommerce_Website_VE_7.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 7

### Description:

Jan can craft special payloads to foil input validation because the
character set is not specified/enforced, or the data is encoded multiple
times, or the data is not fully converted into the same format the
application uses (e.g. canonicalization) before being validated, or
variables are not strongly typed.

### Technical Note:

Without knowing the character encoding accurately, data validation
routines could be inadequate. A web application firewall, a web server,
an application server, a database server, and other interpreters could
each be susceptible, and susceptible in different ways, to malicious
character encoding issues.

Common protection techniques include:

  - Specify proper character sets, such as UTF-8, for all sources of
    input.
  - Encode data to a common character set before validating
    (Canonicalize).
  - Use system components that support UTF-8 extended character sets and
    validate data after UTF-8 decoding is completed.

NB: The key concept for this card is encoding.

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

[4](OWASP_Secure_Coding_Practices_Checklist#4 "wikilink")

</td>

<td>

[5.4](OWASP_Application_Security_Verification_Standard#5.4 "wikilink")

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

[5](OWASP_Secure_Coding_Practices_Checklist#5 "wikilink")

</td>

<td>

[5.8](OWASP_Application_Security_Verification_Standard#5.8 "wikilink")

</td>

<td>

[IE3](AppSensor_DetectionPoints#IE3 "wikilink")

</td>

<td>

[153](https://capec.mitre.org/data/definitions/153.html)

</td>

<td>

[16](SAFECode_Practical_Security_Stories#16 "wikilink")

</td>

</tr>

<tr>

<td>

[7](OWASP_Secure_Coding_Practices_Checklist#7 "wikilink")

</td>

<td>

[10.9](OWASP_Application_Security_Verification_Standard#10.9 "wikilink")

</td>

<td>

[EE1](AppSensor_DetectionPoints#EE1 "wikilink")

</td>

<td>

[165](https://capec.mitre.org/data/definitions/165.html)

</td>

<td>

[24](SAFECode_Practical_Security_Stories#24 "wikilink")

</td>

</tr>

<tr>

<td>

[150](OWASP_Secure_Coding_Practices_Checklist#150 "wikilink")

</td>

<td>

</td>

<td>

[EE2](AppSensor_DetectionPoints#EE2 "wikilink")

</td>

<td>

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_6 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_8 "wikilink")

</div>