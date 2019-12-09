<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="about_docker_top_10">About Docker Top 10</h2>
<p>The OWASP Docker Top 10 project is giving you ten bullet points to plan and implement a secure docker container environment. Those 10 points are ordered by relevance. They don't represent risks as each single point in the OWASP Top 10, they represent security controls. The controls range from baseline security to more advanced controls, depending on your security requirements.</p>
<p>You should use it as a</p>
<ul>
<li>guidance in the design phase as a system specification or</li>
<li>for auditing a docker environment,</li>
<li>also for procurement it could provide a basis for specifying requirements in contracts.</li>
</ul>
<h2 id="where_is_it_getting_involved">Where is it? / Getting Involved</h2>
<p>The development and discussions take place @ <a href="https://github.com/OWASP/Docker-Security">Github</a>. After release you will find the released version also here.</p>
<h2 id="description">Description</h2>
<p><span style="color:#ff0000"></p>
<p>This guide is for developers, auditors, architects, system and networking engineers. As indicated above you can also use this guide for externals to add formal technical requirements in your contract. The information security officer should have some interest too to meet security requirements.</p>
<p>The 10 bullet points here are about system and network security and also architecture. As a developer you don't have to be an expert in those -- that's what this guide is for. But as indicated above best is to start thinking about those points early. Please do not just start building it.</p>
<p>Security in Docker environments seemed often to be misunderstood. It was/is a highly disputed matter what the threats are supposed to be. So before diving into the Docker Top 10 bullet points, the threads are modeled. It not only helps understanding the security impacts but also gives you the ability to prioritize your task.</p>
<p></span

== Why not "Container Security" ==

Albeit the name of this project carries the word "Docker", it also can be used with little abstraction for other containment solutions. Docker is as of now the most popular one, so the in-depth details are focusing for now on Docker. This could change later.

== A single container? ==

If you run more than 3 containers you probably have an orchestration solution to manage them. '''Specific''' security pitfalls of those are currently beyond the scope of this document. That doesn't mean that this guide just looking at one or a few containers managed manually -- on the contrary. It means only that we're looking at the containers including their networking and their host systems in such an orchestrated environment and not on special pitfalls of e.g. ''Kubernetes'', ''Swarm'', ''Mesos'' or'' OpenShift''.

==Licensing==

The Docker OWASP Top 10 document is licensed under the [https://creativecommons.org/licenses/by-nc-sa/4.0/ Creative Commons Attribution-ShareAlike 4.0 license] (CC BY-NC-SA 4.0). Some rights reserved.

[[File:CC-BY-SA-NC.4.0.size88x31.png|link=https://creativecommons.org/licenses/by-nc-sa/4.0/]]

==Roadmap==
The highest priorities for the next months are:
<strong></p>
<ul>
<li>Publish and work on a first draft of the documentation</li>
<li>Complete this first draft</li>
<li>Get other people involved to review the documentation and provide feedback</li>
<li>Incorporate feedback into the documentation</li>
<li>First Release</li>
</ul>
<p></strong></p>
<p>Subsequent Releases will add <strong></p>
<ul>
<li>Go from Draft to Release</li>
<li>Being promoted from an Incubator Project to a Lab Project</li>
</ul>
<p></strong></p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><strong>Github</strong><br />
* See <a href="https://github.com/OWASP/Docker-Security">Github</a><br />
<strong>Slides</strong><br />
* Dirk Wetter: (<a href="https://www.owasp.org/images/f/fd/Dirk_Wetter_-_Docker_Top10-OWASP_KA.pdf">long version, talk in Karlsruhe</a>), (<a href="https://www.owasp.org/images/7/7e/Dirk_Wetter_-_Docker_Security_GOD2018.pdf">short version @ German OWASP Day 2018</a>),</p>
<ul>
<li>Dirk Wetter, older talks from <a href="https://www.owasp.org/images/1/17/Dirk_Wetter_-_Docker_Security_Brussels.pdf">Belgium Chapter Meeting</a>, <a href="https://2018.appsec.eu/presos/DevOps_Docker_201_Security_Dirk-Wetter_AppSecEU2018.pdf">OWASP AppSec Europe 2018</a></li>
</ul>
<ul>
<li>Jack Mannino and Abdullah Munawar: <a href="https://2018.appsec.eu/presos/DevOps_Securing-Containers_Jack-Mannino_Abdullah-Munawar_AppSecEU2018.pptx">Slides of Presentation</a> at OWASP AppSec Europe 2018</li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<p>Dirk Wetter</p>
<h2 id="related_projects">Related Projects</h2>
<p>&lt;!--</p>
<ul>
<li><a href="OWASP_Code_Project_Template" title="wikilink">OWASP_Code_Project_Template</a></li>
<li><a href="OWASP_Tool_Project_Template" title="wikilink">OWASP_Tool_Project_Template</a></li>
</ul>
<p>--?</p></td>
</tr>
</tbody>
</table>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")