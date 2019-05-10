If you are performing an application security verification, you can use
[OWASP Application Security Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
to help create a project schedule. The ASVS verification and reporting
requirements can be translated into project tasks and milestones,
provide insight as to what resources will be required to perform a given
verification, and provide a basis for measuring progress.

![Image:Asvs_project.GIF](Asvs_project.GIF "Image:Asvs_project.GIF")

The first step to perform a verification is to define verification
tasks. Verification tasks will be different, depending on the targeted
OWASP ASVS verification level.

  - Example level 1 tasks: *Collect information, perform initial design
    review, create report, perform scan, review scan results, finalize
    report.*
  - Example level 2 tasks: *Collect information, perform initial design
    review, create report, perform scan, review scan results, create
    manual tests, perform manual tests, review manual test results,
    finalize report.*
  - Example level 3 tasks: *Collect information, perform initial design
    review, create report, perform scan, review scan results, create
    manual tests, perform manual tests, review manual test results,
    perform detailed design review, review detailed design review
    results, finalize report.*
  - Example level 4 tasks: *Collect information, perform initial design
    review, create report, perform scan, review scan results, create
    manual tests, perform manual tests, review manual test results,
    perform detailed design review, review detailed design review
    results, perform search for malicious code, finalize report.*

Milestones would then correspond to the completion of a given
verification task, and a final milestone would correspond to the
completion of all verification tasks.

The increase in level of effort to perform OWASP ASVS verifications at
different levels for a given application is intended to be relatively
linear.

  - Example level 1 overall duration: *1 - 2 weeks*
  - Example level 2 overall duration: *2 - 3 weeks*
  - Example level 3 overall duration: *3 - 4 weeks*
  - Example level 4 overall duration: *4+ weeks*

The above estimates do not include time to perform remediation. The size
and the complexity of the application(s) should always be taken into
account.

The next step to perform a verification is to identify resources that
will be necessary, including both people and materials.

  - Example people resources: *project manager, team lead, verifier.*
  - Example material resources: *dynamic scan tools, source code scan
    tools.*

The availability and cost for both people (e.g. rate) and resources
(e.g. license fees) should then be taken into account.

The next step to perform a verification is to assign people and
materials to individual tasks.

  - Example level 1 assignment: *assign collect information to team
    lead*
  - Example level 1 assignment: *assign perform initial design review to
    team lead and verifier.*
  - Example level 1 assignment: *assign create report to team lead.*
  - Example level 1 assignment: *assign perform scan to verifier.*
  - Example level 1 assignment: *assign review scan results to
    verifier.*
  - Example level 1 assignment: *assign finalize report to team lead and
    verifier.*

The project manager may not in practice be assigned to a specific task,
unless the project schedule is detailed enough to include tasks such as
project status reviews.

The last step to perform a verification is to track verification
progress. OWASP ASVS verification requirements and reporting
requirements can be used towards this end.

  - Example computation to determine a verification task’s percent
    complete: *for each set of applicable verification requirements for
    each application, divide the number completed by the total number.*
  - Example computation to determine a reporting task’s percent
    complete: *for each set of reporting requirements for each
    application, divide the number completed by the total number.*

Helpful hints:

  - The amount of overhead that dedicated project management introduces
    can be significant. Project management activities should be tailored
    for a given verification to minimize costs.

`   `**`DO``   ``NOT``   ``PERFORM``   ``A``   ``DYNAMIC``   ``SCAN``
 ``OR``   ``PENTEST``   ``WITHOUT`**`  `
`   `**`THE``   ``APPLICATION``   ``OWNER'S``   ``PRIOR``   ``WRITTEN``
 ``AGREEMENT!`**

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")