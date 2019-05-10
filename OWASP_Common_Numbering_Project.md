<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

#### Home

<table width="100%" valign="top">

<tr>

<th width="100%">

</th>

<th>

</th>

</tr>

<tr valign="top">

<td>

**Common OWASP Numbering**

An exciting development, a new numbering scheme that will be common
across various OWASP Guides and References is being developed. This
numbering scheme is loosely based on the OWASP ASVS section and detailed
requirements numbering. The OWASP ASVS, Guide, and Reference project
leads and contributors plan to work together to develop a numbering
scheme that facilitates easier mapping between various OWASP Guides and
References, and that would allow for a period of transition as the
Guides and References are updated to reflect the new numbering scheme.
This project will provide a centralized clearinghouse for mapping
information. For more information on this project, or if you wish to
contribute, please contact [Dave
Wichers](mailto:dave.wichers@owasp.org).

This common numbering scheme will be of requirements. A mapping of
vulnerabilities to this requirements list will most likely be developed
after the common requirements list is created. This common numbering
scheme is intended to be independent of any particular OWASP project and
is not intended to dictate how those projects are developed and
organized. Its intent is to be a resource to facilitate cross
referencing between related topics and to encourage, but not require,
projects like the OWASP Guides to adopt a similar structure. But that
decision is up to the respective project leads.

</td>

</tr>

</table>

#### OWASP Common Requirements Numbering Scheme DRAFT

<table width="100%" valign="top">

<tr>

<th width="50%">

</th>

<th>

</th>

</tr>

<tr valign="top">

<td>

**Proposed OWASP Common Requirements Numbering Scheme Format:**

`OCR-AUTHN-01`
`OCR-AUTHN-02`
`OCR-AUTHN-02.01`
`OCR-AUTHN-03`
`OCR-INPVAL-01`
`OCR-INPVAL-02 `

Common Requirements Numbering Scheme Proposed Requirement Areas:

  - OCR-AUTHN: Authentication
  - OCR-SESS: Session Management
  - OCR-INPVAL: Input Validation
  - OCR-OUTENC: Output Encoding
  - OCR-AUTHZ: Functional and Data Layer Access Control
  - OCR-BUS: Business Logic
  - OCR-DATAP: Sensitive Data Protection
  - OCR-CRYPST: Cryptographic Storage
  - OCR-COMMS: Communication Security
  - OCR-ERROR: Error Handling
  - OCR-LOG: Logging
  - OCR-DBASE: Secure Database Usage
  - OCR-FILE: Secure File Access
  - OCR-MEM: Memory Management
  - OCR-GEN: General Coding Practices
  - OCR-CONFIG: Secure System Configuration
  - OCR-INTEG: Integrity
  - OCR-AVAIL: Availability

</td>

<td>

**Reference**

  - 1st Element - Document code (OCR=OWASP Common Requirements Number,
    ODG=OWASP Development Guide, OTG=OWASP Testing Guide, OCG=OWASP Code
    Review Guide, others reserved)
  - 2nd Element - Requirement Area (major)
  - 3rd Element - Detailed Requirement Identifier (minor with up to one
    sublevel (e.g., .01, .02)
  - 4th Element (Optional: DEPRECATED, or \# for iterations, or legacy
    identifiers)

</td>

</tr>

</table>

#### OWASP Common Requirements - DRAFT

The following is the first section we have developed of common
requirements. It is the section on Authentication (OCR-AUTHN). This is
draft, and your feedback is very welcome. Please provide any feedback to
[Dave Wichers](mailto:dave.wichers@owasp.org).

<table>
<tbody>
<tr class="odd">
<td><center>
<p><strong>OWASP Common Number</strong></p>
</center></td>
<td><center>
<p><strong>Common Requirement</strong></p>
</center></td>
</tr>
<tr class="even">
<td><p>align="center" colspan="2"</p></td>
<td><p><strong>Authentication Requirements</strong></p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-01</p></td>
<td><p>All authentication controls operate on a trusted system (e.g., The server).</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-02</p></td>
<td><p>Authentication is required for all pages and resources, except those specifically intended to be public.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-03</p></td>
<td><p>The application utilizes standardized, tested, and centralized authentication services.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-04</p></td>
<td><p>Authentication services utilize a centralized authentication store.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-05</p></td>
<td><p>All authentication controls fail securely.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-06</p></td>
<td><p>System configurable password strength requirements are enforced. This includes both minimum length and minimum complexity rules.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-07</p></td>
<td><p>Disallow account passwords to match any of the last N passwords for that account, where N is a system configurable value. This is done to discourage password re-use.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-08</p></td>
<td><p>Passwords must be a system configurable minimum age (e.g., one day old) before they can be changed, to prevent attacks on password re-use</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-09</p></td>
<td><p>Password entry fields do not echo the user’s password when it is entered.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-10</p></td>
<td><p>Autocomplete is disabled for all password entry fields in HTML forms.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-11</p></td>
<td><p>Passwords are transmitted over an encrypted connection. Temporary passwords associated with email resets may be an exception to this rule.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-12</p></td>
<td><p>For authentication over HTTP, authentication credentials are transmitted only within the POST body and not in the URL.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-13</p></td>
<td><p>Authentication controls and application functionality minimize the leakage of user account names.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-14</p></td>
<td><p>Stored server side passwords are protected using cryptographically strong one-way salted hashes that use salts that are unique per account. (e.g., Do not use the MD5 or SHA-1 algorithms).</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-15</p></td>
<td><p>Use large numbers of hash iterations or password based encryption to make it time consuming to calculate a single hashed password value.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-16</p></td>
<td><p>Stored passwords and cryptographic keys are readable and writeable only by the application.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-17</p></td>
<td><p>Brute force protection is provided after a system configurable number of invalid login attempts occur against an account within a configurable period of time (e.g., account is locked, CAPTCHA required, throttling enabled).</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-18</p></td>
<td><p>Implement monitoring to identify attacks against multiple user accounts, utilizing the same password. This attack pattern is used to bypass standard lockouts, when valid user IDs can be harvested or inferred.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-19</p></td>
<td><p>The date/time of the last successful login is reported to the user after they login, along with the number of failed login attempts since the last successful login.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-20</p></td>
<td><p>Password changing mechanisms are at least as resistant to attack as the primary authentication mechanism.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-21</p></td>
<td><p>Passwords are required to be changed before they become older than a system configurable maximum age.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-22</p></td>
<td><p>Password reset questions support sufficiently random answers. (e.g., "favorite color" is a bad question because red, blue, green, are very common answers. Favorite book is another bad question that generates insufficiently random answers.).</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-23</p></td>
<td><p>For email based resets, only send email to a pre-registered address with a temporary link/password. Reset questions should be asked after the user goes to the temporary page, not before the email is generated.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-24</p></td>
<td><p>Temporary passwords and links have a short, system configurable, expiration time.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-25</p></td>
<td><p>Users are required to change temporary passwords as soon as they are used.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-26</p></td>
<td><p>Users are notified when a password reset occurs on their account.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-27</p></td>
<td><p>Users must re-authenticate prior to performing security critical operations, such as change password, change email address, change mailing address, change mailing address, view very sensitive data, send funds, etc.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-28</p></td>
<td><p>All administrative and account management functions are at least as secure as the primary authentication mechanism.</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-29</p></td>
<td><p>Authentication is required for services exposed to external systems that provide sensitive information or functions.</p></td>
</tr>
<tr class="even">
<td><p>OCR-AUTH-30</p></td>
<td><p>All authentication credentials for accessing services external to the application are encrypted and stored in a protected location (e.g., not in source code).</p></td>
</tr>
<tr class="odd">
<td><p>OCR-AUTH-31</p></td>
<td><p>Multi-Factor Authentication is used for highly sensitive or high value systems or for specific high value transactions.</p></td>
</tr>
</tbody>
</table>

#### Project About

__NOTOC__ <headertabs />

[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:OWASP_Alpha_Quality_Document](Category:OWASP_Alpha_Quality_Document "wikilink")
[Common Numbering Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Application_Security_Verification_Standard_Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How_To](Category:How_To "wikilink")