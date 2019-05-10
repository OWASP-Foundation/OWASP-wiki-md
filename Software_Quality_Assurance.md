[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

## Objective

The software quality assurance goal is to confirm the confidentiality
and integrity of private user data is protected as the data is handled,
stored, and transmitted. The QA testing should also confirm the
application cannot be hacked, broken, commandeered, overloaded, or
blocked by denial of service attacks, within acceptable risk levels.
This implies that the acceptable risk levels and threat modeling
scenarios are established up front, so the developers and QA engineers
know what to expect and what to work towards.

## Platforms Affected

All

## Best practices

  - Leverage the available resources like the OWASP Top Ten list, CLASP,
    or the policy compliance frameworks described in Chapter 5 and the
    threat modeling processes described in Chapter 7. These processes
    will help identify design parameters, establish measurable goals,
    and ensure that security testing proceeds in a systematic, thorough,
    and quantified fashion.

<!-- end list -->

  - Effective software quality assurance involves three complementary
    factors: Process, Metrics, and Automation.
  - Plan to test and quantify application security behavior during the
    QA process, just like any other system functionality.
  - Include the following considerations in your test plans:
      - The policy compliance framework requirements
      - Overviews of security testing methods, tools, training, and
        resource allocations
      - The operating budget and schedule considerations
      - Select a preferred vulnerability scoring system (CVSS, OVAL,
        etc.) and a management/tracking system (Bugzilla, a third-party
        vulnerability management package or service, etc.)
      - Establish and collect useful metrics that will facilitate
        decision making (for example, the count of open defects by
        severity and category, the arrival count over time, the close
        rate, total testing coverage, etc.)
      - Identify the testing activities which will be automation
        candidates and discuss how it will be done.
  - Have a set of QA entry criteria, which identifies the items
    necessary to begin testing:
      - Policy compliance validation requirements
      - The applicable threat modeling scenarios
      - The testing schedule, resource list, and budget
      - The metric and vulnerability scoring system selections
      - An organizationally meaningful certification, which shows the QA
        team participated in design reviews and was satisfied with the
        security parameters of the system.
      - The completed test plans
  - The QA exit criteria should include proof of application security
    integrity and readiness including:
      - A summary report with charts, which summarize the collected
        metrics.
      - A security testing report, which describes how well the
        application performed, compared to the policy compliance
        requirements and threat modeling scenarios, and its readiness
        compared to the established security baselines.
      - No outstanding high-severity security defects (for example, a
        simple list showing that all severity 1 security bugs have been
        resolved and verified).
      - An assessment which uses metrics to show that application
        security meets or exceeds established baselines, and that all
        security-related design goals have been met (that is, proof that
        the job is well done).

**Note:** Ideally, the reports should use visual presentation techniques
whenever possible, via charts, graphs, and other methods for displaying
the information visually, so the numbers are easy to comprehend and will
facilitate the decision making process.

## Process

### Description

Utilize the test planning, test results, and metrics data to quantify
the application security meets or exceeds the policy compliance and risk
assessment goals.

### How to identify if you are vulnerable

The presence of a working process results in an operating culture having
certain distinguishing characteristics. Make sure you see some or all of
these operating in yours.

For example,

  - The development team members are getting routinely updated on secure
    coding practices.

<!-- end list -->

  - Design reviews incorporate and encourage security considerations.

<!-- end list -->

  - The QA process includes planning and testing time for security
    assessments, instead of covering them as an afterthought or in an
    ad-hoc fashion.

<!-- end list -->

  - Security-related bugs are specifically tracked and have an
    established escalation policy.

### How to protect yourself

  - Make “Security” an operating word in the engineering team’s
    vocabulary. Encourage training opportunities, discussions, coding
    examples, and on-going interest.

<!-- end list -->

  - Select and employ a vulnerability scoring system, such as CVSS,
    OVAL, or the like. Or at least make sure that security related
    defects have some special tracking method or tag.

<!-- end list -->

  - Make sure the question of “Got security?” comes up during design
    reviews.

<!-- end list -->

  - Establish a working escalation procedure for security-related
    defects.

## Metrics

### Description

The QA group will identify, select, and employ the meaningful metrics to
provide the baseline measurement of application security. This baseline
will serve as a comparison point for future assessments, too.

### How to identify if you are vulnerable

A good system of metrics provides a basis for the following:

  - Summary charts, showing the security-related bug counts over time,
    their open and closure rates, and the progress towards policy
    compliance and risk assessment goals.

<!-- end list -->

  - The numbers necessary to answer management’s questions about “How
    secure is the application?” or “Is risk increasing or decreasing
    over time?”

<!-- end list -->

  - A known security defect density (that is, the average number of
    security bugs per unit of code is being monitored and the rate is
    going in the right direction: Down\!)

### How to protect yourself

  - Establish a working set of metrics. For example, count the number of
    high, medium, and low severity security bugs as a start. Follow with
    rate assessments, which will answer questions like, “How fast are
    security-related bugs being discovered in QA testing?”, “How severe
    are the bugs that are being detected?”, and “How complete is the
    testing coverage for the areas prioritized by our policy compliance
    or risk assessment goals?”

<!-- end list -->

  - Track that all security related tests have been checked (a simple
    spreadsheet will do).

<!-- end list -->

  - Automate the calculation and charting of the metrics as possible, so
    accurate information is available on-demand, even in a dashboard
    summary fashion.

<!-- end list -->

  - Make sure all high-priority security bugs are fixed and
    regression-checked, prior to software release.

## Testing Activities

### Description

### How to identify if you are vulnerable

Not every QA team will employ all of the following testing activities,
but the more you employ strategically, the better your security
assurance will be:

  - Cross-site scripting and SQL injection tests have been run.

<!-- end list -->

  - An assessment of how well the application handles user input,
    including special or multibyte characters, excessively long strings,
    null inputs, or invalid values has been done.

<!-- end list -->

  - Cookie or credentials manipulation testing has been performed.

<!-- end list -->

  - Denial of Service scenarios have been checked. It is understood how
    the application will perform in the presence of connection, login,
    or transaction flooding.

### How to protect yourself

  - Run user agent injection tests (cross-site scripting, SQL query
    injections, data manipulation checks).

<!-- end list -->

  - Check how the application handles user input that is ill-formed, too
    short or too long, or that contains special or multibyte characters.

<!-- end list -->

  - Check how sensitive the application is to cookie manipulation or
    session tampering.

<!-- end list -->

  - Verify the application’s behavior under load. For example, what
    happens if 1,000 users login simultaneously? Or if a flood of TCP/IP
    connections are established, but no SYNs are received?

**Test Data**

PCI DSS Section 6.3.4, ISO 27002:2005 section 12.4.2, COBIT 4.0 AI3.3
all require that production data containing personally identifiable
information not be used for testing purposes.

  - Require data and application owner authorization for requests of
    production data.
  - Replace email addresses, phone numbers, IP addresses, mailing
    address, etc. anatomizing the data as much as possible.

`         o Example: replace the name portion of the email address with a one-way hash value, leaving the domain. `
`         o Other techniques are character scrambling, numerical variance (example: a random number +/- 10% of the original value), nulling, truncating, encoding, aggregating.`
`         o If possible, have your Operations team obfuscate the data prior to restoration.`
`         o Ensure this is performed for any data that can uniquely identify an individual.`
`         o Consider the process whereby data is extracted, stored, transmitted, and sanitized, ensuring that live data remains protected.`

  - Consider artificial data generation using regular expressions and
    pre-defined ranges of values to generate realistic but fake test
    data.

`         o For new new functions with no historical data, this may be the only option.`
`         o This is the safest option.`

  - The full dataset may be too large to use efficiently on slower test
    hardware. A smaller artificial dataset or a subset of obfuscated
    data may be necessary.
  - Enlist the assistance of a Database Administrator, the SQL language
    contains commands like RAND, REPLICATE, and REPLACE.
  - There are open source data generation tools available, such as

`         o dbMonster - `<http://dbmonster.kernelpanic.pl/>
`         o Generate Data - `<http://www.generatedata.com>

## Links

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Activity](Category:Activity "wikilink")
[Category:Test](Category:Test "wikilink")
[Category:Maintenance](Category:Maintenance "wikilink")