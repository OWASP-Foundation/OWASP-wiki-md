<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

If you are looking for the [OWASP Security Logging
Project](OWASP_Security_Logging_Project "wikilink"), it is
[here](OWASP_Security_Logging_Project "wikilink").

#### Main

The OWASP Logging Project
[Roadmap](:Category:OWASP_Logging_Project_-_Roadmap "wikilink")

<b>The OWASP Logging Project presented at IBWAS09</b>
![Image:IBWAS09_OWASP_Logging_Project_Presentation.ppt](IBWAS09_OWASP_Logging_Project_Presentation.ppt
"Image:IBWAS09_OWASP_Logging_Project_Presentation.ppt")
![Image:IBWAS09_Proyecto_OWASP_Logging_Presentación_en_Español.ppt](IBWAS09_Proyecto_OWASP_Logging_Presentación_en_Español.ppt
"Image:IBWAS09_Proyecto_OWASP_Logging_Presentación_en_Español.ppt")

Project Roadmap
![Image:Owasp_Logging_Project_Roadmap.pdf](Owasp_Logging_Project_Roadmap.pdf
"Image:Owasp_Logging_Project_Roadmap.pdf")
Logging Guide
![Image:OWASP Logging Guide.pdf](OWASP_Logging_Guide.pdf
"Image:OWASP Logging Guide.pdf")

## Goals

<http://www.pisa.org.hk/event/eventlog-mgt.jpg>


Provide tools for software developers in order to help them define and
provide meaningful logs

Provide code audit tools to ensure that log messages are consistent and
complete (content, format, timestamps)

Facilitate the integration of logs from different sources

Facilitate attack reconstruction

Facilitate information sharing around security events

## Existing tools and use cases


**1) IDE integration** (auto-completion, templates, logging policy
definition support) for guiding software developers to define and
provide meaningful logs

For example, a template can provide checks/hints/defaults s.a. those
defined by the OWASP Enterprise Security API :
\- something equivalent to a generated logging session ID, or a hashed
value of the session ID so they can track session specific events
without risking the exposure of a live session's ID
\- identity of the user that caused the event
\- description of the event (supplied by the caller)
\- whether the event succeeded or failed (indicated by the caller)
\- severity level of the event (indicated by the caller)
\- that this is a security relevant event (indicated by the caller)
\- hostname or IP where the event occurred (and ideally the user's
source IP as well)
\- a time stamp

**IDE templates**
<http://www.owasp.org/index.php/File:Eclipse_Create_Template.png>
<http://www.owasp.org/index.php/File:NetBeans_Create_Live_Template.png>
<http://wiki.netbeans.org/Java_EditorUsersGuide>

**OWASP ESAPI Logger** interface (Logger.java) and implementations
<http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API>
<http://code.google.com/p/owasp-esapi-java/downloads/list>


**2/ Code audit tools** s.a. OWASP yasca can be easily adapted in order
to ensure that logging standards are respected and that log messages are
consistent and complete (content, format, timestamps)
See <http://www.owasp.org/index.php/Category:OWASP_Yasca_Project>
Related OWASP projects:
<http://www.owasp.org/index.php/Category:OWASP_Orizon_Project>


**3) Integrating application logs into a Security Information Management
configuration**
OSSIM (http://www.ossim.net/) has numerous plugins for parsing
webserver, appserver, WAF, IPS, IDS logs and generating/storing events
in its standard format.

Adding a plugin for parsing custom application logs is as easy as
finding the correct regular expression provided that developers included
all relevant information in the log message and that they have done so
in a consistent way.

You can refer to the OSSIM database model to see what data is stored for
events.

See <http://www.owasp.org/index.php/File:OWASP_Logging_Guide.pdf> for
more details/screenshots on application event integration and
correlation via OSSIM


**4) Reconstructing attacks**
It is difficult to analyze, filter and generally reconstruct an attack
because messages are spread around various log levels.

See the Logging part of the OWASP ESAPI project
<http://code.google.com/p/owasp-esapi-java/downloads/list>

Along the same lines, Arshan Dabirsiaghi's proposal of adding a security
log level is very interesting
<http://www.owasp.org/index.php/How_to_add_a_security_log_level_in_log4j>


**5) Implement scripts for filtering/scrubbing logs in order to enable
log data sharing between organizations**
Goal: information sharing around security events
Custom logger implementations based on the OWASP ESAPI might also filter
out any sensitive data specific to the current application or
organization, such as credit cards, social security numbers etc.

See the Logging part of the OWASP ESAPI project
See <http://code.google.com/p/owasp-esapi-java/downloads/list>

#### Project Details

__NOTOC__ <headertabs />

[Logging Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:OWASP_Alpha_Quality_Document](Category:OWASP_Alpha_Quality_Document "wikilink")