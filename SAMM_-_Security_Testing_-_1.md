<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Independent verification of expected security mechanisms surrounding
    critical business functions
  - High-level due diligence toward security testing
  - Ad hoc growth of a security test suite for each software project

#### Success Metrics

  - \>50% of projects specifying security test cases in past 12 months
  - \>50% of stakeholders briefed on project status against security
    tests in past 6 months

#### Costs

  - Buildout or license of security test cases
  - Ongoing project overhead from maintenance and evaluation of security
    test cases

#### Personnel

  - QA Testers (1-2 days/yr)
  - Security Auditor (1-2 days/yr)
  - Developers (1 day/yr)
  - Architects (1 day/yr)
  - Business Owners (1 day/yr)

#### Related Levels

  - Security Requirements - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Derive test cases from known security requirements

From the known security requirements for a project, identify a set of
test cases to check the software for correct functionality. Typically,
these test cases are derived from security concerns surrounding the
functional requirements and business logic of the system, but should
also include generic tests for common vulnerabilities based on the
implementation language or technology stack.

Often, it is most effective to use the project team’s time to build
application-specific test cases and utilize publicly available resources
or purchased knowledge bases to select applicable general test cases for
security. Although not required, automated security testing tools can
also be utilized to cover the general security test cases.

This test case planning should occur during the requirements and/or
design phases, but must occur before final testing prior to release.
Candidate test cases should be reviewed for applicability, efficacy, and
feasibility by relevant development, security, and quality assurance
staff.

### B. Conduct penetration testing on software releases

Using the set of security test cases identified for each project,
penetration testing should be conducted to evaluate the system’s
performance against each case. It is common for this to occur during the
testing phase prior to release.

Penetration testing cases should include both application-specific tests
to check soundness of business logic as well as common vulnerability
tests to check the design and implementation. Once specified, security
test cases can be executed by security-savvy quality assurance or
development staff, but first-time execution of security test cases for a
project team should be monitored by a security auditor to assist and
coach team members.

Prior to release or deployment, stakeholders must review results of
security tests and accept the risks indicated by failing security tests
at release time. In the latter case, a concrete timeline should be
established to address the gaps over time.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-ST-1](:Category:SAMM-ST-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-ST-1](Category:SAMM-ST-1 "wikilink")