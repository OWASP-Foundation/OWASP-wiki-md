![Cornucopia_-_Ecommerce_Website_SM_9.png](Cornucopia_-_Ecommerce_Website_SM_9.png
"Cornucopia_-_Ecommerce_Website_SM_9.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 9

### Description:

Ivan can steal session identifiers because they are sent over insecure
channels, or are logged, or are revealed in error messages, or are
included in URLs, or are accessible unnecessarily by code which the
attacker can influence or alter.

### Technical Note:

Protect session identifiers as if they are account credentials. For HTTP
cookies:

  - Set cookies with the HttpOnly attribute, unless you specifically
    require client-side scripts within your application to read or set a
    cookie's value.
  - Set the 'secure' attribute for cookies transmitted over an TLS
    connection.
  - Consider making the whole ecommerce website 'SSL-only', adding the
    HTTP Strict Transport Security (HSTS) header and adding the domain
    to web browser pre-load lists.

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

[69](OWASP_Secure_Coding_Practices_Checklist#69 "wikilink")

</td>

<td>

[3.6](OWASP_Application_Security_Verification_Standard#3.6 "wikilink")

</td>

<td>

[SE4](AppSensor_DetectionPoints#SE4 "wikilink")

</td>

<td>

[31](https://capec.mitre.org/data/definitions/31.html)

</td>

<td>

[28](SAFECode_Practical_Security_Stories#28 "wikilink")

</td>

</tr>

<tr>

<td>

[75](OWASP_Secure_Coding_Practices_Checklist#75 "wikilink")

</td>

<td>

[3.14](OWASP_Application_Security_Verification_Standard#3.14 "wikilink")

</td>

<td>

[SE5](AppSensor_DetectionPoints#SE5 "wikilink")

</td>

<td>

[60](https://capec.mitre.org/data/definitions/60.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[76](OWASP_Secure_Coding_Practices_Checklist#76 "wikilink")

</td>

<td>

[3.15](OWASP_Application_Security_Verification_Standard#3.15 "wikilink")

</td>

<td>

[SE6](AppSensor_DetectionPoints#SE6 "wikilink")

</td>

<td>

</td>

<td>

</td>

</tr>

<tr>

<td>

[119](OWASP_Secure_Coding_Practices_Checklist#119 "wikilink")

</td>

<td>

[8.10](OWASP_Application_Security_Verification_Standard#8.10 "wikilink")

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

[138](OWASP_Secure_Coding_Practices_Checklist#138 "wikilink")

</td>

<td>

[10.3](OWASP_Application_Security_Verification_Standard#10.3 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_8 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_10 "wikilink")

</div>