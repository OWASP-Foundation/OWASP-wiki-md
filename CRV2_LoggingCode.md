\<\< This is a draft \>\>

## Overview

Applications log messages of varying intensity and to varying sinks.
Many logging APIs allow you to set the granularity of log message from a
state of logging nearly all messages at level 'trace' or 'debug' to only
logging the most important messages at level 'critical'. Where the log
message is written to is also a consideration, sometimes it can be
written to a local file, other times to a database log table, or it
could be written over a network link to a central logging server.

The volume of logging has to be controlled since the act of writing
messages to the log uses CPU cycles, thus writing every small detail to
a log will use up more resources (CPU, network bandwidth, disk space).
Couple that with the fact that the logs have to be parsed or interpreted
by a tool or human in order for them to be useful, the consumer of the
log could have to parse through thousands of lines to find a message of
consequence.

## Description

Logs can vary by type; for example a log may simply contain application
state or process data, allowing support or development track what the
system is doing when a bug has occurred. Other logs may be specific to
security, only logging important information that a central security
system will have interest in. Further logs could be used for business
purposes, such as billing.

Application logs can be powerful as the application business logic has
the most information about the user (e.g. identity, roles, permissions)
and the context of the event (target, action, outcomes), and often this
data is not available to either infrastructure devices, or even
closely-related applications. Application logging is an important
feature of a production system, especially to support personnel and
auditors, however it is often forgotten and is rarely described in
sufficient detail in design/requirement documentation. The level and
content of security monitoring, alerting and reporting needs to be set
during the requirements and design stage of projects, and should be
proportionate to the information security risks. Application logging
should also be consistent within the application, consistent across an
organization's application portfolio and use industry standards where
relevant, so the logged event data can be consumed, correlated, analyzed
and managed by a wide variety of systems.

All types of applications may send event data to remote systems, either
directly over a network connection, or asynchronously though a
daily/weekly/monthly secure copy of the log to some centralized log
collection and management system (e.g. SIEM or SEM) or another
application elsewhere.

If the information in the log is important, and could possibly be used
for legal matters, consider how the source (log) can be verified, and
how integrity and non-repudiation can be enforced. Log data, temporary
debug logs, and backups/copies/extractions, must not be destroyed before
the duration of the required data retention period, and must not be kept
beyond this time. Legal, regulatory and contractual obligations may
impact on these periods.

Server applications commonly write event log data to the file system or
a database (SQL or NoSQL), however logging could be required on client
devices such as applications installed on desktops and on mobile devices
may use local storage and local databases. Consider how this client
logging data is transferred to the server.

## What to Review

When reviewing code modules from an logging point of view, some common
issues to look out for include:

  - When using the file system, it is preferable to use a separate
    partition than those used by the operating system, other application
    files and user generated content
  - For file-based logs, apply strict permissions concerning which users
    can access the directories, and the permissions of files within the
    directories
  - In web applications, the logs should not be exposed in
    web-accessible locations, and if done so, should have restricted
    access and be configured with a plain text MIME type (not HTML)
  - When using a database, it is preferable to utilize a separate
    database account that is only used for writing log data and which
    has very restrictive database, table, function and command
    permissions
  - Consider what types of messages should be logged:
      - Input validation failures e.g. protocol violations, unacceptable
        encodings, invalid parameter names and values
      - Output validation failures e.g. database record set mismatch,
        invalid data encoding
      - Authentication successes and failures
      - Authorization (access control) failures
      - Session management failures e.g. cookie session identification
        value modification
      - Connection timings

Consider what each log message should contain:

  -   - Date and time, in some common format (also makes sense to ensure
        all nodes of an application are synced through something like
        NTP
      - User ID performing the action
      - Action being performed/attempted
      - Information on the client, e.g. IP address, source port,
        user-agent

  - External classifications e.g. NIST Security Content Automation
    Protocol (SCAP), Mitre Common Attack Pattern Enumeration and
    Classification (CAPEC)

  - Perform sanitization on all event data to prevent log injection
    attacks e.g. carriage return (CR), line feed (LF) and delimiter
    characters (and optionally to remove sensitive data)

  - If writing to databases, read, understand and apply the SQL
    injection cheat sheet

  - Ensure logging is implemented and enabled during application
    security, fuzz, penetration and performance testing

  - Ensure logging cannot be used to deplete system resources, for
    example by filling up disk space or exceeding database transaction
    log space, leading to denial of service

  - The logging mechanisms and collected event data must be protected
    from mis-use such as tampering in transit, and unauthorized access,
    modification and deletion once stored

  - Store or copy log data to read-only media as soon as possible

  - Consider what should not be logged:

      - Session identification values (consider replacing with a hashed
        value if needed to track session specific events)
      - Sensitive personal data and some forms of personally
        identifiable information (PII)
      - Authentication passwords (successful or unsuccessful)
      - Database connection strings
      - Keys
      - Data of a higher security classification than the logging system
        is allowed to store

## References

  - See NIST SP 800-92 Guide to Computer Security Log Management for
    more guidance.
  - Mitre Common Event Expression (CEE)
  - PCISSC PCI DSS v2.0 Requirement 10 and PA-DSS v2.0 Requirement 4
  - Other Common Log File System (CLFS), Microsoft