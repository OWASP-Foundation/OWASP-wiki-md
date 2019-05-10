<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Increased confidence in accuracy and applicability of code analysis
    results
  - Organization-wide baseline for secure coding expectations
  - Project teams with an objective goal for judging code-level security

#### Add’l Success Metrics

  - \>50% of projects using code analysis customizations
  - \>75% of projects passing code review audit in past 6 months

#### Add’l Costs

  - Buildout and maintenance of custom code review checks
  - Ongoing project overhead from code review audit
  - Organization overhead from project delays caused by failed code
    review audits

#### Add’l Personnel

  - Architects (1 day/yr)
  - Developers (1 day/yr)
  - Security Auditors (1-2 days/yr)
  - Business Owners (1 day/yr)
  - Managers (1 day/yr)

#### Related Levels

  - Policy & Compliance - 2
  - Secure Architecture - 3

</div>

<div style="float:left; width:65%;">

## Activities

### A. Customize code analysis for application-specific concerns

Code scanning tools are powered by built-in a knowledge-base of rules to
check code based on language APIs and commonly used libraries, but have
limited ability to understand custom APIs and designs to apply analogous
checks. However, through customization, a code scanner can be a
powerful, generic analysis engine for finding organization and
project-specific security concerns.

While details vary between tools in terms of ease and power of custom
analysis, code scanner customization generally involves specifying
checks to be performed at specific APIs and function call sites. Checks
can include analysis for adherence to internal coding standards,
unchecked tainted data being passed to custom interfaces, tracking and
verification of sensitive data handling, correct usage of an internal
API, etc.

Checkers for usage of shared code-bases are an effective place to begin
scanner customizations since the created checkers can be utilized across
multiple projects. To customize a tool for a code-base, a security
auditor should inspect both code and high-level design to identify
candidate checkers to discuss with development staff and stakeholders
for implementation.

### B. Establish release gates for code review

To set a code-level security baseline for all software projects, a
particular point in the software development life-cycle should be
established as a checkpoint where a minimum standard for code review
results must be met in order to make a release.

To begin, this standard should be straightforward to meet, for example
by choosing one or two vulnerability types and a setting the standard
that no project may pass with any corresponding findings. Over time,
this baseline standard should be improved by adding additional criteria
for passing the checkpoint.

Generally, the code review checkpoint should occur toward the end of the
implementation phase, but must occur before release.

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

[:Category:SAMM-CR-3](:Category:SAMM-CR-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-CR-3](Category:SAMM-CR-3 "wikilink")