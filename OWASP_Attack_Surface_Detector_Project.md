<div style="width:100%;height:120px;border:0,margin:0;overflow: hidden;">

![ASD-banner.png](ASD-banner.png "ASD-banner.png")

</div>

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p><span style="color:#ff0000"></span></p>
<h2 id="introduction">Introduction</h2>
<p><span style="color:#000000"></p>
<p><code>   During web application penetration testing, it is important to enumerate your application's attack surface. While Dynamic Application Security Testing (DAST) tools (such as </code><a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project"><code>OWASP</code><code> </code><code>ZAP</code></a><code> and </code><a href="https://portswigger.net/"><code>PortSwigger</code><code> </code><code>Burp</code><code> </code><code>Suite</code></a><code>) are good at spidering to identify application attack surfaces, they will often fail to identify unlinked endpoints, optional parameters, and parameter datatypes and name. These endpoints and parameters not found often go untested, which can leave your application open to an attacker.</code></p>
<p></span></p>
<h2 id="what_is_the_attack_surface_detector">What is the Attack Surface Detector?</h2>
<p>The Attack Surface Detector tool uncovers the endpoints of a web application, the parameters these endpoints accept, and the data type of those parameters. This includes the unlinked endpoints a spider won't find in client-side code, or optional parameters totally unused in client-side code. It also has the capability to calculate the changes in attack surface between two versions of an application.<br />
The Attack Surface Detector is available as a plugin to both ZAP and Burp Suite, and a Command Line Interface (CLI) tool is also available. The CLI tool exports the attack surface as a JSON output, which can then be used by the ZAP and Burp Suite plugin. This is helpful for cases where the source code is not provided to the penetration tester directly. The CLI tool can also be used for other custom integration where you want to discover an application attack surface or changes in the attack surface.<br />
For a quick overview of the Attack Surface Detection tool, see this YouTube video:</p>
<p>{{#ev:youtube|jUUJNRcmqwI}}</p>
<p>Below is a screenshot of the Burp Suite Attack Surface Detector plugin where you can see a list of endpoints, endpoint details, and their corresponding requests: <img src="ASD-Endpoint-Screens.png" title="fig:ASD-Endpoint-Screens.png" alt="ASD-Endpoint-Screens.png" /></p>
<h2 id="how_it_works">How it Works</h2>
<p><span style="color:#000000"> The Attack Surface Detector performs static code analyses to identify web application endpoints by parsing routes and identifying parameters (with supported languages and frameworks). This data is made available in ZAP and Burp Suite to help improve testing coverage. </span></p>
<h2 id="supported_languages_and_frameworks">Supported Languages and Frameworks</h2>
<p><span style="color:#000000"></p>
<table>
<tbody>
<tr class="odd">
<td><p><b>Java:</b></p></td>
<td><p>JSPs, Servlets, Struts, Spring MVC</p></td>
</tr>
<tr class="even">
<td><p><b>C#:</b></p></td>
<td><p>ASP.NET MVC, Web Forms</p></td>
</tr>
<tr class="odd">
<td><p><b>Ruby:</b></p></td>
<td><p>Rails</p></td>
</tr>
<tr class="even">
<td><p><b>Python:</b></p></td>
<td><p>Django</p></td>
</tr>
</tbody>
</table>
<p></span></p>
<h2 id="roadmap">Roadmap</h2>
<p>We continue to improve the attack surface detection accuracy for existing supported languages and frameworks, and we are looking to add additional language support, particularly for PHP and Python. If there are any PHP or Python developers that are looking to contribute, <a href="mailto:info@securedecisions.com">please let us know</a>.<br />
We are also looking to extend ASD for use in automated headless usage of ZAP and Burp and move the ASD ZAP plugin out of alpha classification, which requires <a href="https://github.com/zaproxy/zap-extensions/wiki/AddOnsBeta">internationalization</a>. If anyone can help, we would love your contributions.<br />
Finally, we are really interested in what the community thinks will help improve ASD and we will adjust our roadmap based on that feedback.</p>
<h2 id="getting_involved">Getting Involved</h2>
<p>Contributions to the Attack Surface Detector project are encouraged and welcome. Additions of new features and enhancements can be provided through <a href="https://github.com/secdec/">GitHub</a>. We are eager to get user feedback, so please <a href="mailto:info@securedecisions.com">reach out to us</a> or fill out this <a href="https://www.surveymonkey.com/r/D2N87GB">ASD survey</a>.</p>
<h2 id="licensing">Licensing</h2>
<p><span style="color:#000000"> The Attack Surface Detector plugin is free to use. It is licensed under the <a href="https://www.mozilla.org/en-US/MPL/2.0/">link Mozilla Public License 2.0</a>. </span></p>
<h2 id="acknowledgements">Acknowledgements</h2>
<p><span style="color:#000000"> The Attack Surface Detection project is led by <a href="https://securedecisions.com/">Secure Decisions</a> and was developed in collaboration with <a href="https://www.denimgroup.com/">Denim Group</a> under a research grant sponsored by the Department of Homeland Security (DHS) Science and Technology Directorate, Cyber Security Division (DHS S&amp;T/CSD), BAA via contract number HHSP233201600058C. </span></p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><span style="color:#ff0000"></span></p>
<p>The Attack Surface Detector is available in the ZAP Marketplace and PortSwigger BApp Store, and can be installed directly from within those tools.</p>
<h4 id="asd_plugin_for_owasp_zap">ASD Plugin for OWASP ZAP:</h4>
<p><a href="https://github.com/secdec/attack-surface-detector-zap/releases">Download ZAP Plugin</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-zap/wiki">Documentation</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-zap/issues">Submit Feedback</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-zap">GitHub Source Code</a></p>
<h4 id="asd_plugin_for_portswigger_burp">ASD Plugin for PortSwigger Burp:</h4>
<p><a href="https://github.com/secdec/attack-surface-detector-burp/releases">Download Burp Suite Plugin</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-burp/wiki">Documentation</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-burp/issues">Submit Feedback</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-burp">GitHub Source Code</a></p>
<p>====ASD Command-Line <a href="Tool:====">Tool:====</a> <a href="https://github.com/secdec/attack-surface-detector-cli/releases">Download ASD CLI</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-cli/wiki">Documentation</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-cli/issues">Submit Feedback</a></p>
<p><a href="https://github.com/secdec/attack-surface-detector-cli">GitHub Source Code</a></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li><span style="background: #66CCFF; font-size:85%;padding:2px;">24 Aug 2018</span> <a href="https://github.com/secdec/attack-surface-detector-zap/releases">Version 1.1.2 of the ASD ZAP plugin is out!</a></li>
<li><span style="background: #66CCFF; font-size:85%;padding:2px;">23 Aug 2018</span> <a href="https://github.com/secdec/attack-surface-detector-burp/releases">Version 1.1.2 of the ASD Burp Suite plugin is out!</a></li>
<li><span style="background: #66CCFF; font-size:85%;padding:2px;">20 Jul 2018</span> <a href="https://github.com/secdec/attack-surface-detector-cli/releases">Version 1.2.16 of the ASD CLI is out!</a></li>
</ul>
<h2 id="contact_us">Contact Us</h2>
<p>Project Leader: Ken Prole</p>
<p>Email: <a href="mailto:ken.prole@securedecisions.com">ken.prole@securedecisions.com</a></p>
<ul>
<li><a href="mailto:info@securedecisions.com">Email us</a></li>
<li><a href="https://twitter.com/secdec">@SecDec</a></li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<p><span style="color:#000000"></span></p>
<ul>
<li><a href="OWASP_Zed_Attack_Proxy_Project" title="wikilink">OWASP Zed Attack Proxy Project</a></li>
<li><a href="OWASP_Code_Pulse_Project" title="wikilink">OWASP Code Pulse Project</a></li>
</ul></td>
</tr>
</tbody>
</table>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")