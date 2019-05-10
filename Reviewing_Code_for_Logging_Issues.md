__TOC__

### In Brief

Logging is the recording of information into storage that details who
performed what and when they did it (like an audit trail). This can also
cover debug messages implemented during development, as well as any
messages reflecting problems or states within the application. It should
be an audit of everything that the business deems important to track
about the application’s use. Logging provides a detective method to
ensure that the other security mechanisms being used are performing
correctly.

There are three categories of logs; application, operation system, and
security software. While the general principles are similar for all
logging needs, the practices stated in this document are especially
applicable to application logs.

A good logging strategy should include log generation, storage,
protection, analysis, and reporting.

#### Log Generation

Logging should be at least done at the following events:
**Authentication**: Successful and unsuccessful attempts.
**Authorization requests**.
**Data manipulation**: Any (CUD) Create, Update, Delete actions
performed on the application.
**Session activity**: Termination/Logout events.
The application should have the ability to detect and record possible
malicious use, such as events that cause unexpected errors or defy the
state model of the application, for example, users who attempt to get
access to data that they shouldn’t, and incoming data that does not meet
validation rules or has been tampered with. In general, it should detect
any error condition which could not occur without an attempt by the user
to circumvent the application logic. Logging should give us the
information required to form a proper audit trail of a user's actions.

Leading from this, the date/time actions were performed would be useful,
but make sure the application uses a clock that is synched to a common
time source. Logging functionality should not log any personal or
sensitive data pertaining to the user of function at hand that is being
recorded; an example of this is if your application is accepting HTTP
GET the payload is in the URL and the GET shall be logged. This may
result in logging sensitive data.

Logging should follow best practice regarding data validation; maximum
length of information, malicious characters…. We should ensure that
logging functionality only logs messages of a reasonable length and that
this length is enforced. Never log user input directly; validate, then
log.

#### Log Storage

In order to preserve log entries and keep the sizes of log files
manageable, log rotation is recommended. Log rotation means closing a
log file and opening a new one when the first file is considered to be
either complete or becoming too big. Log rotation is typically performed
according to a schedule (e.g. daily) or when a file reaches a certain
size.

#### Log Protection

Because logs contain records of user account and other sensitive
information, they need to be protected from breaches of their
confidentiality, integrity, and availability, the triad of information
security.

#### Log Analysis and Reporting

Log analysis is the studying of log entries to identify events of
interest or suppress log entries for insignificant events. Log reporting
is the displaying of log analysis. Although these are normally the
responsibilities of the system administrator, an application must
generate logs that are consistent and contain info that will allow the
administrator to prioritize the records. Logging should create an audit
of system events and also be time stamped in GMT as not to create
confusion. In the course of reviewing logging transactional events such
as Create, Update, or Delete (CUD), business execution such as data
transfer and also security events should be logged.

### Common open source logging solutions

Log4J: <http://logging.apache.org/log4j/docs/index.html>

Log4net: <http://logging.apache.org/log4net/>

Commons Logging:
<http://jakarta.apache.org/commons/logging/index.html>
In Tomcat(5.5), if no custom logger is defined (log4J) then everything
is logged via Commons Logging and ultimately ends up in catalina.out.
catalina.out grows endlessly and does not recycle/rollover. Log4J
provides “Rollover” functionality, which limits the size of the log.
Log4J also gives the option to specify “appenders” which can redirect
the log data to other destinations such as a port, syslog, or even a
database or JMS.

The parts of log4J which should be considered apart from the actual data
being logged by the application are contained in the log4j.properties
file:

`#`
`# Configures Log4j as the Tomcat system logger`
`#`

`#`
`# Configure the logger to output info level messages into a rolling log file.`
`#`
`log4j.rootLogger=INFO, R`

`#`
`# To continue using the "catalina.out" file (which grows forever),`
`# comment out the above line and uncomment the next.`
`#`
`#log4j.rootLogger=ERROR, A1`

`#`
`# Configuration for standard output ("catalina.out").`
`#`
`log4j.appender.A1=org.apache.log4j.ConsoleAppender`
`log4j.appender.A1.layout=org.apache.log4j.PatternLayout`
`#`
`# Print the date in ISO 8601 format`
`#`
`log4j.appender.A1.layout.ConversionPattern=%d [%t] %-5p %c - %m%n`

`#`
`# Configuration for a rolling log file ("tomcat.log").`
`#`
`log4j.appender.R=org.apache.log4j.DailyRollingFileAppender`
`log4j.appender.R.DatePattern='.'yyyy-MM-dd`
`#`
`# Edit the next line to point to your logs directory.`
`# The last part of the name is the log file name.`
`#`
`log4j.appender.R.File=/usr/local/tomcat/logs/tomcat.log`
`log4j.appender.R.layout=org.apache.log4j.PatternLayout`
`#`
`# Print the date in ISO 8601 format`
`#`
`log4j.appender.R.layout.ConversionPattern=%d [%t] %-5p %c - %m%n`

`#`
`# Application logging options`
`#`
`#log4j.logger.org.apache=DEBUG`
`#log4j.logger.org.apache=INFO`
`#log4j.logger.org.apache.struts=DEBUG`
`#log4j.logger.org.apache.struts=INFO`

## Vulnerable patterns examples for Logging

### .NET

The following are issues one may look out for or question the
development/deployment team. Logging and auditing are detective methods
of fraud prevention. They are much overlooked in the industry, which
enables attackers to continue to attack/commit fraud without being
detected.

They cover Windows and .NET issues.

**Check that:**

1.  Windows native log puts a timestamp on all log entries.
2.  GMT is set as the default time.
3.  The Windows operating system can be configured to use network
    timeservers.
4.  By default the event log will show the name of the computer that
    generated the event and the application in the source field of the
    viewer. Additional information such as request identifier, username,
    and destination should be included in the body of the error event.
5.  No sensitive or business critical information is sent to the
    application logs.
6.  Application logs are not located in the web root directory.
7.  Log policy allows different levels of log severity.

### Writing to the Event Log

In the course of reviewing .NET code ensure that calls the EventLog
object do not provide any confidential information.

`EventLog.WriteEntry( "`<password>`",EventLogEntryType.Information);`

### Classic ASP

You can add events to Web server Log or Windows log, for Web Server Log
use.

`Response.AppendToLog("Error in Processing")`

This is the common way of adding entries to the Windows event log.

`Const EVENT_SUCCESS = 0`
`Set objShell = Wscript.CreateObject("Wscript.Shell")`
`objShell.LogEvent EVENT_SUCCESS, _`
`  "Payroll application successfully installed."`

Notice all the previous bullets for ASP.NET are pretty much applicable
for classic ASP as well.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
.NET Project](Category:OWASP_.NET_Project "wikilink")