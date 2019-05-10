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

#### Main

__TOC__

# Summer of Code 2008 Status

<div align="right">

[Edit
Status](:Project_Information:template_JSP_Testing_Tool_Project "wikilink")

</div>

# About the Project

This project started as part of the Summer of Code 2008. The original
proposal can be found
[here](OWASP_Summer_of_Code_2008_Applications#P028_-_OWASP_UI_Component_Verification_Project_.28a.k.a._OWASP_JSP_Testing_Tool.29 "wikilink")
(much of it is duplicated below).

## Project Motivation

Cross-site scripting is one of the most pervasive web application
security vulnerabilities present in today's applications, ranking at the
top of the most recent OWASP Top Ten (2007). Recently, UI frameworks
have emerged that allow application developers to create web components
quickly and effortlessly. Java EE facilitates this ability by providing
JSP tags that can be conglomerated as a tag library, such as was done
with Java Server Faces (JSF). These tags allow developers to create rich
user interfaces by parameterizing attributes of the web component. With
the advent of this design, a unique opportunity arises to prevent
cross-site scripting. If tag libraries offered built-in protection from
cross-site scripting, then using parameterized web components to prevent
cross-site scripting could become analogous to using parameterized
queries to prevent SQL injection. However, security is not always in
mind when such tag libraries are developed and thus it is not clear
which libraries, if any, offer such built-in protection. This project
would allow developers to quickly determine the protection mechanisms
provided by any tag libraries they develop or of any third-party tag
libraries they are considering using for their application. This will
enable a push to parameterize web components which will serve to make
web applications safer.

## Project Background

This project was born out of an idea while supporting a client. The
client had created their own custom UI components based on the core JSF
components. Developers were encouraged to use this custom library as it
was thought to be “safe” from cross-site scripting. After the library
gained popularity internally, the client decided they should verify the
library did indeed protect web developers from cross-site scripting.
This testing required a lot of manual generation of test pages in order
to instantiate the various tags and thoroughly exercise each of the
various attributes. We realized that the concept of having a safe UI
component library is a sound idea and potentially popular across many
organizations. Hence, the idea was born to create a tool that could test
custom UI tag libraries to measure the level of protection from
cross-site scripting offered by the library. This project is the
implementation of that idea.

## About the Author

Jason is an Application Security Engineer at [Aspect
Security](http://www.aspectsecurity.com) during which time he has
performed code reviews, penetration testing and training at a variety of
financial, commercial, and government institutions. He is a certified
[GIAC Secure Software
Programmer](http://www.giac.org/certifications/software/gssp-java.php)
in Java and before joining Aspect, he was a Java Software Developer at a
telecommunications company and a Java course instructor for [Johns
Hopkins University](http://www.jhu.edu/). He is a core developer on the
[OWASP AntiSamy Project](:Category:OWASP_AntiSamy_Project "wikilink").
Jason earned his Post-Master's in Computer Science with a concentration
in Information Security from [Johns Hopkins
University](http://www.jhu.edu). He previously earned his his Master's
and B.S from [Cornell University](http://www.cornell.edu) (both in
Computer Science).

# Overview

<div align="center">

<https://www.owasp.org/images/7/77/OWASP_JSP_Testing_Tool_Report_Sreenshot.png>

</div>

This project uses a report in order to show the level of protection
offered by a library. The goal of the report is for developers to
quickly ascertain what protections a custom tag library offers. In
addition, the report can be used to identify specific tags or attributes
that are not safe and need a different protection mechanism (for
example, enforcing a particular code pattern or practice).

This information is displayed in tabular format with each individual tag
having its own table. Each row is an attribute of the tag, except for
the first row which is reserved for testing the text content of a tag
(for example, <b>*content*</b>). Each column is a test attack that is
attempted within the tag. Each corresponding cell’s color indicates the
status of that particular attribute against that test attack with *red*
indicating the test failed, *green* indicating the test passed and
*yellow* indicating an error occurred during testing.

## How the Report Works

The report is a combination of JSPs, HTML and JavaScript. Each *(tag,
attribute, attack)* tuple is tested in a separately generated JSP page
(based on `testcase.vm`) to provide isolation. Each test attack attempts
to execute a script function named `x()` that is defined on the test
page. The function populates an element on the page with an indicator
that the test either passed or failed. The overall report page is a
generated HTML page that contains the table described above and hidden
IFRAME with every test page. Once the pages load, the report page
evaluates the status indicated in the frame and changes the color of the
corresponding table cell accordingly. Note that clicking on any table
cell will toggle the visibility of the corresponding test case's IFRAME.

### Handling Special Case Tags

Tag libraries often have requirements or dependencies that cannot be
encapsulated in the standard TLD. For example, an attribute may be of
type java.lang.String, but in reality the implementation limits the
attribute to a choice of select values. Another example is that the tag
may have to be embedded in another tag (for example, a tag representing
a selection option may have to be embedded in a combo box tag). To
account for these special cases, the code utilizes a tag properties
configuration file that allows users to specify values to be used in
required attributes or to configure special prefixes and suffixes to
enclose tags. A graphical user interface (see below) is provided as part
of this tool to facilitate the creation of a configuration file for this
purpose.

### Handling Errors

The web application configures an error page (`error.jsp`) which handles
the inevitable application errors from improper usage of custom tags.
The error page generates a status indicator that includes the exception
stack trace, both of which can be read by the containing report page. In
addition to appearing *yellow*, the title attribute of the corresponding
table cell is populated with the exception stack trace and will appear
in most browsers as a tooltip. As the project matures, some mechanism
will be provided to address tag generation errors (see later section).

### Handling OnEvents

One of the many ways JavaScript can be executed is through event
handlers such as `onblur` or `onmouseover`. To handle this, at the end
of each test page is a script which examines all the HTML tags generated
by the custom JSP tag and looks for any attributes matching one of the
defined JavaScript event handlers. Upon finding any event handlers, the
script invokes the handler to test if the attack is propagated. This
simulates the attack being triggered by a user event.

### Browser Differences

Note that because this report strategy relies heavily on a web browser,
the results may differ from browser to browser. For example, the CSS
based attack renders successfully in Internet Explorer but not in
Firefox. The report could be made browser agnostic by instead searching
through the generated JSP content. That approach has tradeoffs as it
raises the possibility of false positives. By keeping the browser
involved, organizations can test against browsers they support and be
assured that if the attack test case executed, it is an issue.

## How the Report is Generated

The report generation is broken down into three phases:

1.  Parsing of the Tag Library Document (TLD)
2.  Generation of Test Pages
3.  Serializing the Report

### Parsing of the Tag Library Document

Ideally, this project would have leveraged existing code to parse TLDs.
Application servers routinely parse TLDs in order to compile JSPs that
use tag libraries and several application servers are open source
(Tomcat, JBoss, etc). However, upon further investigation, most existing
implementations were tightly intertwined with the rest of the
application server. Nonetheless, the core Java EE API includes several
classes to encapsulate tag information (see the javax.servlet.jsp.tagext
package). This project used as many of these existing classes as
possible to both mitigate the volume of work and also to permit
leveraging existing application server code in the future. The code uses
JAXP, which has been implemented in standard Java since version 1.4, to
parse TLD documents.

### Generation of Test Pages

The code uses a report and test case template that is populated using
Apache Velocity. Using the encapsulated TLD metadata from the parsed
TLD, the code iterates through all tags and attributes to construct test
case pages for each test attack. The test attacks come from an XML file
(`attacks.xml`) which represents a repository of various cross-site
scripting attacks that invoke the `x()` function.

### Serializing the Report

After the report HTML and test case JSPs are generated, they must be
deployed to a JSP container in order to be rendered. The code uses an
embedded instance of Tomcat to deploy the test case JSPs and then
serializes them by retrieving the rendered response from Tomcat and
writing it to a local file.

# Running the Tool

The section below outlines the system requirements and procedures for
running the tool. The tool was written with Java 1.4 compatibility in
mind, though execution in this environment has not been tested.

## Requirements

The tool requires that an appropriate Java Development Kit is installed
along with an Apache Tomcat Runtime (\>=6.0.16). In addition, the
following third-party libraries are required:

  - [Apache Commons HTTP
    Client](http://hc.apache.org/httpclient-3.x/index.html) (\>=3.1)
  - [Apache Commons IO](http://commons.apache.org/io/) (\>=1.4)
  - [Apache Velocity](http://velocity.apache.org/) (\>=1.5)
  - [Apache Commons Codec](http://commons.apache.org/codec/) (\>=1.3)
    (used by Apache Velocity)
  - [Apache Commons Collections](http://commons.apache.org/collections/)
    (\>=3.2.1) (used by Apache Velocity)
  - [Apache Commons Lang](http://commons.apache.org/lang/) (\>=2.4)
    (used by Apache Velocity)
  - [Jakarta ECS](http://jakarta.apache.org/ecs/index.html) (\>=1.4.2)
  - [Jakarta ORO](http://jakarta.apache.org/oro/) (\>=1.0.8)
  - [OWASP ESAPI](:Category:OWASP_Enterprise_Security_API "wikilink")
    (\>=1.3)

Older versions of the runtimes and libraries may be compatible, but were
not tested.

## Project Layout

The project source tree is laid out in the following directories:

  - `src/`
  - `docs/`
  - `lib/`
  - `resources/`
  - `standalone/`
  - `template/`

## Using the Tool

The source tree includes an Ant build file to compile and run the
project. To make use of the included build file, the required libraries
enumerated above should be placed in the `lib` directory. In addition,
the `tomcat.home` (Tomcat runtime directory) and `jdk.home` (JDK home
directory) properties should be set in the build file. The build file
defines three tasks relevant to running the tool: `run-tag-report`,
`run-full-report` and `run-gui`.

### run-tag-report

This task creates a report on a specific tag from a tag library. This is
useful for retesting a specific tag's status after modifications of the
tag implementation have been made. The parameters for this task are:

  - the location of the tag library definition file
  - the location of the tag properties configuration file
  - the location of the output directory
  - the name of the tag to test

### run-full-report

This task creates a report on an entire tag library. Note that this task
can take an extremely long time to execute. For example, this task run
on the the JSF HTML Basic tag library ran for over 24 hours on an
average desktop machine. The parameters for this task are:

  - the location of the tag library definition file
  - the location of the tag properties configuration file
  - the location of the output directory
  - the name of the tag to test

### run-gui

This task runs the graphical user interface for creating tag properties
configuration files. The parameters for this task are:

  - the location of the tag properties configuration file
  - the location of the tag library definition file

# Future Vision

While tag libraries offer a means to parameterize web components and
potentially better protection from XSS, there are still applications
that use raw JSPs and scriptlets. With the insight gained from
generating test cases, the JSP Testing Tool should be enhanced to test
not only pages using JSP tag libraries, but also basic JSPs as well. One
possible strategy is to create a wrapper HttpServletRequest class that
overrides methods to provide input directly from test cases generated
from the earlier stages of this project. A similar wrapper
HttpServletResponse class can then be used to test the results. The tool
could then be used to quickly test the XSS protection level of any Java
EE application that uses JSP technology. Unlike automated web scanners,
this tool enhancement would have the benefit of internal insight to the
application to determine injectable parameters. Additionally, this tool
enhancement would be an improvement to static code analysis as it could
reduce the number of false positives with the ability to invoke actual
rendering of the HTTP response.

## Feature Enhancements

These ideas are features that are recognized as desirable but will not
be considered until the tool can test a reasonable JSP tag library.
Currently, that measuring stick is the JSF Core library.

### Programmatic Tag Generation

One of the limitations in the current tag generation is that tags are
generated relatively blindly. This strategy can result in errors when
supplied tag attributes do not conform to required formats. One possible
strategy is to integrate a JSP/Servlet container where tags can be
generated and rendered programmatically. This approach was deemed too
complicated for the first iteration of this tool.

### Attribute Permutation

Another issue is that different permutations of attributes may result in
different behavior which can affect the outcome of a test case. This
issue can be resolved by generating multiple permutations of attributes,
but this becomes infeasible as the number of attributes grows.

#### Project Identification

<headertabs/>

[JSP Testing Tool Project](Category:OWASP_Project "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")