# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_flagship_big.jpg](_flagship_big.jpg "_flagship_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_dependency_track">OWASP Dependency-Track</h2>
<p>Dependency-Track is an intelligent Software <a href="Component_Analysis" title="wikilink">Supply Chain Component Analysis</a> platform that allows organizations to identify and reduce risk from the use of third-party and open source components. Dependency-Track takes a unique and highly beneficial approach by leveraging the capabilities of Software Bill-of-Materials (SBOM). This approach provides capabilities that traditional Software Composition Analysis (SCA) solutions cannot achieve.</p>
<p>Dependency-Track monitors component usage across all versions of every application in its portfolio in order to proactively identify risk across an organization. The platform has an API-first design and is ideal for use in Continuous Integration (CI) and Continuous Delivery (CD) environments.</p>
<figure>
<img src="Integrations.png" title="Integrations.png" alt="Integrations.png" /><figcaption>Integrations.png</figcaption>
</figure>
<h2 id="features">Features</h2>
<ul>
<li>Tracks application, library, framework, operating system, and hardware components</li>
<li>Tracks component usage across all version of every application in an organizations portfolio</li>
<li>Identifies multiple forms of risk including
<ul>
<li>Components with known vulnerabilities</li>
<li>Out-of-date components</li>
<li>Modified components</li>
<li>License risk</li>
<li>More coming soon...</li>
</ul></li>
<li>Integrates with multiple sources of vulnerability intelligence including:
<ul>
<li><a href="https://nvd.nist.gov">National Vulnerability Database</a> (NVD)</li>
<li><a href="https://www.npmjs.com/advisories">NPM Public Advisories</a></li>
<li><a href="https://ossindex.sonatype.org">Sonatype OSS Index</a></li>
<li><a href="https://vulndb.cyberriskanalytics.com">VulnDB</a> from <a href="https://www.riskbasedsecurity.com">Risk Based Security</a></li>
<li>More coming soon.</li>
</ul></li>
<li>Ecosystem agnostic with built-in repository support for:
<ul>
<li>Ruby Gems</li>
<li>Maven</li>
<li>NPM</li>
<li>NuGet</li>
<li>Python (Pypi)</li>
<li>More coming soon.</li>
</ul></li>
<li>Includes a comprehensive auditing workflow for triaging results</li>
<li>Configurable notifications supporting Slack, Microsoft Teams, Webhooks, and Email</li>
<li>Supports standardized SPDX license ID’s and tracks license use by component</li>
<li>Supports importing <a href="https://cyclonedx.org">CycloneDX</a> and <a href="https://spdx.org/">SPDX</a> Software Bill-of-Materials (SBOM) formats</li>
<li>Easy to read metrics for components, projects, and portfolio</li>
<li>Native support for Kenna Security, Fortify SSC, and ThreadFix</li>
<li>API-first design facilitates easy integration with other systems</li>
<li>API documentation available in OpenAPI format</li>
<li>Supports internally managed users, Active Directory/LDAP, and API Keys</li>
<li>Simple to install and configure. Get up and running in just a few minutes</li>
</ul>
<h2 id="distributions">Distributions</h2>
<p>Dependency-Track supports the following three deployment options:</p>
<ul>
<li>Executable WAR</li>
<li>Conventional WAR</li>
<li>Docker container</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>OWASP Dependency-Track is licensed under the <a href="https://www.apache.org/licenses/LICENSE-2.0">Apache 2.0 license</a>.</p></td>
<td><figure>
<img src="Dependency-Track-logo-300x100.png" title="Dependency-Track-logo-300x100.png" alt="Dependency-Track-logo-300x100.png" width="250" /><figcaption>Dependency-Track-logo-300x100.png</figcaption>
</figure>
<h2 id="quick_download">Quick Download</h2>
<p>Ready-to-deploy distributions are available from the Dependency-Track website</p>
<ul>
<li><a href="https://dependencytrack.org/">Website</a></li>
<li><a href="https://github.com/DependencyTrack">Source Code</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[28 Sep 2019] v3.6.0 Released</li>
<li>[17 Jul 2019] v3.5.1 Released</li>
<li>[07 Jun 2019] v3.5.0 Released</li>
<li>[16 Apr 2019] v3.4.1 Released</li>
<li>[22 Dec 2018] v3.4.0 Released</li>
</ul>
<h2 id="community_integrations">Community Integrations</h2>
<ul>
<li><a href="https://github.com/ozonru/dtrack-audit">dtrack-audit</a></li>
<li><a href="https://github.com/pmckeown/dependency-track-maven-plugin">Dependency-Track Maven plugin</a></li>
</ul>
<h2 id="media">Media</h2>
<p><a href="https://www.youtube.com/channel/UC8xdttysl3gNAQYvk1J9Efg">OWASP Dependency-Track Channel (YouTube)</a></p>
<p><a href="https://www.appsecpodcast.org/2018/04/12/dependency-check-and-dependency-track-s03e13/">AppSec Podcast (S03E13)</a></p>
<h2 id="documentation">Documentation</h2>
<p><a href="https://docs.dependencytrack.org">Dependency-Track Documentation</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Steve_Springett" title="wikilink">Steve Springett</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_Dependency_Check" title="wikilink">OWASP Dependency-Check</a></li>
</ul></td>
</tr>
</tbody>
</table>

# Screenshots

[File:Dependency-Track_Screenshot-_Dashboard.png|Dashboard](File:Dependency-Track_Screenshot-_Dashboard.png%7CDashboard)
[File:Dependency-Track_Screenshot_-_Projects.png|Projects](File:Dependency-Track_Screenshot_-_Projects.png%7CProjects)
[File:Dependency-Track_Screenshot_-_Vulnerable_Component.png|Vulnerable](File:Dependency-Track_Screenshot_-_Vulnerable_Component.png%7CVulnerable)
Component
[File:Dependency-Track_Screenshot_-_Vulnerability.png|Vulnerability](File:Dependency-Track_Screenshot_-_Vulnerability.png%7CVulnerability)

# Acknowledgements

This project would not be possible without the existence of the
[OWASP_Dependency_Check](OWASP_Dependency_Check "wikilink") project.
Special thanks to Jeremy Long and the Dependency-Check core team for
their hard work.

## Dependency-Track Core Team

  - [Steve Springett](User:Steve_Springett "wikilink")

## Sponsors

Dependency-Track is created by a worldwide group of volunteers who have
dedicated their time, talent, or provided financial support to the
project.

The project would like to acknowledge and thank the following
organizations that have helped move this project forward

  - [Risk Based Security](https://www.riskbasedsecurity.com/)

OWASP Dependency-Track is an open source project, created by people who
believe that the knowledge of using vulnerable components should be
accessible to anyone with a desire to know. By supporting this project,
you'll allow the team to outsource testing, infrastructure, further
research and development efforts, and engage in outreach to various
communities that would benefit from this technology.

{{\#widget:PayPal Donation |target=_blank |budget=OWASP
Dependency-Track }}

# Road Map

Dependency-Track uses [GitHub
milestones](https://github.com/DependencyTrack/dependency-track/milestones)
to track roadmaps and future releases.

# Community

Feedback from the community is always encouraged. Tell us what you like,
what needs to be improved, and what features would be beneficial to your
organization.

Three ways to get involved:

  - [GitHub
    Issues](https://github.com/DependencyTrack/dependency-track/issues)
    - Collaborate on open issues
  - [Gitter](https://gitter.im/dependency-track/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
    - Chatroom built around GitHub
  - [Slack](https://owasp.slack.com/messages/proj-dependency-track) -
    The Dependency-Track Slack channel

Pull requests are highly encouraged. No contribution is too small. Do
you know how to create test cases? Help us out. Want to write (or
correct) some docs? Yes please... All contributions are appreciated.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink") [Category:Flagship
Projects](Category:Flagship_Projects "wikilink")