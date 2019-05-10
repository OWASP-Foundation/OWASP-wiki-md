`    <td ``>`

Some vulnerable components (e.g., framework libraries) can be identified
and exploited with automated tools, expanding the threat agent pool
beyond targeted attackers to include chaotic actors.

</td>

`    <td ``>`

Attacker identifies a weak component through scanning or manual
analysis. He customizes the exploit as needed and executes the attack.
It gets more difficult if the used component is deep in the application.

</td>

`    <td colspan=2  ``>`

Virtually every application has these issues because most development
teams don’t focus on ensuring their components/libraries are up to date.
In many cases, the developers don’t even know all the components they
are using, never mind their versions. Component dependencies make things
even worse.

</td>

`    <td ``>`

The full range of weaknesses is possible, including injection, broken
access control, XSS, etc. The impact could range from minimal to
complete host takeover and data compromise.

</td>

`    <td ``>`

Consider what each vulnerability might mean for the business controlled
by the affected application. It could be trivial or it could mean
complete compromise.

</td>

In theory, it ought to be easy to figure out if you are currently using
any vulnerable components or libraries. Unfortunately, vulnerability
reports for commercial or open source software do not always specify
exactly which versions of a component are vulnerable in a standard,
searchable way. Further, not all libraries use an understandable version
numbering system. Worst of all, not all vulnerabilities are reported to
a central clearinghouse that is easy to search, although sites like
[CVE](http://cve.mitre.org/) and [NVD](http://nvd.nist.gov/home.cfm) are
becoming easier to search.

Determining if you are vulnerable requires searching these databases, as
well as keeping abreast of project mailing lists and announcements for
anything that might be a vulnerability. If one of your components does
have a vulnerability, you should carefully evaluate whether you are
actually vulnerable by checking to see if your code uses the part of the
component with the vulnerability and whether the flaw could result in an
impact you care about.

One option is not to use components that you didn’t write. But that’s
not very realistic.

Most component projects do not create vulnerability patches for old
versions. Instead, most simply fix the problem in the next version. So
upgrading to these new versions is critical. Software projects should
have a process in place to:

1.  Identify all components and the versions you are using, including
    all dependencies. (e.g., the
    [versions](http://mojo.codehaus.org/versions-maven-plugin/) plugin).
2.  Monitor the security of these components in public databases,
    project mailing lists, and security mailing lists, and keep them up
    to date.
3.  Establish security policies governing component use, such as
    requiring certain software development practices, passing security
    tests, and acceptable licenses.
4.  Where appropriate, consider adding security wrappers around
    components to disable unused functionality and/ or secure weak or
    vulnerable aspects of the component.

Component vulnerabilities can cause almost any type of risk imaginable,
ranging from the trivial to sophisticated malware designed to target a
specific organization. Components almost always run with the full
privilege of the application, so flaws in any component can be serious,
The following two vulnerable components were downloaded 22m times in
2011.

  - [Apache CXF Authentication
    Bypass](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-3451)
    – By failing to provide an identity token, attackers could invoke
    any web service with full permission. (Apache CXF is a services
    framework, not to be confused with the Apache Application Server.)
  - [Spring Remote Code
    Execution](http://www.infosecurity-magazine.com/view/30282/remote-code-vulnerability-in-spring-framework-for-java/)
    – Abuse of the Expression Language implementation in Spring allowed
    attackers to execute arbitrary code, effectively taking over the
    server.

Every application using either of these vulnerable libraries is
vulnerable to attack as both of these components are directly accessible
by application users. Other vulnerable libraries, used deeper in an
application, may be harder to exploit.

  - [OWASP Dependency Check (for Java
    libraries)](OWASP_Dependency_Check "wikilink")
  - [OWASP SafeNuGet (for .NET libraries thru
    NuGet)](https://github.com/OWASP/SafeNuGet)

<!-- end list -->

  - [The Unfortunate Reality of Insecure
    Libraries](http://www.aspectsecurity.com/research-presentations/the-unfortunate-reality-of-insecure-libraries)
  - [Open Source Software
    Security](http://en.wikipedia.org/wiki/Open_source_software_security)
  - [Addressing Security Concerns in Open Source
    Components](http://img.en25.com/Web/SonatypeInc/%7Bb2fa5ed8-938d-4bce-8a9c-d08ebeba826d%7D_Executive_Brief_-_Study-_Understanding_Security_Risks_in_OSS_Components-1.pdf)
  - [MITRE Common Vulnerabilities and Exposures](http://cve.mitre.org/)
  - [Example Mass Assignment Vulnerability that was fixed in
    ActiveRecord, a Ruby on Rails
    GEM](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-0277)