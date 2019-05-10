# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_assimilation_project_summary">OWASP Assimilation Project Summary</h2>
<p>Many people compare securing systems against attackers as a form of warfare. In <em>The Art of War</em>, Sun Tzu said <a href="https://en.wikiquote.org/wiki/Sun_Tzu#/media/File:Enchoen27n3200.jpg">"If you know your enemies and know yourself, you will not be imperiled in a hundred battles"</a>. The Assimilation software helps you know yourself - your systems, networks, configurations in great detail, and then keeps it all that information <em>continually</em> up to date in a graph-based Configuration Management Database. This information is useful regardless of your threat model.</p>
<p>We then leverage this knowledge to compare your systems against hardening best practices, to validate checksums of files, look for vulnerable versions of packages, and help you triage your way to better security.</p>
<h2 id="description">Description</h2>
<p>The Assimilation Project tracks many aspects of system configuration and security and compares them against best practices in near-real-time.</p>
<p>Here are a few of the kinds of things we track for you:</p>
<ul>
<li>IP and MAC addresses</li>
<li>Services - including details on which ports, which binaries and what arguments, user id, group id, current directory</li>
<li>Client connections (same details as above)</li>
<li>Security-sensitive configuration details</li>
<li>Versions of packages</li>
<li>Checksums of network-facing binaries, libraries, and JARs.</li>
</ul>
<p>This is all done in a <a href="http://assimilationsystems.com/2015/04/14/scalability-from-doing-nothing/">highly scalable</a> way which cannot set off network security alarms and requires minimal human configuration.</p>
<p>In addition, we continually evaluate system configurations against best practices from the <a href="http://ITBestPractices.info">IT Best Practices</a> project and compute risk scores for servers based on how they compare to security best practices, and evaluations of what areas and systems are at greater risk. Since everything is stored in the <a href="http://neo4j.org">Neo4J</a> graph database, visualizations of things like your <a href="http://assimilationsystems.com/2016/02/22/attack-surface/">attack surface</a> are natural and straightforward.</p>
<p>The project includes <a href="http://assimilationsystems.com/2015/12/07/assimilation-event-api-overview/">event APIs</a> and <a href="http://assimilationsystems.com/2014/04/02/new-command-line-queries-in-the-assimilation-software/">canned queries</a>.</p>
<h2 id="licensing">Licensing</h2>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the GNU GPL v3 License as published by the Free Software Foundation.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/assimilation/assimilation-official/blob/master/buildtools/installme">Universal Installation Script</a></p>
<p><a href="http://bit.ly/assimreleases">Released Packages</a></p>
<p><a href="https://github.com/assimilation/assimilation-official">Source Code</a></p>
<p><a href="https://github.com/assimilation/assimilation-official/releases">Release History</a></p>
<p><a href="http://AssimProj.org/">Project Home Page and Documentation</a></p>
<p><a href="https://trello.com/b/98QrdEK1/issues-bugs">Issue Tracker</a></p>
<p><a href="https://speakerdeck.com/ossalanr">Slide Presentations</a></p>
<p><a href="http://assimilationsystems.com/category/videos/">Talk Videos</a></p>
<p><a href="http://assimilationsystems.com/category/getting-started/">Getting Started articles</a></p>
<p><a href="http://assimilationsystems.com/category/how-to/">How-To articles</a></p>
<p><a href="http://assimilationsystems.com/category/blog/">Blog</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Project leader: <a href="mailto:AlanR@AssimilationSystems.com">Alan Robertson</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><span style="color:#ff0000"></p>
<p><code>   This is where you can link to other OWASP Projects that are similar to yours. </code></p>
<p></span></p>
<ul>
<li><a href="OWASP_Code_Project_Template" title="wikilink">OWASP_Code_Project_Template</a></li>
<li><a href="OWASP_Documentation_Project_Template" title="wikilink">OWASP_Documentation_Project_Template</a></li>
<li>External project: <a href="http://ITBestPractices.info/">IT Best Practices project</a> - provides the definitions of the best practices which we use to evaluate your systems.</li>
</ul>
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
<td><figure>
<img src="Agplv3-155x51.png" title="Agplv3-155x51.png" alt="Agplv3-155x51.png" /><figcaption>Agplv3-155x51.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>Project <a href="http://assimilationsystems.com/assimevents/">events page</a>.</li>
<li><a href="http://lists.community.tummy.com/cgi-bin/mailman/listinfo/assimilation">mailing list</a></li>
<li>IRC: #assimilation on irc.freenode.net</li>
</ul></td>
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
administrator. See the Road Map and Getting Involved tab for more
details.

# Acknowledgements

## Contributors

The OWASP Assimilation Project is developed by a worldwide team of
volunteers.

The first contributors to the project were:

  - Alan Robertson
  - Carrie Oswald
  - Dave Quigley
  - Roger Massey

# Road Map and Getting Involved

## Roadmap

Future plans include:

  - Expanding the best practices we cover
  - Making it easy to see which machines are in need of security patches
    - take that into account with the security scores.
  - Taking better advantage of checksums - take that into account with
    security scores.
  - Many more discovery agents. These turn out to be typically pretty
    simple, and can be written with very little knowledge of the project
    internals. They have a very shallow learning curve to get started.

There is also a page that describes the future thinking as of August
2016 [on our latest roadmap blog
post](http://assimilationsystems.com/2016/08/06/assimilation-2016-security-roadmap/).

There are a variety of roadmap-related artifacts on the project's Trello
boards. You can find them here:

  - [feature
    board](https://trello.com/b/KKs4rI8g/assimilation-features-current-and-desired)
  - [Issue/bug/feature board](https://trello.com/b/98QrdEK1/issues-bugs)

You should also consider contributing to our sister project the [IT Best
Practices project](http://IIBestPractices.info) - since that's where the
best practices we implement are defined.

You can also read more about the project's "current thinking" in our
[mailing list
archives](http://lists.community.tummy.com/pipermail/assimilation/).

## Getting Involved

Involvement in the development and promotion of <strong>Assimilation
Project</strong> is actively encouraged\! You do not have to be a
security expert or a programmer to contribute. Some of the ways you can
help are as follows:

### Coding

The software is intended to be able to run on any POSIX system and
Microsoft Windows. Currently it runs on at least a dozen different Linux
versions. We are actively seeking people to do ports to other systems -
particularly Windows.

The project has a [contributor
agreement](http://linux-ha.org/source-doc/assimilation/html/_contributing.html#WhyAContributorAgreement)
for things that go into source control.

So far, the code is written in the following languages:

  - C - core nanoprobe code and communications libraries
  - Python - CMA code and a few utilities
  - POSIX shell - scripts to do discovery and monitoring
  - C\# - one Windows discovery agent - should be rewritten in
    PowerShell
  - PowerShell - *future* Windows discovery agents

### Localization

There is significant opportunity for localization in our sister [IT
BestPractices](http://ITBestPractices.info) project, and some in our
[canned
queries](https://github.com/assimilation/assimilation-official/tree/master/queries).
All strings in the project are UTF-8.

### Testing

We have need both for human testers - people to do trials and provide
feedback, and people to enhance our automated testing environment. Most
of the automated testing is in Python, with some in the shell, and C. We
have a unique and powerful system-level testing methodology which was
[described on our
blog](http://assimilationsystems.com/2016/05/24/testing-distributed-systems-with-fuzzy-monkey-testing/).
The source code for these system-level tests can be found [in this
directory](https://github.com/assimilation/assimilation-official/tree/master/cma/systemtests)
on GitHub.

### Building and Related Topics

We need help getting properly signed RPM and .deb repositories set up
for the various versions of Linux we have set up. We have some basic
continuous integration set up, and a good set of build procedures for
64-bit versions of Linux. But things could always be better and release
production more automated.

### Feedback

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

# Minimum Viable Product

The OWASP Assimilation Project needs to have the following capabilities
in order to be considered minimally viable:

  - Discovery of IP and MAC addresses through ARP
  - Discovery of services offered on each system including IP:port
    combinations and binaries and arguments for the services
  - Discovery of packages and package versions installed on the system
    (OS, pip, GEMs, NPM, etc).
  - Discovery of checksums of network-facing binaries (discovered by
    services above)
  - Discovery of security-related settings
  - Comparision of security-related settings against best practices from
    the IT Best Practices project
  - A dozen or more database queries to retrieve the information above
  - Event API so that notifications can be performed as things change or
    are added in the system

The project has had all these capabilities since 2015.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")