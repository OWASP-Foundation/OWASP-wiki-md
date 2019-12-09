<div style="width:100%;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

# Main

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_serverless_top_10___first_released">OWASP Serverless Top 10 - First Released</h2>
<p>The <a href="https://www.owasp.org/images/5/5c/OWASP-Top-10-Serverless-Interpretation-en.pdf">OWASP Top 10: Serverless Interpretation</a> is now available.</p>
<h2 id="introduction">Introduction</h2>
<p>When adopting serverless technology, we eliminate the need to develop a server to manage our application. By doing so, we also pass some of the security threats to the infrastructure provider such as <a href="https://aws.amazon.com/serverless/">AWS</a>, <a href="https://azure.microsoft.com/en-us/services/functions/">Azure</a> and <a href="https://cloud.google.com/functions/">Google Cloud</a>. In addition to the many advantages of serverless application development, such as cost and scalability, some security aspects are also handed to our service provider. Serverless services run code without provisioning or managing servers and the code is executed only when needed.</p>
<p>However, even if these applications are running without a managed server, they still execute code. If this code is written in an insecure manner, it can still be vulnerable to application-level attacks.</p>
<p>The first report will examine the differences in attack vectors, security weaknesses, and the business impact of application attacks on in the serverless world, and, most importantly, the report will suggest ways to to prevent them. As we will be able to see in the report, attack and defense techniques are different from what we used to in the traditional application world.</p>
<p>After that, an open-call will be established to collect data in the wild and establishing the official Serverless Top 10 Report.</p>
<h2 id="purpose">Purpose</h2>
<p>OWASP Serverless Top 10 aims at educating practitioners and organizations about the consequences of the most common serverless application security vulnerabilities, as well as providing basic techniques to identify and protect against them.</p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP Serverless Top 10 is free to use. It is licensed under the <a href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 license</a> (CC BY-SA 4.0).</p>
<h2 id="project_sponsors">Project Sponsors</h2>
<p>The OWASP Serverless Top 10 project is sponsored by</p>
<p><img src="Protego_logo_black.png" title="fig:Protego_logo_black.png" alt="Protego_logo_black.png" />                 <img src="PureSec-Logo.png" title="fig:PureSec-Logo.png" alt="PureSec-Logo.png" />                 <img src="Whitesource_logo_rgb-02.png" title="fig:Whitesource_logo_rgb-02.png" alt="Whitesource_logo_rgb-02.png" /></p></td>
<td><h2 id="quick_downloads">Quick Downloads</h2>
<p><a href="https://www.owasp.org/images/5/5c/OWASP-Top-10-Serverless-Interpretation-en.pdf">OWASP Top 10: Serverless Interpretation</a></p>
<h2 id="presentation">Presentation</h2>
<p><a href="https://www.owasp.org/images/1/1e/OWASP_DC_SLS_Top10.pdf">Download</a></p>
<h2 id="news_events">News &amp; Events</h2>
<ul>
<li>[01 Sep 2018]: Hello World! Project was donated by <a href="https://protego.io">Protego Labs</a></li>
<li>[18 Sep 2018]: Join our <a href="https://join.slack.com/t/owasp/shared_invite/enQtNDI5MzgxMDQ2MTAwLTEyNzIzYWQ2NDZiMGIwNmJhYzYxZDJiNTM0ZmZiZmJlY2EwZmMwYjAyNmJjNzQxNzMyMWY4OTk3ZTQ0MzFhMDY">Slack-channel</a> <strong>#project-sls-top-10</strong>.</li>
<li>[22 Sep 2018]: Follow our <a href="https://github.com/OWASP/Serverless-Top-10-Project/">Git Repo</a>.</li>
<li>[25 Oct 2018]: <a href="https://www.owasp.org/images/5/5c/OWASP-Top-10-Serverless-Interpretation-en.pdf"><strong>First Release!</strong></a></li>
<li>[30 Oct 2018]: PureSec joined as sponsor</li>
<li>[02 Nov 2018]: OWASP <a href="https://owasp.blogspot.com/2018/11/serverless-top-10-added-to-project.html">Official Announcement</a></li>
<li>[13 Dec 2018]: WhiteSource joined as sponsor</li>
</ul>
<h2 id="project_leaders">Project Leaders</h2>
<p><a href="User:Tal_Mel" title="wikilink">Tal Melamed</a></p>
<p><a href="User:MarcinHoppe" title="wikilink">Marcin Hoppe</a></p>
<p><a href="Coming_soon!" title="wikilink">Coming soon!</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><a href=":Category:OWASP_Top_Ten_Project" title="wikilink">OWASP Top 10 Project</a></p></td>
</tr>
</tbody>
</table>

# Translation Efforts

  - <b>Chinese:</b> <u>[OWASP Top 10 - Serverless Interpretation
    中文版（PDF)](https://www.owasp.org/images/2/23/OWASP-Top-10-Serverless-Interpretation-cn-v1.0.pdf)</u>

项目牵头人：肖文棣、王颉（wangj@owasp.org.cn）
项目组成员：刘晓辉、李宇全、明敏、王斌（排名不分先后，按姓氏拼音排列）

# Acknowledgments

###

|                                                                                             |
| ------------------------------------------------------------------------------------------- |
| **<big>Sponsors </big>**                                                                    |
|                                                                                             |
| ![Protego_logo_black.png](Protego_logo_black.png "Protego_logo_black.png")                |
|                                                                                             |
| ![PureSec-Logo.png](PureSec-Logo.png "PureSec-Logo.png")                                    |
|                                                                                             |
| ![Whitesource_logo_rgb-02.png](Whitesource_logo_rgb-02.png "Whitesource_logo_rgb-02.png") |

|                                  |
| -------------------------------- |
| **<big>Report Reviewers </big>** |
| Assaf Hefetz, Snyk               |
| Erez Metula, AppSec Labs         |
| Erez Yalon, Checkmarx            |
| Frank M. Catucci, OWASP          |
| Guy Bernhart-Magen, Intel        |
| Hemed Gur Ary, OWASP             |
| Jeff Williams, Contrast Security |
| Jim DelGrosso, Synopsys          |
| Jochanan Sommerfeld, RDuck       |
| Kobi Lechner, INFINIDAT          |
| Limor Sylvie Kessem, IBM         |
| Marcin Hoppe, Auth0              |
| Mark Johnston, Google            |
| Martin Knobloch, OWASP           |
| Matthew Henderson, Microsoft     |
| Matteo Meucci, Minded Security   |
| Owen Pendlebury, OWASP           |
| Paco Hope, AWS                   |
| Patrick Laverty, Rapid7          |
| Rupack Ganguly, Serverless Inc.  |
| Tanya Janca, Microsoft           |
| Tash Norris, Capital One         |
| Tom Brennan, IOActive            |
| Yan Cui, DAZN                    |
| Youssef Elmalty, AWS             |

# Project Resources

## OWASP Serverless Top 10 - First Released

The [OWASP Top 10: Serverless
Interpretation](https://www.owasp.org/images/5/5c/OWASP-Top-10-Serverless-Interpretation-en.pdf)
is now available.

[GitHub repository](https://github.com/OWASP/Serverless-Top-10-Project/)

# Roadmap

# Get involved

Get involved in <strong> OWASP Serverless Top 10</strong>\!

You do not have to be a security expert or a programmer to contribute.
Contact the Project Leader(s) to get involved, we welcome any type of
suggestions and comments.

Possible ways to get contribute:

  - We are actively looking for organizations and individuals that will
    provide vulnerability prevalence data.
  - Translation efforts (later stages)
  - Assisting in the development of related tools (e.g. DVSA)

Individuals and organizations that will contribute to the project will
listed on the acknowledgments page.

Also, join our Slack Channel
[**\#project-sls-top-10**](https://join.slack.com/t/owasp/shared_invite/enQtNDI5MzgxMDQ2MTAwLTEyNzIzYWQ2NDZiMGIwNmJhYzYxZDJiNTM0ZmZiZmJlY2EwZmMwYjAyNmJjNzQxNzMyMWY4OTk3ZTQ0MzFhMDY)

GitHub [project
page](https://github.com/OWASP/Serverless-Top-10-Project/)

# About

<span style="color:#ff0000">

__NOTOC__ <headertabs />



[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")