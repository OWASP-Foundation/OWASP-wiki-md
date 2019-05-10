[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

### In Brief

Logging is the recording of information into storage that details who
performed what and when they did it (like an audit trail) This can also
cover debug messages implemented during development as well as any
messages reflecting problems or states within the application. It should
be an audit of everything that the business deems important to track
about the applications use. Logging provides a detective method to
ensure that the other security mechanisms being used are performing
correctly.
Logging should be at least done at the following events:

  - Authentication: Successful & unsuccessful attempts.
  - Authorization requests.
  - Data manipulation: Any (CUD) Create, Update, Delete actions
    performed on the application.
  - Session activity: Termination/Logout events.

A good logging strategy should include the recording of any errors that
occur in the application.
The application should have the ability to detect and record possible
malicious use such as events that cause unexpected errors or defy the
state model of the application. Users who attempt to get access to data
that they shouldn’t (authorization), and incoming data that does not
meet validation rules or has been tampered with. In general any error
condition which could not occur without an attempt by the user to
circumvent the application logic.
Logging should give us the information required to form a proper audit
trail of a users actions.
Leading from this the date/time the actions were performed would be
useful. Logging functionality should not log a any personal or sensitive
data pertaining to the user of function at hand that is being recorded;
An example of this if your application is accepting HTTP GET the payload
is in the URL and the GET shall be loged. This may result in logging
sensitive data.
Logging should follow best practice regarding data validation; maximum
length of information, malicious characters….
We should ensure that logging functionality only log’s messages of a
reasonable length and that this length is enforced.
Common open source logging solutions:

`Log4J:      `<http://logging.apache.org/log4j/docs/index.html>

`Log4net:    `<http://logging.apache.org/log4net/>

`Commons Logging: `<http://jakarta.apache.org/commons/logging/index.html>


In Tomcat(5.5), if no custom logger is defined (log4J) then everything
is logged via Commons Logging and ultimately ends up in catalina.out.
catalina.out grows endlessly and does not recycle/rollover. Log4J
provides “Rollover” functionality, which limits the size of the log.
Log4J also gives the option to specify “appenders” which can redirect
the log data to other destinations such as a port, syslog or even a
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

### Vulnerable patterns examples for Logging

#### .NET

The following are issues one may look out for or question the
development team /deployment team. Logging and auditing are detective
methods of fraud prevention. Much overlooked in the industry, which
enables attackers to continue to attack/commit fraud without being
detected.

They cover Windows and .NET issues: **Check that:**

1.  Windows native log puts a timestamp on all log entries.
2.  GMT is set as the default time.
3.  The Windows operating system can be configured to use network
    timeservers.
4.  By default the event log will show: Name of the computer that
    generated the event; The application in the source field of the
    viewer. Additional information such as request
    identifier,username,and destination should be included in the body
    of the error event.
5.  No sensitive or business critical information is sent to the
    application logs.
6.  Application logs are not located in the web root directory.
7.  Log policy allows different levels of log severity.

##### Writing to the Event Log

In the course of reviewing .NET code ensure that calls the EventLog
object do not provide any confidential information.

`EventLog.WriteEntry( "`<password>`",EventLogEntryType.Information);`

#### JAVA

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")