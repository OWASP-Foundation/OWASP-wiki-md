## Overview

Purpose:

  - How to detect suspicious activities as soon as possible to reduce
    the impact of incidence or make prevention if possible.
  - How to unify the log format and elements as well as the functions?

Role:

  - Who typically does this?

Security Administrator or independent party who has no access
rights/accounts in the reviewed systems. You can't be an user
administrator. At the same time, you review your activity everyday.
However, if there is a resource limitation, you need another supervisor
to authorize your log review.

Frequency:

It depends on the criticality (i.e. payment system, customer
information, business secret, etc.) of the system labelled by the
organization, logs could be reviewed ranging from minute, every day,
weekly, monthly or even 3 months. In fact, log review is a kind of
detective control and the preventive control is lacking. Log review will
be the Goal Keeper and frequency is critical.

However, user account and authority list should be reviewed at least 3
to 6 months and never take a check ONLY when the audit cycle is coming

## Log Review Tips

Critical systems require at least daily log review, however, what types
of logs/activities should we pay attention to?

1\. Consecutive login failure especially in non-office hour.

2\. Login in non-office hour.

3\. Authority change, addition and removal. Check them against with
authorized application.

4\. Any system administrator's activities

5\. Any unknown workstation/server are plugged into the network?

6\. Logs removal/log overwritten/log size is full

7\. Pay more attention to the log reports after week-end and holiday

8\. Any account unlocked/password reset by system administrators without
authorized forms?

## Log Standard

In fact, we are suffering various log format and standard from various
systems even we are working in-house or act as a consultant. Why don't
we produce a standard/guidelines to developer before they design the
user administrative and audit trail functions to fulfill security
control.

Functions:-

  - Search - By date and time, by event type, by criticality, by
    account/user ID, by department

<!-- end list -->

  - Sorting - By date and time, by event type, by criticality, by
    account/user ID, by department

<!-- end list -->

  - Paging (Optional)

<!-- end list -->

  - Critical event is marked by "\*"

<!-- end list -->

  - Log archive and export

<!-- end list -->

  - Log code and description table

<!-- end list -->

  - Highlighting system and user adminsitrator activities

Mandatory Fields:-

  - User ID and Name (Sometimes, event may involve the action from
    administrator)

<!-- end list -->

  - Activity Date/Timestamp

<!-- end list -->

  - Activity Code, Type and Description

<!-- end list -->

  - Terminal IP address and Location

User Account List:-

  - User Info - Name, Department, Role

<!-- end list -->

  - Last Accessed Time

<!-- end list -->

  - Account Creation Date/Time

<!-- end list -->

  - Current Authority and Role

<!-- end list -->

  - Account authority and information change history

<!-- end list -->

  - Show expired and inactive accounts (for example: 90 days)

## Logging Tools

**Resources from Syslog.org**

  - Event Notification

<u><http://www.syslog.org/wiki/Main/EventNotification></u>

  - Syslog Clients

<u><http://www.syslog.org/wiki/Main/SyslogClients></u>

  - Syslogd Replacements

<u><http://www.syslog.org/wiki/Main/SyslogdReplacements></u>

  - Event Viewers

<u><http://www.syslog.org/wiki/Main/EventViewers></u>

  - Log Analyzers

<u><http://www.syslog.org/wiki/Main/LogAnalyzers></u>

  - Event Correlation

<u><http://www.syslog.org/wiki/Main/EventCorrelation></u>

  - Windows

<u><http://www.syslog.org/wiki/Main/Windows></u>

  - Misc Log Tools

<u><http://www.syslog.org/wiki/Main/MiscLogTools></u>

**Best Practice and Tips from Syslog**

  - Syslog Security Tip

<u><http://www.syslog.org/wiki/Main/SyslogSecurityTip></u>

  - Central Syslog Tip

<u><http://www.syslog.org/wiki/Main/CentralSyslogTip></u>

  - Logging Windows To Syslog Server

<u><http://www.syslog.org/wiki/Main/LoggingWindowsToSyslogServer></u>

  - Logging Troubleshoot

<u><http://www.syslog.org/wiki/Main/TroubleshootingSyslogForwarding></u>

  - Syslog Best Practices

<u><http://www.syslog.org/wiki/Main/SyslogBestPractices></u>

  - Logging, Log File Rotation, and Syslog Tutorial

<u><http://www.hccfl.edu/pollock/AUnix2/Logging.htm></u>

[Category:Activity](Category:Activity "wikilink")
[Category:Logging](Category:Logging "wikilink") [Category:OWASP Logging
Project](Category:OWASP_Logging_Project "wikilink")