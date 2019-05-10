![Cornucopia_-_Ecommerce_Website_VE_5.png](Cornucopia_-_Ecommerce_Website_VE_5.png
"Cornucopia_-_Ecommerce_Website_VE_5.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 5

### Description:

Jee can bypass the centralized encoding routines since they are not
being used everywhere, or the wrong encodings are being used.

### Technical Note:

Centralized output encoding routines are a good programming practice,
but developers need to understand how they work, how to use them and any
limitations. Such routines can be tested independently of other code and
not only provide assurance on the quality of the validation, but it
makes refactorization an easy task and it eliminates code duplicates and
bad interpretations. Ouput encodings are a must when handling data from
un-trusted sources. It should also be a mandatory security check when
outputting data to queries for SQL, XML, and LDAP and in every case when
hazardous special characters must be allowed as input (such as \< \> " '
% ( ) & + \\ \\' \\"). Some common attacks of bad implementation (or
lack) of output encoding routines are:

  - Cross Site Scripting (XSS).
  - Code injection.
  - Fuzzing.

If third party output encoding libraries are used, it is important to
test each routine before its implementation.

NB: This card relates to bypass of **output encoding**. See [VE
6](Cornucopia_-_Ecommerce_Website_-_VE_6 "wikilink") for the similar
bypass of input data validation.

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

[3](OWASP_Secure_Coding_Practices_Checklist#3 "wikilink")

</td>

<td>

[5.19](OWASP_Application_Security_Verification_Standard#5.19 "wikilink")

</td>

<td>

</td>

<td>

[28](https://capec.mitre.org/data/definitions/28.html)

</td>

<td>

[2](SAFECode_Practical_Security_Stories#2 "wikilink")

</td>

</tr>

<tr>

<td>

[15](OWASP_Secure_Coding_Practices_Checklist#15 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[31](https://capec.mitre.org/data/definitions/31.html)

</td>

<td>

[17](SAFECode_Practical_Security_Stories#17 "wikilink")

</td>

</tr>

<tr>

<td>

[18](OWASP_Secure_Coding_Practices_Checklist#18 "wikilink")

</td>

<td>

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

[19](OWASP_Secure_Coding_Practices_Checklist#19 "wikilink")

</td>

<td>

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

[20](OWASP_Secure_Coding_Practices_Checklist#20 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[468](https://capec.mitre.org/data/definitions/468.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[21](OWASP_Secure_Coding_Practices_Checklist#21 "wikilink")

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

[22](OWASP_Secure_Coding_Practices_Checklist#22 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_4 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_6 "wikilink")

</div>