This update to the OWASP Top 10 focuses on identifying the most serious
risks for a broad array of organizations. For each of these risks, we
provide generic information about likelihood and technical impact using
the following simple ratings scheme, which is based on the OWASP Risk
Rating Methodology.

<center>

| Threat Agent | Attack Vector | Weakness Prevalence | Weakness Detectability | Technical Impact | Business Impact |
| ------------ | ------------- | ------------------- | ---------------------- | ---------------- | --------------- |
| ?            |               | Easy                |                        | Widespread       |                 |
| ?            |               | Average             |                        | Common           |                 |
| ?            |               | Difficult           |                        | Uncommon         |                 |

</center>

However, only you know the specifics of your environment and your
business. For any given application, there may not be a threat agent
that can perform the relevant attack, or the technical impact may not
make any difference. Therefore, you should evaluate each risk for
yourself, focusing on the threat agents, security controls, and business
impacts in your enterprise.

Although previous versions of the OWASP Top 10 focused on identifying
the most common “vulnerabilities”, they were also designed around risk.
The names of the risks in the Top 10 stem from the type of attack, the
type of weakness, or the type of impact they cause. We chose the name
that is best known and will achieve the highest level of awareness.

<table>
<tbody>
<tr class="odd">
<td><center>
<p><a href="Top_10_2010-A1" title="wikilink">A1-Injection</a></p>
</center></td>
<td><p>Injection flaws, such as SQL, OS, and LDAP injection, occur when untrusted data is sent to an interpreter as part of a command or query. The attacker’s hostile data can trick the interpreter into executing unintended commands or accessing unauthorized data.</p></td>
</tr>
<tr class="even">
<td><center>
<p><a href="Top_10_2010-A2" title="wikilink">A2-Cross Site Scripting (XSS)</a></p>
</center></td>
<td><p>XSS flaws occur whenever an application takes untrusted data and sends it to a web browser without proper validation and escaping. XSS allows attackers to execute scripts in the victim’s browser which can hijack user sessions, deface web sites, or redirect the user to malicious sites.</p></td>
</tr>
<tr class="odd">
<td><center>
<p><a href="Top_10_2010-A3" title="wikilink">A3-Broken Authentication and Session Management</a></p>
</center></td>
<td><p>Application functions related to authentication and session management are often not implemented correctly, allowing attackers to compromise passwords, keys, session tokens, or exploit other implementation flaws to assume other users’ identities.</p></td>
</tr>
<tr class="even">
<td><center>
<p><a href="Top_10_2010-A4" title="wikilink">A4-Insecure Direct Object References</a></p>
</center></td>
<td><p>A direct object reference occurs when a developer exposes a reference to an internal implementation object, such as a file, directory, or database key. Without an access control check or other protection, attackers can manipulate these references to access unauthorized data.</p></td>
</tr>
<tr class="odd">
<td><center>
<p><a href="Top_10_2010-A5" title="wikilink">A5-Cross Site Request Forgery (CSRF)</a></p>
</center></td>
<td><p>A CSRF attack forces a logged-on victim’s browser to send a forged HTTP request, including the victim’s session cookie and any other automatically included authentication information, to a vulnerable web application. This allows the attacker to force the victim’s browser to generate requests the vulnerable application thinks are legitimate requests from the victim.</p></td>
</tr>
<tr class="even">
<td><center>
<p><a href="Top_10_2010-A6" title="wikilink">A6-Security Misconfiguration</a></p>
</center></td>
<td><p>Good security requires having a secure configuration defined and deployed for the application, frameworks, application server, web server, database server, and platform. All these settings should be defined, implemented, and maintained as many are not shipped with secure defaults. This includes keeping all software up to date, including all code libraries used by the application.</p></td>
</tr>
<tr class="odd">
<td><center>
<p><a href="Top_10_2010-A7" title="wikilink">A7-Insecure Cryptographic Storage</a></p>
</center></td>
<td><p>Many web applications do not properly protect sensitive data, such as credit cards, SSNs, and authentication credentials, with appropriate encryption or hashing. Attackers may steal or modify such weakly protected data to conduct identity theft, credit card fraud, or other crimes.</p></td>
</tr>
<tr class="even">
<td><center>
<p><a href="Top_10_2010-A8" title="wikilink">A8-Failure to Restrict URL Access</a></p>
</center></td>
<td><p>Many web applications check URL access rights before rendering protected links and buttons. However, applications need to perform similar access control checks each time these pages are accessed, or attackers will be able to forge URLs to access these hidden pages anyway.</p></td>
</tr>
<tr class="odd">
<td><center>
<p><a href="Top_10_2010-A9" title="wikilink">A9-Insufficient Transport Layer Protection</a></p>
</center></td>
<td><p>Applications frequently fail to authenticate, encrypt, and protect the confidentiality and integrity of sensitive network traffic. When they do, they sometimes support weak algorithms, use expired or invalid certificates, or do not use them correctly.</p></td>
</tr>
<tr class="even">
<td><center>
<p><a href="Top_10_2010-A10" title="wikilink">A10-Unvalidated Redirects and Forwards</a></p>
</center></td>
<td><p>Web applications frequently redirect and forward users to other pages and websites, and use untrusted data to determine the destination pages. Without proper validation, attackers can redirect victims to phishing or malware sites, or use forwards to access unauthorized pages.</p></td>
</tr>
</tbody>
</table>

  - [OWASP Risk Rating
    Methodology](OWASP_Risk_Rating_Methodology "wikilink")
  - [Article on Threat/Risk Modeling](Threat_Risk_Modeling "wikilink")

<!-- end list -->

  - [FAIR Information Risk
    Framework](http://fairwiki.riskmanagementinsight.com/)
  - [Microsoft Threat Modeling (STRIDE and
    DREAD)](http://msdn.microsoft.com/en-us/library/aa302419.aspx)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")