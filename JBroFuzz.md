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

This project is currently inactive. If you would like more information
on the OWASP JBroFuzz Project, please [Contact
Us](http://owasp4.owasp.org/contactus.html).

![JBroFuzz-ScreenShot.png](JBroFuzz-ScreenShot.png
"JBroFuzz-ScreenShot.png")![JBroFuzz-SplashScreen.jpg](JBroFuzz-SplashScreen.jpg
"JBroFuzz-SplashScreen.jpg")![Jbrofuzz-fuzz-header.png](Jbrofuzz-fuzz-header.png
"Jbrofuzz-fuzz-header.png")![Jbrofuzz-results.png](Jbrofuzz-results.png
"Jbrofuzz-results.png") **JBroFuzz** is a web application fuzzer for
requests being made over [HTTP](http://en.wikipedia.org/wiki/HTTP) or
[HTTPS](http://en.wikipedia.org/wiki/Https). Its purpose is to provide a
single, portable application that offers stable web protocol fuzzing
capabilities.

**Current version is 2.4**. Get it from the [SourceForge Download
Section](http://sourceforge.net/projects/jbrofuzz/).

![
link=<http://sourceforge.net/project/platformdownload.php?group_id=180679>](JBroFuzzDownload.png
" link=http://sourceforge.net/project/platformdownload.php?group_id=180679")

**Release Notes (2.4):**

  - Commandline support - main class analyzing and executing the
    commandline options
  - Added --no-execute option to command line support
  - Added "Connection: close" preference option to be added to the
    headers automatically
  - Massive UI revamp for Fuzzing Tab: Contains 3 Sub-Tabs: Input,
    Output, On the wire
  - Introduction of Fuzzing Transforms for those double-URL,
    triple-Base64 encodings
  - Added HTTP proxy support & authentication for checking updates
  - EncoderHashWindow improvements in keeping history within different
    row selections
  - Fixed ZBase32 Encoding/Decoding to work as Phil wants it to
  - Prefix/Suffix in Fuzzer Transforms:
    <http://www.owasp.org/index.php/OWASP_JBroFuzz_Tutorial#Added_Fuzzer_Transformations>
  - Added a plain-text encoder, similar to Zero-Fuzzer for theoretical
    completeness
  - Fixed a bunch of supposed "security holes" reported by static
    analyzers
  - Small Oracle payloads update

## Vulnerability Identification

JBroFuzz generates requests, puts them on the wire and records the
corresponding responses received back. It does not attempt to identify
if a particular site is vulnerable or not; this requires further human
analysis.

However, certain payloads included in fuzzers that can be used to
generate requests (e.g. XSS) are crafted to attempt to successfully
exploit flaws. Such flaws represent previously known vulnerabilities for
web applications. JBroFuzz groups fuzzers with their corresponding
payloads into a number of categories, depending on previously known
vulnerabilities.

Thus, the human analyst would have to select the fuzzers to use in order
to test against a particular set of vulnerabilities and review the
results in order to recognize if exploitation succeeded or not.

## JBroFuzz Documentation

### Online Documentation

[JBroFuzz Tutorial](OWASP_JBroFuzz_Tutorial "wikilink")

[Frequently Asked Questions (FAQs)](OWASP_JBroFuzz_FAQ "wikilink")

[JBroFuzz Install Guide](OWASP_JBroFuzz_Install_Guide "wikilink")

[JBroFuzz Payloads and
Fuzzers](OWASP_JBroFuzz_Payloads_and_Fuzzers "wikilink")

### Built-in Documentation

Frequently Asked Questions: `Help -> FAQ`

Help Topics: `Help -> Topics`

## Application Overview

The components of JBroFuzz are presented into tabs, with more options
(encodings, hash calculator, headers from popular browsers) available
under the `Tools` option. The basic components are:

**Fuzzing** The fuzzing tab is the main tab of JBroFuzz, responsible for
all fuzzing operations performed over the network. Depending on the
fuzzer payloads selected, it creates the malformed data for each
request, puts it on the wire and writes the response to a file.

**Graphing** The graphing tab is responsible for graphing (in a variety
of forms) the responses received while fuzzing. This tab can offer a
clear indication of a response that is different then the rest received,
an indication of further examination being required.

**Payloads** The payloads tab is a collection of fuzzers with their
corresponding payloads that can be used while fuzzing. Payloads are
added to the request in the fuzzing tab; a more clear view of what
payloads are available, how they are grouped and what properties each
fuzzer has can be seen in this tab.

**Headers** The headers window is a collection of browser headers that
can be used while fuzzing. Headers are obtained from different browsers
on different platforms and operating systems. This tab is provided, as
many web applications respond differently to different browser
impersonation attacks.

**System** The system tab represents the logging console of JBroFuzz at
runtime. Here you can access java runtime information, see any errors
that might occur and also track operation in terms of events being
logged.

## Roadmap

Building a web application fuzzer that sits at the rim of breaking known
protocol specifications, can be a very time consuming exercise. Thus,
JBroFuzz has a roadmap, based on how much time it would take to achieve
each task.

You can find the [project roadmap
here](http://www.owasp.org/index.php/Category:OWASP_JBroFuzz_Project_-_Roadmap).

## Source Code

JBroFuzz is written in Java and requires a [1.6
JRE/JDK](http://www.java.com) (or higher) installed, to run. It is
constituted of more or less 70 classes, using, in total, 10 external
libraries. It builds under [Apache Ant](http://ant.apache.org/).

**[SVN (Subversion)](http://sourceforge.net/svn/?group_id=180679)** is a
tool used by many software developers to manage changes within their
source code tree. This project's SourceForge.net Subversion repository
can be checked out through SVN with the following instruction set:

` svn co  `<https://svn.code.sf.net/p/jbrofuzz/code/>`  jbrofuzz `

If the above sounds a bit greek, you can also browse through the
complete source code at:

<http://jbrofuzz.svn.sourceforge.net/viewvc/jbrofuzz/>

## Feedback and Participation

We hope you find the OWASP JBroFuzz Project useful. Please contribute to
the project by volunteering for one of the tasks on the roadmap, sending
your comments, questions, and suggestions to `subere@uncon.org`.

To join the OWASP JBroFuzz Project mailing list or view the archives,
please visit the [subscription
page.](http://lists.owasp.org/mailman/listinfo/owasp-jbrofuzz)

[Release SHA1SUM](OWASP_JBroFuzz_Hashes "wikilink")

\-- ==== Project Identification ==== --\>

\-- ==== Project Identification ====  --\>

\---- ==== Project Details ====  ---\>

#### Project About

__NOTOC__ <headertabs/>

[JBroFuzz](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Release
Quality Tool](Category:OWASP_Release_Quality_Tool "wikilink")