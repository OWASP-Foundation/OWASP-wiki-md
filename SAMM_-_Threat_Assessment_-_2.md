<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Granular understanding of likely threats to individual projects
  - Framework for better tradeoff decisions within project teams
  - Ability to prioritize development efforts within a project team
    based on risk weighting

#### Add’l Success Metrics

  - \>75% of project teams with identified and rated threats
  - \>75% of project stakeholders briefed on threat and abuse models of
    relevant projects within past 6 months

#### Add’l Costs

  - Project overhead from maintenance of threat models and attacker
    profiles

#### Add’l Personnel

  - Security Auditor (1 day/yr)
  - Business Owner (1 day/yr)
  - Managers (1 day/yr)

#### Related Levels

  - Strategy & Metrics - 2
  - Secure Architecture - 2

</div>

<div style="float:left; width:65%;">

## Activities

### A. Build and maintain abuse-case models per project

Further considering the threats to the organization, conduct a more
formal analysis to determine potential misuse or abuse of functionality.
Typically, this process begins with identification of normal usage
scenarios, e.g. use-case diagrams if available.

If a formal abuse-case technique isn’t used, generate a set of
abuse-cases for each scenario by starting with a statement of normal
usage and brainstorming ways in which the statement might be negated, in
whole or in part. The simplest way to get started is to insert the word
“no” or “not” into the usage statement in as many ways as possible,
typically around nouns and verbs. Each usage scenario should generate
several possible abuse-case statements.

Further elaborate the abuse-case statements to include any
application-specific concerns based on the business function of the
software. The ultimate goal is for the completed set of abuse statements
to form a model for usage patterns that should be disallowed by the
software. If desired, these abuse cases can be combined with existing
threat models.

After initial creation, abuse-case models should be updated for active
projects during the design phase. For existing projects, new
requirements should be analyzed for potential abuse, and existing
projects should opportunistically build abuse-cases for established
functionality where practical.

### B. Adopt a weighting system for measurement of threats

Based on the established attacker profiles, identify a rating system to
allow relative comparison between the threats. Initially, this can be a
simple high-medium-low rating based upon business risk, but any scale
can be used provided that there are no more than 5 categories.

After identification of a rating system, build evaluation criteria that
allow each threat to be assigned a rating. In order to do this properly,
additional factors about each threat must be considered beyond
motivation. Important factors include capital and human resources,
inherent access privilege, technical ability, relevant goals on the
threat model(s), likelihood of successful attack, etc.

After assigning each threat to a rating, use this information to
prioritize risk mitigation activities within the development life-cycle.
Once built for a project team, it should be updated during design of new
features or refactoring efforts.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-TA-2](:Category:SAMM-TA-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-TA-2](Category:SAMM-TA-2 "wikilink")