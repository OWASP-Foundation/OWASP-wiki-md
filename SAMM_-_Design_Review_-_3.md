<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Granular view of weak points in a system design to encourage better
    compartmentalization
  - Organization-level awareness of project standing against baseline
    security expectations for architecture
  - Comparisons between projects for efficiency and progress toward
    mitigating known flaws

#### Add’l Success Metrics

  - \>80% of projects with updated data-flow diagrams in past 6 months
  - \>75% of projects passing design review audit in past 6 months

#### Add’l Costs

  - Ongoing project overhead from maintenance of data-flow diagrams
  - Organization overhead from project delays caused by failed design
    review audits

#### Add’l Personnel

  - Developers (2 days/yr)
  - Architects (1 day/yr)
  - Managers (1-2 days/yr)
  - Business Owners (1-2 days/yr)
  - Security Auditors (2-3 days/yr)

#### Related Levels

  - Secure Architecture - 3
  - Code Review - 3

</div>

<div style="float:left; width:65%;">

## Activities

### A. Develop data-flow diagrams for sensitive resources

Based on the business function of the software project, conduct analysis
to identify details on system behavior around high-risk functionality.
Typically, high-risk functionality will correlate to features
implementing creation, access, update, and deletion of sensitive data.
Beyond data, high-risk functionality also includes project-specific
business logic that is critical in nature, either from a
denial-of-service or compromise perspective.

For each identified data source or business function, select and use a
standardized notation to capture relevant software modules, data
sources, actors, and messages that flow amongst them. It is often
helpful to start with a high-level design diagram and iteratively flesh
out relevant detail while removing elements that do not correspond to
the sensitive resource.

With data-flow diagrams created for a project, conduct analysis over
them to determine internal choke-points in the design. Generally, these
will be individual software modules that handle data with differing
sensitivity levels or those that gate access to several business
functions of various levels of business criticality.

### B. Establish release gates for design review

Having established a consistent design review program, the next step of
enforcement is to set a particular point in the software development
life-cycle where a project cannot pass until an design review is
conducted and findings are reviewed and accepted. In order to accomplish
this, a baseline level of expectations should be set, e.g. no projects
with any high-severity findings will be allowed to pass and all other
findings must be accepted by the business owner.

Generally, design reviews should occur toward the end of the design
phase to aide early detection of security issues, but it must occur
before releases can be made from the project team.

For legacy systems or inactive projects, an exception process should be
created to allow those projects to continue operations, but with an
explicitly assigned timeframe for each to be reviewed to illuminate any
hidden vulnerabilities in the existing systems. Exceptions for should be
limited to no more than 20% of all projects.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-DR-3](:Category:SAMM-DR-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-DR-3](Category:SAMM-DR-3 "wikilink")