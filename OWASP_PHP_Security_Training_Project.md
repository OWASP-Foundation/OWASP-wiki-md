# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_php_security_training_project">OWASP PHP Security Training Project</h2>
<p>OWASP PHP Security Training Project is...</p>
<h2 id="introduction">Introduction</h2>
<p>The goal of this project is to create an interactive training system, consisting of several units, for PHP developers. Every unit is divided in an attack and a defense part.</p>
<h2 id="description">Description</h2>
<p>The goal of this project is to create an interactive training system, consisting of several units, for PHP developers. Every unit shall be divided in an attack and a defense part. When working through the attack part, the developers will have to strike against a vulnerable application. Through this, they will learn to think like a hacker. Weaknesses to detect and exploit might be XSS, CSRF or SQL Injection, which are listed in the OWASP top 10. While viewing the defense part, the user shall be introduced to securing the vulnerable application, for example by safeguarding the code.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP PHP Security Training Project is free to use. It is licensed under the GNU GPL v3 License, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_php_security_training">What is PHP Security Training</h2>
<p>OWASP PHP Security Training Project provides:</p>
<ul>
<li>VirtualBox-Machine</li>
<li>Debian Package</li>
</ul>
<h2 id="informations">Informations</h2>
<p>Paper: <a href="http://files.timo-pagel.de/php-security-trainig-system/paper.pdf">http://files.timo-pagel.de/php-security-trainig-system/paper.pdf</a> Poster: <a href="http://files.timo-pagel.de/php-security-trainig-system/poster2.pdf">http://files.timo-pagel.de/php-security-trainig-system/poster2.pdf</a> Presentation: <a href="http://files.timo-pagel.de/vortraege/security/phpug_php_security_training_system.pdf">http://files.timo-pagel.de/vortraege/security/phpug_php_security_training_system.pdf</a> (German)</p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="mailto:timo.pagel@owasp.org">Timo Pagel</a></p>
<h2 id="related_projects">Related Projects</h2>
<h2 id="ohloh">Ohloh</h2></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="http://files.timo-pagel.de/php-security-trainig-system/">http://files.timo-pagel.de/php-security-trainig-system/</a></li>
</ul>
<h2 id="source_code">Source Code</h2>
<ul>
<li><a href="https://bitbucket.org/tpagel/php-security-training-system">https://bitbucket.org/tpagel/php-security-training-system</a></li>
</ul>
<h2 id="email_list">Email List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp_php_security_training_project">Sign up</a></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[21 Jan 2015] Poster and Paper is available.</li>
</ul>
<h2 id="in_print">In Print</h2>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="New_projects.png" title="New_projects.png" alt="New_projects.png" width="100" /><figcaption>New_projects.png</figcaption>
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

# FAQs

  - How to install OWASP PSeTS?

<!-- end list -->

    wget http://files.timo-pagel.de/php-security-trainig-system/php-security-training-system-vagrant.tar
    tar xfv php-security-training-system-vagrant.tar
    cd vagrant/
    vagrant plugin install vagrant-hostsupdater
    vagrant up
    goto http://guidesystem.local/ in your browser

  - In which languages is OWASP PSeTS translated?
    So far, it is only available in German.

# Acknowledgements

## Volunteers

XXX is developed by a worldwide team of volunteers. The primary
contributors to date have been:

  - xxx
  - xxx

## Others

  - xxx
  - xxx

# Road Map and Getting Involved

As of July, the priorities are:

  - Internationalization of existing units
  - UnitTests
  - Enhancement of existing units
  - Creation of more units
  - Java integration
  - Error message: Enhance details
  - Point system
  - Track clicks on the help button/solution to asses the quality of a
    unit
  - Possibility to reset single units

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")