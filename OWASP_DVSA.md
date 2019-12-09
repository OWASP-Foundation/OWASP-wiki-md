<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="dvsa">DVSA</h2>
<h3 id="a_damn_vulnerable_serverless_application">a Damn Vulnerable Serverless Application</h3>
<p>Damn Vulnerable Serverless Application (DVSA) is a deliberately vulnerable application aiming to be an aid for security professionals to test their skills and tools in a legal environment, help developers better understand the processes of securing serverless applications and to aid both students &amp; teachers to learn about serverless application security in a controlled class room environment.</p>
<p>The aim of DVSA is to practice some of the most common serverless vulnerabilities, with a simple straightforward interface.</p>
<p>Please note, there are both documented and undocumented vulnerabilities with this software. This is intentional. You are encouraged to try and discover as many issues as possible.</p>
<h2 id="disclaimer">Disclaimer</h2>
<p>We do not take responsibility for the way in which any one uses this application (DVSA). We have made the purposes of the application clear and it should not be used maliciously. We have given warnings and taken measures to prevent users from installing DVSA on to production accounts.</p>
<h2 id="license">License</h2>
<p>Damn Vulnerable Serverless Application (DVSA) is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.</p>
<p>Damn Vulnerable Serverless Application (DVSA) is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.</p>
<p>You should have received a copy of the GNU General Public License along with Damn Vulnerable Serverless Application (DVSA). If not, see <a href="http://www.gnu.org/licenses/">http://www.gnu.org/licenses/</a>.</p>
<h2 id="deployment">Deployment</h2>
<h3 id="application_repository">Application Repository</h3>
<p>Deploy DVSA from the AWS <a href="https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:889485553959:applications~DVSAServerless">Applicaiton Repository</a></p>
<p>After deployment is complete. Click on 'View CloudFormation Stack'</p>
<p>Under 'Outputs' you will find the URL for the application (DVSA Website URL)</p>
<h3 id="serverless_framework">Serverless Framework</h3>
<p>clone project from github</p>
<p><code>npm install</code></p>
<h4 id="deploy_backend">Deploy Backend</h4>
<p><code>sls deploy</code></p>
<h4 id="build_client">Build Client</h4>
<p><code>npm run-script client:build</code></p>
<h4 id="deploy_client">Deploy Client</h4>
<p><code>sls client deploy</code></p>
<h2 id="cheat_sheet">Cheat Sheet</h2>
<p>Lessons can be found <strong><a href="https://github.com/OWASP/DVSA/blob/master/AWS/LESSONS.md">here</a></strong></p>
<h2 id="roadmap">Roadmap</h2>
<ul>
<li><strong>25 DEC 2018</strong>: <a href="http://serverless.fail">http://serverless.fail</a> (official website) was launched.</li>
<li><strong>08 JAN 2019</strong>: v1.0 beta release <a href="https://github.com/owasp/dvsa">GitHub</a>)</li>
<li><strong>01 FEB 2019</strong>: v1.0 official version.</li>
</ul>
<h2 id="project_sponsors">Project Sponsors</h2>
<p>The project was initially developed by Protego Labs:</p>
<figure>
<img src="Protego_logo_black.png" title="Protego_logo_black.png" alt="Protego_logo_black.png" /><figcaption>Protego_logo_black.png</figcaption>
</figure>
<h2 id="getting_involved">Getting Involved</h2>
<p>You do not have to be a security expert or a programmer to contribute.</p>
<p>Contact the Project Leader(s) to get involved, we welcome any type of suggestions and comments.</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:889485553959:applications~DVSA">AWS Application Repository</a></p>
<p><a href="http://serverless.fail">Online version</a></p>
<p><a href="https://github.com/OWASP/DVSA">GitHub Repo</a></p>
<p><a href="https://join.slack.com/t/owasp/shared_invite/enQtNDI5MzgxMDQ2MTAwLTEyNzIzYWQ2NDZiMGIwNmJhYzYxZDJiNTM0ZmZiZmJlY2EwZmMwYjAyNmJjNzQxNzMyMWY4OTk3ZTQ0MzFhMDY">Slack <strong>#project-sls-top-10</strong></a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Tal_Mel" title="wikilink">Tal Melamed</a></p>
<h2 id="presentation">Presentation</h2>
<p>Soon!</p>
<h2 id="news_events">News &amp; Events</h2>
<ul>
<li>[25 Dec 2018]: <a href="http://serverless.fail">http://serverless.fail</a> - Launched</li>
<li>[01 Jan 2019]: Project was donated by <a href="https://protego.io">Protego Labs</a></li>
<li>[03 Jan 2019]: <a href="https://www.theregister.co.uk/2019/01/03/damn_vulnerable_serverless_application/">The Register</a></li>
<li>[04 Jan 2019]: <a href="https://sdtimes.com/cloud/sd-times-news-digest-protegos-dvsa-quicklogic-acquires-ai-company-and-iot-interoperability/">SDTimes</a></li>
<li>[07 Jan 2019]: <a href="http://www.eweek.com/security/protego-labs-boosts-serverless-security-with-open-source-project">eWEEK</a></li>
<li>[08 Jan 2019]: <a href="https://www.computerweekly.com/news/252455429/Protego-Labs-launches-serverless-app-security-tool">Computer Weekly</a></li>
<li>[08 Jan 2019]: <a href="https://technical.ly/baltimore/2019/01/08/protego-has-a-new-open-source-tool-to-provide-serverless-security-training/">Technical.ly</a></li>
<li>[09 Jan 2019]: <a href="https://github.com/owasp/dvsa">Beta release!</a></li>
</ul></td>
</tr>
</tbody>
</table>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")