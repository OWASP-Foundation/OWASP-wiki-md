[\< Back to The
Application_Security_Program_Quick_Start_Guide](Application_Security_Program_Quick_Start_Guide "wikilink")

## Key Activities

  - Measure current vulnerability posture.
  - Initiate vulnerability testing.
  - Triage vulnerabilities.

<span id="Vulnerability Assessments"></span>

## Vulnerability Assessments

To determine what sort of vulnerability assessment is most appropriate,
consider your current status and resources:

| Scenario                                                                                         | Appropriate Assessments                                                                        |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| Resources and support for immediate unlimited continuous assessments                             | Perform assessments across all discovered assets                                               |
| Limited resources or appetite for unlimited continuous assessments                               | At a minimum frequency of testing should keep or exceed rate of change in asset                |
| Application currently exist in production environment:                                           | Begin dynamic\* assessments for these existing applications                                    |
| Source Code of your application(s) is available on the internet (Freely available, stolen, etc.) | Begin Static Analysis assessments                                                              |
| Business is subject to compliance mandate requiring Static Analysis                              | Begin Static Analysis assessments                                                              |
| New development project of an application Begin Static Analysis assessments                      | Dynamic assessments completed and application security program in continuous improvement cycle |
| Begin Static Analysis assessments                                                                | Begin Dynamic Analysis in QA/Staging                                                           |

Other scenarios to consider Static Analysis as the first assessment type
or in parallel with Dynamic Analysis:

  - High developer attrition rate
  - Known internal bad actors
  - Disgruntled current or former employee with access to source code
  - Outsourced code

## Static Analysis

Static Code Analysis (also known as Source Code Analysis or Static
Application Security Testing (SAST)) is usually performed as part of a
Code Review (also known as white-box testing) and is carried out at the
Implementation phase of a Security Development Lifecycle (SDL). Static
Code Analysis commonly refers to the running of Static Code Analysis
tools that attempt to highlight possible vulnerabilities within ‘static’
(non-running) source code by using techniques such as Taint Analysis and
Data Flow Analysis.

## Dynamic Analysis

Dynamic Application Security Testing (DAST), also referred to as
“black-box” testing, identifies vulnerabilities in running web
applications – testing of the application from the outside in.

<span id="Vulnerability Delivery"></span>

## Vulnerability Delivery

To deliver valuable vulnerability information to your business, you
must:

  - Document vulnerability delegation and vulnerability lifecycle
    process
  - Feed issues into existing tracking systems where possible to
    preserve the existing workflow
  - Triage vulnerabilities prior to feeding them into your defect
    management systems
  - Ensure only true positives are fed to development teams
  - Track re-testing of vulnerabilities via new incident/ticket or
    update existing incident/ticket.
  - Define which issues are important to the business
  - Create a baseline of the issues that are important to the business
  - Align vulnerability remediation strategy with loss exposure versus
    resources available to fix
  - Create a knowledge base of common issues and their solutions
  - Dedicate resource(s) to developer interactions, including educating
    developers on security topics
  - Publish aggregate metrics internally
  - Match or outpace release cycles in detecting and responding to
    vulnerabilities.

[\< Back to The
Application_Security_Program_Quick_Start_Guide](Application_Security_Program_Quick_Start_Guide "wikilink")