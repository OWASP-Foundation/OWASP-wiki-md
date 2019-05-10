<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Development enabled to consistently self-check for code-level
    security vulnerabilities
  - Routine analysis results to compile historic data on per-team secure
    coding habits
  - Stakeholders aware of unmitigated vulnerabilities to support better
    tradeoff analysis

#### Add’l Success Metrics

  - \>50% of projects with code review and stakeholder sign-off in past
    6 months
  - \>80% of projects with access to automated code review results in
    past 1 month

#### Add’l Costs

  - Research and selection of code analysis solution
  - Initial cost and maintenance of automation integration
  - Ongoing project overhead from automated code review and mitigation

#### Add’l Personnel

  - Developers (1-2 days/yr)
  - Architects (1 day/yr)
  - Managers (1-2 days/yr)
  - Security Auditors (3-4 days/yr)

#### Related Levels

</div>

<div style="float:left; width:65%;">

## Activities

### A. Utilize automated code analysis tools

Many security vulnerabilities at the code level are complex to
understand and require careful inspection for discovery. However, there
are many useful automation solutions available to automatically analyze
code for bugs and vulnerabilities.

There are both commercial and open-source products available to cover
popular programming languages and frameworks. Selection of an
appropriate code analysis solution is based on several factors including
depth and accuracy of inspection, product usability and usage model,
expandability and customization features, applicability to the
organization’s architecture and technology stack(s), etc.

Utilize input from security-savvy technical staff as well as developers
and development managers in the selection process, and review overall
results with stakeholders.

### B. Integrate code analysis into development process

Once a code analysis solution is selected, it must be integrated into
the development process to encourage project teams to utilize its
capabilities. An effective way to accomplish this is to setup the
infrastructure for the scans to run automatically at build time or from
code in the project’s code repository. In this fashion, results are
available earlier thus enabling development teams to self-check along
the way before release.

A potential problem with legacy systems or large ongoing projects is
that code scanners will typically report findings in modules that were
not being updated in the release. If automatic scanning is setup to run
periodically, an effective strategy to avoid review overhead is to limit
consideration of findings to those that have been added, removed, or
changed since the previous scan. If is critical to not ignore the rest
of the results however, so development managers should take input from
security auditors, stakeholders, and the project team to formulate a
concrete plan for addressing the rest of the findings.

If unaddressed findings from code review remain at release, these must
be reviewed and accepted by project stakeholders.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-CR-2](:Category:SAMM-CR-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-CR-2](Category:SAMM-CR-2 "wikilink")