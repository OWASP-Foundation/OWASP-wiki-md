# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_lab_big.jpg](_lab_big.jpg "_lab_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_webgoat_project">OWASP WebGoat Project</h2>
<h2 id="introduction">Introduction</h2>
<p><strong>WebGoat</strong> is a deliberately insecure web application maintained by <a href="http://www.owasp.org">OWASP</a> designed to teach web application security lessons. You can install and practice with WebGoat. There are other 'goats' such as <a href="http://owasp.org/index.php/WebGoatFor.Net">WebGoat for .Net</a>. In each lesson, users must demonstrate their understanding of a security issue by exploiting a real vulnerability in the WebGoat applications. For example, in one of the lessons the user must use <a href="SQL_injection" title="wikilink">SQL injection</a> to steal fake credit card numbers. The application aims to provide a realistic teaching environment, providing users with hints and code to further explain the lesson.</p>
<p>Why the name "WebGoat"? Developers should not feel bad about not knowing security. Even the best programmers make security errors. What they need is a scapegoat, right? <em>Just blame it on the 'Goat</em>!</p>
<p>To get started download the the latest release here: <a href="https://github.com/WebGoat/WebGoat/releases">https://github.com/WebGoat/WebGoat/releases</a></p>
<h2 id="webgoat_8">WebGoat 8</h2>
<p><strong>The WebGoat team is proud to present WebGoat version 8!</strong> It has been a long time since the last WebGoat 7 release,</p>
<h4 id="lessons">Lessons</h4>
<p>The most important change is we moved towards a lesson model instead of 'just hacking' we now focus on explaining from the beginning what for example a SQL injection is. Each lesson within WebGoat now contains three elements:</p>
<ul>
<li>Explain the vulnerability</li>
<li>Assignments to learn about how to exploit the vulnerability</li>
<li>Describe the possible mitigation scenarios</li>
</ul>
<p>The screenshot shows the start of the lesson. At the top of the page there is a navigation bar which shows the number of steps within the lesson. A number with a red background means there is an assignment to solve. When you successfully complete the assignment the background will become green.</p>
<p><br />
<a href="https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/assignment.png">https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/assignment.png</a><br />
<br />
As you can see we also thought about the visual appearance of our assignments. In short: WebGoat is now a <strong>teaching platform</strong> instead of just a hacking platform.</p>
<h2 id="webwolf">WebWolf</h2>
<p>We used WebGoat 8 during our workshops/training and we one of the feedback items was that sometimes an assignment was not realistic enough: it was difficult to grasp the perspective of the "hacker" vs the user. During one of the 'Project summits' at the OWASP AppSec conference we came up with the idea of creating WebWolf which would make the distinction more clear between actions you are performing as a hacker and actions are performed from the perspective of the user.</p>
<p>WebWolf is a completely separate web application which you **can** use to solve assignments. In the current version a couple of assignment/challenges use WebWolf. At the moment WebWolf is able to host files, receive e-mails and serve as a landing page. More details can be found in our new WebWolf lesson inside WebWolf.<br />
Some screenshots:<br />
<a href="https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/files.png">https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/files.png</a><br />
<a href="https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/mailbox.png">https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/mailbox.png</a> <a href="https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/requests.png">https://raw.githubusercontent.com/wiki/WebGoat/WebGoat/images/8.0-milestone/requests.png</a><br />
<br />
How to get started with WebWolf is described in a lesson within WebGoat, click [here](http://localhost:8080/WebGoat/start.mvc#lesson/WebWolfIntroduction.lesson)<br />
<br />
<strong>Big thanks to OWASP for making it possible for us to go to the Project summits at AppSec conferences</strong></p>
<h3 id="challengesctf">Challenges/CTF</h3>
<p>During a couple of conferences we were asked to host a small Capture the Flag event with WebGoat. The first one was a success so we added a separate section in WebGoat with CTF challenges. Some of the challenges have a direct connection with the lessons but a couple of them are more for fun. Having the CTF challenges has two purposes:</p>
<ul>
<li>As a teacher you can start WebGoat to host only the challenges (next release)</li>
<li>A lesson can point to a specific challenges to solve in which a user of WebGoat can test the knowledge of a vulnerability (end challenge)</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>OWASP WebGoat Project is free to use. It is licensed under the GNU General Public License version 2.0 (GPLv2)</p>
<h2 id="project_sponsors">Project Sponsors</h2>
<p>The WebGoat project is sponsored by {{MemberLinks</p></td>
<td><p>link=<a href="http://www.aspectsecurity.com">http://www.aspectsecurity.com</a></p></td>
<td><p>logo=Aspect_logo_owasp.jpg}}</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><a href="https://github.com/WebGoat/WebGoat/releases">Download WebGoat 8</a></p>
<h2 id="project_leaders">Project Leaders</h2>
<p><a href="mailto:webgoat@owasp.org">Bruce Mayhew</a><br />
<a href="mailto:nanne.baars@owasp.org">Nanne Baars</a><br />
<a href="mailto:jason.white@owasp.org">Jason White</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><a href="https://www.owasp.org/index.php/OWASP_Security_Shepherd">OWASP Security Shepherd</a></p>
<h2 id="sources">Sources</h2>
<p><a href="https://github.com/WebGoat">WebGoat on Github</a></p>
<h2 id="social_media">Social media</h2>
<p><a href="https://twitter.com/owasp_webgoat">@OWASP_WebGoat</a></p>
<h2 id="email_list">Email List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp-webgoat">Sign Up</a></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[January 2018] <a href="https://github.com/WebGoat/WebGoat/releases/">WebGoat 8 released</a></li>
<li>[November 2017] <a href="https://github.com/WebGoat/WebGoat/wiki/Milestone-release-8">Milestone release 8</a></li>
<li>[November 2016] <a href="https://github.com/WebGoat/WebGoat/releases/tag/7.1">WebGoat 7.1 released</a></li>
<li>[February 2016] WebGoat 7.0.1 released</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Midlevel_projects.png" title="Midlevel_projects.png" alt="Midlevel_projects.png" width="100" /><figcaption>Midlevel_projects.png</figcaption>
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
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Acknowledgements

## Volunteers

The WebGoat project is run by Bruce Mayhew. He can be contacted at
**webgoat AT owasp.org**. WebGoat distributions are currently maintained
on [GitHub](https://github.com/WebGoat). The WebGoat framework makes it
extremely easy to add additional lessons. We are actively seeking
developers to add new lessons as new web technologies emerge. If you are
interested in volunteering for the project, or have a comment, question,
or suggestion, please join the WebGoat [mailing
list](http://lists.owasp.org/mailman/listinfo/owasp-webgoat).

# Road Map and Getting Involved

## Road Map / Goals

The project's overall goal is to...

` Be the defacto standard web application security training environment`

In the near term, we are focused on the following tactical goals...

1.  Add educational support for secure coding practices
2.  User management: add the ability to define new users through the UI
3.  Enhance enterprise lesson tracking
4.  Attract more contributions of lessons
5.  Translate all lessons to other languages
6.  Increase ease-of-use and expand user base
7.  Update code base to Spring Boot and improve overall code quality
    (remove technical dept)
8.  Introduces category based way of displaying lessons
9.  Port old lessons to the new teaching frame

Here are the current tasks defined to help us achieve these goals

**Architectural**

  - Create a service layer (done)
  - Create plugin architecture and port all lessons to plugins (done)
  - Remove dependencies on Tomcat (done)
  - Rewrite user administration to allow better user management
    (non-hackable)
  - Fix Logoff (done)
  - Defuse all lessons to disallow inadvertent harm to user's OS

**General**

  - General security cleanup. Remove exploits that are not lesson
    specific
  - Remove non working lessons

**New Lessons**

  - Server side forward allows access to WEB-INF resources (obsolete)
  - XML attacks - Entity recursion (done)

## Getting Involved

For more information contact one of the project leads. Involvement in
the development and promotion of WebGoat is actively encouraged\! You do
not have to be a security expert in order to contribute.

If you'd like to contribute coding-wise ...

1.  Get on the WebGoat mailing list
    (http://lists.owasp.org/mailman/listinfo/owasp-webgoat)
2.  Fork one of the repo's on github:
    1.  <https://github.com/WebGoat/WebGoat>
3.  Keep you repo in sync
    (https://help.github.com/articles/syncing-a-fork/)
4.  Issue pull requests as you fix bugs, add features etc.

**Testers are always welcome/needed**. Again, log issues and features
requests at <https://github.com/WebGoat/WebGoat>. If you are a college
or university and would like to use WebGoat for classes, we'd especially
love to hear your feedback and what content/lessons you would like to
see added to the project.

**Adding content/lesssons** We are working to make adding your own
content easier and to integrate with other OWASP projects/content. We'd
love to hear from you to move this forward.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:SAMM-EG-1](Category:SAMM-EG-1 "wikilink")