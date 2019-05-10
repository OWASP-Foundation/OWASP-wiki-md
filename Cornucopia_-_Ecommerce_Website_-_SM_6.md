![Cornucopia_-_Ecommerce_Website_SM_6.png](Cornucopia_-_Ecommerce_Website_SM_6.png
"Cornucopia_-_Ecommerce_Website_SM_6.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 6

### Description:

Gary can take over a user's session because there is a long or no
inactivity timeout, or a long or no overall session time limit, or the
same session can be used from more than one device/location.

### Technical Note:

There should be a session inactivity timeout that is as short as
possible, based on balancing risk and business functional requirements.
This could be role-dependent. Additionally disallow persistent logins
and enforce periodic session terminations (e.g. after 8 or 12 hours),
even when the session is active, especially for applications supporting
rich network connections or connecting to critical systems. Termination
times should support business requirements and the user should receive
sufficient notification to mitigate negative impacts.

NB: This card primarily relates to session timeout, but also includes
using the **same session identifier** in concurrent sessions. See [SM
3](Cornucopia_-_Ecommerce_Website_-_SM_3 "wikilink") for concurrent
sessions created by **authenticating more than once** in different
browsers/devices.

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

[64](OWASP_Secure_Coding_Practices_Checklist#64 "wikilink")

</td>

<td>

[3.3](OWASP_Application_Security_Verification_Standard#3.3 "wikilink")

</td>

<td>

[SE5](AppSensor_DetectionPoints#SE5 "wikilink")

</td>

<td>

[21](https://capec.mitre.org/data/definitions/21.html)

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

<tr>

<td>

[65](OWASP_Secure_Coding_Practices_Checklist#65 "wikilink")

</td>

<td>

[3.16](OWASP_Application_Security_Verification_Standard#3.16 "wikilink")

</td>

<td>

[SE6](AppSensor_DetectionPoints#SE6 "wikilink")

</td>

<td>

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_5 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_7 "wikilink")

</div>