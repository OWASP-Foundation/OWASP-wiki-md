![Cornucopia_-_Ecommerce_Website_AT_4.png](Cornucopia_-_Ecommerce_Website_AT_4.png
"Cornucopia_-_Ecommerce_Website_AT_4.png") **Suit:**
[Authentication](Cornucopia_-_Ecommerce_Website_-_AT "wikilink")

**Card/Value:** 4

### Description:

Sebastien can easily identify user names or can enumerate them.

### Technical Note:

This attack is often the result of one or more of the following:

  - User names (IDs, account names) may be guessable, published
    elsewhere, or are simply email addresses
  - Authentication and related mechanisms may indicate whether a
    username is valid or not (registration, password reset/recovery,
    username recovery, change password, change email address)
  - Missing authentication failure detection
  - Missing monitoring to identify attacks against multiple user
    accounts, utilizing the same password

Additionally another web or non-web application (e.g. mobile app,
telephone service) that utilises the same credentials has one or more of
the above problems.

NB: This card relates to **user names**. See [AT
7](Cornucopia_-_Ecommerce_Website_-_AT_7 "wikilink") for the similar
password cracking (brute forcing, dictionary attacks, guessing,
credential stuffing, credential cracking).

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

[33](OWASP_Secure_Coding_Practices_Checklist#33 "wikilink")

</td>

<td>

[2.18](OWASP_Application_Security_Verification_Standard#2.18 "wikilink")

</td>

<td>

[AE1](AppSensor_DetectionPoints#AE1 "wikilink")

</td>

<td>

[383](https://capec.mitre.org/data/definitions/383.html)

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

<tr>

<td>

[53](OWASP_Secure_Coding_Practices_Checklist#53 "wikilink")

</td>

<td>

[2.19](OWASP_Application_Security_Verification_Standard#2.19 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_AT_3 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span>
[Authentication](Cornucopia_-_Ecommerce_Website_-_AT "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_AT_5 "wikilink")

</div>