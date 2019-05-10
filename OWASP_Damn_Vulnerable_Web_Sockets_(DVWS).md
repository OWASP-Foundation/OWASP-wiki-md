# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_damn_vulnerable_web_sockets_dvws_project">OWASP Damn Vulnerable Web Sockets (DVWS) Project</h2>
<p>Damn Vulnerable Web Sockets (DVWS) is a deliberately vulnerable and insecure web application which works on web sockets for client-server communication. It is built on PHP with Ratchet and utilizes MySQL as backend database. It allows users to test their web sockets testing skills, tools and scripts for web socket vulnerabilities. Web socket testing can be performed using <a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project">OWASP ZAP</a> and <a href="https://portswigger.net/burp/">Burp Suite</a>.</p>
<h2 id="description">Description</h2>
<p><em>Damn Vulnerable Web Sockets (DVWS)</em> is a deliberately vulnerable and insecure web application which works on web sockets for client-server communication. It is built on PHP with Ratchet and utilizes MySQL as backend database. DVWS has a number of functionalities which you commonly see in every other web application, they have been implemented in web sockets which is different from a typical web application communication.</p>
<p>The following vulnerabilities can be found:</p>
<ul>
<li>Brute Force</li>
<li>Command Execution</li>
<li>Cross-Site Request Forgery</li>
<li>File Inclusion</li>
<li>Error based SQL Injection</li>
<li>Blind SQL Injection</li>
<li>Reflected Cross-Site Scripting</li>
<li>Stored Cross-Site Scripting</li>
<li>Session Management Issues</li>
<li>Cross Origin Issue</li>
</ul>
<p>It requires the following to work properly:</p>
<ul>
<li>Apache + PHP + MySQL</li>
<li>PHP with MySQLi support</li>
<li><a href="https://github.com/ratchetphp/Ratchet">Ratchet</a></li>
<li><a href="https://github.com/bixuehujin/reactphp-mysql/">ReactPHP-MySQL</a></li>
</ul>
<p>Note: Ratchet and ReactPHP-MySQL are packaged inside DVWS. Separate installation is not required.</p>
<h2 id="licensing">Licensing</h2>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the <a href="http://www.gnu.org/licenses/agpl-3.0.html">link GNU Affero General Public License 3.0</a> as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/interference-security/DVWS/">DVWS Source Code</a></p>
<p><a href="https://github.com/interference-security/DVWS/issues">Issue Tracker</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="https://www.owasp.org/index.php/User:Abhineet">Abhineet Jayaraj</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/OWASP_Bricks">OWASP Bricks</a></li>
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
<td><figure>
<img src="Agplv3-155x51.png" title="Agplv3-155x51.png" alt="Agplv3-155x51.png" /><figcaption>Agplv3-155x51.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[08 Feb 2017] DVWS part of OWASP project.</li>
<li>[07 Jan 2017] Released DVWS on GitHub.</li>
</ul></td>
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
is key. You can also file pull requests on Github here:
<https://github.com/interference-security/DVWS/pulls>.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers and graphic designers.

## I found a bug or want a feature, where do I file it?

We are tracking issues and feature requests on GitHub. We recommend you
to file an issue or feature request here:
<https://github.com/interference-security/DVWS/issues>.

## Do you have a Docker image for DVWS?

Officially we do not have a Docker image right now. However, a user has
created an unofficial version which can be found here:
<https://hub.docker.com/r/tssoffsec/dvws/>

## I have another question, where do I ask?

We recommend using [GitHub
project](https://github.com/interference-security/DVWS/issues) or use
the contact details
[here](https://www.owasp.org/index.php/User:Abhineet).

# Acknowledgements

## Contributors

The first contributors to the project were:

  - [Abhineet Jayaraj](https://www.owasp.org/index.php/User:Abhineet) :
    Project Leader
  - *Your name can be here*.
    [Contribute](https://github.com/interference-security/DVWS)

# Screenshots and Videos

## Screenshots

![Dvws_02.png](Dvws_02.png "Dvws_02.png") ![Dvws_03.png](Dvws_03.png
"Dvws_03.png")

# Project About

__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")