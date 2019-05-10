  - What's new?
    OWASP has come a long way since the last top was released in January
    2003. This update incorporates all the discussion and up to date
    views, opinions and debate in the OWASP community over the past 12
    months. Overall, there have been minor improvements to all parts of
    the Top Ten, and only a few major changes:

<!-- end list -->

  - WAS-XML Alignment
    One of the new projects initiated in 2003 is the Web Application
    Security Technical Committee (WAS TC) at OASIS. The purpose of the
    WAS TC is to produce a classification scheme for web security
    vulnerabilities, a model to provide guidance for initial threat,
    impact and therefore risk ratings, and an XML schema to describe web
    security conditions that can be used by both assessment and
    protection tools. The OWASP Top Ten project has used the WAS TC as a
    reference for reprofiling the Top Ten to provide a standardized
    approach to the classification of web application security
    vulnerabilities. The WAS Thesaurus defines a standard language for
    discussing web application security, and we adopt that vocabulary
    here.

<!-- end list -->

  - Addition of Denial of Service
    The only top level category that changed was the addition of the A9
    Denial of Service category to the list. Our research has shown that
    a broad array of organizations are susceptible to this type of
    attack. Based on the likelihood of a denial of service attack and
    the consequences if the attack succeeds, we have determined that it
    warrants inclusion in the Top Ten. To accommodate this new entry, we
    have combined last year’s A9 Remote Administration Flaws into the A2
    Broken Access Control category as it is a special case of that
    category. We believe this is appropriate, as the types of flaws in
    A2 are typically the same as those in A9 and require the same types
    of remediation.

The table below highlights the relationship between the new Top Ten,
last year’s Top Ten, and the WAS TC Thesaurus.

<table>
<tbody>
<tr class="odd">
<td><div align="center">
<p><strong>New Top Ten 2004</strong></p>
</div></td>
<td><div align="center">
<p><strong>Top Ten 2003</strong></p>
</div></td>
<td><div align="center">
<p><strong>New WAS Thesaurus</strong></p>
</div></td>
</tr>
<tr class="even">
<td><p>A1 Unvalidated Input</p></td>
<td><p>A1 Unvalidated Parameters</p></td>
<td><p>Input Validation</p></td>
</tr>
<tr class="odd">
<td><p>A2 Broken Access Control</p></td>
<td><p>A2 Broken Access Control<br />
(A9 Remote Administration Flaws)</p></td>
<td><p>Access Control</p></td>
</tr>
<tr class="even">
<td><p>A3 Broken Authentication and Session Management</p></td>
<td><p>A3 Broken Account and Session Management</p></td>
<td><p>Authentication and Session Management</p></td>
</tr>
<tr class="odd">
<td><p>A4 Cross Site Scripting (XSS) Flaws</p></td>
<td><p>A4 Cross Site Scripting (XSS) Flaws</p></td>
<td><p>Input Validation-&gt;Cross site scripting</p></td>
</tr>
<tr class="even">
<td><p>A5 Buffer Overflows</p></td>
<td><p>A5 Buffer Overflows</p></td>
<td><p>Buffer Overflows</p></td>
</tr>
<tr class="odd">
<td><p>A6 Injection Flaws</p></td>
<td><p>A6 Command Injection Flaws</p></td>
<td><p>Input Validation-&gt;Injection</p></td>
</tr>
<tr class="even">
<td><p>A7 Improper Error Handling</p></td>
<td><p>A7 Error Handling Problems</p></td>
<td><p>Error Handling</p></td>
</tr>
<tr class="odd">
<td><p>A8 Insecure Storage</p></td>
<td><p>A8 Insecure Use of Cryptography</p></td>
<td><p>Data Protection</p></td>
</tr>
<tr class="even">
<td><p>A9 Denial of Service</p></td>
<td><p>N/A</p></td>
<td><p>Availability</p></td>
</tr>
<tr class="odd">
<td><p>A10 Insecure Configuration Management</p></td>
<td><p>A10 Web and Application Server Misconfiguration</p></td>
<td><p>Application Configuration Management<br />
Infrastructure Configuration Management</p></td>
</tr>
</tbody>
</table>

__NOEDITSECTION__

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")