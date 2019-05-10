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

## Overview

Developers consistently implement sporadic, ad-hoc input validation
mechanisms for web applications. Lack of a centralized and well-defined
input validation mechanism opens the application to a variety of
attacks: including SQL Injection, Cross Site Scripting (XSS), and
Command Injection. The OWASP Stinger Project aims to develop a
centralized input validation component which can be easily applied to
existing or developmental applications. Using a declarative security
model, Stinger has the ability to validate all HTTP requests coming into
an application. Stinger is such a simplistic yet strong validation
engine that organizations have begun integrating it into their software
development life-cycle.

## Project Lead

Current Project Leader: [Jeroen de Beer](mailto:jeroen.debeer@anoigo.nl)

Previous Project Leader: [Wesley West](mailto:Wesley.M.West@ge.com).

## License

Stinger is offered under the
[LGPL](http://www.gnu.org/copyleft/lesser.html). For further information
on OWASP licenses, please consult the [OWASP
Licenses](OWASP_Licenses "wikilink") page.

## Versions

:\*[Click here](OWASP_Stinger_Version_2 "wikilink") to view the OWASP
Stinger 2.x Project page

:\****Deprecated*** [Click here](OWASP_Stinger_Version_1 "wikilink") to
view the OWASP Stinger 1.x Project page

:\****Defunct*** [Click here](OWASP_Stinger_Version_3 "wikilink") to
view the OWASP Stinger 3.x Project page

## Stinger News

`'''Latest version available! - 25 March 2009 '''`

Well, I have updated the site with version 2.2.2 of Stinger for JDK 1.4.
There have been some questions about why I have updated from version
2.2, rather than 2.5. This is because I have only been working with the
version supporting JDK 1.4, as that's what my environments are. This
version includes the fix to the MutableHTTPRequest to support multiple
parameter values, as well as the fix to address the multipart
vulnerability as included in 2.5.

I am trying to get the request object changes made to the later code to
allow for a 2.6 release. But my schedule isn't allowing me much time to
work on Stinger lately.

`'''Major Flaw: New versions coming soon! - 26 August 2008 '''`

In working with Stinger over the past year I have found some issues in
the way that Stinger implemented handling of the HTTP request. In short,
it overlooked the fact that a parameter can have multiple values. This
has been corrected and will be available for download within the next
week or two.

**`Security``   ``Fix:``   ``Stinger``   ``2.5``   ``Released``   ``-``
 ``13:32,``   ``12``   ``August``   ``2007``   ``(EDT)`**

Meder Kydyraliev recently brought to my attention a flawed assumption in
the implementation of a J2EE filter-based input validation solution.
Much of the J2EE HttpServletRequest API assumes the content of a POST
request is form-urlencoded. Calls like "getParameter(String)" and
"getParameterNames()" will only return values of a form-urlencoded POST
request. Consequently, these API will return nothing of the body of the
request is multipart encoded, allowing the attacker to bypass
filter-based validation.

[Click
here](http://www.owasp.org/index.php/Bypassing_servlet_input_validation_filters_%28OWASP_Stinger_%2B_Struts_example%29)
for the original write-up provided by Meder Kydyraliev.

[Click here](http://www.owasp.org/index.php/OWASP_Stinger_Version_2) to
download Stinger 2.5

**`Stinger``   ``2.4``   ``Released``   ``-``   ``13:58,``   ``21``
 ``May``   ``2007``   ``(EDT)`**

The OWASP Stinger Project is proud to release Stinger 2.4. As noted in
RC1, this release is intended to address code quality issues as well as
implement several community suggested updates. The following is a list
of notable changes:

:\*Backported the Stinger 3.0 "DROP/CONTINUE/PROCESS" doAction() logic.
No need for "BreakChainException"

:\*Cleaned up some code quality issues (removed all instances of
System.out and printStackTrace, using interfaces properly, fixed
synchronization issues)

:\*Added the ability to define an "exclude" list which searches for
patterns within a pattern. For example, if we allow the character '.'
and the character '/', we may want to prevent instances of '../'. This
can now be done by adding an "<exclude>../</exclude>" tag underneath the
"<regex></regex>" element of a rule. See the example "stinger.xml" file
included with the Stinger Eclipse project for more information.

:\*Modified the Log action to hashsession ID's before logging them as
well as fixed "getHandler()" property default bug

:\*The inclusion of the "exclude-set" value which tells Stinger to do
nothing with these pages. Useful for patterns that cover too much (ex.
\*.\*)

:\*The stinger.xml file is expected to be found relative to /WEB-INF.
This means that we simply set the filter-init "config" parameter to
"stinger.xml" rather than "C:\\Documents and
Settings....\\WEB-INF\\stinger.xml"

:\*Removed the "DisplayMessage" action as it is not very useful

:\*Added better logging throughout the code base

You can get the latest Stinger release
[here](http://www.owasp.org/index.php/OWASP_Stinger_2_Releases).

**`Stinger``   ``2.4``   ``RC1``   ``Released``   ``-``   ``11:40,``
 ``29``   ``January``   ``2007``   ``(EST)`**

The OWASP Stinger Project is proud to release Stinger 2.4 RC1. This
release is largely intended to address some code quality issues.

The following is a list of notable changes:

:\* We now allow for an "exclude" option for each parameter. After
defining a regular expression for a parameter, we can now define strings
that should \*NOT\* exist within the input. For example, let us assume
our regular expression accepts all numbers, characters, a period, and a
slash (/). However, note that "aaa../../etc/passwd" would be considered
a valid input. Therefore, we can specify an "exclude" tag to prevent
such input:

`...`
<rule>
`   `<name>`file`</name>
`   `<regex>`filetext`</regex>
`   `<exclude>`../`</exclude>
`...`

:\* The "invalidate" action will properly clear the cookie from the
user's browser.

The current list of tasks to complete is as follows:

:\* Remove the absolute path dependence when specifying the Stinger
configuration file in web.xml

As always, let me know if you have any suggestions for improving the
Stinger 2.4 release\!

[Click here](http://www.owasp.org/index.php/OWASP_Stinger_2_Releases)
for the Stinger 2.x release page.

**[Click here for old
news...](http://www.owasp.org/index.php/Stinger_News)**

## Feedback and Participation

We hope you find Stinger useful. Please contribute back to the project
by sending your comments, questions, and suggestions to the Stinger
mailing list. Thanks\!

To join the OWASP Stinger mailing list or view the archives, please
visit the [subscription
page](http://lists.owasp.org/mailman/listinfo/owasp-stinger).

## Donations

The Open Web Application Security Project is purely an open-source
community driven effort. As such, all projects and research efforts are
contributed and maintained with an individual's *spare time.* If you
have found this or any other project useful, please support OWASP with a
[donation](https://www.owasp.org/index.php/Contributions).

## Project Sponsors

None at this time

[Category:OWASP Validation
Project](Category:OWASP_Validation_Project "wikilink")