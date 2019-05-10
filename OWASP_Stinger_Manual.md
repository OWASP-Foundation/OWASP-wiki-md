# Overview

The purpose of the OWASP Stinger manual is to provide users a
comprehensive guide to developing upon and deploying the OWASP J2EE
Stinger filter. If you have any comments or suggestions concerning the
Stinger manual, please to not hesitate to email me at
<eric.sheridan@owasp.org>.

# Development

# Deployment

## Fetch the Latest Files

The latest Stinger release can be downloaded
[here](http://www.owasp.org/index.php/OWASP_Stinger_Version_2). The user
implementing Stinger should download the jar file into a directory
accessible by the Java container. For example, deploying Stinger in
Tomcat would require downloading the files in the WEB-INF/lib/
directory.

## Configure Deployment Descriptor

There are two major pieces of information necessary to deploy Stinger in
your J2EE environment. First, the Java container must be told to
implement the Stinger J2EE filter. This is specified in the web.xml file
via the following:

<filter>
`   `<filter-name>`StingerFilter`</filter-name>
`   `<filter-class>`org.owasp.stinger.StingerFilter`</filter-class>
`   `<init-param>
`       `<param-name>`config`</param-name>
`       `<param-value>`stinger.xml`</param-value>
`   `</init-param>
`   `<init-param>
`       `<param-name>`error-page`</param-name>
`       `<param-value>`fatal-error.html`</param-value>
`   `</init-param>
`   `<init-param>
`       `<param-name>`reload`</param-name>
`       `<param-value>`false`</param-value>
`   `</init-param>
</filter>

Stinger 2.x accepts three filter parameters: *config*, *error-page*, and
*reload*. The *config* parameter tells the Stinger filter the location
of the SVDL file. The *error-page* parameter is actually the result of a
new feature in Stinger 2.x. All exceptions that are thrown from the web
application are now caught in Stinger. This prevents sending exceptions
to the client and potentially revealing sensitive information (think
database exceptions). Instead of leaking sensitive information, Stinger
simply redirects the client to a specified page upon catching an
exception. The third parameter, *reload*, tells Stinger whether to
dynamically load the SVDL file for each incoming HTTP request. As a rule
of thumb, set *reload* to true in testing environments and false for
production environments.

The second major piece of information dictates which requests should
pass the Stinger J2EE filter. This is specified in the web.xml file via
the following:

<filter-mapping>
`   `<filter-name>`StingerFilter`</filter-name>
`   `<url-pattern>`/*`</url-pattern>
</filter-mapping>

This entry tells the J2EE container that every request handled by the
container should pass through the Stinger filter.

## Configure Your SVDL File

A template SVDL file for the latest Stinger release can be found here:
[Stinger_template.xml.zip‎‎](Media:Stinger_template.xml.zip‎ "wikilink").
The SVDL file is broken down into three sections.

:\*The Regular Expression Section

:\*The Cookie Rule Section

:\*The Parameter Rule Section

### The Regular Expression Section

All regular expressions to be used in Stinger are defined in this
section. Essentially, a regular expression entry is comprised of a name,
a regular expression, and a description. The description element is for
user readability and is not used within Stinger. The regular expressions
equiped with Stinger were taken from the [OWASP RegEx
Repository](http://www.owasp.org/index.php/OWASP_Validation_Regex_Repository).
If you have custom regular expressions and would like to donate them to
the Stinger project, please email me at <eric.sheridan@owasp.org>.

The following is a sample entry in the regular expression section:

<regex>
`   `<name>`JSESSIONID`</name>
`   `<pattern>`^[A-F0-9]{32}$`</pattern>
`   `<description>`JSESSIONID character and length enforcement`</description>
</regex>

### The Cookie Rule Section

This section contains definitions for all of the cookies for which we
are assigning a rule. A cookie rule is comprised of a name, a regular
expression, the URI in which it is created, the URI's which it is
enforced, and the actions taken if the cookie is missing or malformed.
For most web applications, we wish to create and enforce a cookie for a
particular URI. In this case, we have an entry similar to the one found
below. In this case the following rule applies: *if a cookie is missing
from the request sent to the created/enforced URI, then no violation
occurs. However, if a cookies is malformed in the request sent to the
created/enforced URI, then a violation occurs.*

The missing and malformed sections simply specify the severity of the
violation as well as the actions to be executed. There exists three
possible severities: *FATAL*, *CONTINUE*, and *IGNORE*.

:\*If a severity is *FATAL*, then Stinger stops processing the packet
and immediately executes the associated actions.

:\*If a severity is *CONTINUE*, then Stinger appends the violation a
list and continues to process the packet.

:\*If a severity is *IGNORE*, no violation is appended to the list of
violation and Stinger continues its request validation.

Several actions accept parameters which are designated by the
<parameter> tag.

The following is a sample entry in the cookie rule section:

<cookie>
`   `<name>`JSESSIONID`</name>
`   `<regex>`JSESSIONID`</regex>
`   `<created>`/Stinger-2.2.*`</created>
`   `<enforce>`/Stinger-2.2.*`</enforce>
`   `<missing>
`       `<severity>`FATAL`</severity>
`       `<action class="org.owasp.stinger.actions.Log">
`           `<parameter>
`               `<name>`log`</name>
`               `<value>`default.log`</value>
`           `</parameter>
`           `<parameter>
`               `<name>`level`</name>
`               `<value>`SEVERE`</value>
`           `</parameter>
`           `<parameter>
`               `<name>`message`</name>
`               `<value>
`                   The required JSESSIONID cookie is missing`
`               `</value>
`           `</parameter>
`       `</action>
`       `<action class="org.owasp.stinger.actions.Invalidate" />
`       `<action class="org.owasp.stinger.actions.Redirect">
`           `<parameter>
`               `<name>`page`</name>
`               `<value>`error.html`</value>
`           `</parameter>
`       `</action>
`   `</missing>
`   `<malformed>
`       `<severity>`FATAL`</severity>
`       `<action class="org.owasp.stinger.actions.Log">
`           `<parameter>
`               `<name>`log`</name>
`               `<value>`default.log`</value>
`           `</parameter>
`           `<parameter>
`               `<name>`level`</name>
`               `<value>`SEVERE`</value>
`           `</parameter>
`           `<parameter>
`               `<name>`message`</name>
`               `<value>`The JSESSIONID cookie is malformed`</value>
`           `</parameter>
`       `</action>
`       `<action class="org.owasp.stinger.actions.Invalidate" />
`       `<action class="org.owasp.stinger.actions.Redirect">
`           `<parameter>
`               `<name>`page`</name>
`               `<value>`error.html`</value>
`           `</parameter>
`       `</action>
`   `</malformed>
</cookie>

### The Parameter Section

The parameter section describes the parameter rules associated with a
particular URI. A URI and its associated rules constitute a *rule set*.
Every SVDL implementation must contain a default rule set similar to the
following:

<ruleset>
`   `<name>`STINGER_DEFAULT`</name>
`   `<path>`STINGER_DEFAULT`</path>
`   `<rule>
`       `<name>`STINGER_ALL`</name>
`       `<regex>`safetext`</regex>

`       `<missing>
`           `<severity>`ignore`</severity>
`       `</missing>
`       `<malformed>
`           `<severity>`continue`</severity>
`           `<action class="org.owasp.stinger.actions.Log">
`               `<parameter>
`                   `<name>`log`</name>
`                   `<value>`default.log`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`level`</name>
`                   `<value>`info`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`message`</name>
`                   `<value>
`                       parameter %name with value %encoded_value from %ip has been encoded`
`                   `</value>
`               `</parameter>
`           `</action>
`                       `<action class="org.owasp.stinger.actions.Encode" />
`              `</malformed>
`   `</rule>
</ruleset>

A default Stinger rule set must have the path (the URI) set to
STINGER_DEFAULT and the rule name set to STINGER_ALL. When a request
to a URI without an associated rule set is submitted, the default rule
set is utilized. When a parameter without an associated rule is sent to
the application, then the default rules are utilized.

The following is a sample rule set entry for a fictitious web
application:

<ruleset>
`   `<name>`Main`</name>
`   `<path>`/Stinger-2.4.*`</path>

`   `<rule>
`       `<name>`username`</name>
`       `<regex>`safetext`</regex>

`       `<missing>
`           `<severity>`continue`</severity>
`       `</missing>
`       `<malformed>
`           `<severity>`continue`</severity>
`           `<action class="org.owasp.stinger.actions.Log">
`               `<parameter>
`                   `<name>`log`</name>
`                   `<value>`default.log`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`level`</name>
`                   `<value>`info`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`message`</name>
`                   `<value>
`                       The username parameter from %ip is malformed`
`                   `</value>
`               `</parameter>
`           `</action>
`           `<action class="org.owasp.stinger.actions.Encode" />
`       `</malformed>
`   `</rule>
`   `<rule>
`       `<name>`hidden1`</name>
`       `<regex>`safetext`</regex>

`       `<missing>
`           `<severity>`fatal`</severity>
`           `<action class="org.owasp.stinger.actions.Log">
`               `<parameter>
`                   `<name>`log`</name>
`                   `<value>`default.log`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`level`</name>
`                   `<value>`info`</value>
`               `</parameter>
`               `<parameter>
`                   `<name>`message`</name>
`                   `<value>`The hidden1 parameter is missing`</value>
`               `</parameter>
`           `</action>
`           `<action class="org.owasp.stinger.actions.Invalidate" />
`           `<action class="org.owasp.stinger.actions.Redirect">
`               `<parameter>
`                   `<name>`page`</name>
`                   `<value>`error.html`</value>
`               `</parameter>
`           `</action>
`       `</missing>
`       `<malformed>
`           `<severity>`fatal`</severity>
`           `<action class="org.owasp.stinger.actions.Log">
`               `<parameter>
`                   `<name>`log`</name>
`                   `<value>`default.log`</value>
`                   `</parameter>
`               `<parameter>
`                   `<name>`level`</name>
`                   `<value>`SEVERE`</value>
`               `</parameter>
`                               `<parameter>
`                       `<name>`message`</name>
`                   `<value>
`                       hidden1 parameter from %ip is malformed`
`                   `</value>
`                               `</parameter>
`           `</action>
`           `<action class="org.owasp.stinger.actions.Invalidate" />
`           `<action class="org.owasp.stinger.actions.Redirect">
`                               `<parameter>
`                   `<name>`page`</name>
`                   `<value>`error.html`</value>
`               `</parameter>
`           `</action>
`       `</malformed>
`   `</rule>
</ruleset>

Although this entry is quite large, there are only a few new entries
which must be noted. As we see, this rule set utilizes a regular
expression which is intended to cover the following URIs:

:\* /Stinger-2.4

:\* /Stinger-2.4/

:\* /Stinger-2.4/index.jsp.

For this rule set, we have specified two rules, each describing a
parameter accepted by the web application. These two parameters,
username and hidden1, have very similar entries to that of the cookie
rules. Each parameter has an associated regular expression, a missing
section, and a malformed section.

### Important SVDL Rules/Guidelines

When creating your own SVDL file, please remember the following
rules/guidelines:

**Defaults:**

1.  Stinger assumes there will always exist a default rule set
2.  Requested URI's without a rule set will use the default rule set
3.  Parameters without an associated rule will use the default rule

**Cookies:**

1.  You must specify a created page for a cookie rule
2.  If a cookie is missing on the created page, then no violation
3.  If a cookie is malformed on the created page, then violation
4.  You must specify at least one enforced uri per cookie rule
5.  You can specify more than one enforced uri per cookie rule

**Rule Sets:**

1.  There must exist at least one path per rule set.
2.  There can exist multiple paths for a single rule set.

**Actions:**

1.  Order actions carefully and appropriately. Ex. You cannot drop a
    packet and then display a message.
2.  Several actions accept parameters. They must be defined

## SVDL Learner Filter

A project is underway to create a J2EE filter which generates an SVDL
file based on captured HTTP traffic. The learner filter will behave
similar to that of the SVDL Generator filter whereby parameters without
an associated rule will be colored red. The learner filter will then
look for a user-submitted value for that parameter and build an
appropriate rule with default *missing* and *malformed* actions. When
the user is finished crawling the site, the J2EE container is shut down
and the Learner filter writes the rules to disk. The learner filter is
considered developmental, yet it is included in the Stinger 2.x
releases.

## Deployment Checklist

  - Download the latest Stinger jar files into the appropriate container
    directory
  - Configure your web.xml file to:

<!-- end list -->

  -
    Load Stinger with the appropriate parameters:
      -
        *config* - the location of the SVDL file under WEB-INF
        *error-page* - the error page displayed if any exception is
        caught
        *reload* - specifies whether the SVDL should be dynamically
        loaded at runtime
    Apply Stinger to a URI Pattern

<!-- end list -->

  - Configure the SVDL for your application

# Actions

Stinger is an action based input validation engine. The user can specify
actions to be taken place upon violations found in an HTTP request. The
following section describes how the actions are implemented as well as
the parameters they accept. One major goal of this section is to
illustrate the simplicity of creating Stinger actions. If you have
created a custom action and are interested in submitting it to the
Stinger project, please email me at <eric.sheridan@owasp.org>.

## AbstractAction

### Description

Developing your own action is relatively straight forward within
Stinger. To implement a custom class, simply extend the *AbstractAction*
class and implement the abstract *doAction* method. For more information
related to building custom actions, please refer to the development
section.

### Source Code

`public abstract class AbstractAction {`
`   `
`   public final static int DROP = -1;`
`   `
`   public final static int CONTINUE = 0;`
`   `
`   public final static int PROCESS = 1;`
`   `
`   private HashMap<String, String> parameters = new HashMap<String, String>();`
`   `
`   public String getParameter(String name) {`
`       return parameters.get(name);`
`   }`
`   `
`   public void setParameter(String name, String value) {`
`       parameters.remove(name);`
`       parameters.put(name, value);`
`   }`
`   `
`   public abstract void init(ServletContext context);`
`   `
`   public abstract int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response);`
`}`

## Drop

### Description

The *Drop* action simply DROP when called. This effectively prevents the
HTTP request from ever reaching the web application.

### Parameters

The *Drop* action currently accepts zero parameters:

### Source Code

`public class Drop extends AbstractAction {`
`   `
`   public void init(ServletContext context) {`
`       `
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       return DROP;`
`   }`
`}`

## Invalidate

### Description

If the session object exists, then it will be invalidated by this
action. This action is considered more severe and should be deployed
only when an obvious attack occurs. For example, cookie values are
rarely tampered with by the client side code (i.e. javascript).
Therefore, we can (safely?) assume that any cookie modification is
considered a deliberate attack.

### Parameters

The *Invalidate* action currently accepts no parameters.

### Source Code

`public class Invalidate extends AbstractAction {`
`   `
`   public void init(ServletContext context) {`
`       `
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       HttpSession session = request.getSession(false);`
`       `
`       if(session != null) { session.invalidate(); }`
`       `
`       Cookie cookie = new Cookie("JSESSIONID", "");`
`       cookie.setMaxAge(0);`
`       response.addCookie(cookie);`
`       `
`       return CONTINUE;`
`   }`
`}`

## Log

### Description

As the name implies, we can log any and every request sent to the web
application. The *Log* action is an essential action and should be
heavily implemented in Stinger deployment.

### Parameters

The *Log* action currently accepts 3 parameters:

**`log`**` - the log file where the message should be recorded`

**`level`**` - the level of the log message (i.e. INFO, SEVERE, etc.)`

**`message`**` - the message which shall be logged. The message parameter itself accepts 3 format parameters.`
`          These include the offender's ip address, the offender's remote port, the parameter/cookie name,`
`          the parameter/cookie value, an entity encoded version of the parameter/cookie value, and the JSESSIONID.`
`          The format strings are %ip, %port, %name, %value, %encoded_value, and %js respectively.`
**`limit`**` - the limit of the log file size`
**`count`**` - the maximum number of log files to use`
**`append`**` - specifies append mode (true/false)`

### Source Code

`public class Log extends AbstractAction {`
`   `
`   private static Logger logger = Logger.getLogger("org.owasp.stinger.actions.Log");`
`   `
`   private static FileHandler handler = null;`
`   `
`   private ServletContext context = null;`
`   `
`   public Log() {`
`       `
`   }`
`   `
`   public void init(ServletContext context) {`
`       this.context = context;         `
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       String log = getParameter("log");`
`       String level = getParameter("level");`
`       String message = getParameter("message");`
`       String limit = getParameter("limit");`
`       String count = getParameter("count");`
`       String append = getParameter("append");`
`       `
`       if(handler == null) {`
`           getHandler(log, limit, count, append);`
`       }`
`       `
`       /** Offender's IP **/`
`       message = message.replace("%ip", request.getRemoteAddr());`
`       `
`       /** Offender's Port **/`
`       message = message.replace("%port", String.valueOf(request.getRemotePort()));`
`       `
`       /** Offending parameter name **/`
`       if(violation.getName() != null) {`
`           message = message.replace("%name", violation.getName());`
`       } else {`
`           message = message.replace("%name", "NULL");`
`       }`
`       `
`       /** Offending parameter value **/`
`       if(violation.getValue() != null) {`
`           message = message.replace("%value", violation.getValue());`
`       } else {`
`           message = message.replace("%value", "NULL");`
`       }`
`       `
`       /** Offending parameter value HTML Encoded **/`
`       if(violation.getValue() != null) {`
`           message = message.replace("%encoded_value", violation.getValue());`
`       } else {`
`           message = message.replace("%encoded_value", "NULL");`
`       }`
`       `
`       /** Offender's JSESSIONID (HASHED) **/`
`       if(request.getCookie("JSESSIONID") != null) {`
`           String s = request.getCookie("JSESSIONID").getValue();`
`           byte[] b = null;`
`           `
`           try {`
`               b = CryptoUtil.doWeakHash(s.getBytes());`
`           } catch (CryptoException e) {`
`               context.log("[Stinger-Filter] caught crypto exception in doAction", e);`
`           }`
`           `
`           message = message.replace("%js", Encoder.BASE64Encode(b));`
`       } else {`
`           message = message.replace("%js", "NULL");`
`       }`
`       `
`       logger.log(new LogRecord(Level.parse(level.toUpperCase()), message));`
`       `
`       return CONTINUE;`
`   }`
`   `
`   private synchronized void getHandler(String log, String limit, String count, String append) {`
`       int l = -1;`
`       int c = -1;`
`       boolean a = false;`
`       `
`       try {`
`           l = Integer.parseInt(limit);`
`       } catch (NumberFormatException e) {`
`           context.log("[Stinger-Filter] getHandler: " + l + " is not a valid int, defaulting to " +    (1024*1024));`
`           `
`           l = 1024*1024;`
`       }`
`       `
`       try {`
`           c = Integer.parseInt(count);`
`       } catch (NumberFormatException e) {`
`           context.log("[Stinger-Filter] getHandler: " + count + " is not a valid int, defaulting to  1");`
`           `
`           c = 1;`
`       }`
`       `
`       a = Boolean.parseBoolean(append);`
`       `
`       getHandler(log, l, c, a);`
`   }`
`   `
`   private synchronized void getHandler(String log, int limit, int count, boolean append) {`
`       `
`       try {`
`           if(handler == null) {`
`               handler = new FileHandler(log, limit, count, append);`
`           }`
`       } catch (IOException ioe) {`
`           context.log("[Stinger-Filter] exception in getHandler", ioe);`
`       }`
`   }`
`}`

## Redirect

### Description

The *Redirect* action redirects a user to a specific page. This action
is often used to send a user to an error message upon finding a
violation.

### Parameters

The *Redirect* action currently accepts 1 parameter:

**`page`**` - the page to redirect the user to`

### Source Code

`public class Redirect extends AbstractAction {`
`   `
`   private ServletContext context = null;`
`   `
`   public void init(ServletContext context) {`
`       this.context = context;`
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       String page = getParameter("page");`
`       `
`       try {`
`           response.sendRedirect(page);`
`       } catch (IOException ioe) {`
`           context.log("[Stinger-Filter] caught exception during redirect", ioe);`
`       }`
`       `
`       return PROCESS;`
`   }`
`}`

## Forward

### Description

The *Forward* action Forwards users request to a specific page for
processing.

### Parameters

The *Forward* action currently accepts 1 parameter:

**`page`**` - the page to forward the user to`

### Source Code

`public class Forward extends AbstractAction {`
`   `
`   private ServletContext context = null;`
`   `
`   public void init(ServletContext context) {`
`       this.context = context;`
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       String page = getParameter("page");`
`       `
`       try {`
`           request.getRequestDispatcher(page).forward(request, response);`
`       } catch (IOException ioe) {`
`           context.log("[Stinger-Filter] exception in doAction", ioe);`
`       } catch (ServletException se) {`
`           context.log("[Stinger-Filter] exception in doAction", se);`
`       }`
`       `
`       return PROCESS;`
`   }`
`}`

## Encode

### Description

The *encode* action will HTML Entity Encode the violating value. This
effectively prevents cross site scripting from the violating input
value.

### Source Code

`public class Encode extends AbstractAction {`
`   `
`   private void entityEncode(MutableHttpRequest request, String name, String value) {`
`       String result = null;`
`       `
`       if(value != null) {`
`           result = Encoder.HTMLEntityEncode(value);`
`           `
`           request.addParameter(name, result);`
`       }`
`   }`
`   `
`   public void init(ServletContext context) {`
`       `
`   }`
`   `
`   public int doAction(Violation violation, MutableHttpRequest request, HttpServletResponse response) {`
`       String name = null;`
`       String value = null;`
`       `
`       name = violation.getName();`
`       value = request.getParameter(name);`
`       `
`       entityEncode(request, name, value);`
`       `
`       return CONTINUE;`
`   }`
`}`

# Example SVDL Configuration Files

The following are example SVDL configuration files. With the
introduction of the global rules concept, configuring Stinger becomes
significantly less cumbersome for even the most complex apps.

## Template SVDL File

This configuration should be used as a template for creating your own
SVDL files. It contains a basic regular expression section, a basic
cookie section, and no parameter rules.

Download this template SVDL file:
[Stinger_template.xml.zip‎‎](Media:Stinger_template.xml.zip‎ "wikilink").

## Encode all Input

This SVDL configuration encodes all parameters in the HTTP request. By
entity encoding all parameter-based user input, we significantly reduce
the likelihood of certain forms of Cross Site Scripting and SQL
Injection attacks.

Download this sample SVDL file:
[Stinger_encode_all.xml.zip‎](Media:Stinger_encode_all.xml.zip‎ "wikilink").

## Encode all Input and Log All Violations

This SVDL configuration encodes all parameters in the HTTP request and
logs all violations that may occur. As a result, we significantly reduce
the likelihood of certain input validation attacks and we have a logging
mechanism to detect and verifies these attacks.

Download this sample SVDL file:
[Stinger_encode_log_all.xml.zip‎](Media:Stinger_encode_log_all.xml.zip‎ "wikilink").

## Encode all Input for a Particular URI

This SVDL configuration encodes all parameters in the HTTP request that
are sent to a specific set of URI's. If a malformed parameter is sent to
another URI not listed in our rule, then the global rule handles the
packet. Since the global rule does nothing, the malformed data will be
accepted.

Download this sample SVDL file:
[Stinger_encode_specific_uri.xml.zip‎‎](Media:Stinger_encode_specific_uri.xml.zip‎ "wikilink").

# Feedback and Participation

We hope you find Stinger useful. Please contribute back to the project
by sending your comments, questions, and suggestions to the Stinger
mailing list. Thanks\!

To join the OWASP Stinger mailing list or view the archives, please
visit the [subscription
page](http://lists.owasp.org/mailman/listinfo/owasp-stinger).

# Project Sponsors

The Stinger project is sponsored by
[<http://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com).

[Category:OWASP Stinger
Project](Category:OWASP_Stinger_Project "wikilink")