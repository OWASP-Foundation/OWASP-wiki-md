If you are planning on adding an application security verification
activity to your existing SDLC using the [OWASP Application Security
Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink"),
you will need to do some planning. You will need to work closely with
both project managers and developers. It is not enough, although it is a
necessary prerequisite, to have buy-in from application owners. This
article describes one possible way to bootstrap your SDLC with
verification activities.

![Image:Asvs_boot.gif](Asvs_boot.gif "Image:Asvs_boot.gif")

The first step is to clearly set expectations with both project managers
and with developers. It is strongly advised to meet for a full day or
two with project managers and developers after the decision has been
made by application owners that application security verification
activities will be added to your SDLC. You should:

  - Present an overview of the process
      - Generic information about architecture review
      - Generic information about automated and manual verification
      - Generic information about adding verification activities into
        SDLC
  - Collect inputs
      - Code and available documentation
      - Perform an ASVS Level 1 or 2 security architecture review
      - Determine an ASVS Level 1 verification strategy (do NOT attempt
        higher level since is first time)
  - Produce a verification report template

The verification report template document will contain collected
information, information about techniques that you will use, and
information about how verifications can be inserted into their SDLC.
This document will also contain warnings about revised cost estimates
based on unexpected complexity and additional caveats.

The next step is to collect and address comments received on the
verification report template, and create a project schedule at this
point as well. An addendum should also be generated for the proposal if
the initial cost estimates change based on information collected up to
this point.

The next step is to perform the initial verification. Perform dynamic
and static analysis using tools, and go a little deeper in reviewing the
design information. Although, perhaps defer performing further design
review for this go-round if available hours or patience is short. Write
up your results as you perform the different reviews. Make sure not just
to write up problems, but also at least identify parts of code that were
reviewed that were not found to have problems.

The next step is to communicate your findings and proposed ways to fix
or otherwise mitigate your findings. It is strongly advised to meet for
a full day or two with project managers and developers to:

  - Present all findings,
  - Answer any questions,
  - Identify findings which they do not plan to remediate, and
  - Propose frequency and ASVS levels for future verifications performed
    as a new activity added to their *existing* SDLC

Make sure to write down rationale for why they are going to assume the
risk for those they do not plan to remediate. Update the verification
report with this information. Further update the verification report
with any corrections based on presentation of findings. Work with
project managers and developers to identify frequency and depth of
future verifications as a new activity added to their *existing* SDLC.
Update the verification report with this information. Create a proposal
for future work based on proposed SDLC that has been bootstrapped with
verification activities.

Helpful hints:

  - Keep project managers and developers in the loop over the entire
    course of the above activities by providing weekly status reports to
    them. A simple email that lists accomplishments, plans for next
    week, issues, and any updates to project schedules will help project
    managers and developers manage their time and resources, and will
    help build trust.

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")