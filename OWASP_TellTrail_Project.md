# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p><span style="color:#ff0000"> Instructions are in RED text and should be removed from your document by deleting the text with the span tags. This document is intended to serve as an example of what is required of an OWASP project wiki page. The text in red serves as instructions, while the text in black serves as an example. Text in black is expected to be replaced entirely with information specific to your OWASP project. </span></p>
<h2 id="owasp_telltrail_project">OWASP TellTrail Project</h2>
<p>TellTrail lets individuals control the transfer of their personal data to third parties. People can specify "data policies" that dictate what data may be accessed, and who may access it. We want to make a responsible data ecosystem for everyone.</p>
<h2 id="description">Description</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you need to add your more robust project description. A project description should outline the purpose of the project, how it is used, and the value it provides to application security. Ideally, project descriptions should be written in such a way that there is no question what value the project provides to the software security community. This section will be seen and used in various places within the Projects Portal. Poorly written project descriptions therefore detract from a project’s visibility, so project leaders should ensure that the description is meaningful.  </code></p>
<p></span></p>
<h2 id="licensing">Licensing</h2>
<p><a href="https://tldrlegal.com/license/apache-license-2.0-%28apache-2.0%29">Apache 2.0</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to the key locations for project files, including setup programs, the source code repository, online documentation, a Wiki Home Page, threaded discussions about the project, and Issue Tracking system, etc. </code></p>
<p></span></p>
<h2 id="project_leaders">Project Leaders</h2>
<p><a href="mailto:loren.davie@owasp.org">Loren Davie</a> <a href="mailto:judy.katzman@owasp.org">Judy Katzman</a> <a href="mailto:sean.auriti@owasp.org">Sean Auriti</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to other OWASP Projects that are similar to yours. </code></p>
<p></span></p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><p><a href="https://tldrlegal.com/license/apache-license-2.0-%28apache-2.0%29">Apache 2.0</a></p></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can provide project updates, links to any events like conference presentations, Project Leader interviews, case studies on successful project implementations, and articles written about your project. </code></p>
<p></span></p></td>
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

# Acknowledgements

## Contributors

[Loren Davie](mailto:loren.davie@owasp.org) [Judy
Katzman](mailto:judy.katzman@owasp.org) [Sean
Auriti](mailto:sean.auriti@owasp.org)

# Road Map and Getting Involved

## TellTrail Roadmap

TellTrail is an ambitious initiative comprised of three layers of
effort, that work together to achieve an effect greater than the sum of
its parts:

Technology: TellTrail will develop technology for the collection,
distribution and verification of data citizen policies. It will also
create a reference implementation of a data compliance library, to serve
as an example of how to properly scrub data in response to TellTrail
data policies.

Legal: TellTrail will create a certification program, using licenses
that require the agreement of data consumers to adhere to data citizen
policies. TellTrail will retain a certification trademark, which will be
used by compliant organizations to indicate their compliance with data
policies. Finally, TellTrail will operate an auditing program to provide
a means for organizations to prove their compliance with data policies
to the public.

Advocacy: TellTrail will execute a program of advocacy, spreading the
TellTrail concept to the public and to the data industry. The goal of
the advocacy program is to educate and popularize the public in the
TellTrail approach to data privacy.

### Phase 1: Initial Tool Development

The first step for TellTrail is to develop the core technology: the
policy server, the web UI for the policy server, and the reference data
cleaning library.

We will create a requirements document for the data policy server, and a
high level technical architecture specification. Part of this will be
the definition of the Policy Request Protocol (PRP) used by compliance
tools to query the policy server for data policies. Formal definition of
the PRP will allow for independent development of the policy server, web
UI and compliance tools. The policy server will be developed in an
API-first manner, meaning all functionality will be accessible via API.
Our own web UI will use the same API. (The possible exception to this
rule is the acquisition of API access tokens.)

We select an appropriate tech stack and develop the policy server. The
purpose of the policy server is to collect and serve data citizen
policies, implementing the PRP. The policy server will be developed as
an open source project, with a proper test suite to verify its
functionality.

We will develop a web user interface for data citizens to interact with
the policy server. The main purpose of this is to allow citizens to
specify their data policy, and to associate identity information with
their policy. (Note: the policy server will not store plaintext identify
information. We will hold salted, hashed identities, which is all we
need to look up policies).

We will establish a hosting solution for the policy server and web UI.
We will deploy both on this solution.

We will develop a reference data compliance library to demonstrate
proper data cleaning techniques. The library, which will be
well-documented and open source, will contain data sets with associated
identity information. It will query the policy server via the PRP, and
scrub the affected records from the data sets in response to the
received data policies. The reference compliance library will also be an
open source project.

**Skills Required: Software Development, Operations, Security, Project
Management**

### Phase 2: Development of Legal and Governance Framework

In order for TellTrail to function, it requires a legal framework. In
this phase we would establish this framework.

We would establish a governance mechanism for TellTrail, such as a
steering committee. This body would rule on TellTrail policy decisions
moving forward. Potentially we would also establish an acting director
at this point.

We would consult with legal counsel to determine the best course of
action, vetting our plans with expert advice.

Assuming the plan was not significantly changed in response to legal
counsel, we would establish a registered certification trademark for
TellTrail with the USPTO. A certification mark (for example: “Certified
Organic”) is a trademark used by entities other than the trademark
holder. Use of the trademark is subject to license conditions, which
usually means the trademark user is adhering to standards and practices
determined by the trademark holder.

We would establish usage licenses for the trademark. Licensees would be
data consumers, data exchanges and data producers. The current concept
is that we would establish different levels of compliance, with
associated letter grades (A, B, C) not unlike NYC Department of Health
grades for restaurants. Higher grade levels indicate a higher level of
compliance, and the certification mark the licensees would use would
indicate their compliance level. The very highest levels would be
reserved for audited organizations, but because we anticipate that
significant effort is required to establish the auditing process, those
grades would not be initially offered.

We would develop documentation for the licensing process, and create
online web tools for applying for a license. The documentation would be
Creative Commons licensed, and the sign up app would be open sourced.

We would develop a database of licensed organizations, classified by
their letter grade, their role (data producer, data exchange, data
consumer), and by their industry, and by the data categories in which
they operate. This database would provide a public feedback mechanism,
in which people could provide feedback on the organizations. In this
feedback mechanism it would be possible to establish a complaint against
the organization, indicating they were not honoring their TellTrail
license. Complaints could potentially lead to an investigation by
TellTrail, with the potential of the organization’s license being
revoked.

As per the previous item, we would establish an investigation procedure
to address complaints against registered organizations.

**Skills Required: Legal, governance, software development, ops,
communications, project management**

### Phase 3: Advocacy Program

With the technical and legal frameworks in place, the next hurdle to
clear would be for TellTrail to let the world know. The goals of the
advocacy program would be:

To let the general public know about TellTrail, its approach, and why it
should be adopted.

To let companies and organizations that collect, use and sell data to
know about TellTrail, and to let them feel public pressure to comply
with its standards. Companies should be told that it is to their
competitive advantage to be TellTrail compliant.

To this end we would engage in the following efforts:

We would establish a public facing advocacy website, explaining the
TellTrail concept and why it is good for everyone in the ecosystem.

We would establish and operate social media accounts, promoting
TellTrail.

We would seek conference attendance, to directly reach the data using
industry. Conferences would be selected for their access to decision
makers in the industry.

We would conduct a public relations campaign, garnering press coverage
of TellTrail and its concept.

**Skills Required: Design, communications, social media, evangelism,
public relations.**

### Phase 4: Auditing Program

In the final phase for this road map, we would establish an Auditing
Program, a means by which compliant organizations could publicly prove
their compliance. A successful audit would grant the licensee the right
to display a better letter grade than non-audited organizations.

Since auditing would put a workload onto TellTrail, a fee would be
charged to an organization for an audit.

We would take the following actions to establish the Auditing Program:

  - Establishment of a standard by which an organization was considered
    to have passed the audit. In other words, what criteria are required
    for a pass?
  - Establish how long the the certification is valid.
  - Establishing an auditing procedure: how is an audit conducted by
    TellTrail?
  - Potentially, creation of auditing tools. Any tools created would be
    open source.
  - Establishment of an audit team to handle audits.
  - Clear online documentation of the audit process and how to apply,
    and an online application for an organization to apply for an audit.

**Skills Required: Security, communications, software development,
project management.**

## Getting Involved

# Minimum Viable Product

The following items

  - Functional and deployed data policy server, with code open sourced
  - Open source code for a reference data compliance library - to be
    used in a data exchange
  - License(s) for use of the TellTrail certification trademark
  - Website explaining, and advocating for, the TellTrail concept.

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")