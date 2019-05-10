![Cornucopia_-_Ecommerce_Website_SM_3.png](Cornucopia_-_Ecommerce_Website_SM_3.png
"Cornucopia_-_Ecommerce_Website_SM_3.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 3

### Description:

Ryan can use a single account in parallel since concurrent sessions are
allowed.

### Technical Note:

In some ecommerce applications it may be desirable to allow customers to
be logged in using multiple browsers/devices. However that would be
unusual for administrative users, or users of more sensitive data. Even
if concurrent sessions are allowed. consider what should occur in other
sessions when a user changes their password, or changes their delivery
address, or logs out, or times out, or authentication failure occurs.

NB: This card relates to concurrent sessions created by **authenticating
more than once** in different browsers/devices. See [SM
6](Cornucopia_-_Ecommerce_Website_-_SM_6 "wikilink") for using the
**same session identifier** in concurrent sessions.

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

[68](OWASP_Secure_Coding_Practices_Checklist#68 "wikilink")

</td>

<td>

[3.16](OWASP_Application_Security_Verification_Standard#3.16 "wikilink")

</td>

<td>

\-

</td>

<td>

\-

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_2 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_4 "wikilink")

</div>