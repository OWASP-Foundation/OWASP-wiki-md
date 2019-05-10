# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="the_owasp_cloud_security_project">The OWASP Cloud Security Project</h2>
<p>We believe that cyber security has a fundamental role to play in protecting the digital future. We also believe that cyber security isn't just about the technology; it's about the people. The customer, the developer, the designer, the security engineer, even the attacker. Not only is cyber security a never-ending process, it's also a conversation.</p>
<p>This project was created to enable that conversation.</p>
<blockquote>
<p>Given the challenge of protecting the digital future And a diverse group of awesomely talented people When we enable the conversation between people Then they can make a real difference to the security of their services</p>
</blockquote>
<p>The rise of DevOps and cloud computing has given organisations unprecedented access to feature-rich and high-scalable elastic platforms that allow them to deliver products and services with a velocity and agility that has never been seen before.</p>
<p>But with new capabilities come new attack vectors. The OWASP Cloud Security project aims to help people secure their products and services running in the cloud by providing a set of easy to use threat and control BDD stories that pool together the expertise and experience of the development, operations and security communities.</p>
<h3 id="why_bdd_stories">Why BDD stories?</h3>
<p>Behaviour Driven Development (BDD) adds a natural language layer on top of test-driven development by defining requirements in a machine parsable language that is also human readable. While adoption of BDD within development communities has been mixed (often because the developers end up having to duplicate effort as both producers and consumers of the BDD stories), BDD is actually an excellent fit for representing threats and control. For threats it provides a consistent and structured format for express threats and scenarios in a way that can be shared between all stakeholders, from engineers to management. For mitigating controls BDD is ideal because it expresses control requirements in a way that is also continuously testable. Rather than burying a control requirement in a policy document that nobody reads, it can be represented in a way that an auditor would be happy with at the same time as being implemented as automated detective or preventative tests.</p>
<p>By bringing together threat and control stories, provided by the community, the OWASP Cloud Security project helps organisations understand the risks they face on their journey into the cloud.</p>
<h3 id="threat_modelling">Threat modelling</h3>
<p>Threat modelling addresses security issues at a fundamental, architectural level. Rather than trying to bolt on controls haphazardly, threat modelling results in more robust and secure systems by baking security into the design as well as identifying the gaps and weaknesses. Using threat stories allows the sharing of common threats in a way that can be tweaked and tuned by individual organisations. Improvements to the threats can then be fed back to the community for the benefit of everyone.</p>
<h2 id="description">Description</h2>
<p>The OWASP Cloud Security project started life as a BDD for Cloud Security session held at the awesome OWASP Summit 2017. In this session approximately ten people spent an hour discussing whether it made sense to use BDD a way of capturing cloud control requirements in a way that fostered collaboration between development, operations, and security. The question then became - where do the requirements come from? PCI/DSS or some other standard? After spending the rest of the summit in various threat modelling sessions, it became clear to the project leader that it would be good to threat model the cloud services and then to write BDD stories for the mitigating controls from those threat models.</p>
<p>This project provides the following for an ever-expanding list of cloud providers and services:</p>
<ul>
<li>Threats expressed as BDD (Gherkin) stories</li>
<li>Mitigating controls expressed as BDD (Gherkin) stories</li>
<li>Proof-of-concept attack scripts and tools</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p><strong>The OWASP Cloud Security project resources are all completely free to use!</strong></p>
<p>Documentation and related resources are licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">Creative Commons Attribution-ShareAlike 3.0 license</a>, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p>
<p>Code is licensed under the <a href="https://opensource.org/licenses/MIT">MIT license</a>.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_owasp_cloud_security_project">What is OWASP Cloud Security Project?</h2>
<p>The OWASP Cloud Security project aims to help people secure their products and services running in the cloud by providing a set of easy to use threat and control BDD stories that pool together the expertise and experience of the development, operations, and security communities.</p>
<p><a href="https://github.com/owasp-cloud-security/owasp-cloud-security#contributing">Please contribute!</a></p>
<h2 id="presentation">Presentation</h2>
<ul>
<li><a href="https://www.devseccon.com/london-2017/session/cloudy-chance-threat-models/">DevSecCon London 2017</a></li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/User:Fraserscott">Fraser Scott</a></li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/OWASP_Threat_Model_Project">OWASP Threat Model Project</a></li>
<li><a href="https://www.owasp.org/index.php/OWASP_Threat_Dragon">OWASP Threat Dragon</a></li>
</ul>
<h2 id="openhub">Openhub</h2>
<ul>
<li><a href="https://www.openhub.net/orgs/OWASP">OWASP Project Openhub</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="source_code_and_documentation">Source code and documentation</h2>
<p>The home of the OWASP Cloud Security project is on is on <a href="https://github.com/owasp-cloud-security/owasp-cloud-security">GitHub.</a> You are encourged to fork, edit and push your changes back to the project through git or edit the project directly on github.</p>
<p>Please note that the project is still in its own organisation. This will be moved over to the <a href="https://github.com/owasp">OWASP</a> organisation soon.</p>
<h2 id="news_and_events">News and Events</h2>
<p>The project has appeared in the follow posts:</p>
<ul>
<li><a href="https://adam.shostack.org/blog/2017/12/threat-modeling-tooling-from-2017/">https://adam.shostack.org/blog/2017/12/threat-modeling-tooling-from-2017/</a></li>
<li><a href="https://automationpanda.com/2017/12/10/yaml-comments-in-gherkin-feature-files/">https://automationpanda.com/2017/12/10/yaml-comments-in-gherkin-feature-files/</a></li>
</ul>
<h2 id="in_print">In Print</h2>
<p>This project is not currently available to purchase as a book.</p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>rowspan="2" align="center" valign="top" width="50%"</p></td>
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

# FAQs

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

To participate, please see the [Getting
involved](https://github.com/owasp-cloud-security/owasp-cloud-security#getting-involved)
section of the repository README.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

For more information, visit the
[GitHub](https://github.com/owasp-cloud-security/owasp-cloud-security#getting-involved)
repository.

# Acknowledgements

## Contributors

The OWASP Cloud Security project is developed by volunteers. A live
update of project [contributors is found
here](https://github.com/owasp-cloud-security/owasp-cloud-security/graphs/contributors).

The first contributors to the project were:

  - [Fraser Scott](https://www.owasp.org/index.php/User:Fraserscott)
  - Steven Wierckx
  - Adam Shostack
  - Manish S. Saindane
  - Paulo Gomes
  - Francois Raynaud
  - Paul Cutting
  - **YOUR NAME BELONGS HERE**

# Road Map and Getting Involved

As of October 2017, the priorities are:

  - Threat models and BDD stories for top 10 AWS services
  - Threat models and BDD stories for top 10 Azure services
  - Threat models and BDD stories for top 10 Google Cloud Platform
    services
  - Provider-agnostic threat models and BDD stories
  - Threats models and BDD stories based on published standards (e.g.
    PCI/DSS) and best-practices (e.g. whitepapers)

To get involved, see the [Github
repository](https://github.com/owasp-cloud-security/owasp-cloud-security).

__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")