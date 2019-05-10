![Cornucopia_-_Ecommerce_Website_VE_J.png](Cornucopia_-_Ecommerce_Website_VE_J.png
"Cornucopia_-_Ecommerce_Website_VE_J.png") **Suit:** [Data Validation
and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")

**Card/Value:** J

### Description:

Dennis has control over input validation, output validation or output
encoding code or routines so they can be bypassed.

### Technical Note:

Validation and encoding are sometimes undertaken in client applications
or external sources that interact with the system. This is a bad
practice, as external sources are usually more vulnerable to attacks,
can be spoofed and are generally less accountable for malicious
behaviour. An attacker can try to bypass these routines using
non-controlled unexpected behaviour:

  - Modifying/deleting code.
  - Generating unexpected handcrafted requests.
  - Use an automated exploring tool (web crawler) to get information
    about the file structure and then try to access well known resource
    locations.
  - Abusing an ill-defined zone of trust.
  - Modifying data between the client application and the server (e.g.
    Trojan, modification in transit)
  - XSS.

In general, all validation and encoding routines should be on the
server-side using robust, tested and protected routines.

NB: Unlike other cards in this suit, this VE J relates to an attacker
being able to change the executing code. This may be due to inadequate
source code control, deployment controls or server protection, but is
more often a standard feature of client-side code.

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

[1](OWASP_Secure_Coding_Practices_Checklist#1 "wikilink")

</td>

<td>

[5.5](OWASP_Application_Security_Verification_Standard#5.5 "wikilink")

</td>

<td>

[RE3](AppSensor_DetectionPoints#RE3 "wikilink")

</td>

<td>

[56](https://capec.mitre.org/data/definitions/56.html)

</td>

<td>

[2](SAFECode_Practical_Security_Stories#2 "wikilink")

</td>

</tr>

<tr>

<td>

[17](OWASP_Secure_Coding_Practices_Checklist#17 "wikilink")

</td>

<td>

</td>

<td>

[RE4](AppSensor_DetectionPoints#RE4 "wikilink")

</td>

<td>

[87](https://capec.mitre.org/data/definitions/87.html)

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

[207](https://capec.mitre.org/data/definitions/207.html)

</td>

<td>

</td>

</tr>

</table>

<div style="padding:5px;background:LightGray;color:White;font-weight:bold;">

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_VE_10 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Data
Validation and Encoding](Cornucopia_-_Ecommerce_Website_-_VE "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_VE_Q "wikilink")

</div>