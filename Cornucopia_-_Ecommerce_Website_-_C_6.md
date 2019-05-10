![Cornucopia_-_Ecommerce_Website_C_6.png](Cornucopia_-_Ecommerce_Website_C_6.png
"Cornucopia_-_Ecommerce_Website_C_6.png") **Suit:**
[Cornucopia](Cornucopia_-_Ecommerce_Website_-_C "wikilink")

**Card/Value:** 6

### Description:

Aaron can bypass controls because error/exception handling is missing,
or is implemented inconsistently or partially, or does not deny access
by default (i.e. errors should terminate access/execution), or relies on
handling by some other service or system.

### Technical Note:

Ensure all forms of error are handled robustly and consistently (e.g.
web server, application server, database server, JavaScript, other
interpreters). This encompasses:

  - Implement generic error messages and use custom error pages.
  - The application should handle application errors and not rely on the
    server configuration.
  - Properly free allocated memory when error conditions occur.
  - Error handling logic associated with security controls should deny
    access by default.
  - When exceptions occur, fail securely.

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

[109](OWASP_Secure_Coding_Practices_Checklist#109 "wikilink")

</td>

<td>

[8.4](OWASP_Application_Security_Verification_Standard#8.4 "wikilink")

</td>

<td>

\-

</td>

<td>

[54](https://capec.mitre.org/data/definitions/54.html)

</td>

<td>

[4](SAFECode_Practical_Security_Stories#4 "wikilink")

</td>

</tr>

<tr>

<td>

[110](OWASP_Secure_Coding_Practices_Checklist#110 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[98](https://capec.mitre.org/data/definitions/98.html)

</td>

<td>

[11](SAFECode_Practical_Security_Stories#11 "wikilink")

</td>

</tr>

<tr>

<td>

[111](OWASP_Secure_Coding_Practices_Checklist#111 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[164](https://capec.mitre.org/data/definitions/164.html)

</td>

<td>

[23](SAFECode_Practical_Security_Stories#23 "wikilink")

</td>

</tr>

<tr>

<td>

[112](OWASP_Secure_Coding_Practices_Checklist#112 "wikilink")

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

[155](OWASP_Secure_Coding_Practices_Checklist#155 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_C_5 "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span>
[Cornucopia](Cornucopia_-_Ecommerce_Website_-_C "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_C_7 "wikilink")

</div>