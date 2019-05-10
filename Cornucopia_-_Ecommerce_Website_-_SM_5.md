![Cornucopia_-_Ecommerce_Website_SM_5.png](Cornucopia_-_Ecommerce_Website_SM_5.png
"Cornucopia_-_Ecommerce_Website_SM_5.png") **Suit:** [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")

**Card/Value:** 5

### Description:

John can predict or guess session identifiers because they are not
changed when the user's role alters (e.g. pre and post authentication)
and when switching between non-encrypted and encrypted communications,
or are not sufficiently long and random, or are not changed
periodically.

### Technical Note:

Ensure the following occur:

  - Ensure sufficiently long and random session identifiers are used
  - Generate a new session identifier:
      - If a session was established before login, and successful login
        has occurred
      - When changing from HTTP to HTTPS
      - When re-authenticating
      - Periodically otherwise.

See [SM 7](Cornucopia_-_Ecommerce_Website_-_SM_7 "wikilink") for session
termination on logging out.

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

[60](OWASP_Secure_Coding_Practices_Checklist#60 "wikilink")

</td>

<td>

[3.2](OWASP_Application_Security_Verification_Standard#3.2 "wikilink")

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

[62](OWASP_Secure_Coding_Practices_Checklist#62 "wikilink")

</td>

<td>

[3.7](OWASP_Application_Security_Verification_Standard#3.7 "wikilink")

</td>

<td>

[SE5](AppSensor_DetectionPoints#SE5 "wikilink")

</td>

<td>

</td>

<td>

</td>

</tr>

<tr>

<td>

[66](OWASP_Secure_Coding_Practices_Checklist#66 "wikilink")

</td>

<td>

[3.8](OWASP_Application_Security_Verification_Standard#3.8 "wikilink")

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

[67](OWASP_Secure_Coding_Practices_Checklist#67 "wikilink")

</td>

<td>

[3.11](OWASP_Application_Security_Verification_Standard#3.11 "wikilink")

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

[71](OWASP_Secure_Coding_Practices_Checklist#71 "wikilink")

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

<tr>

<td>

[72](OWASP_Secure_Coding_Practices_Checklist#72 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_SM_4 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Session
management](Cornucopia_-_Ecommerce_Website_-_SM "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_SM_6 "wikilink")

</div>