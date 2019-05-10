# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_h2h_tool_project">OWASP H2H Tool Project</h2>
<p><span > H2H is an opensource project allowing to detect all entry points of web applications developped in Java. Entry point and EndPoint are defined and explained in these articles : <a href="https://digitalguardian.com/resources/data-security-knowledge-base/endpoint-detection-and-response-edr">https://digitalguardian.com/resources/data-security-knowledge-base/endpoint-detection-and-response-edr</a> and Gartner <a href="http://www.gartner.com/technology/reprints.do?id=1-26F1285&amp;ct=141223&amp;st=sb">http://www.gartner.com/technology/reprints.do?id=1-26F1285&amp;ct=141223&amp;st=sb</a>. From our point of view most web applications written in Java are made of spaghetti code and use more and more complex frameworks. H2H aims at making easier the job of detect vulnerabilities of Web applications written in Java by showing them all endpoints. That means focusing on the code, written by the project's developpers, that answers to requests (http requests, RMI calls, etc.) We could have made a list of all servlets, filters or listeners but, with frameworks such as Spring or JSF, granularity is not enough. That's because these frameworks expose their own component (servlet/listener) first, then dispatch the request (according to the uri or a context) to the code developped by the project. H2H analyze all the most used/frequent frameworks to get all the endpoints.</p>
<p>Notre objectif est de trouver 100% des points d'entrée pour améliorer la couverture de test lors des Pentest ou des audits de sécurité. Our purpose is to find 100% endpoints to improve the coverage of test during Pentests or security audit.</p>
<p></span></p>
<h2 id="description">Description</h2>
<p><span > H2H is a java agent which realizes several tasks :</p>
<ul>
<li>H2H scan the entire application and all frameworks to list all endpoints. Here is the list of components analyzed by H2H (<a href="https://github.com/highway-to-urhell/highway-to-urhell#h2h---java-jvm">framework</a>)</li>
</ul>
<ul>
<li>It is possible to activate a sensor in H2H that monitore each endpoint. For example, this monitoring allows during a Pentest to know if all scenarios have all been through all endpoints.</li>
</ul>
<ul>
<li>It is possible to activate a sensor in H2H that monitore each endpoint's performance</li>
</ul>
<p>Visualization of entry points can be done via a new url added by H2H or by the application H2H-Web <a href="https://github.com/highway-to-urhell/highway-to-urhell-web">Vizualisation Project</a></p>
<p>The project is composed ​of 2 sub-project​s​ : <a href="https://github.com/highway-to-urhell/highway-to-urhell">the Core</a> : Agent for Java project and the web <a href="https://github.com/highway-to-urhell/highway-to-urhell-web">: interface for user​-friendly</a>.</p>
<p></span></p>
<h2 id="licensing">Licensing</h2>
<p><span > H2H is a open source project with licence Apache 2. </span></p>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the <a href="http://www.gnu.org/licenses/agpl-3.0.html">link GNU Affero General Public License 3.0</a> as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. OWASP XXX and any contributions are Copyright © by {the Project Leader(s) or OWASP} {Year(s)}.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><span></p>
<p></span></p>
<p><a href="https://github.com/highway-to-urhell/">Main Page</a></p>
<p><a href="https://github.com/highway-to-urhell/highway-to-urhell">Core Project</a></p>
<p><a href="https://github.com/highway-to-urhell/highway-to-urhell-web">Vizualisation Project</a></p>
<p><a href="https://github.com/highway-to-urhell/highway-to-urhell/blob/master/README.md">Documentation</a></p>
<p><a href="https://github.com/highway-to-urhell/highway-to-urhell/issues">Issue Tracker</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Damien Kerbart<br />
Jean-Louis Boudart<br />
Guillaume Dufour<br />
Nicolas Poirier<br />
</p>
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
<li>[12 Aout 2015] First Release</li>
</ul></td>
</tr>
</tbody>
</table>

# FAQs

<span>

`   Coming soon`

</span>

## How can I participate in your project?

Fork our repository
[Github](https://github.com/highway-to-urhell/highway-to-urhell) and
Pull request \!

\== Installation

For core :
<https://github.com/highway-to-urhell/highway-to-urhell/blob/master/README.md>

For Web-Project :
<https://github.com/highway-to-urhell/highway-to-urhell-web/wiki>

# Acknowledgements

## Contributors

The first contributors to the project were:

  - \[Jean-Louis Boudart\]
  - \[Damien Kerbart\]
  - \[Guillaume Dufour\]
  - \[Nicolas Poirier\]

# Road Map and Getting Involved

  - Add Performance Counter for next Release
  - Add export configuration for Apache, F5, Nginx

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")