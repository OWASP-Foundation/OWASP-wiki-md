# OWASP Project Disclosure Policy

This policy describes the official OWASP Policies on reporting security
vulnerabilities, project staff responsibilities, how users are
protected, and the lifecycle of reported vulnerabilities in OWASP
branded projects.

# What to do if you find a vulnerability

If you find a vulnerability in an OWASP branded software library or
tool, you can send details of that vulnerability to
<security@owasp.org>. Please be sure to include as many details as you
can about the vulnerability, a Proof Of Concept if one has been created,
and your contact information so that the OWASP Global Projects Committee
can stay in contact with you and credit the discovery to you.

Once we have received your initial contact, the GPC will acknowledge
your report and create an issue to track the life cycle of the
vulnerability. In the acknowledgment e-mail, you will receive a
reference number with which to refer to the vulnerability in subsequent
communications, as well as an outline of the vulnerability lifecycle
described below.

## Initial Contact

The Global Projects Committee (GPC) will notify the security liaison or
leader of the project if a security liaison is not assigned as listed on
the project information page of the issue, along with any details
provided by the discoverer and a reference to the open issue in the GPC
Security Issue Vulnerability Database. It is expected that project
leaders or other personnel from the project acknowledge the
vulnerability within seven (7) days of initial contact. This
acknowledgment should present an estimate of the expected time to
resolve the issue and if available, a workaround solution that can be
provided to users who subscribe to the security-alerts@owasp.org mailing
list as well as users subscribed to the
security-alerts@\[project\].owasp.org mailing list.

## Second Contact

If no response from the project leader has been received within seven
(7) days of initial contact, the GPC will send a second notice to the
security liaison or project leader as well as other management staff
listed on the project information page. The project staff will have
seven (7) days from the time of second contact or fourteen (14) days
from the date of initial contact to respond with an acknowledgment to
the GPC.

## Final Contact

If, after fourteen (14) days from initial contact with the project
staff, the GPC has received no response from the project staff, a third
and final email will be sent to the security liaison, project leader,
and all committers on the project. The project will have fourteen (14)
days from the data of final contact or twenty eight (28) days from the
date of initial contact to respond with an acknowledgment to the GPC.

## Resolution

The project will have one hundred eighty (180) days from the date of
initial contact to resolve the issue and notify the GPC of the
resolution. Resolution should be one of the following top level
conditions.

### Vulnerability Fixed

If the project team has fixed the vulnerability, the GPC Vulnerability
Database should be updated with a status of "Fixed" and a patch to the
code should be checked into the projects SCM as well as test cases to
ensure the issue is resolved. In addition, a patch-level release to the
project should be released.

### Won't Fix

If the project team has determined that the issue will not be fixed,
they should notify the GPC of this decision in writing with a detailed
explanation of why and how the decision was reached. In addition the
security liaison or project leader should update the GPC Vulnerability
Database with a status of "Wont Fix".

### More Time Needed

If resolution of the vulnerability is unusually complex or difficult to
implement, the project team can request an extension of time from the
GPC. To request an extension, the security liaison or project leader
should send an email to the GPC with a detailed description of why the
issue is particularly complex to solve and why more time is needed to do
so. The GPC will hold a vote on whether the extension will be granted.
The extension will be valid for thirty (30) days beyond one hundred
eighty (180) day limit.

## Disclosure

\==

# What you need to know if you are a user

# What you need to know if you are a project leader

# Working Session Notes

Ack. From Leader of Issue

First Notice to Project Leaders - Response Expected within 7 days from
initial notice to leader Second Notice to Project Leaders - Response
Expected within 14 days from initial notice to leader Final Notice to
Project Leaders - Response Expected within 30 days from initial notice
to leader

If no ack of issue, full disclosure or disclosure of the issue will be
released. Full or partial disclosure to be determined and voted on by
GPC on a case by case basis.

Ack. of Resolution within 180 days of initial contact

  - if project leader provides detailed explanation of why a fix will
    take longer, GPC can decide to extend the disclosure period in 30
    day increments.

The maximum resolution period that will be granted cannot extend beyond
365 from the date of initial contact.

Projects will be required to assign a person to fill the role of
security liaison as part of the process of becoming a OWASP Mainstream
Projects.

Creation of a new mailing list security-alerts for users to subscribe to
be notified of vulnerabilities and software patches with the disclosure
template

Project leaders will be responsible for notifying their users mailing
list of vulnerabilities with the GPC provided disclosure alert

Projects should have available a private mailing list
security-alerts@\[project\].owasp.org for early notification of
vulnerabilities and workaround solutions