# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="what_is_api_security">What is API Security?</h2>
<p>A foundational element of innovation in today’s app-driven world is the API. From banks, retail and transportation to IoT, autonomous vehicles and smart cities, APIs are a critical part of modern mobile, SaaS and web applications and can be found in customer-facing, partner-facing and internal applications. By nature, APIs expose application logic and sensitive data such as Personally Identifiable Information (PII) and because of this have increasingly become a target for attackers. Without secure APIs, rapid innovation would be impossible.</p>
<p>API Security focuses on strategies and solutions to understand and mitigate the unique vulnerabilities and security risks of Application Programming Interfaces (APIs).</p>
<h2 id="api_security_top_10_release_candidate_is_here">API Security Top 10 Release Candidate is Here!</h2>
<p>The RC version is finally ready and was presented during Global AppSec DC 2019 and Global AppSec Amsterdam 2019. Links to the presentations can be found in the News section on the right. Here is a sneak peek:</p>
<table>
<tbody>
<tr class="odd">
<td><p>API1</p></td>
<td><p>Broken Object Level Authorization</p></td>
<td><p>APIs tend to expose endpoints that handle object identifiers, creating a wide attack surface Level Access Control issue. Object-level authorization checks should be considered in every function that accesses a data source using input from the user.</p></td>
</tr>
<tr class="even">
<td><p>API2</p></td>
<td><p>Broken Authentication</p></td>
<td><p>Authentication mechanisms are often implemented incorrectly, allowing attackers to compromise authentication tokens or to exploit implementation flaws to assume other user's identities temporarily or permanently. Compromising system's ability to identify the client/user, compromises API security overall.</p></td>
</tr>
<tr class="odd">
<td><p>API3</p></td>
<td><p>Excessive Data Exposure</p></td>
<td><p>Looking forward to generic implementations, developers tend to expose all object properties without considering their individual sensitivity, relying on clients to perform the data filtering before displaying it to the user.</p></td>
</tr>
<tr class="even">
<td><p>API4</p></td>
<td><p>Lack of Resources &amp; Rate Limiting</p></td>
<td><p>Quite often, APIs do not impose any restrictions on the size or number of resources that can be requested by the client/user. Not only can this impact the API server performance, leading to Denial of Service (DoS), but also leaves the door open to authentication flaws such as brute force.</p></td>
</tr>
<tr class="odd">
<td><p>API5</p></td>
<td><p>Broken Function Level Authorization</p></td>
<td><p>Complex access control policies with different hierarchies, groups, and roles, and an unclear separation between administrative and regular functions, tend to lead to authorization flaws. By exploiting these issues, attackers gain access to other users’ resources and/or administrative functions.</p></td>
</tr>
<tr class="even">
<td><p>API6</p></td>
<td><p>Mass Assignment</p></td>
<td><p>Binding client provided data (e.g., JSON) to data models, without proper properties filtering based on a whitelist, usually lead to Mass Assignment. Either guessing objects properties, exploring other API endpoints, reading the documentation, or providing additional object properties in request payloads, allows attackers to modify object properties they are not supposed to.</p></td>
</tr>
<tr class="odd">
<td><p>API7</p></td>
<td><p>Security Misconfiguration</p></td>
<td><p>Security misconfiguration is commonly a result of insecure default configurations, incomplete or ad-hoc configurations, open cloud storage, misconfigured HTTP headers, unnecessary HTTP methods, permissive Cross-Origin resource sharing (CORS), and verbose error messages containing sensitive information.</p></td>
</tr>
<tr class="even">
<td><p>API8</p></td>
<td><p>Injection</p></td>
<td><p>Injection flaws, such as SQL, NoSQL, Command Injection, etc. occur when untrusted data is sent to an interpreter as part of a command or query. The attacker's malicious data can trick the interpreter into executing unintended commands or accessing data without proper authorization.</p></td>
</tr>
<tr class="odd">
<td><p>API9</p></td>
<td><p>Improper Assets Management</p></td>
<td><p>APIs tend to expose more endpoints than traditional web applications, making proper and updated documentation highly important. Proper hosts and deployed API versions inventory also play an important role to mitigate issues such as deprecated API versions and exposed debug endpoints.</p></td>
</tr>
<tr class="even">
<td><p>API10</p></td>
<td><p>Insufficient Logging &amp; Monitoring</p></td>
<td><p>Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems to tamper with, extract, or destroy data. Most breach studies demonstrate the time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring.</p></td>
</tr>
</tbody>
</table>
<h2 id="licensing">Licensing</h2>
<p><strong>The OWASP API Security Project documents are free to use!</strong></p>
<p>The OWASP API Security Project is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><h2 id="project_leaders">Project Leaders</h2>
<ul>
<li><a href="User:ErezYalon" title="wikilink">Erez Yalon</a></li>
<li><a href="User:Inon" title="wikilink">Inon Shkedy</a></li>
</ul>
<p><strong>Main Collaborator</strong></p>
<ul>
<li><a href="User:PauloASilva" title="wikilink">Paulo Silva</a></li>
</ul>
<h2 id="quick_links">Quick Links</h2>
<p><a href="https://groups.google.com/a/owasp.org/d/forum/api-security-project">Google Group</a></p>
<p><a href="https://github.com/OWASP/API-Security">GitHub</a></p>
<p><a href="https://github.com/OWASP/API-Security/raw/master/2019/en/dist/owasp-api-security-top-10.pdf">PDF version of API Security Top 10</a></p>
<p><a href="https://www.owasp.org/images/5/59/API_Security_Top_10_RC.pdf">Presentation of the Release Candidate of the API Security Top 10</a></p>
<h2 id="news">News</h2>
<h3 id="sep_30_2019">Sep 30, 2019</h3>
<p>The RC of API Security Top-10 List was published during <a href="https://ams.globalappsec.org/">OWASP Global AppSec Amsterdam</a></p>
<figure>
<embed src="API_Security_Top_10_RC_-_Global_AppSec_AMS.pdf" title="API_Security_Top_10_RC_-_Global_AppSec_AMS.pdf" /><figcaption>API_Security_Top_10_RC_-_Global_AppSec_AMS.pdf</figcaption>
</figure>
<h3 id="sep_13_2019">Sep 13, 2019</h3>
<p>The RC of API Security Top-10 List was published during <a href="https://dc.globalappsec.org/">OWASP Global AppSec DC</a></p>
<figure>
<embed src="API_Security_Top_10_RC.pdf" title="API_Security_Top_10_RC.pdf" /><figcaption>API_Security_Top_10_RC.pdf</figcaption>
</figure>
<h3 id="may_30_2019">May 30, 2019</h3>
<p>The API Security Project was Kicked-Off during <a href="https://telaviv.appsecglobal.org/">OWASP Global AppSec Tel Aviv</a></p>
<figure>
<embed src="OWASP_APIs_Security_Project_Kick_Off.pdf" title="File:OWASP APIs Security Project Kick Off.pdf" /><figcaption><a href="File:OWASP">File:OWASP</a> APIs Security Project Kick Off.pdf</figcaption>
</figure></td>
</tr>
</tbody>
</table>

# Acknowledgments

## Founders

  - Erez Yalon
  - Inon Shkedy

## Sponsors

![Checkmarx-Logo-Horizontal-black-512px.png](Checkmarx-Logo-Horizontal-black-512px.png
"Checkmarx-Logo-Horizontal-black-512px.png")
![SALT_Logo.jpg](SALT_Logo.jpg "SALT_Logo.jpg")

## Main Maintainer

  - Paulo Silva

## Contributors

  - David Sopas
  - Chris Westphal

# Join

## Google Group

Join the discussion on the [OWASP API Security Project Google
group](https://groups.google.com/a/owasp.org/d/forum/api-security-project).

This is the best place to introduce yourself, ask questions, suggest and
discuss any topic that is relevant to the project.

## GitHub

The project is maintained in the [OWASP API Security Project
repo](https://github.com/OWASP/API-Security).

**The latest changes are under the [develop
branch](https://github.com/OWASP/API-Security/tree/develop).**

Feel free to open or solve an
[issue](https://github.com/OWASP/API-Security/issues).

Ready to contribute directly into the repo? Great\! Just make you you
read the [How to Contribute
guide](https://github.com/OWASP/API-Security/blob/master/CONTRIBUTING.md).

# Road Map

## Planned Projects

  - API Security Top 10
  - API Security Cheat Sheet
  - crAPI (**C**ompletely **R**idiculous **API** - an intentionally
    vulnerable API project)

## Road Map

![Roadmap.png](Roadmap.png "Roadmap.png")

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Breakers](Category:OWASP_Breakers "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")