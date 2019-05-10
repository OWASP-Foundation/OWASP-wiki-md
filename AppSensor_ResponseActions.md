# About This Document

These response actions are part of the [OWASP
AppSensor](http://www.owasp.org/index.php/Category:OWASP_AppSensor_Project)
project which advocates bringing intelligent intrusion detection inside
the application. These responses can be used to counter a malicious user
that [has been
detected](http://www.owasp.org/index.php/AppSensor_DetectionPoints)
probing for vulnerabilities or weaknesses within your application.

__TOC__

# Overview

The following table lists possible AppSensor Responses (ASRs), other
than no response (ASR-P). The application response actions are
categorized here from the user's perspective (not from the
application/server's perspective):

  - Silent: User(s) unaware of any application change
  - Passive: Process altered, but user(s) may still continue to process
    completion
  - Active: Functionality reduced or disabled
  - Intrusive: Non-malicious action on user's system

*To add a response action, just use the next available letter (e.g.
"ASR-Q") - they don't have to be in alphabetical order below, but place
it in the appropriate category (silent, passive, active or intrusive).
The image in the table below can be updated later to keep in step with
the page content.*

![<File:Appsensor_response_actions_table_1.png>](Appsensor_response_actions_table_1.png
"File:Appsensor_response_actions_table_1.png")

A text version of the table, with some examples and alternative
classifications, is described in [AppSensor - Response
Actions](http://www.owasp.org/index.php/File:Owasp-appsensor-responses.pdf)
(63 KB PDF). The information on the page below is likely to be more
up-to-date.

# Detailed Listing

Classifications are:

  - Purposes: Logging, Notifying, Disrupting and Blocking
  - Target: One, Some or All users
  - Response duration: Instantaneous (e.g. just for the request), Period
    (e.g. time period or session duration), Permanent

## Silent

### ASR-P: No Response

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-P

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

No Response

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(not applicable)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Silent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

There is no response. This could be used to record in logs that a
detection event did not lead to any particular response action.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A detection point fired, but the threshold for response has
not been reached

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-A: Logging Change

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-A

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging Change

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging | One, some or all users | Instantaneous (request) or for a
period

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Silent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The granularity of logging is changed (typically more logging).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Capture sanitised request headers and response bodies

Example 2: Full stack trace of error messages logged

Example 3: Record DNS data on user's IP address

Example 4: Security logging level changed to include 'informational'
messages

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-B: Administrator Notification

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-B

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Administrator Notification

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging and notifying | One, some or all users | Instantaneous

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Silent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A notification message is sent to the application administrator(s)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Email alert sent to everyone in the administration team

Example 2: SMS alert sent to the on-call administrator

Example 3: Visual indicator displayed on an application monitoring
dashboard

Example 4: Audible alarm in the control room

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-C: Other Notification

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-C

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Other Notification

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging and notifying | One user | Instantaneous

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Silent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Notification message sent to something or someone other than
Administrators (see ASR-B) or the User (see ASR-E)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The message recipient (e.g. firewall) could take some action otherwise
unavailable to the application (e.g. disruptive - the application makes
a silent response, but the firewall actively intervenes and perhaps
blocks the user).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Broadcast event to SIEM

Example 2: Signal sent to upstream network firewall, application
firewall (e.g. XML, web) or load balancer

Example 3: Alert sent to fraud protection department

Example 4: Record added to server event log

Example 5: Event highlighted in a daily management report

Example 6: Email alert to staff member's manager

Example 7: Proactive entry added to customer support system (e.g.
"Someone had difficulty logging in with this customer's username -
request extra validation for telephone enquiries")

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-N: Proxy

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-N

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Proxy

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging | One, some or all users | For a period or permanent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Silent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Send the request to a different back-end location. For redirection that
the user will be aware of, see See ASR-G instead.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Requests from the user invisibly (from the user's
perspective) passed through to a hardened system

Example 2: Request are proxied to a special honeypot system which
closely mimics or has identical user functionality

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

## Passive

### ASR-D: User Status Change

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-D

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

User Status Change

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging | One user | For a period

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Passive

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A parameter related to the user is modified. This may have an impact on
functionality or usability of the application, but only for the one
user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Internal trustworthiness scoring about the user changed

Example 2: Reduce payment transfer limit for the customer before
additional out-of-band verification is required

Example 3: Reduce maximum file size limit for each file upload by the
forum user

Example 4: Increase data validation strictness for all form submissions
by this citizen

Example 5: Reduce the number of failed authentication attempts allowed
before the user's account is locked (ASR-K below)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-E: User Notification

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-E

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

User Notification

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying and disrupting | One user | Instantaneous

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Passive

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A visual, audible and/or mechanical (e.g. vibration) signal or message
is activated, displayed, or sent by other means, to the user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: On-screen message about mandatory form fields (e.g. "The
'occupation' must be completed")

Example 2: On-screen message about data validation issues (e.g. 'The
bank sort code can only contain six digits with optional hyphens')

Example 3: Message sent by email to the registered email address to
inform them their password has been changed

Example 4: On-screen message warning that they have been detected
performing malicious activity (e.g. [Mr
Clippy](http://www.irongeek.com/i.php?page=security/phpids-install-notes)
idea)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-F: Timing Change

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-F

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Timing Change

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging and disrupting | One, some or all users | Instantaneous
(request) or for a period

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Passive

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The usual timescales to perform an operation are altered, usually
extended, or delays are added.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Extend response time for each failed authentication attempt

Example 2: File upload process duration extended artificially

Example 3: Add fixed time delay into every response

Example 4: Order flagged for manual checking

Example 5: Goods despatch put on hold (e.g. despatch status changed)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

## Active

### ASR-G: Process Terminated

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-G

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Process Terminated

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes) and disrupting | One user | Instantaneous

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An interruption to the sending, display or process, such that the user
has to start again, or start somewhere else. For authenticated users,
this would not include termination of their session (see ASR-J). And,
they would be free to attempt the process again (e.g. access the
resource after logging in, submit a payment transfer, etc).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Discard data, display message and force user to begin
business process from start

Example 2: Redirection of an unauthenticated user to the log-in page

Example 3: Redirection to home page

Example 4: Display other content (i.e. terminate process but display the
output of some other page without redirect)

Example 5: Redirection to a page on another website

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-H: Function Amended

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-H

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Function Amended

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes), disrupting and blocking | One, some or
all users | For a period or permanent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The usual functionality is amended but not disabled (see ASR-I).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Limit on feature usage rate imposed

Example 2: Reduce number of times/day the user can submit a review

Example 3: Additional registration identity validation steps

Example 4: Additional anti-automation measures (e.g. out-of-band
verification activated, CAPTCHA introduced)

Example 5: Static rather than dynamic content returned

Example 6: Additional validation requirements for delivery address

Example 7: Watermarks added to pages, images and other content

Example 8: Additional human interactive proof challenges added due to
the number of incorrect guesses of CAPTCHAs outnumbering the correct
guesses by more than a certain factor (e.g. [Token
bucket](http://research.microsoft.com/pubs/74609/CCS2007.pdf) idea)

Example 9: Fuzz responses to mask real functionality or increase
attacker efforts to enumerate the application (e.g. random URL
generation using [ADHD Spider
Trap](http://sourceforge.net/p/adhd/wiki/Home/) or
[Weblabyrinth](https://code.google.com/p/weblabyrinth/), realistic but
invalid cipher text data using techniques such as [honey
encryption](http://www.technologyreview.com/news/523746/honey-encryption-will-bamboozle-attackers-with-fake-secrets/))

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-I: Function Disabled

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-I

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Function Disabled

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes), disrupting and blocking | One, some or
all users | For a period or permanent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A function or functions are disabled for one, some or all users. Other
functionality continues to work as normal.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

For changes that affect multiple users, be careful the response cannot
be used too easily for denial of service.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: 'Add friend' feature inactivated

Example 2: 'Recommend to a colleague' feature links removed and disabled

Example 3: Document library search disabled

Example 4: Prevent new site registrations

Example 5: Web service inactivated or cloaked

Example 6: Content syndication stopped

Example 7: Automated Direct Debit system turned off and manual form
offered instead

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-J: Account Logout

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-J

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Account Logout

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes), disrupting and blocking | One user |
Instantaneous

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The current session is terminated on the server, and the user is logged
out.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Often undertaken in conjunction with process termination (ASR-G) and
sometimes lockout (ASR-K).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Session terminated and user redirected to logged-out message
page

Example 2: Session terminated only (no redirect)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-K: Account Lockout

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-K

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Account Lockout

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes), disrupting and blocking | One user | For
a period or permanent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An account, session or source address is blocked from access and/or
authentication.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

If IP blocking is implemented, it is recommended this is undertaken at
the network layer using the operating system (e.g. iptables, Windows
firewall) or by a network device (e.g. firewall).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: User account locked for 10 minutes

Example 2: User account locked permanently until an Administrator resets
it

Example 3: One user's IP address range blocked

Example 4: Unauthenticated user's session terminated

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

### ASR-L: Application Disabled

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-L

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Application Disabled

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging, notifying (sometimes), disrupting and blocking | All users |
Permanent

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Active

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The whole application is disabled or made unavailable.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Be careful the response cannot be used too easily for denial of service.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Website shut down and replaced with temporary static page

Example 2: Application taken offline

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

## Intrusive

### ASR-M: Collect Data from User

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

id

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ASR-M

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Collect Data from User

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

classifications

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Logging | One user | For a period

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Intrusive

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Direct action to collect further information from the user's system.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

consideration

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This response is meant to be non-malicious in intent - it is simply
additional information gathering - and not retaliatory or damaging to
the user, their systems or data, nor make any permanent change. An alert
user might be aware of the action. Be very wary of data collected and
perform appropriate validation and sanitization. Ensure any use of this
type of response is legally permissible in the relevant jurisdictions,
and complies with corporate policies and the application's terms of use,
privacy notice and corporate policies.

To a certain extent, any additional payload in a response might cause a
user's browser or computer to crash, and this might have unforeseen
circumstances.

The information collection could use techniques like these described
elsewhere:

  - [Panopticlick](http://panopticlick.eff.org)
    [methods](http://panopticlick.eff.org/about.php) to gather
    information on the user's browser and computer configuration
  - [Response content
    injection](http://www.modsecurity.org/projects/modsecurity/apache/feature_content_injection.html)
    using JavaScript to discover the user's real IP address
  - [Embeddable decloaking engine](http://decloak.net/) to discover the
    real IP address of a web user
  - [Using ModSecurity and
    BeEF](https://speakerdeck.com/rcbarnett/building-a-web-attacker-dashboard-with-modsecurity-and-beef)
    to monitor an attacker

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Deploy additional browser fingerprinting using JavaScript in
responses

Example 2: Deploy a Java applet to collect remote IP address

Example 3: Deploy JavaScript to collect information about the user's
network

Example 4: Record mobile phone fingerprint and IMEI number

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

</table>

[Category:OWASP AppSensor
Project](Category:OWASP_AppSensor_Project "wikilink")