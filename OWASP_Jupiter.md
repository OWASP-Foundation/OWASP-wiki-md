# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>style="border-right: 1px dotted gray;padding-right:25px;" valign="top"</p></td>
<td><h2 id="introduction">Introduction</h2>
<table>
<tbody>
<tr class="odd">
<td><p>An Application Security program is more successful when coverage of its processes and tooling can be proven. Unfortunately, software inventory lists consist of some custom-written applications for an organization but also include systems and software that aren't in scope for a traditional AppSec program (Active Directory or Adobe Reader, for instance).</p>
<p>Making matters worse, organizations are constantly transforming the ways they operate. New software is being written and deployed every day:</p>
<ul>
<li>Microservices</li>
<li>Marketing sites</li>
<li>Batch jobs</li>
<li>New e-commerce features</li>
<li>Mobile apps</li>
</ul>
<p>Traditional ITAM solutions aren't tracking these custom-written applications that are the lifeblood of your organization <em>because they aren't designed to find them</em>.</p>
<p>If "who owns this?" or "did you know this was in production?" sounds familiar, you're not alone.</p></td>
</tr>
</tbody>
</table>
<h2 id="owasp_jupiter___application_inventory_management_system">OWASP Jupiter - Application Inventory Management System</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2"</p></td>
<td><p>Existing DevOps processes already know what software is being built and when it is being deployed.</p>
<p>What if we leveraged those DevOps processes to gather crucial information about the organization’s software applications?</p></td>
</tr>
<tr class="even">
<td><figure>
<img src="Jupiter.png" title="Jupiter.png" alt="Jupiter.png" /><figcaption>Jupiter.png</figcaption>
</figure></td>
<td><p>Having quality application inventory data enables:</p>
<ul>
<li>Improved insight into what is being built and deployed across the software portfolio</li>
<li>Efficient onboarding to Application Security tools and processes (static analysis, dynamic analysis, open source software component analysis, penetration testing, vulnerability management)</li>
<li>Enhanced metrics capabilities to determine tool and process coverage as well as the organization’s Application Security maturity level</li>
</ul></td>
</tr>
</tbody>
</table>
<h2 id="defining_application">Defining Application</h2>
<p>What is an application? Asking that question to five different people will probably yield five different answers. In terms of what the Jupiter Application Inventory Management System considers an application, it can be thought of as a singular module or code project unit that is built and deployed independently (aside from data or operating environment dependencies).</p>
<p>Taking another step, an application has certain attributes. It has a name. It has a codebase and thus a code repository. Where is that repository? It might have a team that supports it and somebody who is ultimately responsible for it. Who owns it? These are the types of questions Jupiter helps to solve.</p>
<p>Data collected includes:</p>
<ul>
<li>Common Name: The most widely known or current name of the application</li>
<li>Aliases: Other names the application might have or have had previously</li>
<li>Description: A brief synopsis of the application’s purpose for existing</li>
<li>Code Repository URL: The location where the application’s code is stored and versioned</li>
<li>Binary Repository URL: The location where build artifacts are stored and versioned</li>
<li>Primary Language: The most prominent programming language used in the application’s codebase</li>
<li>Secondary Languages: Additional programming languages used in the application’s codebase</li>
<li>Type: Applications might have a particular role inside of an application ecosystem, such as a microservice, user interface, batch job, etc.</li>
<li>Primary Owner: A person who has ultimate responsibility for the direction or well-being of the application</li>
<li>Secondary Owners: Other people who may be delegates of the Primary Owner</li>
<li>Business Unit: Particularly important in large organizations, this is the specific group within the organization to which the application belongs</li>
<li>Exposure: Applications have varying ways they can be exposed – internal to the organization, publicly available on the internet, or to a select group of users</li>
<li>Number of Users: The number of users (or an estimate) of the application</li>
<li>Data Classification: Many organizations have a data risk classification hierarchy and applications may fall into one of the categories</li>
<li>Deployment Environment: Because the Collector captures information at the build and deployment stages, the specific environment to which the build is destined can be recorded (e.g. QA, UAT, Production, etc.)</li>
<li>Deployment Environment URL: Correlating to the Deployment Environment, this is a URL for the application if it is a web application or service</li>
<li>Risk Level: Many organizations have formal risk levels that determine prioritization of resources aside from data categorization (can be a factor of data classification and exposure)</li>
<li>Regulations: Applicable regulations such as PCI, SOX, HIPPA, etc. can be listed</li>
<li>Chat Channel: Many application development and support teams have a way to communicate with each other and to collaborate within their organization such as Slack or Glip</li>
<li>Agile Scrum Board URL: Development teams often keep a list of their in-flight work and backlog in a project tracking system such as Jira or Redmine</li>
<li>Build Server URL: The CI server from which the recorded build or deployment originated</li>
<li>Age: Applications can have a long life and understanding a given application’s age can help determine risk and gauge other implications</li>
<li>Lifecycle Stage: Similar to age, an application can be New, in a Maintenance steady-state, or in Retirement</li>
<li>Last Deployment Date: The last date on which the application was deployed</li>
</ul>
<h2 id="high_level_design">High Level Design</h2>
<table>
<tbody>
<tr class="odd">
<td><p>Jupiter is a microservice-based solution that consists of several components.</p>
<p>First, the <strong>Jupiter Collector Service</strong> can gather primitive inventory data (antecessors) directly from DevOps tools, such as continuous integration servers like Jenkins via the <strong>Jupiter Collector Plugin</strong>, when the software is built and deployed.</p>
<p>The <strong>Inventory Management Console</strong> connects to the collector service and facilitates enrichment of the antecessor data into “gold records” representing an application.  These records are stored by the <strong>Curated Inventory Service</strong> via REST API or through the management console.</p></td>
<td><figure>
<img src="Jupiter_HLD.png" title="Jupiter_HLD.png" alt="Jupiter_HLD.png" /><figcaption>Jupiter_HLD.png</figcaption>
</figure></td>
</tr>
</tbody>
</table>
<h2 id="inventory_management_console_coming_soon">Inventory Management Console (COMING SOON)</h2>
<p>login.png | Jupiter Inventory Management Console Home antecessors.png |Manage Antecessors collectors.png |Manage Collector Instances</p></td>
<td><p>style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;" valign="top"</p>
<h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/xpert98?tab=repositories">Source Code</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Matt Stanchek</p>
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
<td><p>rowspan="2" width="50%" valign="top" align="center"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td><p>width="50%" valign="top" align="center"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center"</p></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Roadmap

## Jupiter Application Inventory Management System Roadmap

1.  Collector Service
    1.  Authentication
          - Utilize Auth Service for JWT validation
    2.  Authorization
          - Based on JWT payload, enforce restrictions on CRUD
            operations
    3.  Database Connectivity
          - Update Mongo connection code to update deprecated connection
            method
    4.  Input Validation
          - Input length checks
          - Input type checks
    5.  Data Fields
          - Enable data fields beyond Common Name and Primary Owner
    6.  Containerization
          - Prepare Dockerfile
          - Build Docker container
          - Deploy and test Docker container
2.  Curated Inventory Service
    1.  Authentication
          - Utilize Auth Service for JWT validation
    2.  Authorization
          - Based on JWT payload, enforce restrictions on CRUD
            operations
    3.  Input Validation
          - Input length checks
          - Input type checks
    4.  Data Fields
          - Enable Application-specific data fields beyond Common Name
            and Primary Owner
          - Enable capture of Collector Service instance ID
    5.  Data Integrity
          - Restrict Common Name to unique values
    6.  Containerization
          - Prepare Dockerfile
          - Build Docker container
          - Deploy and test Docker container
3.  Auth Service
    1.  Authentication
        1.  Enable LDAP authentication
              - Build LDAP integration capabilities
              - Based on successful username/password LDAP
                authentication, provide time-limited JSON Web Token for
                subsequent requests
              - Enable facility to validate expiration of tokens and
                deny access to expired tokens
    2.  Authentication
          - Define user roles (administrator, reader, creator/updater)
          - Enable issuance of tokens that restrict access based on user
            role
4.  Management Console
    1.  Base Architecture
        1.  Add Local SQLite Database
              - Enable saving of configuration and preferences
    2.  Authentication
        1.  Collector Services
              - Build an interface to allow configuration of Collector
                Services
        2.  Curated Inventory Service
              - Build an interface to allow configuration of Curated
                Inventory Service
    3.  Data Fields
          - Enable Application-specific data fields beyond Common Name
            and Primary Owner
    4.  External Integrations
          -
            Consistent naming across multiple external Application
            Security tools will allow for greater future automation and
            reporting as well as utilization.
        <!-- end list -->
          - Enable set up of Application in Fortify Software Security
            Center
          - Enable set up of Application in OWASP Dependency-Track
          - Enable set up of Application in OWASP Defect Dojo
          - Enable set up of Application in OWASP SecurityRAT
    5.  User Experience
        1.  Antecessors
              - Aggregate all Collectors’ data in available Antecessors
                list when there is more than one Collector Service
                defined
5.  Jenkins Collector Plugin
    1.  Input Validation
          - Input length checks
          - Input type checks
    2.  Connectivity Validation
          - Add a “Test Connection…” button to the Global config screen
            to test the Collector URL and token
    3.  Data Fields
          - Enable Application-specific data fields beyond Common Name
            and Primary Owner under “Advanced”

# About Jupiter

## FAQ

Q: Why is this project named "Jupiter"?

A: In *2001: A Space Odyssey*, the Discovery One embarked on a mission
to investigate the signal sent from the monolith on the Moon to Jupiter.
In *2010: The Year We Make Contact*, the crews of the Discovery and
Leonov witness countless monoliths emerge from Jupiter before it is
converted into a star. Aside from the cool sci-fi reference, there is an
analog to what this project is for -- to start with a small amount of
information about software applications in an organization's portfolio
and build upon that knowledge to find more.

__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")