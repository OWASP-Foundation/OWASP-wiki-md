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

Welcome to the OWASP page presenting [Fiddler](http://www.fiddler2.com)
addons for security testing. This is home of the
[Watcher](Projects/OWASP_Watcher_Project "wikilink") and
[x5s](Projects/OWASP_X5s_Project "wikilink") security testing tools
built as extensions for the [Fiddler](http://www.fiddler2.com) HTTP
proxy. A quick overview:

  - [Watcher](Projects/OWASP_Watcher_Project "wikilink") is a passive
    vulnerability scanner for Web applications
  - [x5s](Projects/OWASP_X5s_Project "wikilink") is an active cross-site
    scripting testing tool for Web applications
  - [Fiddler](http://www.fiddler2.com) is an HTTP debugging proxy with
    support (and scripting support) for traffic interception, traffic
    modification, replay, comparison, data parsing, offline usage,
    NTLM/basic/digest auth, and much more

## Fiddler HTTP Proxy

The [Fiddler](http://www.fiddler2.com) HTTP debugging proxy has a long
history with a wide user base and was chosen as the platform for
building security testing tools found on this page. By leveraging
[Fiddler](http://www.fiddler2.com) we can focus our efforts on the
security testing logic and let the proxy do its job.

## Watcher

![watcher-config.png](watcher-config.png "watcher-config.png")
![watcher-checks.png](watcher-checks.png "watcher-checks.png")
![WatcherResults.png](WatcherResults.png "WatcherResults.png")

***Visit the [Watcher project page on
CodePlex](http://websecuritytool.codeplex.com/)***

Ever find yourself looking for that showstopper exploit in a Web-app,
and forgetting to check out all the low-hanging fruit? That's intitially
why we created Watcher. For one thing, we don't want to manually inspect
a Web-app for many of these issues (cookie settings, SSL configuration,
information leaks, etc), but we still want to find and fix them. Watcher
provides this level of security analysis, plus provides hot-spot
detection to help pen-testers focus in on the spots that will lead to
that showstopper exploit.

  - [Descriptions of the security
    checks](http://websecuritytool.codeplex.com/wikipage?title=Checks)
  - [Detailed
    Documentation](http://websecuritytool.codeplex.com/documentation?referringTitle=Home)
  - [Download
    link](http://websecuritytool.codeplex.com/releases/view/22212)

The security field today has several good choices for HTTP proxies which
assist auditors and pen-testers. We chose to implement this as a plugin
for Fiddler which already provides the proxy framework for HTTP
debugging. Some reasons to use Watcher include:

  - **Safe for the Cloud and hosting environments**

Being passive gives Watcher several advantages - when applications live
in the Cloud there's often a risk that running security testing could
damage the shared infrastructure. However, using a passive tool like
Watcher ensures that there's no chance of damaging Cloud-like
infrastructure.

  - **Safe for production environments**

Watcher does not attack web-applications with loads of intrusive
requests, it doesn't modify inputs to your application. Unlike crawlers
and web-application scanners, Watcher does not generate dangerous
traffic. It quietly analyzes normal user-interaction and makes educated
reports on the security of an application.

  - **Low overhead, no training**

If you’re building web-applications you already have a development and
test staff. Fiddler has been valuable to dev and test for years as a
general-purpose HTTP debugging proxy. Watcher fits seamlessly into the
picture, providing valuable security insight with no special training
requirements, dedicated machines, or other resources.

### User Interface

The main configuration screen for Watcher makes it as simple as clicking
the 'enable' button. Once you do that, all HTTP traffic starts getting
observed and analyzed for security issues. You can also narrow Watcher's
scope by specifying an \*\*\*origin\*\*\* domain that will be the focus
of analysis, all others being ignored. Custom Watcher configurations can
also be saved so you don't need to re-enter the same information each
time you launch the tool.

To get more granular, the checks configuration screen allows you enable
and disable individual checks. Some checks even come with their own
configurations such as noise reduction or string analysis.

The most interesting screen will probably be the results screen, where
each finding is displayed. From here you can remove findings, filter by
severity, and export to XML, HTML, or TFS.

### Source Code

Watcher has been written in C\# for .NET. The source code is hosted by
CodePlex in a Mercurial repository which can be cloned at:

Mercurial repo: <https://hg01.codeplex.com/websecuritytool>

Or simply browse the source code at:
<http://websecuritytool.codeplex.com/SourceControl/BrowseLatest>

Watcher itself can be easily extended to include new checks.

### Extensibility

Watcher was built to be easily extended with new checks. You should be
able to easily add custom checks and have them included in all of
Watcher's functionality. A good way to get started is to [browse the
code](http://websecuritytool.codeplex.com/SourceControl/BrowseLatest)
looking at the **Watcher Check Library**, and picking one of the simpler
checks to use as a template. That will show you the basic structure of
what's required. I should really write a tutorial about this... added to
the roadmap.

### List of Security Checks

The following is a list of [security checks for
Watcher 1.5](http://websecuritytool.codeplex.com/wikipage?title=Checks)
as of December 6, 2010.
[Details](http://websecuritytool.codeplex.com/wikipage?title=Checks) are
available over at Watcher's Codeplex page.

1.  ASP.NET checks
    1.  Insecure VIEWSTATE tampering possibility
2.  Charset checks
    1.  Charset declaration was not UTF-8
    2.  A Charset mismatch was identified
3.  Cookie checks
    1.  Loosely scoped cookie was identified
    2.  Cookie's secure flag was not set
    3.  Cookie's HttpOnly flag was not set
4.  Cross-Domain checks
    1.  Cross-domain CSS resource
    2.  Cross-domain JavaScript src reference
    3.  Cross-domain JavaScript DOM reference
    4.  Cross-domain Form action
5.  Flash checks
    1.  Flash allows JavaScript access
    2.  Flash Crossdomain.xml file contains insecure domain references
6.  HTTP Header checks
    1.  Cache-Control not set to 'no-store'
    2.  Content-Type declaration missing
    3.  X-XSS-PROTECTION disables Internet Explorer protection
    4.  X-XFRAMES-OPTIONS not set to prevent click-jacking
    5.  X-CONTENT-TYPE-OPTIONS not set to prevent MIME-type sniffing
    6.  Weak authentication
7.  Information Disclosure checks
    1.  Information disclosure in error messages
    2.  Information disclosure in database error messages
    3.  Information disclosure in comments
    4.  Information disclosure in HTTP referrer
    5.  Information disclosure in URL parameters
8.  Java checks
    1.  Java Server MyFaces vulnerable to VIEWSTATE tampering
9.  Javascript checks
    1.  Use of javascript eval methods
    2.  Use of javascript domain lowering techniques
10. Sharepoint checks
    1.  Sharepoint insecure document library
11. Silverlight checks
    1.  Silverlight clientaccesspolicy.xml/crossdomain.xml contains
        insecure domain references
    2.  Silverlight settings allow javascript access
12. SSL checks
    1.  Insecure transition from HTTP to HTTPS
    2.  Insecure transition from HTTPS to HTTP
    3.  SSL certificates failed validation
    4.  Legacy SSL v2 protocol was accepted by server
13. Unicode checks
    1.  Ill-formed UTF-8 byte sequence was identified
14. User-Controlled Input checks
    1.  A user-controlled charset declaration was identified
    2.  A potential cookie-poisoning vulnerability was found
    3.  A potential XSS vulnerability was found
    4.  A likely XSS vulnerability was found in a user-controlled page
        event
    5.  A potential XSS vulnerability was found through a
        user-controlled javascript reference
    6.  A user-controlled open redirect was identified

## x5s

![x5s-config-screen.png‎](x5s-config-screen.png‎
"x5s-config-screen.png‎") ![X5s-char-screen.png‎](X5s-char-screen.png‎
"X5s-char-screen.png‎") ![X5s-results-screen.png](X5s-results-screen.png
"X5s-results-screen.png") ![X5s-tutorial.png](X5s-tutorial.png
"X5s-tutorial.png")

***Visit the [x5s project page on CodePlex](http://xss.codeplex.com/)***

X5s can help you find encoding issues that lead to XSS (cross-site
scripting) attacks. It auto-injects test probes into every parameter of
an HTTP request and analyzes responses to find where probes were not
safely encoded.

  - [Quickstart
    Tutorial](http://xss.codeplex.com/wikipage?title=Tutorial&referringTitle=Home)
  - [Detailed
    Documentation](http://xss.codeplex.com/documentation?referringTitle=Home)
  - [Download link](http://xss.codeplex.com/releases/view/43170)

x5s is a [Fiddler](http://www.fiddler2.com) addon which aims to assist
penetration testers in finding cross-site scripting vulnerabilities.
This is not a point and shoot tool, it requires some understanding of
how encoding issues lead to XSS, and it requires manual driving. See the
Quickstart Tutorial to jump right in but be ready to do a little work.
It's main goal is to help you identify the hotspots where XSS might
occur by:

  - Detecting where safe encodings were not applied to emitted
    user-inputs
  - Detecting where Unicode character transformations might bypass
    security filters
  - Detecting where non-shortest UTF-8 encodings might bypass security
    filters

It injects ASCII to find traditional encoding issues, and it injects
special Unicode characters and encodings to help an analyst identify
where XSS filters might be bypassed. The approach to finding these
hotspots involves injecting single-character probes separately into each
input field of each request, and detecting how they were later emitted.
The focus is on reflected XSS issues however persisted issues can also
be detected. The idea of injecting special Unicode characters and
non-shortest form encodings was to identify where transformations occur
which could be used to bypass security filters. This also has the
interesting side effect of illuminating how all of the fields in a
Web-app handle Unicode. For example, in a single page with many inputs,
you may end up seeing the same test case get returned in a variety of
ways – URL encoded, NCR encoded, ill-encoded, raw, replaced, dropped,
etc. In some cases where we’ve had Watcher running in conjunction, we’ve
been able to detect ill-formed UTF-8 byte sequences which is indicative
of ‘other’ problems.

x5s acts as an assistant to the security tester by speeding up the
process of parameter manipulation and aggregating the results for quick
viewing. It automates some of the preliminary XSS testing work by
enumerating and injecting canaries into all input fields/parameters sent
to an application and analyzing how those canaries were later emitted.
E.g. Was the emitted output encoded safely or not? Did an injected
character transform to something else?

### Semi-Automated XSS Test Cases

x5s does not inject XSS payloads - it does not attempt to exploit or
confirm an XSS vulnerability. It's designed to draw your attention to
the fields and parameters which seem likely candidates for
vulnerability. A security-tester would review the results to find issues
where special characters were dangerously transformed or emitted without
a safe encoding. This can be done by quickly scanning the results, which
have been designed with the intention of providing quick visual
inspection. Results filters are also included so the tester could simply
click show hotspots to see only the potential problem areas. After
identifying a hotspot it's the tester's job to perform further
validation and XSS testing.

The types of test cases that x5s includes:

1.  Traditional test cases - characters typically used to test for XSS
    injection such as \<, \>, ",and ' which are used to control HTML,
    CSS, or javascript;
2.  Transformable test cases - characters that might uppercase,
    lowercase, Normalize, best-fit map, or other wise transform to
    completely different characters, E.g. the Turkish 'İ' which will
    lower-case to 'i' in culture-aware software.
3.  Overlong UTF-8 test cases - non-shortest UTF-8 encodings of the
    'traditional' test cases noted above. E.g. the ASCII \< is 0x3C
    normally and 0xC0 0xBC in non-shortest form UTF-8.

It does not inject any XSS payloads in testing. It simply injects
canaries - test strings which include a single-character probe. x5s will
replay a new request for each user-controlled input parameter an
application accepts. In this way each parameter gets tainted and tested
independently of the others.

We wanted to automate the tedious testing process of injecting probes
into every input parameter of a Web-app, followed by trying to figure
out how that probe was later emitted by the Web-app. However, we did not
want to rely on a fully automated scan. Instead we wanted some control
and insight into each test case. Was it encoded safely or not? Was it
transformed into something else? Was it replaced or dropped? In some
cases, testing for XSS involves what can be over-simplified as a 3-step
process:

1.  Test user-controlled input using special characters like \<, \>, ',
    and ".
2.  Review how the output encodes the special characters.
3.  Inject a full XSS payload to validate that a vulnerability exists.

x5s will automate the first two steps of this process. This has been
useful in saving time and effort, and in reducing the potential problem
areas to a small, manageable set of 'hot-spots'. Once a hot-spot has
been identified, the pen-tester can perform the final step of
validation.

### Why should you use this tool?

x5s was first and foremost designed to find encoding and character
transformation issues that can lead to XSS vulnerability, and present
them in a visual way where they could be reviewed with a quickness. Many
tools exist for testing Web-applications to find cross-site scripting
bugs. There are browser plugins, Web-scanners, and static code
analyzers. We use whatever suits us in a given situation and produces
the output we're interested in receiving. We developed x5s for
penetration testers and other security-minded persons who already know
how to find and exploit an XSS vulnerability. The tool has a slightly
different bent than other tools we've used. It's main goals include:

1.  Automate finding the encoding issues that can lead to XSS.
2.  Identify where character transformations occur by injecting
    multibyte characters such as higher Unicode code points and
    non-shortest form character encodings.

Injecting probes to find encoding issues makes sense for finding XSS
hotspots, but why should you be concerned with character
transformations? Bypassing an XSS filter would be a big problem for any
application. By detecting where characters transform, x5s can help you
identify where your filters might be bypassed when special characters or
encodings are used.

Extensibility was intended as well, so that new request parsers could be
included in x5s. So in addition to JSON, and traditional form data, new
or custom protocols can be considered and used in testing. The character
mappings used in the test case configuration are also extensible, by
modifying the XML file that ships with x5s.

#### FAST - Project About

#### Watcher - Project About

#### X5s - Project About

__NOTOC__ <headertabs />

[Fiddler Addons for Security Testing
Project](Category:OWASP_Project "wikilink") [Watcher
Project](Category:OWASP_Project "wikilink") [X5s
Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink") [OWASP Alpha
Quality Document](Category:OWASP_Alpha_Quality_Document "wikilink")
[OWASP Alpha Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[Category:OWASP_Download](Category:OWASP_Download "wikilink")