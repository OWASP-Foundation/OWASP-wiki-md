<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Organization-wide baseline for expected application performance
    against attacks
  - Customized security test suites to improve accuracy of automated
    analysis
  - Project teams aware of objective goals for attack resistance

#### Add’l Success Metrics

  - \>50% of projects using security testing customizations
  - \>75% of projects passing all security tests in past 6 months

#### Add’l Costs

  - Buildout and maintenance of customizations to security testing
    automation
  - Ongoing project overhead from security testing audit process
  - Organization overhead from project delays caused by failed security
    testing audits

#### Add’l Personnel

  - Architects (1 day/yr)
  - Developers (1 day/yr)
  - Security Auditors (1-2 days/yr)
  - QA Testers (1-2 days/yr)
  - Business Owners (1 day/yr)
  - Managers (1 day/yr)

#### Related Levels

  - Policy & Compliance - 2
  - Secure Architecture - 3

</div>

<div style="float:left; width:65%;">

## Activities

### A. Employ application-specific security testing automation

Through either customization of security testing tools, enhancements to
generic test case execution tools, or buildout of custom test harnesses,
project teams should formally iterate through security requirements and
build a set of automated checkers to test the security of the
implemented business logic.

Additionally, many automated security testing tools can be greatly
improved in accuracy and depth of coverage if they are customized to
understand more detail about the specific software interfaces in the
project under test. Further, organization-specific concerns from
compliance or technical standards can be codified as a reusable, central
test battery to make audit data collection and per-project management
visibility simpler.

Project teams should focus on buildout of granular security test cases
based on the business functionality of their software, and an
organization-level team led by a security auditor should focus on
specification of automated tests for compliance and internal standards.

### B. Establish release gates for security testing

To prevent software from being released with easily found security bugs,
a particular point in the software development life-cycle should be
identified as a checkpoint where an established set of security test
cases must pass in order to make a release from the project. This
establishes a baseline for the kinds of security tests all projects are
expected to pass.

Since adding too many test cases initially can result in an overhead
cost bubble, begin by choosing one or two security issues and include a
wide variety of test cases for each with the expectation that no project
may pass if any test fails. Over time, this baseline should be improved
by selecting additional security issues and adding a variety of
corresponding test cases.

Generally, this security testing checkpoint should occur toward the end
of the implementation or testing, but must occur before release.

For legacy systems or inactive projects, an exception process should be
created to allow those projects to continue operations, but with an
explicitly assigned timeframe for mitigation of findings. Exceptions
should be limited to no more that 20% of all projects.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-ST-3](:Category:SAMM-ST-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-ST-3](Category:SAMM-ST-3 "wikilink")