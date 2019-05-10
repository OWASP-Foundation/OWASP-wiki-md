# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![Incubator_big.jpg](Incubator_big.jpg "Incubator_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_webspa_project">OWASP WebSpa Project</h2>
<p>The OWASP WebSpa Project is a Java web knocking tool for sending a single HTTP/S request to your web server in order to authorize the execution of a premeditated Operating System (O/S) command. It provides a cryptographically protected "open sesame" mechanism on the web application layer, comparable to well-known port-knocking techniques.</p>
<h2 id="description">Description</h2>
<p>This project implements the concept of web knocking by offering a jar file that 'tails' the access log of an existing web server. A user submits a specially crafted URL, therefore executing a predefined O/S command. No new ports or services are created.</p>
<p>Similarly to traditional network port-knocking schemes, the OWASP WebSpa Project aims to create a covert channel of communication for O/S commands over the web application layer. This channel is by no means bi-directional: It is only the client that can issue commands to the server. The inverse, i.e. the server issuing commands to the client, is not an option within the current version.</p>
<p>If port knocking is defined as "a form of host-to-host communication in which information flows across closed ports" then we define web knocking as "a form of host-to-host communication in which information flows across erroneous URLs". Finally, in an attempt to mirror the operation of Single Packet Authorisation (SPA), the entirety of a user's action is submitted through a single GET request.</p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP WebSpa Project is free to use. It is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p>
<p>The source code that comes with the OWASP WebSpa Project in the form of the tool named WebSpa is released as open source software under the terms of the <a href="http://www.gnu.org/licenses/quick-guide-gplv3.html">GNU Public License (GPL) version 3</a>. For reference, the full text of the GPL_v3 can be downloaded from the <a href="http://www.fsf.org/">Free Software Foundation</a>. There are no plans to change the license; WebSpa will always remain an open source project free for use by anyone subject to the terms of the license.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_webspa">What is WebSpa?</h2>
<p>OWASP WebSpa provides:</p>
<ul>
<li>A secure channel for executing premeditated O/S commands on your web server</li>
<li>A resource-efficient single jar-file that can either be run as server, or client application, depending on the command line parameters</li>
</ul>
<h2 id="presentation">Presentation</h2>
<p><a href="http://sourceforge.net/projects/webspa/">http://sourceforge.net/projects/webspa/</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p>Release:<br />
<a href="http://sourceforge.net/projects/webspa/files/webspa-08.zip/download">WebSpa v0.8</a></p>
<p>Source:<br />
[<a href="https://github.com/OWASP/WebSpa/archive/v0.8.zip">https://github.com/OWASP/WebSpa/archive/v0.8.zip</a>| WebSpa v0.8.zip]<br />
[<a href="https://github.com/OWASP/WebSpa/archive/v0.8.tar.gz">https://github.com/OWASP/WebSpa/archive/v0.8.tar.gz</a>| WebSpa v0.8.tar.gz]</p>
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

# Videos

|  |                                                                                                                                              |  |                                                                                                                                  |
|  | -------------------------------------------------------------------------------------------------------------------------------------------- |  | -------------------------------------------------------------------------------------------------------------------------------- |
|  | [Poweroff on Apache via Web Knocking with Web-Spa (_v0.7) YouTube Video](https://www.youtube.com/watch?v=S386azVcj-c%7C300%7Cright%7CLinux) |  | [SSH via Web Knocking with Web-Spa (_v0.5) YouTube Video](https://www.youtube.com/watch?v=eHlYnWyf35E%7C300%7Cright%7CEnabling) |
|  | [SSH via Web Knocking with Web-Spa (_v0.4 ) YouTube Video](https://www.youtube.com/watch?v=_VU26ZGG7D8%7C300%7Cright%7CEnabling)            |  | [SSH via Web Knocking with Web-Spa (_v0.4) YouTube Video](https://www.youtube.com/watch?v=pKF_NxHnoyA%7C300%7Cright%7CEnabling) |

# Tutorial

## Supporting Documentation

The discrepant event discussed herein is web knocking. Within the latest
[download](http://sourceforge.net/projects/webspa/files/latest/download?source=directory)
you can find three documents with the purpose of describing how WebSpa
can be used. The three documents are:

  - **'WebSpa Administration Guide** This document describes how to
    setup and use the server component. It details how to create new
    users and add new action numbers with respective O/S commands
    assigned to them

<!-- end list -->

  - **WebSpa Specification Guide** This document describes the actual
    design detailing the use case, specification, requirements and
    actual attacks, which this tool has been engineered to withstand

<!-- end list -->

  - **WebSpa User Guide** This document describes how to use the client
    for issuing commands through a URL request to a web server

The administration guide aims to enable anyone who would be interested
in using WebSpa to be able to setup the server side component of it.
After configuring the server component of WebSpa, you'll be ready to use
the corresponding client for issuing direct actions as O/S commands to
it.

If this is your first time using WebSpa, please note that the server
operations described in this document, will not work if a WebSpa client
does not submit a web-knock to your web server in a timely manner.

Thus, knowing a client implementation goes hand-in-hand with a server
instance for it, please also have a look at the WebSpa user guide
document to see how the two can be used in tandem.

The user guide aims to enable anyone who would be interested in using
WebSpa to do so. As soon as you install the server side component and
decide what actions to allow, you'll be ready to use the corresponding
client for issuing direct actions that work for you.

Finally, the specification guide aims to enable anyone who would be
interested in implementing their own version of WebSpa to do so.

## HelloWorld\! Enabling SSH via Web Knocking with WebSpa

In this section we describe the setup you should follow in order to get
to the stage of being able to execute the video entitled: [Enabling SSH
via Web Knocking with WebSpa
(_v0.5)](https://www.youtube.com/watch?v=eHlYnWyf35E) on your server.

We assume you can SSH into your web server using the user 'web-spa'. We
also assume that the user 'web-spa' has permissions to run the necessary
service start and stop commands for this service. So, let's login to the
box and get the latest WebSpa download:

`ssh web-spa@web.spa.seleucus.net`
`web-spa@web:~$ cd /tmp`
`web-spa@web:/tmp$ wget `<https://downloads.sourceforge.net/project/webspa/webspa-06.zip>

It would be wise at this stage to check the SHA1 digest of what we just
downloaded. Sourceforge publishes the SHA1 of all files available for
download; copying the value into our command prompt yields:

`web-spa@web:/tmp$ echo "a630f23f88c49d02b5895a3d7e16aad245c387f3 *webspa-06.zip" `

| sha1sum -c -

`webspa-06.zip: OK`
`web-spa@web:/tmp$ `

Ok, so we have downloaded something that we can vouch for-ish. Let's
extract and setup.

`unzip webspa-06.zip`

A lot of noise comes back from this command. Apologies, different groups
have clearly stated they have wanted the source code as well the
documentation to be included within the download. Let's have a look at
the install file:

`=================================================`
`- Prerequisites for WebSpa`
`=================================================`

`The following programs must be installed in order`
`for WebSpa to run:`

`- Java 1.6 or later`

If you don't have java installed, consider using the following command:

`sudo aptitude install openjdk-7-jre`

This will meet the one prerequisite for using WebSpa. As this is a
production server, docs and src folders will not be missed. Also, we
like to store things in /opt, ergo:

`web-spa@web:/tmp$ rm -frv /tmp/web-spa-0.6/src/`
`web-spa@web:/tmp$ rm -frv /tmp/web-spa-0.6/docs/`
`web-spa@web:/tmp$ sudo mv -v /tmp/web-spa-0.6/ /opt`

We now have WebSpa in /opt, let's run the server and create some users.

`web-spa@web:/tmp$ cd /opt/web-spa-0.6/`
`web-spa@web:/opt/web-spa-0.6$ java -jar web-spa-0.6.jar -server`

`Web-Spa - Single HTTP/S Request Authorisation`
`version 0.6 (web-spa@seleucus.net)`

`This is a holding prompt, type "exit" or "x" to quit`

`- type "service start" to start the web-spa server`
`- type "help" or "?" for more options`

`web-spa-server>`

The last line above is the server's holding prompt; all commands are
issued via this prompt. In order to exit this prompt, type 'exit' or
'quit'. In the next step we will add 3 users and assign a unique
pass-phrase to each one of them.

`web-spa-server>user add`
`=[Required] Enter the New User's Full Name: Yiannis Pavlosoglou`
`=[Required] Enter the New User's Pass-Phrase: `
`=[Required] Re-enter the above value: `
`-[Optional] Please enter the New User's Email Address: yiannis@xxxxxx.com`
`-[Optional] Please enter the New User's Phone Number: `
`web-spa-server>`

Please note that only a user's full name and pass-phrase are required to
be entered. Let's create another user:

`web-spa-server>user add`
`=[Required] Enter the New User's Full Name: Oliver Merki`
`=[Required] Enter the New User's Pass-Phrase: `
`=[Required] Re-enter the above value: `
`-[Optional] Please enter the New User's Email Address: `
`-[Optional] Please enter the New User's Phone Number: `
`web-spa-server>`

Note that we did not specify a user's e-mail address nor a phone number,
as both these fields were optional. Finally, adding a third user:

` web-spa-server>user add`
`=[Required] Enter the New User's Full Name: Patryk`
`=[Required] Enter the New User's Pass-Phrase: `
`=[Required] Re-enter the above value: `
`-[Optional] Please enter the New User's Email Address: `
`-[Optional] Please enter the New User's Phone Number: `
`web-spa-server>`

For Patryk we only specified his first name and a unique pass-phrase.
You get the picture. Now that we have created our users, let's add some
actions to each user. We would like to give Patryk the ability to bounce
the SSH service; ergo, let's add two actions:

`web-spa-server>action add`
`Users:`
`___________________________________________________________`
`ID  Active  Full Name               Last Modified            `
`-----------------------------------------------------------`
`11  false   Yiannis Pavlosoglou     2014-02-23 12:09:26.240`
`12  false   Oliver Merki            2014-02-23 12:12:13.313`
`13  false   Patryk                  2014-02-23 12:14:57.895`
`___________________________________________________________`
`-[Optional] Select a User ID: 13`
`The existing actions for this user are: `
`Actions for user with ID: 13`
`___________________________________________________________`
`#  O/S Command                     Last Executed            `
`-----------------------------------------------------------`
`___________________________________________________________`
`=[Required] Enter the new O/S Command: sudo service ssh start `
`=[Required] Select an action number for this O/S Command [0,9]: 1`
`web-spa-server>`

The above adds the O/S command 'sudo service ssh start' to action number
1 for user Patryk. Let's also add the stop command:

`web-spa-server>action add`
`Users:`
`___________________________________________________________`
`ID  Active  Full Name               Last Modified            `
`-----------------------------------------------------------`
`11  false   Yiannis Pavlosoglou     2014-02-23 12:09:26.240`
`12  false   Oliver Merki            2014-02-23 12:12:13.313`
`13  false   Patryk                  2014-02-23 12:14:57.895`
`___________________________________________________________`
`-[Optional] Select a User ID: 13`
`The existing actions for this user are: `
`Actions for user with ID: 13`
`___________________________________________________________`
`#  O/S Command                     Last Executed            `
`-----------------------------------------------------------`
`1  sudo service ssh start          has never been executed`
`___________________________________________________________`
`=[Required] Enter the new O/S Command: sudo service ssh stop `
`=[Required] Select an action number for this O/S Command [0,9]: 0`
`web-spa-server>`

The above adds the O/S command 'sudo service ssh stop' to action number
0 for user Patryk. Two very important steps we must not forget is to
enable the user Patryk and start the web-spa listening service.

`web-spa-server>user activate`
`Users:`
`___________________________________________________________`
`ID  Active  Full Name               Last Modified            `
`-----------------------------------------------------------`
`11  false   Yiannis Pavlosoglou     2014-02-23 12:09:26.240`
`12  false   Oliver Merki            2014-02-23 12:12:13.313`
`13  false   Patryk                  2014-02-23 12:14:57.895`
`___________________________________________________________`
`-[Optional] Select a User ID: 13`
`User with ID: 13 is in-active`
`-[Optional] Toggle user activation [Y/n]: `
`User with ID: 13 is active`
`web-spa-server>`

`And finally issue the service start command:`

`web-spa-server>service start`
`[2014-02-23 12-36-07] Attempting to start web-spa...`
`[2014-02-23 12-36-07] Found access log file: /...cus.net/logs/access.log`
`[2014-02-23 12-36-07] Creating tail listener...`
`[2014-02-23 12-36-07] Web-spa server started!`
`[2014-02-23 12-36-07] Please make sure your web server is also up`
`web-spa-server>`

# News

  - \[19 Feb 2015\] The source WebSpa code repository has been migrated
    to GitHub. The compiled releases (.jar) are still made available on
    SourceForge.
  - \[17 Feb 2015\] WebSpa has a new contributor – Daniel Imber. Dan,
    welcome to the team\!
  - \[12 Jan 2015\] Patryk Arciszewski decided to retire from the
    project. Patryk, thank you for your good work and may the Power of
    SPA be with you.
  - \[23 Nov 2014\] Version 0.8 has been released and can now be found
    in the download section. We are proud to offer a working, stable
    proof-of-concept of WebSpa.
  - \[19 Aug 2014\] Our project was featured in the OWASP Connector
    newsletter.
    [(link)](http://hosted-p0.vresp.com/1479611/4d8d3315c2/ARCHIVE)
  - \[07 May 2014\] Added four video links in the respective "Video"
    tab, referencing YouTube
  - \[24 Apr 2014\] Version 0.7 has been release and can now be found in
    the download section. Also, we welcome Joël to the team.
  - \[20 Mar 2014\] [WebSpa has been presented during OWASP London
    Chapter
    Meeting](http://www.eventbrite.co.uk/e/owasp-london-chapter-meeting-march-2014-tickets-10063386861)
  - \[16 Mar 2014\] WebSpa has a new contributor – Paweł Goleń. Paweł,
    welcome to the team\!
  - \[14 Mar 2014\] [Scheduled the deletion of the Google code project,
    given that downloads require a new
    account](https://code.google.com/p/web-spa/)
  - \[04 Mar 2014\] [The WebSpa podcast has now been
    available\!](https://soundcloud.com/#owasp-podcast/the-owasp-webspa-project-with)
  - \[22 Feb 2014\] Created the WebSpa project on sourceforge, started
    the import from Google code
  - \[22 Dec 2013\] Version 0.6 has been released and can now be found
    in the download section
  - \[08 Nov 2013\] The OWASP Web Knocking Project is created

# FAQs

  - Does WebSpa supports older versions of Java?
    No. WebSpa is tested with an up-to-date JRE package, thus to run
    WebSpa a JRE 1.7 or greater is needed.

Using older versions of Java may lead to unexpected system behaviors.

  - What does the ASCII-Art for WebSpa look like?

`                   __                                           `
`                  /\ \                                          `
`  __  __  __     __\ \ ____             ____  _____      __     `
``/\ \/\ \/\ \  /'__`\ \ '__`\  _______  /',__\/\ '__`\  /'__`\   ``
``\ \ _/ _/ \/\  __/\ \ \L\ \/______\/__, `\ \ \L\ \/\ \L\._ ``
` \ ___x___/'\ ____\\ _,__/\/______/\/____/\ \ ,__/\ __/._\`
`  \/__//__/   \/____/ \/___/           \/___/  \ \ \/  \/__/\/_/`
`                                                \ _\           `
`                                                 \/_/           `

The font is Larry 3D generated
[here](http://patorjk.com/software/taag/#p=display&f=Larry%203D&t=web-spa).

  - Who are the actors required in order to use the WebSpa tool?

There are two actors, the WebSpa administrator and the WebSpa user.
Ultimately, they could be the same person. The administrator agrees with
each user what each of their allowed O/S commands are, while the user,
well, executes these commands on the server by using the client.

  - How does the crypto of WebSpa work?
    From the perspective of cryptographic engineering, WebSpa uses a
    hash [commitment
    scheme](http://en.wikipedia.org/wiki/Commitment_scheme), where the
    commit phase during which a value is chosen is done using an out of
    band channel. WebSpa focuses on receiving a value specified through
    a single request from the client and processing it on the server.

<!-- end list -->

  - Can one deploy WebSpa over HTTP?
    Yes, WebSpa can be deployed over HTTP, however for security reasons
    it is highly recommended to utilize HTTPS.

<!-- end list -->

  - How to report a WebSpa bug?
    To report a WebSpa bug please feel free to create a ticket on the
    [sourceforge.net](http://sourceforge.net/p/webspa/tickets/?source=navbar).
    A sourceforge account is necessary. If you don’t own a sourceforge
    account you may send an e-mail to one of the contributors.

# People

The OWASP WebSpa Project is developed by a worldwide team of volunteers.
Below is a list of all people that have contributed to the project so
far.

Active contributors:

  - [Yiannis Pavlosoglou](User:Yiannis "wikilink") - Inception &
    Development
  - Paweł Goleń - Breaking & Infrastructure
  - Joël Rouiller - Development & Optimisation
  - Daniel Imber - Development & Refactoring
  - [Oliver Merki](User:Oliver_M. "wikilink") - Leader & Operations

Retired contributors:

  - [Markus Maria Miedaner](User:Dr._Markus_Maria_Miedaner "wikilink")
  - Patryk Arciszewski

# Roadmap

## Release 0.9 (Q3/2015)

WebSpa_v0.9 will be major release and include a comprehensive redesign
of the WebKnock format in order to improve overall security and
robustness of the request, but also offer improved usability features,
which will simplify installing, configuring and running WebSpa.. The
tickets for this release are:

`44 New WebKnock request format should be defined`
`42 Do not limit the web knock to 100 characters, instead use SHA-512 lengths    `
`35 A threat model for WebSpa should be created and reviewed     `
`33 Apache should be replaced by nginx   `
`15 Add easy way to run the server as a background daemon     `

## [Release 0.8 (Q4/2014)](http://sourceforge.net/projects/webspa/files/webspa-08.zip/download)

WebSpa_v0.8 is sort of a proof-of-concept of WebSpa. A stable version
to demonstrate the concept of WebKnocking, however, with some
limitations with regards to usability/configuration and modularity (e.g.
changing the hashing algorithm). The tickets for this release are:

`43 Change SSL configuration to allow wget`
`41 WebSpa administrator to WebSpa user output   `
`40 Log to /​var/​log instead of a log.txt file `
`38 umask 077 should be added to webspa.sh   `
`32 A known_hosts file should be used to maintain the list of successfully verified keys     `
`31 Verification of server's public key fingerprint should be possible   `
`30 Help Files Update (0.8)  `
`- FIXED: Modified the checking of 2 arrays being equal to be constant in time (Ticket #27)`
`2  Create maven build task for release  `

## [Release 0.7 (24/Apr/2014)](http://sourceforge.net/projects/webspa/files/webspa-07.zip/download)

This is the current release of WebSpa.

WebSpa _v0.7 offers enhanced user administration functionality. The
WebSpa client now offers the possibility for a user to connect to a web
server with an untrusted/self-signed certificate.

`- NEW: The WebSpa client asks the user if they want to connect web servers with untrusted certificates. (Ticket #28) `
`- NEW: Introduced ‘passwd’ command, which allows the WebSpa administrator to modify a user’s password.`
`- NEW: Introduced ‘pass-phrase show’ command, which allows the WebSpa administrator to print a user’s pass-phrase to the screen.`
`- FIXED: Array is no longer sorted, which reduced the entropy of the web-knock. (Ticket #24)`
`- FIXED: Reworked and added test cases.`
`- FIXED: Removed dependency on Spring security. (Ticket #18)`

## [Release 0.6 (21/Dec/2013)](https://code.google.com/p/web-spa/downloads/detail?name=webspa-06.zip)

WebSpa _v0.6 offers enhanced logging functionality, fixing a bug that
caused the server to become unresponsive upon starting and stopping. The
client now offers to transmit a web knock request, thus not requiring
for a user to copy-paste the URL into their browser.

Additional test cases have been added, the option "?" is now available
to offer "help" and the log functionality tracks via means of a
timestamp all events logged

## [Release 0.5 (21/Oct/2013)](https://code.google.com/p/web-spa/downloads/detail?name=webspa-05.zip)

WebSpa _v0.5 shortens the number of inputs required from a legitimate
user of web-spa to only two: A valid pass-phrase, unique for each user
and a single digit in the range of \[0-9\]. We refer to the latter as an
action number and it represents a premeditated Operating System (O/S)
command.

All the functionality (for both the client and the server) is now within
a single jar file, accompanied by detailed documentation:

`- 00-web-spa-administration-guide.pdf  `
`- 00-web-spa-specification-guide.pdf   `
`- 00-web-spa-user-guide.pdf`

The server side functionality has been re-designed to operate with a
single configuration file (created at first run) as well as a HyperSQL
embedded file database (also created at first run).

Finally, no files are created or are required when web-spa runs in
client mode, with the '-client' option.

## [Release 0.4 (27/Aug/2011)](https://code.google.com/p/web-spa/downloads/detail?name=webspa-04.zip)

A number of updates and bug fixes have been included within this
version. Also, an update on the actual message format to further protect
from replay attacks has been included.

WebSpa _v0.4 contains the necessary client and server components, as
well as an elements API library. Thus, the files within the download
are:

`* webspa-client-04.jar`
`* webspa-elements-04.jar`
`* webspa-server-04.jar`

## [Release 0.3 (11/Jul/2011)](https://code.google.com/p/web-spa/downloads/detail?name=webspa-03.zip)

In its first usable release, WebSpa _v0.3 contains the necessary client
and server components, as well as an elements API library. Thus, the
files within the download are:

`* webspa-client-03.jar`
`* webspa-elements-03.jar`
`* webspa-server-03.jar`

## Contribution

Involvement in the development and promotion of the OWASP WebSpa Project
is actively encouraged\! You do not have to be a security expert in
order to contribute. Some of the ways you can help:

  - Quality assurance of resolved defects
  - Java development (good knowledge of Java desirable)

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")