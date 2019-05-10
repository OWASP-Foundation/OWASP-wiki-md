Code reviews exist in every formal Software Design Life Cycle (SDLC)
(see appendix on SDLC diagrams). Code reviews also vary widely in their
level of formality. Also to confuse the subject more is code reviews
vary in purpose and what the code reviewer is looking for, security,
compliance, programming reviews, etc. Throughout the SDLC ( XP, Agile,
RAD, BSIMM, CMMI, Microsoft ALM ) there are points at which an
application security consultant needs to be involved. The idea of
integrating secure code reviews into your SLDC may sound daunting and
adding another layer of complexity or an additional cost and time
duration to an already budget and time constrained project but it is a
proven cost effective, and provides an additional level of security that
static analyzers can not provide.

When integrating secure code reviews into the SDLC the organization
needs to create standards and policies that the secure code reviewer
should adhere to. This is to create the right importance of the task so
it is not just looked at as a project task that just needs to be checked
off. Project time also needs to be assigned to the task so it has enough
time to complete the tasks and for any remedial tasks that come out of
the secure code review.

A formal test report will provide enough detail information to enable
the code reviewer to classify and prioritize the software
vulnerabilities based on the applications threat model. This formal test
report does not need to be pages in length but it should provide the
following information.

  - Date of review
  - Application Name, Code modules reviewed.
  - Developers and Code Reviewers names.
  - Task name, (TFS, GIT, Subversion, trouble ticket, etc).
  - A brief sentence(s) to classify and prioritize software
    vulnerability if any and what if any remedial tasks need to be
    accomplished or follow up is needed.
  - Threat model used.
  - Code Review checklist if used, or link to organization Code Review
    checklist.
  - If any tools such as FxCop, BinScope Binary Analyzer, etc were used
    prior to code review.

**When to review:** Most Integrated Development Environments (IDE) use
today, (Visual Studio, Eclipse, NetBeans, Microsoft’s Team Foundation
Server (TFS)) have incorporated code reviews process into their IDEs.
When a code review request is submitted the request will show up in the
reviewers work task. The IDEs today can easily show and detect all
changes to the project the reviewer needs to be aware of. This request
for code review can be done at code check in or when project is
submitted to the QA process.

Today most organizations have modified their SDLC process to use add
agile into their SDLC process. Because of this the organization is going
to need to look at their own internal development practices to best
determine where and how often secure code reviews need to happen. At the
minimum an organization needs to complete a secure code review of the
design on a new application or if the application is having major
software upgrade. Second required is a secure coding review during the
QA process before deployment. If QA errors are found the project is
returned to development the software fix may cause software
vulnerability.

If the project a over budget time and money then this increase the
chance of a software fix could cause a secure vulnerability since now
the emphasis is on getting the project to deployment. Code reviews for
code in production may find software vulnerabilities but lets be honest
now we are in a race with hackers to find the bug and the vulnerable
software will remain in production while the remedial fix is being
worked on.

**Who to review:** Code reviewer sounds like a job for a security or
risk-analysis team member but all developers need to understand the
exposure points of their applications and what threats exist for their
applications. Most security teams do not have members with coding
backgrounds, which can make interactions with development teams
challenging. Because of this development teams are usually skeptical of
security input and guidance. Security teams are usually willing to slow
things down to ensure confidentiality and integrity controls are in
place while developers are face with pressure from business units they
support to create and update code as quickly as possible. Unfortunately
the more critical the application to operational or business needs, the
more pressure to deplore the code to production. Adding on top of this
is development teams moving to Agile development style, which main
mantra is “speed above all else with less formal processes”. So who is
going to take on the job of secure code reviews? The answer is not one
individual but a team of people. A “security toll gate” needs to be
established. During the phases of architecture, development, QA each
phase needs to have its own “security tool gate”.

Security team needs to be involved during the design and when
confidentiality and integrity controls are being created or modified.
The security team needs to work risk-analysis so that a threat model is
created so the programmers need to know what threats they need to pay
attention to during coding. Programmers peer or technical lead need to
ensure that all code check in as been run thru static analyzers and the
code has been check by another a peer or technical lead. This will be
done in most cases by the IDE the organization is using. Last is the QA
process needs to be part of the “security toll gate” before the code is
deployed to production.