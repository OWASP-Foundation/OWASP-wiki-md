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
<td></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

## OWASP AntiSamy Project

OWASP AntiSamy is a library for HTML and CSS encoding.

## Introduction

AntiSamy was originally authored by Arshan Dabirsiaghi
(arshan.dabirsiaghi \[at the\] gmail.com) of Contrast Security with help
from Jason Li (jason.li \[at the\] owasp.org) of Aspect Security
(http://www.aspectsecurity.com/).

## Description

The OWASP AntiSamy project is a few things. Technically, it is an API
for ensuring user-supplied HTML/CSS is in compliance within an
application's rules. Another way of saying that could be: It's an API
that helps you make sure that clients don't supply malicious cargo code
in the HTML they supply for their profile, comments, etc., that get
persisted on the server. The term "malicious code" in regards to web
applications usually mean "JavaScript." Cascading Stylesheets are only
considered malicious when they invoke the JavaScript engine. However,
there are many situations where "normal" HTML and CSS can be used in a
malicious manner. So we take care of that too.

Philosophically, AntiSamy is a departure from contemporary security
mechanisms. Generally, the security mechanism and user have a
communication that is virtually one way, for good reason. Letting the
potential attacker know details about the validation is considered
unwise as it allows the attacker to "learn" and "recon" the mechanism
for weaknesses. These types of information leaks can also hurt in ways
you don't expect. A login mechanism that tells the user, "Username
invalid" leaks the fact that a user by that name does not exist. A user
could use a dictionary or phone book or both to remotely come up with a
list of valid usernames. Using this information, an attacker could
launch a brute force attack or massive account lock denial-of-service.
We get that.

Unfortunately, that's just not very usable in this situation. Typical
Internet users are largely pretty bad when it comes to writing HTML/CSS,
so where do they get their HTML from? Usually they copy it from
somewhere out on the web. Simply rejecting their input without any clue
as to why is jolting and annoying. Annoyed users go somewhere else to do
their social networking.

The [OWASP licensing policy](OWASP_Licenses "wikilink") (further
explained in the [membership FAQ](Membership "wikilink")) allows OWASP
projects to be released under any [approved open source
license](http://www.opensource.org/licenses/alphabetical). Under these
guidelines, AntiSamy is distributed under a [BSD
license](http://www.opensource.org/licenses/bsd-license.php).

## What is AntiSamy

OWASP AntiSamy provides:

[This page](AntiSamy_Version_Differences "wikilink") shows a big-picture
comparison between the versions. Since it's an unfunded open source
project, the ports can't be expected to mirror functionality exactly. If
there's something a port is missing -- let us know, and we'll try to
accommodate, or write a patch\!

## Presentations

From OWASP & WASC AppSec U.S. 2007 Conference (San Jose, CA): [AntiSamy
- Picking a Fight with XSS
(ppt)](http://www.owasp.org/images/e/e9/OWASP-WASCAppSec2007SanJose_AntiSamy.ppt)
- by Arshan Dabirsiaghi - AntiSamy project lead

From OWASP AppSec Europe 2008 (Ghent, Belgium): [The OWASP AntiSamy
project (ppt)](http://www.owasp.org/images/4/47/AppSecEU08-AntiSamy.ppt)
- by Jason Li - AntiSamy project contributor

From OWASP AppSec India 2008 (Delhi, India): [Validating Rich User
Content
(ppt)](https://www.owasp.org/images/9/9d/AppSecIN08-ValidatingRichUserContent.ppt)
- by Jason Li - AntiSamy project contributor

From Shmoocon 2009 (Washington, DC): [AntiSamy - Picking a Fight with
XSS
(pptx)](http://www.shmoocon.org/2009/slides/OWASP%20Winter%202009%20Shmoocon%20-%20Anti%20Samy.pptx)
- by Arshan Dabirsiaghi - AntiSamy project lead

## Project Leader

[Arshan Dabirsiaghi](mailto:arshan.dabirsiaghi@gmail.com)

## Related Projects

## Ohloh

  - <https://www.ohloh.net/p/owaspantisamy>

## News and Events

  - \[26 Sep 2017\] Please update AntiSamy to 1.5.5 or later per
    [CVE-2016-10006](https://nvd.nist.gov/vuln/detail/CVE-2016-10006)
  - \[20 Nov 2013\] News 2
  - \[30 Sep 2013\] News 1

## In Print

This project can be purchased as a print on demand book from Lulu.com

## Classifications

|                                                     |                                                                                              |                                         |                                                                                  |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------- | -------------------------------------------------------------------------------- |
| align="center" valign="top" width="50%" rowspan="2" | ![Owasp-incubator-trans-85.png](Owasp-incubator-trans-85.png "Owasp-incubator-trans-85.png") | align="center" valign="top" width="50%" | ![Owasp-builders-small.png](Owasp-builders-small.png "Owasp-builders-small.png") |
| align="center" valign="top" width="50%"             | ![Owasp-defenders-small.png](Owasp-defenders-small.png "Owasp-defenders-small.png")          |                                         |                                                                                  |
| colspan="2" align="center"                          | ![Cc-button-y-sa-small.png](Cc-button-y-sa-small.png "Cc-button-y-sa-small.png")             |                                         |                                                                                  |
| colspan="2" align="center"                          | ![Project_Type_Files_CODE.jpg](Project_Type_Files_CODE.jpg "Project_Type_Files_CODE.jpg") |                                         |                                                                                  |

# How do I get started?

There's 4 steps in the process of integrating AntiSamy. Each step is
detailed in the next section, but the high level overview follows:

1.  Download AntiSamy from Maven
2.  Choose one of the standard policy files that matches as close to the
    functionality you need:
      - antisamy-tinymce-X.X.X.xml
      - antisamy-slashdot-X.X.X.xml
      - antisamy-ebay-X.X.X.xml
      - antisamy-myspace-X.X.X.xml
      - antisamy-anythinggoes-X.X.X.xml
3.  Tailor the policy file according to your site's rules
4.  Call the API from the code

### Stage 1 - Downloading AntiSamy

First, add the dependency from Maven:

<dependency>
`  `<groupId>`org.owasp.antisamy`</groupId>
`  `<projectId>`antisamy`</projectId>
</dependency>

`=== Stage 2 - Choosing a base policy file ===`

Chances are that your site's use case for AntiSamy is at least roughly
comparable to one of the predefined policy files. They each represent a
"typical" scenario for allowing users to provide HTML (and possibly CSS)
formatting information. Let's look into the different policy files:

1\) antisamy-slashdot.xml

Slashdot (http://www.slashdot.org/) is a techie news site that allows
users to respond anonymously to news posts with very limited HTML
markup. Now Slashdot is not only one of the coolest sites around, it's
also one that's been subject to many different successful attacks. Even
more unfortunate is the fact that most of the attacks led users to the
infamous goatse.cx picture (please don't go look it up). The rules for
Slashdot are fairly strict: users can only submit the following HTML
tags and no CSS:

<b/> <u/> <i/> <a/>

>

Accordingly, we've built a policy file that allows fairly similar
functionality. All text-formatting tags that operate directly on the
font, color or emphasis have been allowed.

2\) antisamy-ebay.xml

eBay (http://www.ebay.com/) is the most popular online auction site in
the universe, as far as I can tell. It is a public site so anyone is
allowed to post listings with rich HTML content. It's not surprising
that given the attractiveness of eBay as a target that it has been
subject to a few complex XSS attacks. Listings are allowed to contain
much more rich content than, say, Slashdot- so it's attack surface is
considerably larger. The following tags appear to be accepted by eBay
(they don't publish rules): <a>,...

3\) antisamy-myspace.xml

MySpace (http://www.myspace.com/) was, at the time this project was
born, arguably the most popular social networking site today. Users were
allowed to submit pretty much all HTML and CSS they want - as long as it
doesn't contain JavaScript. MySpace was using a word blacklist to
validate users' HTML, which is why they were subject to the infamous
Samy worm (http://namb.la/). The Samy worm, which used fragmentation
attacks combined with a word that should have been blacklisted (eval) -
was the inspiration for the project.

4\) antisamy-anythinggoes.xml

I don't know of a possible use case for this policy file. If you wanted
to allow every single valid HTML and CSS element (but without JavaScript
or blatant CSS-related phishing attacks), you can use this policy file.
Not even MySpace was _this_ crazy. However, it does serve as a good
reference because it contains base rules for every element, so you can
use it as a knowledge base when using tailoring the other policy files.

### Stage 3 - Tailoring the policy file

Smaller organizations may want to deploy AntiSamy in a default
configuration, but it's equally likely that a site may want to have
strict, business-driven rules for what users can allow. The discussion
that decides the tailoring should also consider attack surface - which
grows in relative proportion to the policy file.

You may also want to enable/modify some "directives", which are
basically advanced user options. [This
page](AntiSamy_Directives "wikilink") tells you what the directives are
and which versions support them.

### Stage 4 - Calling the AntiSamy API

Using AntiSamy is abnormally easy. Here is an example of invoking
AntiSamy with a policy file:

<code>

    import org.owasp.validator.html.*;

    Policy policy = Policy.getInstance(POLICY_FILE_LOCATION);

    AntiSamy as = new AntiSamy();
    CleanResults cr = as.scan(dirtyInput, policy);

    MyUserDAO.storeUserProfile(cr.getCleanHTML()); // some custom function

</code>

There are a few ways to create a Policy object. The `getInstance()`
method can take any of the following:

  - a String filename
  - a File object
  - an InputStream

Policy files can also be referenced by filename by passing a second
argument to the `AntiSamy:scan()` method as the following examples
show.:

<code>

    AntiSamy as = new AntiSamy();
    CleanResults cr = as.scan(dirtyInput, policyFilePath);

</code>

Finally, policy files can also be referenced by File objects directly in
the second parameter:

<code>

    AntiSamy as = new AntiSamy();
    CleanResults cr = as.scan(dirtyInput, new File(policyFilePath));

</code>

### Stage 5 - Analyzing CleanResults

The CleanResults object provides a lot of useful stuff.

`getErrorMessages()` - a list of `String` error messages

`getCleanHTML()` - the clean, safe HTML output

`getCleanXMLDocumentFragment()` - the clean, safe `XMLDocumentFragment`
which is reflected in `getCleanHTML()`

`getScanTime()` - returns the scan time in seconds

# Acknowledgements

## Contacting us

There are two ways of getting information on AntiSamy. The mailing list,
and contacting the project lead directly.

### OWASP AntiSamy mailing list

The first is the mailing list which is located at
<https://lists.owasp.org/mailman/listinfo/owasp-antisamy>. The list was
previously private and the archives have been cleared with the release
of version 1.0. We encourage all prospective and current users and bored
attackers to join in the conversation. We're happy to brainstorm attack
scenarios, discuss regular expressions and help with integration.

### Emailing the project lead

For content which is not appropriate for the public mailing list, you
can alternatively contact the project lead, Arshan Dabirsiaghi, at
\[arshan.dabirsiaghi\] at \[aspectsecurity.com\].

### Issue tracking

Visit the [GitHub issue
tracker](https://github.com/nahsra/antisamy/issues).

## Sponsors

The AntiSamy project is sponsored by [Contrast
Security](http://www.contrastsecurity.com/).

The initial Java project was sponsored by the [OWASP Spring Of Code
2007](OWASP_Spring_Of_Code_2007 "wikilink"). The .NET project was
sponsored by the [OWASP Summer of Code
2008](OWASP_Summer_of_Code_2008 "wikilink").

# Road Map

This section details the status of the various ports of AntiSamy.

### Grails

Daniel Bower created a [Grails
plugin](http://www.grails.org/plugin/sanitizer) for AntiSamy.

### .NET

A .NET port of AntiSamy is available now at the [OWASP AntiSamy
.NET](:Category:OWASP_AntiSamy_Project_.NET "wikilink") page. The
project was funded by a Summer of Code 2008 grant and was developed by
Jerry Hoff.

This port is no longer under active development, and is looking for a
few good developers to help make it feature-synchronized with the .NET
version. If it doesn't suit your needs, consider Microsoft's
[AntiXSS](http://blogs.msdn.com/b/securitytools/archive/2009/09/01/html-sanitization-in-anti-xss-library.aspx)
library.

### Python

A beta Python version is currently being prototyped by a few different
groups. As more information becomes available, we will post it here. If
you are interested in helping, please contact the mailing list.

### PHP

Although a PHP version was initially planned, we now suggest
[HTMLPurifier](http://htmlpurifier.org) for safe rich input validation
for PHP applications.

# Project About

## Project's Assessment

This project was assessed by [Jeff
Williams](:User:Jeff_Williams "wikilink") and his evaluation can be seen
[**here**](http://spreadsheets.google.com/ccc?key=pAX6n7m2zaTW-JtGBqixbTw).
__NOTOC__ <headertabs />

[AntiSamy Project](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Release
Quality Tool](Category:OWASP_Release_Quality_Tool "wikilink")