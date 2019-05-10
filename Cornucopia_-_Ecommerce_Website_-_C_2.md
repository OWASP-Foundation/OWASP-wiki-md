![Cornucopia_-_Ecommerce_Website_C_2.png](Cornucopia_-_Ecommerce_Website_C_2.png
"Cornucopia_-_Ecommerce_Website_C_2.png") **Suit:**
[Cornucopia](Cornucopia_-_Ecommerce_Website_-_C "wikilink")

**Card/Value:** 2

### Description:

Lee can bypass application controls because dangerous/risky programming
language functions have been used instead of safer alternatives, or
there are type conversion errors, or because the application is
unreliable when an external resource is unavailable, or there are race
conditions, or there are resource initialization or allocation issues,
or overflows can occur.

### Technical Note:

This card is framework/language-specific. Examples include:

  - Beware of un-trusted data.
  - Check buffer sizes.
  - Do not rely on garbage collection.
  - Use non-executable stacks when available.
  - Avoid the use of known vulnerable functions.
  - Properly free allocated memory.
  - Use checksums or hashes to verify the integrity of interpreted code,
    libraries, executables, and configuration files.
  - Utilize locking to prevent multiple simultaneous requests.
  - Use a synchronization mechanism to prevent race conditions.
  - Protect shared variables and resources from inappropriate concurrent
    access.
  - Explicitly initialize all your variables and other data store.
  - In cases where the application must run with elevated privileges,
    raise privileges as late as possible, and drop them as soon as
    possible.
  - Make no assumptions about availability of other resources, and
    handle exceptions.

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

[194](OWASP_Secure_Coding_Practices_Checklist#194 "wikilink")

</td>

<td>

[5.1](OWASP_Application_Security_Verification_Standard#5.1 "wikilink")

</td>

<td>

\-

</td>

<td>

[25](https://capec.mitre.org/data/definitions/25.html)

</td>

<td>

[3](SAFECode_Practical_Security_Stories#3 "wikilink")

</td>

</tr>

<tr>

<td>

[195](OWASP_Secure_Coding_Practices_Checklist#195 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[26](https://capec.mitre.org/data/definitions/26.html)

</td>

<td>

[5](SAFECode_Practical_Security_Stories#5 "wikilink")

</td>

</tr>

<tr>

<td>

[196](OWASP_Secure_Coding_Practices_Checklist#196 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[29](https://capec.mitre.org/data/definitions/29.html)

</td>

<td>

[6](SAFECode_Practical_Security_Stories#6 "wikilink")

</td>

</tr>

<tr>

<td>

[197](OWASP_Secure_Coding_Practices_Checklist#197 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[96](https://capec.mitre.org/data/definitions/96.html)

</td>

<td>

[7](SAFECode_Practical_Security_Stories#7 "wikilink")

</td>

</tr>

<tr>

<td>

[198](OWASP_Secure_Coding_Practices_Checklist#198 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[123](https://capec.mitre.org/data/definitions/123.html)

</td>

<td>

[9](SAFECode_Practical_Security_Stories#9 "wikilink")

</td>

</tr>

<tr>

<td>

[199](OWASP_Secure_Coding_Practices_Checklist#199 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[124](https://capec.mitre.org/data/definitions/124.html)

</td>

<td>

[22](SAFECode_Practical_Security_Stories#22 "wikilink")

</td>

</tr>

<tr>

<td>

[200](OWASP_Secure_Coding_Practices_Checklist#200 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[128](https://capec.mitre.org/data/definitions/128.html)

</td>

<td>

[25](SAFECode_Practical_Security_Stories#25 "wikilink")

</td>

</tr>

<tr>

<td>

[201](OWASP_Secure_Coding_Practices_Checklist#201 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[129](https://capec.mitre.org/data/definitions/129.html)

</td>

<td>

[26](SAFECode_Practical_Security_Stories#26 "wikilink")

</td>

</tr>

<tr>

<td>

[202](OWASP_Secure_Coding_Practices_Checklist#202 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[264](https://capec.mitre.org/data/definitions/264.html)

</td>

<td>

[34](SAFECode_Practical_Security_Stories#34 "wikilink")

</td>

</tr>

<tr>

<td>

[205](OWASP_Secure_Coding_Practices_Checklist#205 "wikilink")

</td>

<td>

</td>

<td>

</td>

<td>

[265](https://capec.mitre.org/data/definitions/265.html)

</td>

<td>

</td>

</tr>

<tr>

<td>

[206](OWASP_Secure_Coding_Practices_Checklist#206 "wikilink")

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

[207](OWASP_Secure_Coding_Practices_Checklist#207 "wikilink")

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

[208](OWASP_Secure_Coding_Practices_Checklist#208 "wikilink")

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

[209](OWASP_Secure_Coding_Practices_Checklist#209 "wikilink")

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

[« Previous Card](Cornucopia_-_Ecommerce_Website_-_CR_A "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span>
[Cornucopia](Cornucopia_-_Ecommerce_Website_-_C "wikilink")
<span style="padding-left:10px;padding-right:10px;"> |</span> [Next Card
»](Cornucopia_-_Ecommerce_Website_-_C_3 "wikilink")

</div>