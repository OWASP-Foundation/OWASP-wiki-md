![Cornucopia_-_Ecommerce_Website_SM_10.png](Cornucopia_-_Ecommerce_Website_SM_10.png
"Cornucopia_-_Ecommerce_Website_SM_10.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 10

### Description:

Marce can forge requests because per-session, or per-request for more
critical actions, strong random tokens (i.e. anti-CSRF tokens) or
similar are not being used for actions that change state.

### Technical Note:

Consider supplementing standard session management with:

  - Per-session strong random tokens or parameters.
  - Per-request, as opposed to per-session, strong random tokens or
    parameters.

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

[73](OWASP_Secure_Coding_Practices_Checklist#73 "wikilink")

</td>

<td>

[4.16](OWASP_Application_Security_Verification_Standard#4.16 "wikilink")

</td>

<td>

[IE4](AppSensor_DetectionPoints#IE4 "wikilink")

</td>

<td>

[62](https://capec.mitre.org/data/definitions/62.html)

</td>

<td>

[18](SAFECode_Practical_Security_Stories#18 "wikilink")

</td>

</tr>

<tr>

<td>

[74](OWASP_Secure_Coding_Practices_Checklist#74 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[111](https://capec.mitre.org/data/definitions/111.html)

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_9 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_J "wikilink")

</div>