# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="whats_ninja_pingu">What's NINJA PingU?</h2>
<p><strong>NINJA-PingU Is Not Just a Ping Utility</strong> is a free open-source high performance network scanner tool for large scale analyses. It has been designed with performance as its primary goal and developed as a framework to allow easy plugin integration.<br />
Check it out at its <strong><a href="http://owasp.github.io/NINJA-PingU/">home page</a></strong>.</p>
<h2 id="how_ninja_pingu_works">How NINJA PingU Works?</h2>
<p>NINJA PingU takes advantage of raw sockets to reduce the three-way TCP handshake latency and it's state. Directly sending IP packets also avoids the TCP stack overhead.</p>
<div align="center">
<p>{{#ev:youtube</p></td>
<td><p>_vQwPWJp8Jc?autoplay=1&amp;autohide=1&amp;&amp;rel=0&amp;start=119&amp;hd=1&amp;vq=hd720}}</p>
</div>
<p>It also implements non-blocking networking I/O in the plugin's interface by means of epoll. Each component is multithreaded and they have built-in caches to minimize synchronization points. In addition, the results persistment operations are buffered to reduce disk writes.</p>
<h2 id="why_ninja_pingu">Why NINJA PingU?</h2>
<p>It has been developed to easily allow developers build their custom plugins. Samples of those can be found in its codebase. In addition, more information about NINJA PingU can be found in the FAQ and dev pages. NINJA PingU also integrates gnuplot to automatically plot the analysis results. In addition, a custom terminator has been embedded for enhanced data visualization.</p>
<p>Read more about it in its home page at <a href="http://owasp.github.io/NINJA-PingU/">http://owasp.github.io/NINJA-PingU/</a> and its code base at <a href="https://github.com/OWASP/NINJA-PingU">https://github.com/OWASP/NINJA-PingU</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:25%;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p><strong><a href="http://owasp.github.io/NINJA-PingU/">Home Page</a></strong> <img src="NINJA_PingU_DownaloadV1.jpg" title="fig:" /><br />
<br />
mirror <a href="https://www.owasp.org/images/4/4f/NINJA-PinguV1.0.tar.gz">download</a></p>
<h2 id="features">Features</h2>
<ul>
<li>Services Identification</li>
<li>Operating System Detection</li>
<li>Embedded Devices Identification</li>
<li>High Performance Framework</li>
<li>Easily Plugin Integration</li>
</ul>
<h2 id="links">Links</h2>
<ul>
<li><a href="https://github.com/OWASP/NINJA-PingU/archive/v1.0.tar.gz">PingU V1.0</a></li>
<li><a href="http://owasp.github.io/NINJA-PingU/">Home</a></li>
<li><a href="http://owasp.github.io/NINJA-PingU/faq.html">FAQ</a></li>
<li><a href="http://owasp.github.io/NINJA-PingU/dev.html">Dev</a></li>
<li><a href="http://owasp.github.io/NINJA-PingU/plugins.html">Plugins</a></li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<ul>
<li><a href="mailto:guifre.ruiz@owasp.org">Guifre Ruiz</a></li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>GPLv3</p></td>
<td><p>valign="top" style="padding-left:25px;width25%;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>Version 1.0 released</li>
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

  - Q1
    A1

<!-- end list -->

  - Q2
    A2

# Acknowledgements

## Volunteers

NINJA Pingu is developed by a worldwide team of volunteers. The primary
contributors to date have been:

  - Guifre Ruiz

## Others

# Road Map

## Release 1.0

NINJA Pingu 1.0 has been released, which includes:

  - Host Detection.
  - Services Identification
  - Operating System Detection
  - Special Network Devices (IP Cameras and Prinerts) Identification.

## Release 1.1

The next release has not been scheduled yet.

Involvement in the development and promotion of NINJA PingU is actively
encouraged\! You do not have to be a security expert in order to
contribute.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")