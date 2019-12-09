<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![Sgoatbanner.png](Sgoatbanner.png "Sgoatbanner.png")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="introduction">Introduction</h2>
<p>OWASP ServerlessGoat is a deliberately insecure realistic AWS Lambda serverless application, maintained by OWASP.</p>
<p>You can install ServerlessGoat, learn about the vulnerabilities, how to exploit them, and how to remediate each issue. The project also includes documentation explaining the issues and how they should be remediated with best-practices.</p>
<p>As serverless adoption is expected to continue growing and reach new audiences, we see the importance of education on topics such as how to build robust, secure and reliable AWS Lambda serverless applications. This project will expose developers and security practitioners to basic serverless security concepts, risks, attacks and mitigation best-practices.</p>
<p>OWASP ServerlessGoat is packaged as an AWS SAM application that's available for deployment through the <a href="https://aws.amazon.com/serverless/serverlessrepo/">AWS Serverless Application Repository</a> - this provides three important benefits:</p>
<ul>
<li>A single click installation process. No compilation, building or packaging required</li>
<li>The application uses default serverless application repository permissions (SAM policy templates), making it more realistic</li>
<li>The installation doesn't create custom IAM roles or resource policies on the account in which it is deployed in</li>
</ul>
<h2 id="disclaimer">Disclaimer</h2>
<p>OWASP does not take responsibility for the way in which any one uses the ServerlessGoat application. OWASP made the purposes of the application clear and it should not be used maliciously. We have given warnings and taken measures to prevent users from installing ServerlessGoat on production accounts.</p>
<h2 id="details">Details</h2>
<p>The application is a service which receives a URL to a Word document (with a .doc extension - Office 97-2004), and will reply with an HTML page containing the extracted text.</p>
<p>The vulnerabilities that are included are:</p>
<ul>
<li>Event-data injection (SAS-01)</li>
<li>Insecure Serverless Deployment Configuration (SAS-03)</li>
<li>Over-privileged function permissions &amp; roles (SAS-04)</li>
<li>Inadequate function monitoring and logging (SAS-05)</li>
<li>Insecure 3rd Party Dependencies (SAS-06)</li>
<li>Application layer Denial of Service (SAS-08)</li>
<li>Improper exception handling and verbose error messages (SAS-10)</li>
<li>Other undisclosed *critical* issues, as a bonus!</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>The OWASP ServerlessGoat project is free for use. You can redistribute it and/or modify it under the terms of the <a href="http://www.gnu.org/licenses/agpl-3.0.html">link GNU Affero General Public License 3.0</a> as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.</p>
<h2 id="deployment">Deployment</h2>
<p>ServerlessGoat is a simple AWS Lambda application, which serves as a MS-Word .doc file to plain text converter service. It receives a URL to a .doc file as input, and will return the text inside the document back to the API caller. ​ The application is packaged and published for deployment through the <a href="https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:761130837472:applications~serverless-goat">AWS Serverless Application Repository</a>. ​ Steps for deployment:</p>
<ol>
<li>Make sure you are logged into your AWS account</li>
<li>Click on the following link: AWS Serverless Application Repository</li>
<li>Click 'Deploy'</li>
<li>Click 'Deploy' (again)</li>
<li>Wait until you see the message 'Your application has been deployed'</li>
<li>Click on 'View CloudFormation Stack'</li>
<li>Under 'Outputs' you will find the URL for the application (WebsiteURL) ​</li>
</ol>
<p>You can find a live version of the application hosted by PureSec in the following URL: <a href="https://www.serverless-hack.me/">https://www.serverless-hack.me/</a></p>
<h2 id="roadmap">Roadmap</h2>
<ul>
<li><strong>18-December-2018</strong>: Initial release. Collect feedback from the public (<strong>done</strong>)</li>
<li><strong>1-January-2019</strong>: Beta release with additional features.</li>
<li><strong>15-January</strong>: v1.0 official launch</li>
</ul>
<h2 id="project_sponsors">Project Sponsors</h2>
<p>The project was initially developed by Ory Segal &amp; Yuri Shapira @ <a href="https://www.puresec.io/">PureSec</a>:</p>
<figure>
<img src="PureSec-Logo.png" title="PureSec-Logo.png" alt="PureSec-Logo.png" /><figcaption>PureSec-Logo.png</figcaption>
</figure>
<h2 id="cheat_sheet">Cheat Sheet</h2>
<p>You can find a full walkthrough (with spoilers of course) in the <a href="https://github.com/OWASP/Serverless-Goat/blob/master/LESSONS.md">LESSONS.md</a> file in the Git repo</p>
<h2 id="getting_involved">Getting Involved</h2>
<p>You do not have to be a security expert or a programmer to contribute. Contact the Project Leader(s) to get involved, we welcome any type of suggestions and comments.</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><strong>1-click installation</strong> on your own AWS account via the <a href="https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:761130837472:applications~serverless-goat">AWS Serverless App Repository</a></p>
<p>A <strong>live version</strong> of the application is hosted by PureSec at: <a href="https://www.serverless-hack.me/">https://www.serverless-hack.me/</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Orysegal" title="wikilink">Ory Segal</a> , <a href="https://www.puresec.io/">PureSec</a> (<a href="mailto:ory.segal@owasp.org">email</a>)</p>
<h2 id="project_mailing_list">Project Mailing List</h2>
<p>TBD</p>
<h2 id="github_repo">Github Repo</h2>
<p><a href="https://github.com/OWASP/Serverless-Goat">Project GitHub</a></p></td>
</tr>
</tbody>
</table>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")