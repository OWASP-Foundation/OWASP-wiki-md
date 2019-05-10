![Cornucopia_-_Ecommerce_Website_AZ_4.png](Cornucopia_-_Ecommerce_Website_AZ_4.png
"Cornucopia_-_Ecommerce_Website_AZ_4.png") **Suit:**
[Authorization](Cornucopia_-_Ecommerce_Website_-_AZ "wikilink")

**Card/Value:** 4

### Description:

Kelly can bypass authorization controls because they do not fail
securely (i.e. they default to allowing access).

### Technical Note:

Once an authorization failure is detected, access needs to be blocked.
It is also useful to log (associated with the user's identity if
possible) and flag these as possibly malicious activity for further
analysis, or as input for application intrusion detection systems.

NB: the key concept for this card is allowing access, even though
authorization checks were undertaken and detected a failure. See [AT
8](Cornucopia_-_Ecommerce_Website_-_AT_8 "wikilink") for the similar
authentication failure.

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

[79](OWASP_Secure_Coding_Practices_Checklist#79 "wikilink")

</td>

<td>

[4.8](OWASP_Application_Security_Verification_Standard#4.8 "wikilink")

</td>

<td>

\-

</td>

<td>

[122](https://capec.mitre.org/data/definitions/122.html)

</td>

<td>

[8](SAFECode_Practical_Security_Stories#8 "wikilink")

</td>

</tr>

<tr>

<td>

[80](OWASP_Secure_Coding_Practices_Checklist#80 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

</td>

<td>

[10](SAFECode_Practical_Security_Stories#10 "wikilink")

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

[11](SAFECode_Practical_Security_Stories#11 "wikilink")

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_AZ_3 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span>
[Authorization](Cornucopia_-_Ecommerce_Website_-_AZ "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_AZ_5 "wikilink")

</div>