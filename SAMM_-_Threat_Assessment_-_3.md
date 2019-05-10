<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Deeper consideration of full threat profile for each software
    project
  - Detailed mapping of assurance features to established threats
    against each software project
  - Artifacts to document due diligence based on business function of
    each software project

#### Add’l Success Metrics

  - \>80% of project teams with updated threat models prior to every
    implementation cycle
  - \>80% of project teams with updated inventory of third-party
    components prior to every release
  - \>50% of all security incidents identified a priori by threat models
    in past 12 months

#### Add’l Costs

  - Project overhead from maintenance of detailed threat models and
    expanded attacker profiles
  - Discovery of all third-party dependencies

#### Add’l Personnel

  - Business Owners (1 day/yr)
  - Developers (1 day/yr)
  - Architects (1 day/yr)
  - Security Auditors (2 day/yr)
  - Managers (1 day/yr)

#### Related Levels

  - Security Requirements - 2 & 3

</div>

<div style="float:left; width:65%;">

## Activities

### A. Explicitly evaluate risk from third-party components

Conduct an assessment of your software code-base and identify any
components that are of external origin. Typically, these will include
open-source projects, purchased COTS software, and online services which
your software uses.

For each identified component, elaborate attacker profiles for the
software project based upon potential compromise of third-party
components. Based upon the newly identified attacker profiles, update
software threat models to incorporate any likely risks based upon new
attacker goals or capabilities.

In addition to threat scenarios, also consider ways in which
vulnerabilities or design flaws in the third-party software might affect
your code and design. Elaborate your threat models accordingly with the
potential risks from vulnerabilities and knowledge of the updated
attacker profile.

After initially conducted for a project, this must be updated and
reviewed during the design phase or every development cycle. This
activity should be conducted by a security auditor with relevant
technical and business stakeholders.

### B. Elaborate threat models with compensating controls

Conduct an assessment to formally identify factors that directly prevent
preconditions for compromise represented by the threat models. These
mitigating factors are the compensating controls that formally address
the direct risks from software. Factors can be technical features in the
software itself, but can also be process elements in the development
life-cycle, infrastructure features, etc.

If using attack trees, the logical relationship represented by each
branch will be either an AND or an OR. Therefore, by mitigating against
just one precondition on an AND branch, the parent and all connected
leaf nodes can be marked as mitigated. However, all child nodes on an OR
node must be prevented before the parent can be marked as mitigated.

Regardless of threat modeling technique, identify compensating controls
and annotate the threat models directly. The goal is to maximize
coverage in terms of controls that mark parts of the threat model as
mitigated. For any viable paths remaining, identify potential
compensating controls for feedback into organizational strategy.

After initially conducted for a project, this must be updated and
reviewed during the design phase or every development cycle. This
activity should be conducted by a security auditor with relevant
technical and business stakeholders.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-TA-3](:Category:SAMM-TA-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-TA-3](Category:SAMM-TA-3 "wikilink")