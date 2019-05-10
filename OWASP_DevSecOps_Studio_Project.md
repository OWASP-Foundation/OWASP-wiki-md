# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_devsecops_studio_project">OWASP DevSecOps Studio Project</h2>
<figure>
<img src="DevSecOps-Studio-logo.png" title="DevSecOps-Studio-logo.png" alt="DevSecOps-Studio-logo.png" /><figcaption>DevSecOps-Studio-logo.png</figcaption>
</figure>
<p>DevSecOps Studio is one of its kind, self contained DevSecOps environment/distribution to help individuals in learning DevSecOps concepts. It takes lots of efforts to setup the environment for training/demos and more often, its error prone when done manually. DevSecOps Studio is easy to get started and is mostly automatic.</p>
<p>DevSecOps Studio project aims to reduce the time to bootstrap the environment and help you in concentrating on learning/teaching DevSecOps practices.</p>
<p><strong>Features</strong>:</p>
<ul>
<li>Easy to setup environment with just one command “vagrant up”</li>
<li>Teaches Security as Code, Compliance as Code, Infrastructure as Code</li>
<li>With built-in support for CI/CD pipeline</li>
<li>OS hardening using ansible</li>
<li>Compliance as code using Inspec</li>
<li>QA security using ZAP, BDD-Security and Gauntlt</li>
<li>Static tools like bandit, brakeman, windbags, gitrob, gitsecrets</li>
<li>Security Monitoring using ELK stack.</li>
</ul>
<h2 id="description">Description</h2>
<p>DevSecOps Studio is a virtual environment to learn and teach DevSecOps concepts. It uses modern stack like vagrant, ansible, infrastructure as code, DevOps techniques to setup the environment and provides following benefits.</p>
<p><strong>Free &amp; Open Source  Software</strong></p>
<p>This project is a free and open software  to help more people learn about DevSecOps</p>
<p><strong>Easy to Setup</strong></p>
<p>Takes only few mins to setup and start using with just one command</p>
<p><strong>Reproducible</strong></p>
<p>The aim of this project is to setup reproducible DevSecOps Lab environment for learning and testing different tools.</p>
<h3 id="quick_start">Quick start</h3>
<p>Install <a href="https://www.vagrantup.com/downloads.html">Vagrant</a>, <a href="https://www.virtualbox.org/wiki/Downloads">Virtualbox</a>, <a href="http://docs.ansible.com/ansible/latest/intro_installation.html#installation">Ansible</a> and follow the below steps.</p>
<ol>
<li>Download DevSecOps-Studio Appliance (4.45 GB) from <a href="https://drive.google.com/open?id=1b3Z6BLndohpn_2HHcBfPFUpoSx78OKgG">this link</a></li>
<li>Import the above Appliance by following <a href="https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html">these step</a></li>
<li>Follow the <a href="https://github.com/teacheraio/DevSecOps-Studio/wiki">wiki</a> to embed security as part of DevOps Pipeline.</li>
</ol>
<p>Go grab some coffee while DevSecOps Studio does its job.</p>
<h3 id="detailed_instructions">Detailed Instructions</h3>
<p>More granular details and Installation instructions for various operating systems are below:</p>
<p>MacOS X: <a href="https://dso-studio.teachera.io/getting-started/#macos-installation">https://dso-studio.teachera.io/getting-started/#macos-installation</a></p>
<p>Linux: <a href="https://dso-studio.teachera.io/getting-started/#linux-installation">https://dso-studio.teachera.io/getting-started/#linux-installation</a></p>
<p>Windows: <a href="https://github.com/teacheraio/DevSecOps-Studio#windows-optional">https://github.com/teacheraio/DevSecOps-Studio#windows-optional</a></p>
<p>The environment contains the following tools used in different stages of DevSecOps.</p>
<table>
<thead>
<tr class="header">
<th><p>Technology</p></th>
<th><p>Tools</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PenTest Toolkit:</p></td>
<td><p>Nmap, Metasploit</p></td>
</tr>
<tr class="even">
<td><p>Static Analysis Tools:</p></td>
<td><p>Brakeman, bandit, findbugs</p></td>
</tr>
<tr class="odd">
<td><p>Dynamic Analysis Tools:</p></td>
<td><p>ZAP proxy, Gaunlt</p></td>
</tr>
<tr class="even">
<td><p>Hardening:</p></td>
<td><p>DevSec Ansible OS Hardening</p></td>
</tr>
<tr class="odd">
<td><p>Compliance:</p></td>
<td><p>Inspec</p></td>
</tr>
<tr class="even">
<td><p>Operating System :</p></td>
<td><p>Ubuntu Xenial (16.04)</p></td>
</tr>
<tr class="odd">
<td><p>Programming Languages:</p></td>
<td><p>Java, Python 2, Python 3, Ruby/Rails</p></td>
</tr>
<tr class="even">
<td><p>Container Technology:</p></td>
<td><p>Docker</p></td>
</tr>
<tr class="odd">
<td><p>Source Code Management:</p></td>
<td><p>Gitlab (github like system)</p></td>
</tr>
<tr class="even">
<td><p>CI Server:</p></td>
<td><p>Gitlab CI/Jenkins</p></td>
</tr>
<tr class="odd">
<td><p>Configuration Management:</p></td>
<td><p>Ansible</p></td>
</tr>
<tr class="even">
<td><p>Monitoring and Log management:</p></td>
<td><p>Elastic Search, LogStash and Kibana</p></td>
</tr>
<tr class="odd">
<td><p>Cloud Provider Utilities:</p></td>
<td><p>AWS CLI</p></td>
</tr>
<tr class="even">
<td><p>Utilities:</p></td>
<td><p>Git, Vim, curl, wget,</p></td>
</tr>
</tbody>
</table>
<h2 id="licensing">Licensing</h2>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the <a href="https://apache.org/licenses/LICENSE-2.0.html">link to Apache 2 License</a> as published by the Apache Software Foundation, either version 2 of the License, or (at your option) any later version. OWASP DevSecOps Studio and any contributions are Copyright © by Mohammed A. Imran &amp; Raghunath G 2018.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p>The documentation for this project is available online - <a href="https://dso-studio.teachera.io/">https://dso-studio.teachera.io/</a></p>
<p><a href="https://github.com/teacheraio/DevSecOps-Studio">Installation Package</a></p>
<p><a href="https://github.com/teacheraio/DevSecOps-Studio">Source Code</a></p>
<p><a href="https://github.com/teacheraio/DevSecOps-Studio">What's New (Revision History)</a></p>
<p><a href="https://dso-studio.teachera.io/">Documentation</a></p>
<p><a href="https://github.com/teacheraio/DevSecOps-Studio/wiki">Wiki Home Page</a></p>
<p><a href="https://github.com/teacheraio/DevSecOps-Studio/issues">Issue Tracker</a></p>
<p>Slide Presentation</p>
<p>Video</p>
<h2 id="project_leaders">Project Leaders</h2>
<p><a href="User:Mohammed_Imran" title="wikilink">Imran Mohammed A.</a> <a href="https://twitter.com/secfigo">Twitter</a></p>
<p><a href="https://twitter.com/raseyon">Raghunath G</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_DevSlop_Project" title="wikilink">OWASP DevSlop Project</a></li>
<li><a href="OWASP_AppSec_Pipeline" title="wikilink">OWASP AppSec Pipeline Project</a></li>
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
<td><p>rowspan="2" align="center" valign="top" width="50%"</p></td>
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
<td></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[13 Apr 2018] DevSecOps studio became OWASP Project.</li>
<li>[23 Feb 2018] DevSecOps Studio announced at DevSecCon Singapore.</li>
<li>[16 Nov 2017] DevSecOps Studio started!</li>
</ul></td>
</tr>
</tbody>
</table>

# FAQs

## **How can I follow updates on the project?**

[Imran Mohammed A. on Twitter](https://twitter.com/secfigo)

[Raghunath G on Twitter](https://twitter.com/raseyon)

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

Contribution can be done in three easy steps:

  - Fork
    [DevSecOps-Studio](https://github.com/teacheraio/DevSecOps-Studio)
    repo.
  - Contribute (documentation/features)
  - Raise a Pull Request (PR)

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator. See the Road Map and Getting Involved tab for more
details.

# Acknowledgements

## Contributors

The OWASP DevSecOps Studio Project was started by the project leaders,
Raghu and Imran.

The first contributors to the project were:

  - [Mohammed Abdul
    Mujeeb](https://www.linkedin.com/in/mohammed-abdul-mujeeb-a7295610/)
    who documented the setup behind the firewall/proxy environment
  - [Raghunath G](https://www.owasp.org/index.php/User:Clerkendweller)
    who created bash script for ubuntu/debian environment.
  - Full list of contributors can be found at [contributors
    list](https://github.com/teacheraio/DevSecOps-Studio/graphs/contributors).
  - DevSecOps Studio uses some of the ansible roles
    from [Jeff](https://github.com/geerlingguy)

# Road Map and Getting Involved

## Roadmap

As of <strong>April, 2018, the highest priorities for the next 6
months</strong> are:

  - Each add our own components to our new repo
  - Get ready for Open Security Summit
  - Release and document all work done at the Open Security Summit
  - Provision the stack on AWS using vagrant and terraform
  - Build Images using Packer and upload to vagrant cloud.
  - Build entire stack using docker for ease/
  - Add Container scanning using clair

## Getting Involved

Involvement in the development and promotion of <strong>DevSecOps
Studio</strong> is actively encouraged\! You do not have to be a
security expert or a programmer to contribute. Some of the ways you can
help are as follows:

### Coding

We could implement some of the later items on the roadmap sooner if
someone wanted to help out with unit or automated regression tests.

  - Fork
    [DevSecOps-Studio](https://github.com/teacheraio/DevSecOps-Studio)
    repo.
  - Contribute (documentation/features)
  - Raise a Pull Request (PR)

### Localization

Are you fluent in another language? Can you help translate the text
strings in the <strong>DevSecOps Studio</strong> into that language?

### Testing

Do you have a flair for finding bugs in software? We want to product a
high quality product, so any help with Quality Assurance would be
greatly appreciated. Let us know if you can offer your help.

### Feedback

Please let us know on twitter @secfigo or @raseyon for feedback about:

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

# Minimum Viable Product

The DevSecOps Studio Project must specify the minimum set of tabs a
project should have, provide some an example layout on each tab, provide
instructional text on how a project leader should modify the tab, and
give some example text that illustrates how to create an actual project.

It would also be ideal if the DevSecOps studio was translated into
different languages.

# Project About

DevSecOps Studio is one of its kind, self contained DevSecOps
environment/distribution to help individuals in learning DevSecOps
concepts. It takes lots of efforts to setup the environment for
training/demos and more often, its error prone when done manually.
DevSecOps Studio is easy to get started, mostly automatic and battle
tested during our Free Practical DevSecOps Course

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")