1.  REDIRECT [Path Traversal](Path_Traversal "wikilink")



Last revision (mm/dd/yy): **//**

## Overview

This attack is a variant of Path Traversal and can be exploited when the
application accepts the use of relative traversal sequences such as
"../".

## Related Security Activities

### How to Avoid Path Traversal Vulnerabilities

See the [OWASP Guide](:Category:OWASP_Guide_Project "wikilink") article
on how to [Avoid Path Traversal](File_System#Path_traversal "wikilink")
Vulnerabilities.

### How to Test for Path Traversal Vulnerabilities

See the [OWASP Testing
Guide](:Category:OWASP_Testing_Project "wikilink") article on how to
[Test for Path
Traversal](Testing_for_Path_Traversal_\(OWASP-AZ-001\) "wikilink")
Vulnerabilities.

More detailed information can be found on
[Path_Traversal](Path_Traversal "wikilink")

## Description

TBD

## Examples

The following URLs are vulnerable to this attack:

` http://some_site.com.br/get-files.jsp?file=report.pdf  `
` http://some_site.com.br/get-page.php?home=aaa.html  `
` http://some_site.com.br/some-page.asp?page=index.html  `

A simple way to execute this attack is like this:

` http://some_site.com.br/get-files?file=../../../../some dir/some file  `
` http://some_site.com.br/../../../../etc/shadow  `
` http://some_site.com.br/get-files?file=../../../../etc/passwd `

## Risk Factors

TBD

## Related [Threat Agents](Threat_Agents "wikilink")

  - [: Category: Information
    Disclosure](:_Category:_Information_Disclosure "wikilink")

## Related [Attacks](Attacks "wikilink")

  - [Path Manipulation](Path_Manipulation "wikilink")
  - [Path Traversal](Path_Traversal "wikilink")
  - [Resource Injection](Resource_Injection "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [:Category:Input Validation
    Vulnerability](:Category:Input_Validation_Vulnerability "wikilink")

## Related [Controls](Controls "wikilink")

  - [:Category:Input Validation](:Category:Input_Validation "wikilink")

## References

TBD

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[this link doesn't exist, add the category or change this
link?](Category:FIXME "wikilink") [Category: Resource
Manipulation](Category:_Resource_Manipulation "wikilink")