# Overview

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_description">Project Description</h2>
<p>This project educates security professionals about the risks of reverse engineering and how to ensure that code cannot be reverse engineered or modified. If you are placing sensitive code in an environment in which an attacker can get physical access to that environment (read: mobile, desktops, cloud, particular geographies), you should be concerned with the risks of reverse engineering or unauthorized code modification. This umbrella project will help you understand the risks and how to mitigate them.</p>
<h2 id="a_brief_history_of_this_problem_space">A Brief History of This Problem Space</h2>
<p>Historically, organizations offered their customers web applications that exposed an interface to some necessary business services. The services expose high-value functionality that allows an organization to deliver value to its clients. Attackers had a specific set of threats or goals that they realized by exploiting vulnerabilities that the organization exposed through the application’s presentation layer. Security practitioners address these specific sets of vulnerabilities through the web application or the associated infrastructure security disciplines.</p>
<p>Most often, attackers successfully realized their threats by providing malicious input that they fed into the web application’s presentation layer. Classic attack vectors used by attackers that use this technique include: SQL Injection, Cross-Site (XSS) Scripting, and URL parameter tampering vulnerabilities. Often, security professionals detect the presence of these vulnerabilities through source code analysis or penetration testing. In response to the detection, security professionals recommend to the organization that its Software Engineers should mitigate these vulnerabilities by applying secure coding techniques and adding appropriate data validation security controls to the affected application. Generally, this is sage advice and it works well for traditional web-based applications. In this common scenario, this advice is enforceable because the organization is hosting the web application in a highly controlled (more trustworthy) environment where only the organization’s Software Engineers can modify the application’s underlying code.</p>
<p>In present day, consumers have demanded richer user experiences than what organizations could traditionally offer through web applications they exposed online. In response to these demands, organizations began augmenting the user experience with mobile applications. These applications offer genuinely quicker and richer user experiences than what users would otherwise get through traditional browser-based web applications.</p>
<p>In making the switch to mobile applications, organizations are now deploying more of the presentation layer and business layer of the application on a phone instead of on their own servers. As a result, they lose a lot more control over who gets to see or modify their application’s code. Before the switch, most of the application’s presentation and business layer functionality was hidden within the organization’s trusted server environments. Outside users or attackers did not get much of an opportunity to see executing code in action.</p>
<p>With the recent move towards mobile applications, an attacker can now see, touch, and directly modify a lot of the application’s presentation and business layer code within the attacker’s mobile computing environment. This capability allows the attacker to realize the same traditional business threats as before (with web applications) but in genuinely new and unconventional ways.</p>
<h2 id="licensing">Licensing</h2>
<p>Any documentation or educational material associated with this project is free to use. It is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_does_this_project_deliver">What does this project deliver?</h2>
<p>Prevent an attacker from reverse engineering your code or making unauthorized changes to that code. The following audiences get something from this project:</p>
<ul>
<li><em>Risk Specialists</em> - Understand the business and technical risks that an attacker will deploy in order to reverse engineer or modify your code in unsafe environments;</li>
</ul>
<ul>
<li><em>Security Architects</em> - Understand the architectural features that should be embedded into code to prevent an attacker from reverse engineering or modifying your code;</li>
</ul>
<ul>
<li><em>Penetration Testers</em> - Learn how to conduct binary attacks against mobile apps understand threats that can be realized against various different platforms. You'll have a better understanding of useful attack vectors to verify the strength of reverse engineering prevention or unauthorized code modification;</li>
</ul>
<ul>
<li><em>Software Engineers</em> - Learn things that you can do to make reverse engineering as painful as possible for someone that is interested in reverse-engineering your code.</li>
</ul>
<h2 id="sub_projects">Sub-projects</h2>
<p><em>RISK</em>: <a href="Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification" title="wikilink">Technical Risks of Reverse Engineering and Unauthorized Code Modification</a></p>
<p>This sub-project helps organizations understand the various technical risks that they are exposed to when they host sensitive code in untrustworthy environments. It is useful to stakeholders that must decide how/if to mitigate these risks.</p>
<p><em>ARCHITECTURE</em>: <a href="Architectural_Principles_That_Prevent_Code_Modification_or_Reverse_Engineering" title="wikilink">Architectural Principles That Prevent Code Modification or Reverse Engineering</a></p>
<p>This sub-project helps security architects and designers understand the features of their application that should be included to prevent reverse engineering or code modification.</p>
<h2 id="related_projects">Related Projects</h2>
<p>This project is associated with</p>
<ul>
<li><a href="OWASP_Mobile_Security_Project" title="wikilink">OWASP_Mobile_Security_Project</a></li>
<li><a href="OWASP_AppSensor_Project" title="wikilink">OWASP_AppSensor_Project</a></li>
<li><a href="OWASP_iMAS_iOS_Mobile_Application_Security_Project" title="wikilink">OWASP_iMAS_iOS_Mobile_Application_Security_Project</a></li>
<li><a href="Mobile_Jailbreaking_Cheat_Sheet" title="wikilink">Mobile_Jailbreaking_Cheat_Sheet</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="project_contributors">Project Contributors</h2>
<ul>
<li>Jonathan Carter (Leader)</li>
<li>Kajihara Masao (Project Contributor)</li>
<li>Jim DelGrosso (Project Contributor)</li>
<li>Chris Stahly (Project Contributor)</li>
<li>Rennie Allen (Project Contributor)</li>
</ul>
<h2 id="presentations">Presentations</h2>
<ul>
<li><a href="Media:OWASP_Mobile_App_Hacking_(AppSecUSA_2015)_Workshop_Feedback.pdf" title="wikilink">Media:OWASP Mobile App Hacking (AppSecUSA 2015) Workshop Feedback.pdf</a></li>
<li><a href="Media:Consequences_of_a_Jailbroken_iDevice.pdf" title="wikilink">Media:Consequences_of_a_Jailbroken_iDevice.pdf</a></li>
<li><a href="Media:Mobile_Risks_and_Solutions.pdf" title="wikilink">Media:Mobile Risks and Solutions.pdf</a></li>
<li><a href="Media:OWASP_Mobile_App_Hacking_(AppSecUSA_2014)_Workshop_Content.pdf" title="wikilink">Media:OWASP Mobile App Hacking (AppSecUSA 2014) Workshop Content.pdf</a></li>
<li><a href="Media:OWASP_Mobile_App_Hacking_(AppSecUSA_2014)_Feedback.pdf" title="wikilink">Media:OWASP Mobile App Hacking (AppSecUSA 2014) Feedback.pdf</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[May 2015] - <strong>AppSecEU Workshop 2015 conducted</strong></li>
<li>[May 2015] - Oracle Webinar on Project Conducted</li>
<li>[September 2014] - AppSec USA Workshop 2014 conducted</li>
<li>[April 2014] - Architectural Principles content finalized and released</li>
<li>[March 2014] - Technical Risks content translated into Japanese</li>
<li>[January 2014] - Technical Risks content finalized and released</li>
<li>[December 2013] - Establishment of project wiki</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
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

# FAQs

  - Is there anything that an organization can really do to prevent
    someone from modifying their code if the attacker has physical
    access to the code?
    Absolutely. There are a lot of things that Software Engineers can do
    to prevent an attacker from understanding or modifying their code.

<!-- end list -->

  - Is this really a frequently occurring problem?
    Yes, this is a huge problem that many different business verticals
    have had to deal with over time. It's just now starting to hit the
    web and mobile development communities.

# Road Map and Getting Involved

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")