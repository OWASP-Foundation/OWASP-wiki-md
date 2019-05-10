Our methodology for the Top 10 2007 was simple: take the [MITRE
Vulnerability Trends
for 2006](http://cwe.mitre.org/documents/vuln-trends.html), and distill
the Top 10 ''web application security ''issues. The ranked results are
as follows:

**![Top_10_2007-MitreDataChart.gif](Top_10_2007-MitreDataChart.gif
"Top_10_2007-MitreDataChart.gif")**

'''

<center>

Figure 2: MITRE data on Top 10 web application vulnerabilities for 2006

</center>

'''

Although we tried to preserve a one to one mapping of MITRE raw
vulnerability data to our section headings, we have deliberately changed
some of the later categories to more closely map to root causes. If you
are interested in the final 2006 data from MITRE, we have included an
Excel worksheet on the OWASP Top 10 web site.

All of the protection recommendations provide solutions for the three
most prevalent web application frameworks: Java EE, ASP.NET, and PHP.
Other common web application frameworks, such as Ruby on Rails or Perl
can easily adapt the recommendations to suit their specific needs.

## Why we have dropped some important issues

**Unvalidated input** is a major challenge for any development team, and
is at the root of many application security problems. In fact, many of
the other items in the list recommend validating input as a part of the
solution. We still strongly recommend creating a centralized input
validation mechanism as a part of your web applications. For more
information, read the following data validation articles at OWASP:

  - <http://www.owasp.org/index.php/Data_Validation>
  - <http://www.owasp.org/index.php/Testing_for_Data_Validation>

**Buffer overflows, integer overflows and format string issues** are
extremely serious vulnerabilities for programs written in languages such
as C or C++. Remediation for these issues is covered by the traditional
non-web application security community, such as SANS, CERT, and
programming language tool vendors. If your code is written in a language
that is likely to suffer buffer overflows, we encourage you to read the
buffer overflow content on OWASP:

  - <http://www.owasp.org/index.php/Buffer_overflow>
  - <http://www.owasp.org/index.php/Testing_for_Buffer_Overflow>

**Denial of service** is a serious attack that can affect any site
written in any language. The ranking of DoS by MITRE is insufficient to
make the Top 10 this year. If you have concerns about denial of service,
you should consult the OWASP site and Testing Guide:

  - <http://www.owasp.org/index.php/Category:Denial_of_Service_Attack>
  - <http://www.owasp.org/index.php/Testing_for_Denial_of_Service>

**Insecure configuration management** affects all systems to some
extent, particularly PHP. However, the ranking by MITRE does not allow
us to include this issue this year. When deploying your application, you
should consult the latest OWASP Development Guide and the OWASP Testing
Guide for detailed information regarding secure configuration management
and testing:

  - <http://www.owasp.org/index.php/Configuration>
  - <http://www.owasp.org/index.php/Testing_for_infrastructure_configuration_management>

## Why we have ADDED some important issues

'''Cross Site Request Forgery (CSRF) '''is the major new addition to
this edition of the OWASP Top 10. Although raw data ranks it at \#36, we
believe that it is important enough that applications should start
protection efforts today, particularly for high value applications and
applications which deal with sensitive data. CSRF is more prevalent than
its current ranking would indicate, and it can be highly dangerous.

**Cryptography** The insecure uses of cryptography are not the \#8 and
\#9 web application security issues according to the raw MITRE data, but
they do represent a root cause of many privacy leaks and compliance
issues (particularly with PCI DSS 1.1 compliance).

## Vulnerabilities, not attacks

The previous edition of the Top 10 contained a mixture of attacks,
vulnerabilities and countermeasures. This time around, we have focused
solely on vulnerabilities, although commonly used terminology sometimes
combines vulnerabilities and attacks. If organizations use this document
to secure their applications, and reduce the risks to their business, it
will lead to a direct reduction in the likelihood of:

  - **Phishing attacks** that can exploit any of these vulnerabilities,
    particularly XSS, and weak or non-existent authentication or
    authorization checks ([A1](Top_10_2007-A1 "wikilink"),
    [A4](Top_10_2007-A4 "wikilink"), [A7](Top_10_2007-A7 "wikilink"),
    [A10](Top_10_2007-A10 "wikilink"))
  - **Privacy violations** from poor validation, business rule and weak
    authorization checks ([A2](Top_10_2007-A2 "wikilink"),
    [A4](Top_10_2007-A4 "wikilink"), [A6](Top_10_2007-A6 "wikilink"),
    [A7](Top_10_2007-A7 "wikilink"), [A10](Top_10_2007-A10 "wikilink"))
  - **Identity theft** through poor or non-existent cryptographic
    controls ([A8](Top_10_2007-A8 "wikilink") and
    [A9](Top_10_2007-A9 "wikilink")), remote file include
    ([A3](Top_10_2007-A3 "wikilink")) and authentication, business rule,
    and authorization checks ([A4](Top_10_2007-A4 "wikilink"),
    [A7](Top_10_2007-A7 "wikilink"), [A10](Top_10_2007-A10 "wikilink"))
  - **Systems compromise, data alteration, or data** destruction attacks
    via Injections ([A2](Top_10_2007-A2 "wikilink")) and remote file
    include ([A3](Top_10_2007-A3 "wikilink"))
  - **Financial loss** through unauthorized transactions and CSRF
    attacks ([A4](Top_10_2007-A4 "wikilink"),
    [A5](Top_10_2007-A5 "wikilink"), [A7](Top_10_2007-A7 "wikilink"),
    [A10](Top_10_2007-A10 "wikilink"))
  - **Reputation loss** through exploitation of any of the above
    vulnerabilities ([A1](Top_10_2007-A1 "wikilink") -
    [A10](Top_10_2007-A10 "wikilink"))

Once an organization moves away from worrying about reactive controls,
and moves forward to proactively reducing risks applicable to their
business, they will improve compliance with regulatory regimes, reduce
operational costs, and hopefully will have far more robust and secure
systems as a result.

## Biases

The methodology described above necessarily biases the Top 10 towards
discoveries by the security researcher community. This pattern of
discovery is similar to the methods of [actual
attack](http://www.zone-h.org/archive), particularly as it relates to
entry-level ("script kiddie") attackers. Protecting your software
against the Top 10 will provide a modicum of protection against the most
common forms of attack, but far more importantly, help set a course for
improving the security of your software.

## Mapping

There have been changes to the headings, even where content maps closely
to previous content. We no longer use the WAS XML naming scheme as it
has not kept up to date with modern vulnerabilities, attacks, and
countermeasures. The table below depicts how this edition maps to the
Top 10 2004, and the raw MITRE ranking:

<table>
<thead>
<tr class="header">
<th><p>style='background:#FFFF99'</p></th>
<th><p>'''</p>
<center>
<p>OWASP Top 10 2007</p>
</center>
<p>'''</p></th>
<th><p>style='background:#FFFF99'</p></th>
<th><p>'''</p>
<center>
<p>OWASP Top 10 2004</p>
</center>
<p>'''</p></th>
<th><p>style='background:#FFFF99'</p></th>
<th><p>'''</p>
<center>
<p>MITRE 2006 Raw Ranking</p>
</center>
<p>'''</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong><a href="Top_10_2007-A1" title="wikilink">A1 - Cross Site Scripting (XSS)</a></strong></p></td>
<td><p><strong>A4 - Cross Site Scripting (XSS)</strong></p></td>
<td><p><strong>1</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong><a href="Top_10_2007-A2" title="wikilink">A2 - Injection Flaws</a></strong></p></td>
<td><p><strong>A6 - Injection Flaws</strong></p></td>
<td><p><strong>2</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong><a href="Top_10_2007-A3" title="wikilink">A3 - Malicious File Execution (NEW)</a></strong></p></td>
<td></td>
<td><p><strong>3</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong><a href="Top_10_2007-A4" title="wikilink">A4 - Insecure Direct Object Reference</a></strong></p></td>
<td><p><strong>A2 - Broken Access Control (split in 2007 T10)</strong></p></td>
<td><p><strong>5</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong><a href="Top_10_2007-A5" title="wikilink">A5 - Cross Site Request Forgery (CSRF) (NEW)</a></strong></p></td>
<td></td>
<td><p><strong>36</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong><a href="Top_10_2007-A6" title="wikilink">A6 - Information Leakage and Improper Error Handling</a></strong></p></td>
<td><p><strong>A7 - Improper Error Handling</strong></p></td>
<td><p><strong>6</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong><a href="Top_10_2007-A7" title="wikilink">A7 - Broken Authentication and Session Management</a></strong></p></td>
<td><p>'''A3 - Broken Authentication and Session Management '''</p></td>
<td><p><strong>14</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong><a href="Top_10_2007-A8" title="wikilink">A8 - Insecure Cryptographic Storage</a></strong></p></td>
<td><p><strong>A8 - Insecure Storage</strong></p></td>
<td><p><strong>8</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong><a href="Top_10_2007-A9" title="wikilink">A9 - Insecure Communications (NEW)</a></strong></p></td>
<td><p><strong>Discussed under A10 - Insecure Configuration Management</strong></p></td>
<td><p><strong>8</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong><a href="Top_10_2007-A10" title="wikilink">A10 - Failure to Restrict URL Access</a></strong></p></td>
<td><p><strong>A2 - Broken Access Control (split in 2007 T10)</strong></p></td>
<td><p><strong>14</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>&lt;removed in 2007&gt;</strong></p></td>
<td><p><strong>A1 - Unvalidated Input</strong></p></td>
<td><p><strong>7</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>&lt;removed in 2007&gt;</strong></p></td>
<td><p><strong>A5 - Buffer Overflows</strong></p></td>
<td><p><strong>4, 8, and 10</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>&lt;removed in 2007&gt;</strong></p></td>
<td><p><strong>A9 - Denial of Service</strong></p></td>
<td><p><strong>17</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>&lt;removed in 2007&gt;</strong></p></td>
<td><p><strong>A10 - Insecure Configuration Management</strong></p></td>
<td><p><strong>29</strong></p></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>