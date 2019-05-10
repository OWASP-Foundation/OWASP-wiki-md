Please see new project name corrected on
<https://www.owasp.org/index.php/OWASP_Security_Ninja_Project>

# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p>TEMPORARY NOTE: There is an existing project called the OWASP Security Ninjas Training Program, sponsored by OpenDNS. The project is a single module with labs training class. They used the Ninja metaphor, but not as the backdrop and marketing focus we would do with this new project. I am requesting that the existing Security Ninjas Training modify or relinquish their name.</p>
<p><span style="color:#ff0000"></p>
<p><code>   Instructions are in RED text and should be removed from your document by deleting the text with the span tags. This document is intended to serve as an example of what is required of an OWASP project wiki page. The text in red serves as instructions, while the text in black serves as an example. Text in black is expected to be replaced entirely with information specific to your OWASP project.</code></p>
<p></span></p>
<h2 id="the_owasp_security_principles">The OWASP Security Principles</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you need to add your more robust project description. A project description should outline the purpose of the project, and the value it provides to application security. Ideally, project descriptions should be written in such a way that there is no question what value the project provides to the software security community. This section will be seen and used in various places within the Projects Portal. Poorly written project descriptions therefore detract from a project’s visibility, and project leaders should ensure that the description is meaningful.</code></p>
<p></span></p>
<p>Inevitably applications are designed with security principles architects knew about, security folks included. However, as this project demonstrates there are far more than just a 'few' principles, most of which never make it into the design.</p>
<p>For example, security design happens with perhaps a handful of principles:</p>
<ul>
<li>Least Privilege</li>
<li>Perimeter Security</li>
<li>Defence in Depth</li>
</ul>
<p>However, we regularly see designs without <strong>separation of privilege</strong>!</p>
<p>Think about that, most web applications today have all their eggs in a single basket. The business logic, the identities, passwords, products, policy enforcement, security rules are all found in the same application database that makes up the typical website! It is little wonder then, that attacks on the database have been so completely devastating, since there is no separation of privilege!</p>
<p>The aim of this project, is to identify and describe a minimum functional set of principles that must be present in a secure design.</p>
<h2 id="description">Description</h2>
<p><span style="color:#ff0000"></p>
<p>The OWASP Security Ninja Program exists to educate, empower, and recognize developers and testers in the field of web application security. Security belts measure domain specific knowledge and application, ranging from white to black belt.</p>
<p><code>   This section must include a shorter description of what the project is, why the project was started, and what security issue is being helped by the project deliverable. This description will be used to promote the project so make sure the description represents your project in the best way possible. </code></p>
<p></span></p>
<p>'''Although this is a sample template, the project is real! <a href="http://owasp.github.io/Security-Principles">Please contribute to this project.</a> '''</p>
<p>Over the course of my career, I have come across and collected a number of security <em>aphorisms.</em> These aphorisms constitute the fundamental principles of information security.</p>
<p>None of the ideas or truths are mine, and unfortunately, I did not collect the citations. Initially, I would like to identify the correct citations for each aphorism.</p>
<p>Additionally, many are re-statements of the same idea; thus, the 'collection of ideas' defines a fundamental principle. As such, I would also like to reverse engineer the principles from the aphorisms where appropriate, as well.</p>
<h2 id="licensing">Licensing</h2>
<p>Creative Commons Attribution ShareAlike 3.0 License</p>
<p><span style="color:#ff0000"></p>
<p><code>   A project must be licensed under a community friendly or open source license.  For more information on OWASP recommended licenses, please see </code><a href="https://www.owasp.org/index.php/OWASP_Licenses"><code>OWASP</code><code> </code><code>Licenses</code></a><code>. While OWASP does not promote any particular license over another, the vast majority of projects have chosen a Creative Commons license variant for documentation projects, or a GNU General Public License variant for tools and code projects.</code></p>
<p></span></p>
<p>'''The OWASP Security Principles are free to use. In fact it is encouraged</p></td>
<td><p>! '' Additionally, I also encourage you to contribute back to the project. I have no monopoly on this knowledge; however, we all have pieces of this knowledge from our experience. Let's begin by putting our individual pieces together to make something great. Great things happen when people work together.</p>
<p>The OWASP Security Principles are licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_owasp_security_principles_project">What is OWASP Security Principles Project?</h2>
<p><span style="color:#ff0000"></p>
<p><code>   Here you should add a short description of what your project actually does. What is the primary goal of your project, and why is it important?</code></p>
<p></span> The tangible deliverables are broken down into two categories: content and infrastructure. Content refers to any artifacts that contain specific learning. Infrastructure is any of the systems required to deliver the training to the learner.</p>
<p>On the content side, the deliverables are individual training module videos, assessments, and any associated slides or documentation that assist the learner in understanding the topic (and are used in the training video). Other deliverables may include virtual machines or lab based exercises available for download.</p>
<p>On the infrastructure side, front end interfaces, web servers, databases, storage, and a learning management system are required to deliver the training content to the Internet community. A front end interface and a custom piece of middleware are the main code based deliverables. A discussion will take place with the core team in the future to determine if any of the infrastructure is required, or if the content itself will be released.</p>
<p>The end goal is to identify, cite, and document the fundamental principles of information security. Once this is well organised, I think it would be great to publish this through the <a href="http://scriptogr.am/dennis-groves/post/owasp-press">OWASP Press</a>. Of course, it will always remain freely available, and any money collected will go directly into the project to absorb costs with any remaining funds going to the OWASP Foundation.</p>
<p>This document should serve as a guide to technical architects and designers outlining the fundamental principles of security.</p>
<h2 id="presentation">Presentation</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to slide presentations related to your project. </code></p>
<p></span></p>
<p>AppSec USA 2013 <a href="https://github.com/OWASP/Security-Principles/tree/master/Presentations/AppSec%20NYC%202013">1</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><span style="color:#ff0000"></p>
<p><code>   A project leader is the individual who decides to lead the project throughout its lifecycle. The project leader is responsible for communicating the project’s progress to the OWASP Foundation, and he/she is ultimately responsible for the project’s deliverables. The project leader must provide OWASP with his/her real name and contact e-mail address for his/her project application to be accepted, as OWASP prides itself on the openness of its products, operations, and members.</code></p>
<p></span></p>
<ul>
<li><a href="https://www.owasp.org/index.php/User:Dennis_Groves">Dennis Groves</a></li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to other OWASP Projects that are similar to yours. </code></p>
<p></span></p>
<ul>
<li><a href="OWASP_CISO_Survey" title="wikilink">OWASP_CISO_Survey</a></li>
</ul>
<h2 id="openhub">Openhub</h2>
<ul>
<li><a href="https://www.openhub.net/orgs/OWASP">OWASP Project Openhub</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to your repository.</code></p>
<p></span></p>
<p>The home of the OWASP Security Principles is on <a href="https://github.com/OWASP/Security-Principles">GitHub.</a> You are encourged to fork, edit and push your changes back to the project through git or edit the project directly on github.</p>
<p>However, if you like you may also download the master repository from the following links:</p>
<ul>
<li><a href="https://github.com/OWASP/Security-Principles/zipball/master">.zip file.</a></li>
<li><a href="https://github.com/OWASP/Security-Principles/tarball/master">.tgz file.</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to press your project has been a part of. Appropriate press includes: Project Leader interviews, articles written about your project, and videos about your project. </code></p>
<p></span></p>
<ul>
<li>[20 Nov 2013] News 2</li>
<li>[30 Sep 2013] News 1</li>
</ul>
<h2 id="in_print">In Print</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you place links to where your project product can be downloaded or purchased, in the case of a book. </code></p>
<p></span></p>
<p>This project can be purchased as a print on demand book from Lulu.com</p>
<h2 id="classifications">Classifications</h2>
<p><span style="color:#ff0000"></p>
<p><code>   Here is where you can let the community know what project stage your project is currently in, whether the project is a builder, breaker, or defender project, and what type of project you are running. </code></p>
<p></span></p>
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

# FAQs

<span style="color:#ff0000">

`   Many projects have "Frequently Asked Questions" documents or pages. However, the point of such a document is not the questions. `*`The``
 ``point``   ``of``   ``a``   ``document``   ``like``   ``this``
 ``are``   ``the``
 `**`answers`***`. The document contains the answers that people would otherwise find themselves giving over and over again. The idea is that rather than laboriously compose and post the same answers repeatedly, people can refer to this page with pre-prepared answers. Use this space to communicate your projects 'Frequent Answers.'`

</span>

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

# Acknowledgements

## Contributors

<span style="color:#ff0000">

`   The success of OWASP is due to a community of enthusiasts and contributors that work to make our projects great. This is also true for the success of your project. `

Be sure to give credit where credit is due, no matter how small\! This
should be a brief list of the most amazing people involved in your
project. Be sure to provide a link to a complete list of all the amazing
people in your project's community as well. </span>

The OWASP Security Principles project is developed by a worldwide team
of volunteers. A live update of project [contributors is found
here](https://github.com/OWASP/Security-Principles/graphs/contributors).

The first contributors to the project were:

  - [Dennis Groves](https://www.owasp.org/index.php/User:Dennis_Groves)
  - [Andrew Martin](https://github.com/sublimino)
  - [Josh Thomas](https://github.com/Lambdanaut)
  - **YOUR NAME BELONGS HERE**

# Road Map and Getting Involved

<span style="color:#ff0000"> The OWASP Security Ninja program is a
multi-phase undertaking. The OWASP White and Yellow Belts require the
creation of a series of video based training modules. The Green, Brown,
and Black belts require the creation of an activity submission process,
including a tracking and review component.

The high level content creation process per module consists of: -
outline of topic - review of outline - draft content - technical review
- instructional design review - final content - generate assessment

Multiple modules can be processed in parallel, presuming that multiple
community resources are available to assist with content creation and
review.

Major Milestones

Identify Project Vision & Strategy (November 2015 - January 2016)

\- Scope and Governance (January 2016) - Initial project summit (January
2016)

OWASP White Belt (maximum of 8 modules) (January 2016 - September 2016)

\- Content creation (January - March 2016) - Content recording (March
2016) - Infrastructure code and build (January - September 2016) - Alpha
(July 2016) - Second project summit @ AppSec EU (July 2016) - Beta
(August 2016) - Launch of content at AppSec USA (September 2016)

OWASP Yellow Belt (maximum of 32 modules: 16 core, 8 dev, 8 test)
(October 2016 - September 2017)

\- Content creation (October 2016 - March 2017) - Content recording
(April 2017) - Infrastructure update (January - September 2017) - Alpha
(July 2017) - Beta (August 2017) - Launch of content at AppSec USA
(September 2017)

OWASP Green Belt, OWASP Brown Belt, OWASP Black Belt (October 2017 -
September 2018)

\- Infrastructure update (January - July 2018) - Finalize governance and
oversight (January - March 2018) - Alpha (July 2018) - Beta (August
2018) - Launch of concept and completion of initial scope (September
2018)

Then the cycle begins again, with a refresh of OWASP White Belt.

`   A project roadmap is the envisioned plan for the project. The purpose of the roadmap is to help others understand where the project is going. It gives the community a chance to understand the context and the vision for the goal of the project. Additionally, if a project becomes inactive, or if the project is abandoned, a roadmap can help ensure a project can be adopted and continued under new leadership.`

</span> 

<span style="color:#ff0000">

`   Roadmaps vary in detail from a broad outline to a fully detailed project charter. Generally speaking, projects with detailed roadmaps have tended to develop into successful projects. Some details that leaders may consider placing in the roadmap include: envisioned milestones, planned feature enhancements, essential conditions, project assumptions, development timelines, etc. You are required to have at least 4 milestones for every year the project is active. `

</span>

As of October 2013, the priorities are:

  - Finish the referencing for each principle.
  - Update the Project Template.
  - Use the OWASP Press to develop a book.
  - Finish and publish the book on Lulu.

Involvement in the development and promotion of the OWASP Security
Principles Project is actively encouraged\! You do not have to be a
security expert in order to contribute. Some of the ways you can help:

  - Helping find references to some of the principles.
  - Project administration support.
  - Wiki editing support.
  - Writing support for the book.

# Project About

<span style="color:#ff0000">

`   This page is where you need to place your legacy project template page if your project was created before October 2013. To edit this page you will need to edit your project information template. You can typically find this page by following this address and substituting your project name where it says "OWASP_Example_Project". When in doubt, ask the OWASP Projects Manager. `

Example template page:
<https://www.owasp.org/index.php/Projects/OWASP_Example_Project> </span>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")