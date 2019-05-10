### News

15<sup>th</sup> February 2008 - [New version of OWASP ORIZON FRAMEWORK
TOOL](http://orizon.svn.sourceforge.net/viewvc/orizon/orizon_package/src/org/owasp/orizon/demo/jCrawlerDemo.java?view=markup&pathrev&9)
with the source code crawling APIs available for Java and CSharp.

3<sup>rd</sup> November 2007 - Orizon version 0.50 is the final
deliverable for Spoc 2007. I did not reach all the goals I draw for my
self back when Spoc started. After all, I'm really happy seeing the
final project status. If I had more support from community may be things
would go in a better way... however.

15<sup>th</sup> October 2007 - Official roadmap is located
[here](http://orizon.sourceforge.net/roadmap.html). Please refer to this
page for project milestones. I deleted support for C language to
milestones because more effort I'm spending to make dawn quite usable. I
think having dawn 50% working is more valuable than having partial C
language support.

11<sup>st</sup> October 2007 - Dawn engine is now operative. It creates
helper applications from Java methods, it compiles them, it runs them
and collecting their output it scans it for XSS attack pattern to
appear. Further improvement will follow asap :)

22<sup>nd</sup> August 2007 - Orizon release 0.40 is available at
[sourceforge](http://orizon.sf.net/) site. This is an important
milestone in the development process. Safe coding recipes APIs are
working and the class handling source code being reviewed is now capable
of applying a check over the source code xml representation. In fact,
**static code review** is possible by now.

13<sup>th</sup> July 2007 - The project status as Spoc 2007 start is
summarized in the following:

  - java sources are translated into XML using JDK6 APIs;
  - Orizon classes are in a refactoring stage in order to reflect a
    better approach in design phase;
  - library containing checks is now a Zip file instead of a plain XML
    file. The library file will contain "receipts", XML files containing
    security checks grouped by category.

What is missing by now is some checks. I'm looking the web in order to
collect "coding best practices" and trying to formalize them in XML.

### Next actions

<table border="1">

<tr>

<th>

Id

</th>

<th>

Description

</th>

<th>

Priority

</th>

<th>

Blocking?

</th>

</tr>

<tr>

<td>

OR-1

</td>

<td>

Collecting safe coding best practices

</td>

<td>

High

</td>

<td>

No

</td>

</tr>

<tr>

<td>

OR-2

</td>

<td>

Creating APIs for XML reports

</td>

<td>

Low

</td>

<td>

No

</td>

</tr>

<tr>

<td>

OR-3

</td>

<td>

Creating code to handle dynamic test cases generation

</td>

<td>

Medium

</td>

<td>

No

</td>

</tr>

</table>

### SpoC 2007 Goals

<table border="1">

<tr>

<th>

Goal

</th>

<th>

Completeness (%)

</th>

</tr>

<tr>

<td>

Static analysis

</td>

<td>

complete

</td>

</tr>

<tr>

<td>

Dynamic analysis - codename: *dawn*

</td>

<td>

50%

</td>

</tr>

<tr>

<td>

Creating a library with 30 checks included

</td>

<td>

66,67% (20 tests out of 30)

</td>

</tr>

<tr>

<td>

Capability to export results in XML with customizable CSS

</td>

<td>

10%

</td>

</tr>

</table>