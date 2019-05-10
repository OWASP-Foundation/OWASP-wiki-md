# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="the_owasp_security_principles">The OWASP Security Principles</h2>
<p>The project is to discuss SaaS rest API threats, security design and operation best practices for the following key roles.</p>
<ol>
<li>SaaS API provider: For API builder, the key challenge is to build secure API and ensure the security validation for public API uses</li>
<li>App Builder based on SaaS API: App builder needs to securely implement the authorization/authentication to access the SaaS resource. Handling of access token are the key security topic in App builder.</li>
<li>3SaaS platform service provider: SaaS platform service provider is to ensure the API platform security such as authorization/authentication management, API interaction between app and end user, abnormal API access monitoring, resource access control and so on.</li>
</ol>
<p>The SaaS API security is an ecosystem. The security practices require not only SaaS provider but also app builder, and end user involvement. For SaaS API builder, he may follow secure coding guide, OWASP Top 10 to deliver the restAPI. For App builder, he needs to handle the access token securely, verify the certificate of target website, redirect user to authentication (JWT, OpenID connect, SAML) and authorization (Oauth2) through secure transmission HTTPS/TLS. Any missing of the security practices will introduce security risks. Then, the SaaS platform provider constantly monitoring and auditing the usage of services, manage accounts/API, hardening platform. Finally, the end user security awareness to identify phishing app/site will complete the whole security cycle.</p>
<p>Proposed Agenda</p>
<ul>
<li>Key threats</li>
</ul>
<ol>
<li>Access Token misuses</li>
<li>Insecure Transmission</li>
<li>3rd party App insecure implementation</li>
<li>End user Awareness</li>
</ol>
<ul>
<li>API Provider</li>
</ul>
<ol>
<li>Authentication (SSO, JWT, SAML, OpenID connect)</li>
<li>Authorization (Oauth2.0)</li>
<li>Error handling</li>
<li>Input Validation</li>
<li>Security Token</li>
</ol>
<ul>
<li>App Builder security</li>
</ul>
<ol>
<li>Handling of Access Token</li>
<li>Secure Transmission</li>
<li>Target SaaS host CA verification</li>
<li>Storage of sensitive information</li>
<li>Secure rest API implementation</li>
<li>App Security Release Review</li>
</ol>
<ul>
<li>SaaS platform Operation Security</li>
</ul>
<ol>
<li>Password Policy</li>
<li>Auditing and Logging</li>
<li>Access Control</li>
<li>API access rate/traffic Management</li>
<li>Login and Authentication</li>
<li>Session Management</li>
<li>Compliance</li>
<li>Host/Platform Security</li>
</ol>
<h2 id="licensing">Licensing</h2>
<p>The OWASP Proactive Controls document is free to use under the <a href="https://creativecommons.org/licenses/by-sa/3.0/us/">Creative Commons ShareAlike 3 License</a>.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_owasp_security_principles_project">What is OWASP Security Principles Project?</h2>
<p>The end goal is to identify, cite, and document the fundamental principles of Rest API security in terms of API builder, SaaS platform provider, and API consumer/builder.</p>
<p>This document should be as a guide to security technical architects, API builder and SaaS platform API provider outlining the fundamental principles of security.</p>
<h2 id="presentation">Presentation</h2>
<p><span style="color:#ff0000"></p>
<ul>
<li>To be updated</li>
</ul>
<p></span></p>
<h2 id="project_leader">Project Leader</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/User:Tony_Hsu_HsiangChih">Tony Hsu</a> <a href="mailto:hsiang_chih@yahoo.com">@</a></li>
</ul>
<h2 id="key_contributors">Key Contributors</h2>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_Top_Ten_Project" title="wikilink">OWASP Top Ten Project</a></li>
<li><a href="Cheat_Sheets" title="wikilink">Cheat Sheets</a></li>
<li><a href="REST_Security_Cheat_Sheet" title="wikilink">REST Security Cheat Sheet</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><span style="color:#ff0000"></p>
<p><code>   To be updated</code></p>
<p></span></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[June 2016] Project Initiated. Call for Contributors.</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="New_projects.png" title="New_projects.png" alt="New_projects.png" width="100" /><figcaption>New_projects.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_DOC.jpg" title="Project_Type_Files_DOC.jpg" alt="Project_Type_Files_DOC.jpg" /><figcaption>Project_Type_Files_DOC.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# REST API Builder

## Summary

# REST API Consumer

# REST API Platform

# Top 10 Mapping

# FAQs

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key. Project Lead contact [Tony
Hsu](https://www.owasp.org/index.php/User:Tony_Hsu_HsiangChih)
[@](mailto:hsiang_chih@yahoo.com)

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

# Acknowledgements

## Contributors

The first contributors to the project were:

  - [Tony Hsu](https://www.owasp.org/index.php/User:Tony_Hsu_HsiangChih)

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")