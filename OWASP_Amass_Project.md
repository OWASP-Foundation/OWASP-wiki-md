# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_amass_project">OWASP Amass Project</h2>
<p>In-depth DNS Enumeration, Attack Surface Mapping and External Asset Discovery!</p>
<p>The OWASP Amass Project has developed a tool to help information security professionals perform network mapping of attack surfaces and perform external asset discovery using open source information gathering and active reconnaissance techniques.</p>
<h2 id="description">Description</h2>
<p>The OWASP Amass project is focused on DNS enumeration and network infrastructure mapping techniques. These techniques include: obtaining subdomain names by scraping web pages, accessing web APIs, querying public databases, recursive brute forcing, crawling web archives, permuting/altering DNS names, reverse DNS sweeping, and querying ASNs and netblocks associated with IP addresses. The information collected during an enumeration is used to build a graph database that maps an organization's presence on the Internet.</p>
<p>When the enumeration is complete, an Amass tool is capable of converting the results into several different formats accepted by popular network graph visualization engines. This aids analysts and infosec experts attempting to quickly identify network layout and external networks being utilized by the target organization.</p>
<p>The software is implemented in the Go programming language, and is portable across popular operating systems such as Windows, Linux, MacOS, FreeBSD, etc. The command-line tools can be obtained via several mechanisms described on the installation page, such as through a Go development environment, the release binaries, the Snap package manager for Linux systems and various packages maintained by others.</p>
<h2 id="licensing">Licensing</h2>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the <a href="https://www.apache.org/licenses/LICENSE-2.0">Apache 2.0</a> license. OWASP Amass and any contributions are Copyright © by Jeff Foley 2017.</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="Https:/github.com/OWASP/Amass_Source_Code" title="wikilink"><a href="Https://github.com/OWASP/Amass">Https://github.com/OWASP/Amass</a> Source Code</a></p>
<p><a href="Https:/github.com/OWASP/Amass/releases_What&#39;s_New_(Revision_History)" title="wikilink"><a href="Https://github.com/OWASP/Amass/releases">Https://github.com/OWASP/Amass/releases</a> What's New (Revision History)</a></p>
<p><a href="Https:/github.com/OWASP/Amass/issues_Issue_Tracker" title="wikilink"><a href="Https://github.com/OWASP/Amass/issues">Https://github.com/OWASP/Amass/issues</a> Issue Tracker</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="https://www.owasp.org/index.php/User:Caffix">Jeff Foley</a></p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[31 Jul 2019] OWASP Amass Project shows up in DarkReading "8 Free Tools to Be Showcased at Black Hat and DEF CON" article.</li>
</ul>
<ul>
<li>[1 Jun 2019] Anthony Rhodes and Jeff Foley talked about advanced features and configuration options of Amass at the Bugcrowd LevelUp 0x04 virtual conference.</li>
</ul>
<ul>
<li>[8 May 2019] Jeff Foley and Anthony Rhodes talked about Amass at the OWASP Rochester Chapter.</li>
</ul>
<ul>
<li>[1 May 2019] Jeff Foley talked about "Discovering Exposure on the Internet" on the CSIAC Webinar.</li>
</ul>
<ul>
<li>[23 Mar 2019] Jeff Foley and Anthony Rhodes talked about Amass at BSidesROC.</li>
</ul>
<ul>
<li>[8 Feb 2019] Adobe announced its integration of OWASP Amass with their Marinus project on Twitter.</li>
</ul>
<ul>
<li>[28 Nov 2018] OWASP Seattle Chapter meeting (hosted by T-Mobile) demonstration (remote) of the OWASP Amass project.</li>
</ul></td>
</tr>
</tbody>
</table>

## How can I participate in the project?

All you have to do is make the Project Leader aware of your available
time to [contribute to the
project](https://github.com/OWASP/Amass/blob/master/CONTRIBUTING.md). It
is also important to let the leader know how you would like to
contribute and pitch in to help the project meet its goals and
milestones. There are many different ways you can contribute to an OWASP
Project, but communication with the leader is key.

## If I am not a programmer can I participate in the project?

Yes, you can certainly participate in the project if you are not a
programmer. The project needs different skills and expertise at
different times during its development. Currently, we are looking for
researchers, programmers, writers, and graphic designers. See the Road
Map and Getting Involved tab for more details.

## Contributors

The Founder and Project Leader:

  - **Jeff Foley**

Contributors that have joined the project include:

  - **Mikail Tunç**

<!-- end list -->

  - **Wael Nasreddine**

<!-- end list -->

  - **Randall Marsden**

<!-- end list -->

  - **Anthony Rhodes**

<!-- end list -->

  - **Adam Zinger**

<!-- end list -->

  - **Daniel Martin**

<!-- end list -->

  - **Benjamin Murray**

<!-- end list -->

  - **Shane Ditton**

<!-- end list -->

  - **Semtex Oliviero**

<!-- end list -->

  - **Daniel Hauenstein**

<!-- end list -->

  - **John Daniel Leon**

<!-- end list -->

  - **Daniel Miessler**

<!-- end list -->

  - **Kian Jamali**

<!-- end list -->

  - **Nikos Gkogkos**

<!-- end list -->

  - **Jason Haddix**

<!-- end list -->

  - **Julio Hawthorne**

# Road Map and Getting Involved

## Roadmap

As of <strong>January, 2019, the highest priorities for the next 6
months</strong> are:

  - For version 3.0.0, update the user interfaces (UI) available
  - Feature enhancement: Allow Amass to connect to proxies
  - Feature enhancement: Inform users of what Amass will do once an
    enumeration is executed
  - Feature enhancement: Clean lists of DNS resolvers provided by users
  - Continue to update data sources that provide DNS names
  - Implement documentation regarding Amass architecture and the
    enumeration process
  - Develop slides and videos to serve as demonstration material

## Getting Involved

There are many ways you can support the OWASP Amass project. Below are
some of the roles that definitely need additional support:

### Coding

We could implement some of the later items on the roadmap sooner if some
Go network programmers wanted to join the project.

### Testing

Amass leverages concurrency and produces quite a bit of network traffic,
which can always use additional testing. Anyone interested in stressing
the software and helping to improve its quality is welcome.

### Writing

The project could currently use technical writers to join the team in
order to capture how the software works.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")