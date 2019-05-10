![Cornucopia_-_Ecommerce_Website_VE_6.png](Cornucopia_-_Ecommerce_Website_VE_6.png
"Cornucopia_-_Ecommerce_Website_VE_6.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 6

### Description:

Jason can bypass the centralized validation routines since they are not
being used on all inputs.

### Technical Note:

Centralized input validation routines are a good programming practice,
but like other routines, developers need to understand how they work,
how to use them and any limitations. Such routines can be tested
independently of other code and not only provide assurance on the
quality of the input validation, but it make refactorization an easy
task and eliminate code duplicates and bad interpretations. Use of white
list validation is recommended where possible. Black lists are usually
good as a double-check complement, as they can trigger alerts for fake
positives. Common attacks to bad implementation (or lack) of validation
rutines are:

  - Buffer overflows.
  - Code injection.
  - Fuzzing.

If third party input validation libraries are used, it is important to
test each routine before its implementation.

NB: This card relates to bypass of **input data validation**. See [VE
5](Cornucopia_-_Ecommerce_Website_-_VE_5 "wikilink") for the similar
bypass of output encoding.

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

[5.6](OWASP_Application_Security_Verification_Standard#5.6 "wikilink")

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

[168](OWASP_Secure_Coding_Practices_Checklist#168 "wikilink")

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

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_5 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_7 "wikilink")

</div>