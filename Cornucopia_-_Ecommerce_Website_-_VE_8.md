![Cornucopia_-_Ecommerce_Website_VE_8.png](Cornucopia_-_Ecommerce_Website_VE_8.png
"Cornucopia_-_Ecommerce_Website_VE_8.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** 8

### Description:

Sarah can bypass the centralized sanitization routines since they are
not being used comprehensively.

### Technical Note:

Sanitization may be used to strip some inputs or outputs of certain
unwanted characters. It is not a substitute for data validation and
encoding, but may be used in combination (e.g. to remove
leading/trailing whitespace from keyboard input). If sanitization is
part of the validation and encoding processes, ensure that no relevant
input/output is excluded, or can be bypassed by submitting data through
a different input stream (e.g. GET instead of POST) or using a different
app (e.g. mobile vs. desktop).

NB: The key concept for this card is use of sanitization, and whether
such routines are comprehensively applied.

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

[169](OWASP_Secure_Coding_Practices_Checklist#169 "wikilink")

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

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_7 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_9 "wikilink")

</div>