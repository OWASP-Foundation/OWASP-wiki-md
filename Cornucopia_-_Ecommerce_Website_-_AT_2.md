![Cornucopia_-_Ecommerce_Website_AT_2.png](Cornucopia_-_Ecommerce_Website_AT_2.png
"Cornucopia_-_Ecommerce_Website_AT_2.png") **Suit:**
[Authentication](Cornucopia_-_Ecommerce_Website_-_AT "wikilink")

**Card/Value:** 2

### Description:

James can undertake authentication functions without the real user ever
being aware this has occurred (e.g. attempt to log in, log in with
stolen credentials, reset the password).

### Technical Note:

Security event logs should record key actions and the results of
important security checks (in some cases successes as well as failures).
If users have access to this information, they may well be able to help
detect attempted or actual account/data breaches as they know more of
the usage context. This information might be sent as alert messages
(e.g. SMS, email, post), by making event data available as an API, or
might appear in the web application as a short summarised activity log
available once authenticated such as on the logged-in welcome page, or
during the process of logging-off, and also within a user's account
details to be accessed on demand. It maybe useful to include non web
application events (e.g. mobile app password reset, a major event
initiated by letter or the telephone call to the contact centre).

NB: The key concept here is notification of events to users.

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

[47](OWASP_Secure_Coding_Practices_Checklist#47 "wikilink")

</td>

<td>

[2.12](OWASP_Application_Security_Verification_Standard#2.12 "wikilink")

</td>

<td>

[UT1](AppSensor_DetectionPoints#UT1 "wikilink")

</td>

<td>

\-

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

<tr>

<td>

[52](OWASP_Secure_Coding_Practices_Checklist#52 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_A "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span>
[Authentication](Cornucopia_-_Ecommerce_Website_-_AT "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_AT_3 "wikilink")

</div>