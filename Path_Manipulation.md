1.  REDIRECT [Path Traversal](Path_Traversal "wikilink")



Last revision (mm/dd/yy): **//**

## Description

Path manipulation errors occur when the following two conditions are
met:

1.  An attacker can specify a path used in an operation on the
    filesystem.
2.  By specifying the resource, the attacker gains a capability that
    would not otherwise be permitted. For example, the program may give
    the attacker the ability to overwrite the specified file or run with
    a configuration controlled by the attacker.

Allowing user input to control paths used in filesystem operations may
enable an attacker to access or modify protected system resources.

## Risk Factors

TBD

## Examples

### Example 1

The following code uses input from an HTTP request to create a file
name. The programmer has not considered the possibility that an attacker
could provide a file name such as "../../tomcat/conf/server.xml", which
causes the application to delete one of its own configuration files.

```
    String rName = request.getParameter("reportName");
    File rFile = new File("/usr/local/apfr/reports/" + rName);
    ...
    rFile.delete();
```

### Example 2

The following code uses input from a configuration file to determine
which file to open and echo back to the user. If the program runs with
privileges and malicious users can change the configuration file, they
can use the program to read any file on the system that ends with the
extension .txt.

```
    fis = new FileInputStream(cfg.getProperty("sub")+".txt");
    amt = fis.read(arr);
    out.println(arr);
```

## Related [Threat Agents](Threat_Agents "wikilink")

  - [:Category:Information
    Disclosure](:Category:Information_Disclosure "wikilink")

## Related [Attacks](Attacks "wikilink")

  - [Resource Injection](Resource_Injection "wikilink")
  - [Relative Path Traversal](Relative_Path_Traversal "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [:Category:Input Validation
    Vulnerability](:Category:Input_Validation_Vulnerability "wikilink")

## Related [Controls](Controls "wikilink")

  - [:Category:Input Validation](:Category:Input_Validation "wikilink")

## References

TBD

## Credit

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[this link doesn't exist, create category or change
link?](Category:FIXME "wikilink") [Category:Injection
Attack](Category:Injection_Attack "wikilink")