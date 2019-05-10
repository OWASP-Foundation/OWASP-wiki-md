# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_security_logging_project">OWASP Security Logging Project</h2>
<p>The OWASP Security Logging project provides developers and ops personnel with APIs for logging security-related events. The aim is to let developers use the same set of logging APIs they are already familiar with from over a decade of experience with Log4J and its successors, while also adding powerful security features.</p>
<h2 id="description">Description</h2>
<p>Logging is often neglected by developers when thinking of security considerations. However, proper logging practice can provide the crucial forensics needed to investigate after a breach, and perhaps more importantly, a change to detect security issues as they happen. Most developers are already familiar with using logging for debugging and diagnostic purposes, so it should be easy for them to grasp the concept of security logging as well. The OWASP Security Logging project aims to give developers an easy way to get started with logging security events, tracking extra forensic information like the who (username), what (event type), and where (IP address, server name) needed for forensics. It also provides a means for classifying the information in log messages and applying masking if necessary.</p>
<h2 id="licensing">Licensing</h2>
<p>This library is free software: you can redistribute it and/or modify it under the terms of the Apache License, Version 2.0. You can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="quick_start">Quick Start</h2>
<p>Overview of benefits and what you need to get started quickly.</p>
<p><a href="http://www.securitycurmudgeon.com/2016/03/owasp-security-logging-project-explored.html">OWASP Security Logging Project Explored</a></p>
<h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/javabeanz/owasp-security-logging">Source Code</a></p>
<p><a href="https://github.com/javabeanz/owasp-security-logging/wiki">Documentation</a></p>
<p><a href="https://github.com/javabeanz/owasp-security-logging/issues">Issue Tracker</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="Logging_Cheat_Sheet" title="wikilink">Logging Cheat Sheet</a></li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
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
<td><p><a href="http://www.apache.org/licenses/LICENSE-2.0.html">ASLv2</a></p></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="project_leaders">Project Leaders</h2>
<p><a href="mailto:sytze.vonkoningsveld@owasp.org">Sytze van Koningsveld</a></p>
<p><a href="mailto:august.detlefsen@owasp.org">August Detlefsen</a></p>
<p><a href="mailto:milton.smith@owasp.org">Milton Smith</a></p>
<h2 id="news_and_events">News and Events</h2>
<p>18 Jan 2018, <a href="https://github.com/javabeanz/owasp-security-logging/releases/tag/v1.1.4">Version 1.1.4 released</a></p>
<p>1 Jul 2016, <a href="http://www.slideshare.net/MiltonSmith6/how-to-use-owasp-security-logging">How to Use OWASP Security Logging, AppSecEU 2016 Lightning Talk</a></p>
<p>5 Mar 2015, Version 1.0.0 deployed to Maven Central</p>
<p>23 Dec 2014, Project Created and source code now available!</p></td>
</tr>
</tbody>
</table>

<paypal>OWASP Security Logging Project</paypal>

# FAQs

The following provides answers to frequently asked questions.

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

# Acknowledgements

## Volunteers

Only project leads for the moment. Email projects leads if you would
like to participate.

# Roadmap & Getting Involved

Today many logging technologies are available providing powerful
application logging capabilities. But while powerful, these technologies
are not designed for specific use-cases like security and auditing. The
generalized approach to logging platforms makes these platforms more
useful to the widest possible audience but it also places more
responsibility on designers. In short, we don't consider our desire for
additional improvement for security and audit logs is no oversight on
the part of logging platform designers.

It's the OWASP Security Logging Project desire to leverage existing
technologies and apply them to improve security, audit, in addition to
diagnostic logging. We understand logging is mostly an afterthought on
many project schedules, if it's included at all. We believe a logging
solution embracing this project will help the community produce better
logs, a better understanding of our information systems, and higher
quality software.

## Getting involved

Are you passionate about logging? Are you motivated share your time and
knowledge with the community? Send the project leads an email, listed on
project home page, and explain your ideas and how you can help. Don't be
discouraged if we don't immediately respond. We occasionally get
distracted with life but rest assured we will respond.

## What is the OWASP Security Logging Project?

OWASP Security Logging Project purpose is to deliver a suitable logging
solution for general-purpose security, audit, and diagnostics log
messaging. Beyond code and technology, the project provides
architectural and implementation considerations you may find useful in
your own projects, or technologies you may not have previously
considered.

## Project goals

  - Develop a set of logging requirements for key domains like security,
    auditing, and diagnostics
  - Develop interface specifications that support the projects
    requirements
  - Develop a base implementation supporting project interface
    specifications
  - Develop documentation artifacts (described later)

## Considerations and restraints

  - Ease of use
  - Compelling value on initial deployment (without any refactoring).
    Increased value for refactoring
  - Compatibility with existing industry standard logging technologies
    (e.g., log4\*, logback, FluentD, etc)
  - Typical scenarios considered, 1) stand-alone applications on mobile
    or desktop, 2) enterprise applications, and 3) cloud-based
    applications.

## Anticipated support

  - Java 1.7 and Java 1.8
  - .NET (tbd)

*We have considered other platforms for the future but everything
depends upon community interest and support.*

## Proposed features

Following is a list of numbered features.

  -
    1\. MDC metadata improvements
      -
        a. process id (TBD)
        b. application id and application instance id
        c. server time\\date in UTC
        d. client time\\date in UTC
        e. client IP address
        f. username or ID
        g. global client session ID
        h. security policy identifier
        i. transaction id
    2\. Log system properties on startup
    3\. Log command line options on startup
    4\. Log application server properties on startup
    5\. Log HTTP request parameters
    6\. Log HTTP session attributes
    7\. Internationalization considerations
    8\. Redirect system streams like system.out and system.err security
    logging framework
    9\. Asynchronous message logging, store and forward
    10\. Message correlation
    11\. Performance options for transport compression
    12\. Authenticated client logging
    13\. Secure log message transport
    14\. Signed log messages
    15\. Guaranteed log message delivery

## Delivery phases

**Alpha 1**, some features code complete.
**Alpha 2**, more features code complete.
**Beta**, release code complete. Public encouraged to test and respond
with comments.
**Early Availability(EA)**, includes improvements to beta based upon
public and team recommendations.

## Use-case applicability & delivery schedule

The following table shows a proposed applicability of each feature to
the projects areas of concern, diagnostics, security, and audit logging
along with a suggested delivery phase.

|                                                                                        | Diagnostics | Security | Audit | Delivery |
| -------------------------------------------------------------------------------------- | ----------- | -------- | ----- | -------- |
| Feature 1a, process id                                                                 | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1b, application id and application instance id                                 | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1c, server time\\date in UTC                                                   | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1d, client time\\date in UTC                                                   | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1e, client IP address                                                          | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1f, username or ID                                                             | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1g, global client session ID                                                   | **X**       | **X**    | **X** | Alpha 1  |
| Feature 1h, security policy identifier                                                 |             | **M**    | **X** | Alpha 1  |
| Feature 1i, transaction id                                                             | **X**       | **X**    | **X** | Alpha 1  |
| Feature 2, Log system properties on startup                                            | **X**       | **X**    | **X** | Alpha 1  |
| Feature 3, Log command line properties on startup                                      | **X**       |          |       | Alpha 1  |
| Feature 4, Log application server properties on startup                                | **X**       |          |       | Alpha 2  |
| Feature 5, Log HTTP request parameters                                                 | **X**       | **X**    |       | Alpha 2  |
| Feature 6, Log HTTP session attributes                                                 | **X**       | **X**    | **?** | Alpha 2  |
| Feature 7, Internationalization considerations                                         | **X**       | **X**    | **X** | Alpha 1  |
| Feature 8, Redirect system streams like System.out and System.err to logging framework | **X**       |          |       | Alpha 2  |
| Feature 9, Asynchronous message logging, store and forward                             | **X**       | **X**    | **X** | Alpha 2  |
| Feature 10, Message correlation                                                        | **X**       | **X**    | **X** | Alpha 2  |
| Feature 11, Performance options for transport compression                              | **X**       | **X**    | **X** | Alpha 2  |
| Feature 12, Authenticated client logging                                               |             | **X**    | **X** | Alpha 2  |
| Feature 13, Secure log message transport                                               |             | **X**    | **X** | Alpha 2  |
| Feature 14, Signed log messages                                                        |             | **X**    | **X** | Alpha 1  |
| Feature 15, Guaranteed log message delivery                                            |             | **X**    | **X** | Alpha 2  |

***Legend, X=applicable use-case, M=maybe useful, ?=tbd***

## Project delivery artifacts

  -
    **Logging primer**, architectural considerations for security,
    audit, and diagnostics for community projects. Provide information
    how logging project can be leverage to address concerns provided by
    each use case, general logging best practices, template for using
    message levels (e.g., INFO, WARN, etc).
    **Logging design**, specific technical details to apply project
    logging to community logging projects.
    **Code**, software program code that implements project feature
    goals.

## Code areas

  -
    **Logging layouts**, at the moment this is Common Event Format(CEF)
    and Common Log File System(CLFS).
    **MDC filter**, include system information handy for most
    deployments into logbacks Mapped Diagnostics Context(MDC).
    **MDC marker**,
    **Unit testing**, various software code we use (and you can also
    use) to test project code.

## Detailed use-case descriptions

Following are detailed use-case descriptions for each feature. The
purpose of this section is to help readers to understand more about each
feature and it's potential benefits.

## Feature 1, MDC metadata improvements

This feature adds certain metadata useful for security purposes to
logback’s Mapped Diagnostics Context. The following metadata will be
mapped where available.

### process id (feature 1a)

This is the process id of the application as assigned by the operating
system at execution. On \*nix and Windows environments this the PID.
Depending upon the language platform process id may not be readily
available. As an alternative, server hostname or IP may be used.

### application id and application instance id (feature 1b)

This an identifier set by the application designer to identify a unique
application instance. This identifier is useful to identify applications
uniquely where many instances of the same program (e.g., web
application) are hosted on 1 or more physical servers. The application
id is useful visual indicator of the type of application component. The
instance id is useful to identify the application instance. The instance
is particularly useful where the same process may host 2 or more
application instances. An instance id may be a generated hash (e.g.,
VMID) or unique index where size is a concern. Once the id is used it
should persist between process restarts. A suggested format: {APP
ID}:{APP INSTANCE ID}. An sample
POS:ace22c02aa858f670e3c227fbab141e2d8d6bea6 or POS:14563.

### server time\\date in UTC (feature 1c)

Time, date, and day, on the server with timezone offset at the time the
message was logged. A suggested format\[1\],
{yyyy-MM-dd'T'HH:mm:ss.SSSZ}. An example, 2001-07-04T12:08:56.235-0700

### client time\\date in UTC (feature 1d)

Time, date, and day, on the client with timezone offset at the time the
message was logged. A suggested format\[1\],
{yyyy-MM-dd'T'HH:mm:ss.SSSZ}. An example, 2001-07-04T12:08:56.235-0700

### client ip address (feature 1e)

MDC property for the IP address of the client host where the log message
originated. An example, 192.168.1.30

### user name or ID (feature 1f)

This MDC property to property is an application account name associated
with a human (if available) this is associated with this log message.
This property may not be available if the log message is not
specifically related to an individual's activity. An example,
milton.smith

### global client session id (feature 1g)

This MDC property is a session id assigned by an application designer
that is shared across multiple application instances. Usually this is a
secure hash to avoid reverse engineering. An example,
ace22c02aa858f670e3c227fbab141e2d8d6bea6

### security policy identifier (feature 1h)

MDC property that identifies activities associated with a sites security
policy. The value is site defined and can be useful when producing
information for audits. An example, Violation:SEC.5.2a

### transaction id (feature 1i)

MDC property to identify activities associated with a single user
action. For example, execution of a single application user feature may
require many activities from the main application program along with
components like LDAP servers and databases. The transaction id is useful
to correlate all the related system activities that support a specific
user request. Each subsequent user request receives a new transaction
id. An example, TRX:1005862

## Feature 2, Log system properties on startup

The requirement is to log all system properties on application startup.
Often it’s difficult to perform an investigation without understanding
the initial state of the system. An example how properties may appear in
logs (without MDC information).

```
 *******************************************
 JAVA PROPERTY SETTINGS
 *******************************************
Setting, java.runtime.name=Java(TM) SE Runtime Environment
Setting, sun.boot.library.path=C:\Program Files\Java\jre6\bin
Setting, java.vm.version=14.0-b16
Setting, java.vm.vendor=Sun Microsystems Inc.
Setting, java.vendor.url=http://java.sun.com/
Setting, path.separator=;
Setting, java.vm.name=Java HotSpot(TM) Client VM
Setting, file.encoding.pkg=sun.io
Setting, sun.java.launcher=SUN_STANDARD
 Setting, user.country=US
Setting, sun.os.patch.level=
Setting, java.vm.specification.name=Java Virtual Machine Specification
Setting, user.dir=C:\Users\Milton\workspace\MyProject
Setting, java.runtime.version=1.6.0_14-b08
Setting, java.awt.graphicsenv=sun.awt.Win32GraphicsEnvironment
Setting, java.endorsed.dirs=C:\Program Files\Java\jre6\lib\endorsed
Setting, os.arch=x86
Setting, java.io.tmpdir=C:\Users\Milton\AppData\Local\Temp\
Setting, line.separator=

Setting, java.vm.specification.vendor=Sun Microsystems Inc.
Setting, user.variant=
Setting, os.name=Windows 7
Setting, sun.jnu.encoding=Cp1252
Setting, java.library.path=C:\Program Files\Java\jre6\bin;.;C:\Windows\Sun\Java\bin;C:\Windows\system32;C:\Windows;C:/Program Files/Java/jre6/bin/client;C:/Program Files/Java/jre6/bin;C:\Program Files\JavaFX\javafx-sdk1.2\bin;C:\Program Files\JavaFX\javafx-sdk1.2\emulator\bin;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;c:\usershellcommands;C:\Program Files\QuickTime\QTSystem\
 Setting, java.specification.name=Java Platform API Specification
Setting, java.class.version=50.0
Setting, sun.management.compiler=HotSpot Client Compiler
Setting, os.version=6.1
Setting, user.home=C:\Users\Milton
Setting, user.timezone=
Setting, java.awt.printerjob=sun.awt.windows.WPrinterJob
Setting, file.encoding=Cp1252
Setting, java.specification.version=1.6
Setting, java.class.path=C:\Users\Milton\workspace\SDA\bin;C:\Java-Libs\jmx-1_2_1-bin\lib\jmxri.jar;C:\Java-Libs\apache-log4j-1.2.15\log4j-1.2.15.jar
Setting, user.name=Milton
```

## Feature 3, Log command line options on startup

The requirement is to log all command line arguments on application
startup. All command line arguments must be logged. In Java, the entire
arg array passed into the main(String args\[\]) method should be logged.
Any whitespace or special characters should be filtered before logged.
For example a small program that echos the input to the command line may
produce an output that looks like the following.

```
 *******************************************
    COMMAND LINE ARGS
 *******************************************
java testapp “Hello World!”
Hello World!
```

## Feature 4, Log application server properties on startup

The requirement is to log all key\\value pairs that influence
application behavior upon execution. In Java, there parameters are
defined by HttpServlet.getInitParameterNames() An example of logged J2EE
properties may look like the following.

```
 *******************************************
    J2EE PROPERTIES
 *******************************************
Setting, thread.pool.size=1000
Setting, request.ttlms=30000
```

## Feature 5, Log HTTP request parameters

The requirement is to log all key\\value pairs associated with all
application HTTP requests. Raw HTTP requests parameters across the cloud
may generate significantly increase log volume. The goal is to define a
request log that overwrites itself (e.g., a ring buffer) at a small
designer specified interval or a default of 15 mins. This allows highly
granular diagnostic messages over a short duration.

An ancillary requirement is that sensitive key\\value pairs will be
masked. A default set of masking rules will be included with the project
with an option for designers to assign their own masking rules specific
for their applications.

(TODOMS: need to insert some raw http requests from zap in a suitable
log format)

## Feature 6, Log HTTP session attributes

The requirement is to log all key\\value pairs associated with a users
HttpSession instance. These properties should be logged once upon user
session initialization. In Java, key\\value pairs from
HttpSession.getAttributeName() should be logged when the HttpSession is
created.

(TODOMS: need to insert some sample HTTP session attributes)

## Feature 7, Internationalization considerations

The action is to use string resources so that logs are compatible across
languages. The project will initially define US English. Designers are
encouraged to translate resources to different languages. If the
translations are made available to us we may include them.

## Feature 8, Redirect system streams like System.out and System.err to security logging framework

This requirement captures any legacy messaging from older code without
refactoring. The approach redirects any messages to system defined
streams into the logging framework. Log messages will not be a content
rich since since the caller, old code in this case, does not calling the
Security API directly. The advantage is instant out of the box
compatibility with no refactoring. In Java, the action is to capture
calls like System.out.println(“My wife loves security.”) and
System.err() reroute them to the logging framework without modification
to legacy programs.

An ancillary requirement is that sensitive key\\value pairs will be
masked. A default set of masking rules will be included with the project
with an option for designers to assign their own masking rules specific
for their applications.

## Feature 9, Asynchronous message logging, store and forward

The requirement for this feature one of performance. Log messages sent
to a remote location (e.g., central log server) can take some time to
send over networks. It may be desirable in some deployments for the
caller not to block when logging these messages. The goal is to log the
message locally, freeing the caller, then send the message in a
background thread to the remote server. See Feature 15 also.

## Feature 10, Message correlation

A problem with logs today is that it’s often difficult to reconstruct a
series of activities leading to an event of interest. System logs are
often out of order with messages originating from different threads and
hosts. The goal of message correlation is to provide identifier(s) so
that all log messages can be sequenced into a narrative of system
activities leading to an event of interest. For example, with
correlation it will be possible to separate log entries to see the
activities involved in a single administrative user operation like Add
User. Log entries to add a user may begin with HTTP posts from the
clients browser, system permission checks, next a log message describing
the insert of the new user into the user table, a log message of
positive confirmation a SMTP message was sent to indicate the users new
account is ready for initial signon.

## Feature 11, Performance options for transport compression

Where log message will transit networks facilities will be provided to
compress traffic to remote hosts.

## Feature 12, Authenticated client logging

This feature is useful to ensure each message logged is attributable to
a known source and trusted source. Messages from anonymous sources may
still be allowed, depending upon system preferences, but authenticated
messages will clearly indicate the identity of the source.

## Feature 13, Secure transport

To facilitate secure transport a TLS 1.2 compliant connection be
negotiated. Options must be provided to allow designers to control
ciphersuite negotiation. Negotiation options must include provision for,
a) the name of each ciphersuite permitted, b) order of negotiation which
is ideally strongest suites first as a default but can be changed by the
designer. The trust roots will be those supplied by the supporting
language platform (e.g., Java, .NET, etc).

## Feature 14, Signed log messages

To facilitate tamper resistant log messages log messages will be signed
by the client. Each field of the log message will be included in the
signing process. The signature will be included with the log message
entry along with strongest fingerprint included within signing
certificate. The fingerprint of the signing certificate is an aid to
identify the signing certificate and may be important for enterprise or
cloud environments where many clients are logging. Signed logs may or
may not be encrypted.

## Feature 15, Guaranteed log message delivery

This feature builds upon the Feature 9, Asynchronous message logging,
store and forward to include guaranteed delivery. The goal is that no
messages are lost. Messages received from the caller will be queued for
delivery. Clients logging messages must block until their log message is
committed to a queue. For simplicity, the queue will exist on the client
computer. The function is somewhat analogous to a local print spooler.
If committing to a queue is not possible an instance of a
RuntimeException must be thrown to the caller. Once committed to a
queue, worker threads will send the message in the background to the
remote server. On the client, worker threads will not remove the log
message from the queue until the server has acknowledged receipt.

From the server side, the server must maintain the client connection
until the message is logged. If the message cannot be logged an instance
of an Exception must be thrown. Using this system no message will ever
be lost. A message will exist in only 3 states, 1) with the blocked
client, 2) within the client’s log queue, 3) logged on the server. For a
completely reliable solution, HA hardware and RAID media are required
which is a consideration for system designers.

## Feedback

Please report any concerns, correction, or other feedback to any of the
project leads listed on the main project page.

# Minimum Viable Product

<span style="color:#ff0000"> This page is where you should indicate what
is the minimum set of functionality that is required to make this a
useful product that addresses your core security concern. Defining this
information helps the project leader to think about what is the critical
functionality that a user needs for this project to be useful, thereby
helping determine what the priorities should be on the roadmap. And it
also helps reviewers who are evaluating the project to determine if the
functionality sufficiently provides the critical functionality to
determine if the project should be promoted to the next project
category. </span>

# Project About

<span style="color:#ff0000">

`   This page is where you need to place your legacy project template page if your project was created before October 2013. To edit this page you will need to edit your project information template. You can typically find this page by following this address and substituting your project name where it says "OWASP_Example_Project". When in doubt, ask the OWASP Projects Manager. `

Example template page:
<https://www.owasp.org/index.php/Projects/OWASP_Example_Project> </span>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")