![Cornucopia_-_Ecommerce_Website_SM_8.png](Cornucopia_-_Ecommerce_Website_SM_8.png
"Cornucopia_-_Ecommerce_Website_SM_8.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 8

### Description:

Matt can abuse long sessions because the application does not require
periodic re-authentication to check if privileges have changed.

### Technical Note:

A user's privileges may change during a session. If this information is
also stored in session data, it will not reflect the changes. Consider
forcing re-authentication.

See Authentication [AT
9](Cornucopia_-_Ecommerce_Website_-_AT_9 "wikilink") for other
re-authentication requirements.

### References:

<table class="wikitable" style="text-align:center;">

<tr class="tableizer-firstrow">

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

[96](OWASP_Secure_Coding_Practices_Checklist#96 "wikilink")

</td>

<td>

\-

</td>

<td>

\-

</td>

<td>

[21](https://capec.mitre.org/data/definitions/21.html)

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_7 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_9 "wikilink")

</div>