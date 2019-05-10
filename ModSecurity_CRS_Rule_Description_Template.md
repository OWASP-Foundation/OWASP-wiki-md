`- This is a template for submitting or documenting ModSecurity CRS rule/signature descriptions to`
`    the OWASP ModSecurity Core Rule Set (CRS) Project.`
`- Project participants are encouraged to copy this template and create landing pages for each CRS rule`
`- Use this template and create a new page using the following format - `<http://www.owasp.org/index.php?title=ModSecurity_CRS_RuleID-XXXXX>` (where XXXXX is the CRS ruleID)`

## Rule ID: XXXXX

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Place Rule ID Here

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Message

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Place Rule Message Here

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Summary

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Provide rule background. What is the rule looking for? What attack is
trying to identify or prevent.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Impact

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This should be the Severity rating specified in the rule. (Example: 4 -
Warning)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

`Provide the entire rule/rule chain here`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Detailed Rule Information

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Provide detailed information about the rule construction such as:

  - Why the variable list specified was used
  - What actions are used and why

<!-- end list -->

    A description of the regular expression used - what is is looking for in plain english (Example RegEx analysis from Expresso tool)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Payload

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Provide an example payload that will trigger this rule.

`Example Apache log entry or HTTP payload captured by another tool`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Audit Log Entry

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Include an example ModSecurity Audit Log Entry for when this rule
matchs.

    Audit Log Entry

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Attack Scenarios

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Provide any data around "how" the attack is carried out.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Ease of Attack

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

How easy is it for an attacker to carry out the attack?

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Ease of Detection

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

How easy is it for a defender to use ModSecurity to accurately detect
this attack?

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

False Positives

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

If there are any known false positives - specify them here Also sign-up
for the Reporting False Positives mail-list here:
<https://lists.sourceforge.net/lists/listinfo/mod-security-report-false-positives>

Send FP Report emails here:
mod-security-report-false-positives![10x](Justat.gif
"10x")lists.sourceforge.net

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

False Negatives

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Are there any know issues with evasions or how an attacker might bypass
detection?

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Maturity

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

10 point scale (0-9) where:
0 = Beta/Experimental
9 = Heavily Tested

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Accuracy

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

10 point scale (0-9) where:
0 = High % of FP
5 = No false positives reported

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Documentation Contributor(s)

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Specify your name and email if you want credit for the rule or
documentation of it. Example: Ryan Barnett -
ryan.barnett![Justat.gif](Justat.gif "Justat.gif")owasp.org

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Additional References

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Provide any external reference links (e.g. - if this is a virtual patch
for a known vuln link to the Bugtraq or CVE page).

</td>

</tr>

</table>

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")