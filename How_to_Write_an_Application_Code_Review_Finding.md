__TOC__

An application security "finding" is how an application security team
communicates information to a software development organization.
Findings may be vulnerabilities, architectural problems, organization
problems, failure to follow best practices or standards, or "good"
practices that deserve recognition.

## Choose a Great Title

When writing an application security finding, you should choose a title
that captures the issue clearly, succinctly, and convincingly for the
intended audience. In general, it's best to phrase the title in a
positive way, such as “Add access control to business logic” or “Encode
output to prevent [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink")."

## Identify the Location of the Vulnerability

The finding should be as specific as possible about the location in both
the code and as a URL. If the finding represents a pervasive problem,
then the location should provide many examples of actual instances of
the problem.

## Detail the vulnerability

The finding should provide enough detail about the problem that anyone
can:

  - understand the vulnerability
  - understand possible attack scenarios
  - know the key factors driving likelihood and impact

## Discuss the Risk

There is value in both assigning a qualitative value to each finding and
further discussing why this value was assigned. Some possible risk
ratings are:

  - Critical
  - High
  - Moderate
  - Low

Justifying the assigned risk ratings is very important. This will allow
stakeholders (especially non-technical ones) to gain more of an
understanding of the issue at hand. Two key points to identify are:

  - Likelihood (ease of discovery and execution)
  - Business/Technical impact

You should have a standard methodology for rating risks in your
organization. The [OWASP Risk Rating
Methodology](How_to_value_the_real_risk "wikilink") is a comprehensive
method that you can tailor for your organization's priorities.

## Suggest Remediations

  - alternatives
  - include effort required
  - discuss residual risk

## Include References

  - Important note: if you use OWASP materials for any reason, you must
    follow the terms of our license

## Sample Report

Below is a sample format for a finding report resulting from a secure
code review.

<div class=Section1>

<table class=MsoTableGrid border=1 cellspacing=0 cellpadding=0 width=631
 style='width:473.4pt;border-collapse:collapse;border:none'>

<tr>

<td width=631 colspan=4 valign=top style='width:473.4pt;border:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Review /Engagement

` reference:`</span>

</td>

</tr>

<tr>

<td width=631 colspan=4 valign=top style='width:473.4pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Package/Component/Class

` Name`</span>

</td>

</tr>

<tr>

<td width=631 colspan=4 valign=top style='width:473.4pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'> </span>

</td>

</tr>

<tr>

<td width=227 valign=top style='width:169.95pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Finding

` description`</span>

</td>

<td width=131 valign=top style='width:98.45pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Location(S)</span>

</td>

<td width=117 valign=top style='width:88.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Severity</span>

</td>

<td width=156 valign=top style='width:117.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'>Recommendation</span>

</td>

</tr>

<tr>

<td width=227 valign=top style='width:169.95pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:Arial'>No input

` validation of the `<b>`HTTPRequest object.getID()`</b>` function. `</span>

<span style='font-size:9.0pt;font-family:Arial'> </span>

<span style='font-size:9.0pt;font-family:Arial'>Lack of

` input validation may make the application vulnerable to many types of`
` injection`</span>

</td>

<td width=131 valign=top style='width:98.45pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:Arial'>com.inc.dostuff.java</span>

<span style='font-size:9.0pt;font-family:Arial'>Lines 20,

` 55,106`</span>

<span style='font-size:9.0pt;font-family:Arial'> </span>

<span style='font-size:9.0pt;font-family:Arial'>com.inc.main.java</span>

<span style='font-size:9.0pt;font-family:Arial'>Lines 34,

` 99`</span>

</td>

<td width=117 valign=top style='width:88.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'>Critical

` `</span><b><span style='font-size:11.0pt;font-family:"Microsoft Sans Serif"'>`▪`</span></b>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'>Required

` □`</span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'>Recommended

` □`</span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:"Microsoft Sans Serif"'>Informational

` □`</span>

<span style='font-family:"Microsoft Sans Serif"'> </span>

</td>

<td width=156 valign=top style='width:117.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>

<span style='font-family:"Microsoft Sans Serif"'> </span>

<span style='font-size:9.0pt;font-family:Arial'>It is critical

` that this be addressed prior to deployment to production`</span>

</td>

</tr>

</table>

 

</div>

[Category:How To](Category:How_To "wikilink") [Category:OWASP Code
Review Project](Category:OWASP_Code_Review_Project "wikilink")