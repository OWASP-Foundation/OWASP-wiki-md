# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="bywaf">ByWaf</h2>
<p>ByWaf is a command-line tool for streamlining web application firewall auditing. It consists of a command-line interpreter and a set of plugins.</p>
<h2 id="introduction">Introduction</h2>
<p>Develop an application that streamlines the auditor's job when making a Pen Test. It's main fuction is to detect, evade and display vulnerabilities. The tool works using coding methods developed by our teammembers throughout their experience.</p>
<h2 id="description">Description</h2>
<p>The Bywaf application is built on Python's built-in cmd.Cmd class. Cmd is a lightweight command interpreter loop that provides several useful facilities for the developer, including overridable hook methods and easy addition of commands and help. For the user, it offers commandline editing with readline, including automatic tab completion of commands, command options and filenames.</p>
<p>Bywaf contains a sub-classed version of Cmd called Wafterpreter, which adds some important additions, including:</p>
<p><code>  - Loading and selecting plugins</code><br />
<code>  - Getting and setting global and per-plugin options</code><br />
<code>  - Additional methods exposing functionality to the plugins</code><br />
<code>  - Backgrounding jobs, ending running jobs and querying job status</code><br />
<code>  - Loading scripts from the the command-line or within the interpreter   </code><br />
<code>  - Loading, saving, showing and clearing the command history</code></p>
<p>Wafterpreter employs a simple plugin system consisting of python modules containing commands exposed to the user (functions starting with "do_") and a dictionary of user-modifiable options ("options").</p>
<p>A number of Wafterpreter methods have been exposed to plugins, allowing them to change the interpreter's behavior and access other modules' options.</p>
<p>For notifications of changes in plugin options, Bywaf supports callback functions. The Wafterpreter will call a function for a given plugin option if it begins with "set_"; for example, for an option like "FILENAME", the Wafterpreter will search for and call a set_FILENAME(), if it exists. The Wafterpreter will also search for and call "set_default()", if it exists, for any option that does not have a specific setter function. Failing these attempts, Wafterpreter will perform a direct assignment on the plugin's option.</p>
<h2 id="licensing">Licensing</h2>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or Rafael Gil any later version.</p>
<p>This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.</p>
<p>You should have received a copy of the GNU General Public License along with this program. If not, see &lt;<a href="http://www.gnu.org/licenses/">http://www.gnu.org/licenses/</a>&gt;.</p>
<p>Contact:</p>
<p>Home: <a href="https://www.owasp.org/index.php/OWASP_Bywaf_Project">https://www.owasp.org/index.php/OWASP_Bywaf_Project</a></p>
<p>Mail: rafael.gillarios@owasp.org</p>
<p>skype: depasonic0</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_bywaf">What is ByWaf?</h2>
<p>ByWaf provides:</p>
<ul>
<li>Pentesting tool</li>
<li>Auditing tool</li>
<li>so on</li>
</ul>
<h2 id="presentation">Presentation</h2>
<p>On going...</p>
<h2 id="project_leader">Project Leader</h2>
<p>Project leader's name:</p>
<ul>
<li>Rafael Gil</li>
</ul>
<p>Development leader's name:</p>
<ul>
<li>Roey Katz</li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://github.com/depasonico/bywaf-owasp">https://github.com/depasonico/bywaf-owasp</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[15 Nov 2013] Beta release</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-breakers-small.png" title="Owasp-breakers-small.png" alt="Owasp-breakers-small.png" /><figcaption>Owasp-breakers-small.png</figcaption>
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
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# FAQs

On going...

# Acknowledgements

## Volunteers

ByWaf is developed by a worldwide team of volunteers. The primary
contributors to date have been:

Development team members:

  - Adar Grof
  - Chris Luciano

Tesnting team members:

  - Luis Brauer

## Others

  - Adan Bazan

# Road Map and Getting Involved

As of ByWaf, the priorities are:

  - Wafterpreter
  - Base plugins
  - Extra plugins

Involvement in the development and promotion of ByWaf is actively
encouraged\! You do not have to be a security expert in order to
contribute. Some of the ways you can help:

  - Development
  - Researching
  - Promoting

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Breakers](Category:OWASP_Breakers "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink")