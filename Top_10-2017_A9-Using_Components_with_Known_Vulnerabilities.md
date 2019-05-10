`   <td colspan=2 ``>`

While it is easy to find already-written exploits for many known
vulnerabilities, other vulnerabilities require concentrated effort to
develop a custom exploit. 

</td>

`   <td colspan=2  ``>`

`Prevalence of this issue is very widespread. Component-heavy development patterns can lead to development teams not even understanding which components they use in their application or API, much less keeping them up to date.`
`Some scanners such as retire.js help in detection, but determining exploitability requires additional effort. `

</td>

`   <td colspan=2  ``>`

`While some known vulnerabilities lead to only minor impacts, some of the largest breaches to date have relied on exploiting known vulnerabilities in components. Depending on the assets you are protecting, perhaps this risk should be at the top of the list. `

</td>

You are likely vulnerable:

  - If you do not know the versions of all components you use (both
    client-side and server-side). This includes components you directly
    use as well as nested dependencies.
  - If software is vulnerable, unsupported, or out of date. This
    includes the OS, web/application server, database management system
    (DBMS), applications, APIs and all components, runtime environments,
    and libraries.
  - If you do not scan for vulnerabilities regularly and subscribe to
    security bulletins related to the components you use.
  - If you do not fix or upgrade the underlying platform, frameworks,
    and dependencies in a risk-based, timely fashion. This commonly
    happens in environments when patching is a monthly or quarterly task
    under change control, which leaves organizations open to many days
    or months of unnecessary exposure to fixed vulnerabilities.
  - If software developers do not test the compatibility of updated,
    upgraded, or patched libraries.
  - If you do not secure the components' configurations
    (see <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>).

There should be a patch management process in place to:

  - Remove unused dependencies, unnecessary features, components, files,
    and documentation.
  - Continuously inventory the versions of both client-side and
    server-side components (e.g. frameworks, libraries) and their
    dependencies using tools
    like <u>[versions](http://www.mojohaus.org/versions-maven-plugin/)</u>, <u>[DependencyCheck](OWASP_Dependency_Check "wikilink")</u>,
    <u>[retire.js](https://github.com/retirejs/retire.js/)</u>, etc.
    Continuously monitor sources
    like <u>[CVE](https://cve.mitre.org/)</u> and <u>[NVD](https://nvd.nist.gov/)</u>
    for vulnerabilities in the components. Use software composition
    analysis tools to automate the process. Subscribe to email alerts
    for security vulnerabilities related to components you use.
  - Only obtain components from official sources over secure links.
    Prefer signed packages to reduce the chance of including a modified,
    malicious component.
  - Monitor for libraries and components that are unmaintained or do not
    create security patches for older versions. If patching is not
    possible, consider deploying a <u>[virtual
    patch](Virtual_Patching_Best_Practices#What_is_a_Virtual_Patch.3F "wikilink")</u>
    to monitor, detect, or protect against the discovered issue.

Every organization must ensure that there is an ongoing plan for
monitoring, triaging, and applying updates or configuration changes for
the lifetime of the application or portfolio.

<b>Scenario \#1</b>: Components typically run with the same privileges
as the application itself, so flaws in any component can result in
serious impact. Such flaws can be accidental (e.g. coding error) or
intentional (e.g. backdoor in component). Some example exploitable
component vulnerabilities discovered are:

  - <u>[CVE-2017-5638](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5638)</u>,
    a Struts 2 remote code execution vulnerability that enables
    execution of arbitrary code on the server, has been blamed for
    significant breaches.
  - While <u>[internet of things
    (IoT)](https://en.wikipedia.org/wiki/Internet_of_things)</u> are
    frequently difficult or impossible to patch, the importance of
    patching them can be great (e.g. biomedical devices).

There are automated tools to help attackers find unpatched or
misconfigured systems. For example, the <u>[Shodan IoT search
engine](https://www.shodan.io/report/89bnfUyJ)</u> can help you find
devices that still suffer from
<u>[Heartbleed](https://en.wikipedia.org/wiki/Heartbleed)</u>
vulnerability that was patched in April 2014.

  - <u>[OWASP Application Security Verification Standard: V1
    Architecture, design and threat
    modelling](ASVS_V1_Architecture "wikilink")</u>
  - <u>[OWASP Dependency Check (for Java and .NET
    libraries)](OWASP_Dependency_Check "wikilink")</u>
  - <u>[OWASP Testing Guide - Map Application Architecture
    (OTG-INFO-010)](Map_Application_Architecture_\(OTG-INFO-010\) "wikilink")</u>
  - <u>[OWASP Virtual Patching Best
    Practices](Virtual_Patching_Best_Practices "wikilink")</u>

<!-- end list -->

  - <u>[The Unfortunate Reality of Insecure
    Libraries](https://cdn2.hubspot.net/hub/203759/file-1100864196-pdf/docs/Contrast_-_Insecure_Libraries_2014.pdf)</u>
  - <u>[MITRE Common Vulnerabilities and Exposures (CVE)
    search](https://www.cvedetails.com/version-search.php)</u>
  - <u>[National Vulnerability Database
    (NVD)](https://nvd.nist.gov/)</u>
  - <u>[Retire.js for detecting known vulnerable JavaScript
    libraries](https://github.com/retirejs/retire.js/)</u>
  - <u>[Node Libraries Security
    Advisories](https://nodesecurity.io/advisories)</u>
  - <u>[Ruby Libraries Security Advisory Database and
    Tools](https://rubysec.com/)</u>