[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

## Objective

To ensure that the application is robust against all forms of input
data, whether obtained from the user, infrastructure, external entities
or database systems.

## Platforms Affected

All.

## Relevant COBIT Topics

DS11 – Manage Data. All sections should be reviewed

## Description

The most common web application security weakness is the failure to
properly validate input from the client or environment. This weakness
leads to almost all of the major vulnerabilities in applications, such
as [Interpreter Injection](Interpreter_Injection "wikilink"),
locale/Unicode attacks, file system attacks and buffer overflows. Data
from the client should never be trusted for the client has every
possibility to tamper with the data.

In many cases, [Encoding](Encoding "wikilink") has the potential to
defuse attacks that rely on lack of input validation. For example, if
you use HTML entity encoding on user input before it is sent to a
browser, it will prevent most
[XSS](Cross-site_Scripting_\(XSS\) "wikilink") attacks. However, simply
preventing attacks is not enough - you must perform [Intrusion
Detection](Intrusion_Detection "wikilink") in your applications.
Otherwise, you are allowing attackers to repeatedly attack your
application until they find a vulnerability that you haven't protected
against. Detecting attempts to find these weaknesses is a critical
protection mechanism.

## Definitions

These definitions are used within this document:

  - **Integrity checks**

Ensure that the data has not been tampered with and is the same as
before

  - **Validation**

Ensure that the data is strongly typed, correct syntax, within length
boundaries, contains only permitted characters, or that numbers are
correctly signed and within range boundaries

  - **Business rules**

Ensure that data is not only validated, but business rule correct. For
example, interest rates fall within permitted boundaries.

Some documentation and references interchangeably use the various
meanings, which is very confusing to all concerned. This confusion
directly causes continuing financial loss to the organization.

## Where to include integrity checks

Integrity checks must be included wherever data passes from a trusted to
a less trusted boundary, such as from the application to the user's
browser in a hidden field, or to a third party payment gateway, such as
a transaction ID used internally upon return.

The type of integrity control (checksum, HMAC, encryption, digital
signature) should be directly related to the risk of the data transiting
the trust boundary.

## Where to include validation

Validation must be performed on every tier. However, validation should
be performed as per the function of the server executing the code. For
example, the web / presentation tier should validate for web related
issues, persistence layers should validate for persistence issues such
as SQL / HQL injection, directory lookups should check for LDAP
injection, and so on.

## Where to include business rule validation

Business rules are known during design, and they influence
implementation. However, there are bad, good and "best" approaches.
Often the best approach is the simplest in terms of code.

### Example - Scenario

  - You are to populate a list with accounts provided by the back-end
    system
  - The user will choose an account, choose a biller, and press next

### Wrong way

The account select option is read directly and provided in a message
back to the backend system without validating the account number if one
of the accounts provided by the backend system.

### Why this is bad

An attacker can change the HTML in any way they choose:

  - The lack of validation requires a round-trip to the backend to
    provide an error message that the front end code could easily have
    eliminated

<!-- end list -->

  - The back end may not be able to cope with the data payload the
    front-end code could have easily eliminated. For example, buffer
    overflows, XML injection, or similar.

### Acceptable Method

The account select option parameter ("payee_id") is read by the code,
and compared to an already-known list.

<code>

    if (account.hasPayee( session.getParameter("payee_id") )) {
        backend.performTransfer( session.getParameter("payee_id") );
    }

</code>

This prevents parameter tampering, but requires the list of possible
payee_id's to be to be calculated beforehand.

### Best Method

The original code emitted indexes \<option value="1" ... \> rather than
account names.

*int payeeLstId = session.getParameter('payeelstid');*

*accountFrom = account.getAcctNumberByIndex(payeeLstId);*

Not only is this easier to render in HTML, it makes validation and
business rule validation trivial. The field cannot be tampered with.

### Conclusion

To provide defense in depth and to prevent attack payloads from trust
boundaries, such as backend hosts, which are probably incapable of
handling arbitrary input data, business rule validation is to be
performed (preferably in workflow or command patterns), even if it is
known that the back end code performs business rule validation.

This is not to say that the entire set of business rules need be applied
- it means that the fundamentals are performed to prevent unnecessary
round trips to the backend and to prevent the backend from receiving
most tampered data.

## Data Validation Strategies

There are four strategies for validating data, and they should be used
in this order:

### Accept known good

This strategy is also known as "whitelist" or "positive" validation. The
idea is that you should check that the data is one of a set of tightly
constrained known good values. Any data that doesn't match should be
rejected. Data should be:

  - Strongly typed at all times
  - Length checked and fields length minimized
  - Range checked if a numeric
  - Unsigned unless required to be signed
  - Syntax or grammar should be checked prior to first use or inspection

If you expect a postcode, validate for a postcode (type, length and
syntax):

<code>

    public String isPostcode(String postcode) {
        return (postcode != null && Pattern.matches("^(((2|8|9)\d{2})|((02|08|09)\d{2})|([1-9]\d{3}))$", postcode)) ? postcode : "";
    }

</code>

Coding guidelines should use some form of visible tainting on input from
the client or untrusted sources, such as third party connectors to make
it obvious that the input is unsafe:

<code>

    String taintPostcode = request.getParameter("postcode");
    ValidationEngine validator = new ValidationEngine();
    boolean isValidPostcode = validator.isPostcode(taintPostcode);

</code>

### Reject known bad

This strategy, also known as "negative" or "blacklist" validation is a
weak alternative to positive validation. Essentially, if you don't
expect to see characters such as %3f or JavaScript or similar, reject
strings containing them. This is a dangerous strategy, because the set
of possible bad data is potentially infinite. Adopting this strategy
means that you will have to maintain the list of "known bad" characters
and patterns forever, and you will by definition have incomplete
protection.

```

public String removeJavascript(String input) {

Pattern p = Pattern.compile("javascript", CASE_INSENSITIVE);

p.matcher(input);

return (!p.matches()) ? input : '';

}
```

It can take upwards of 90 regular expressions (see the CSS Cheat Sheet
in the Development Guide 2.0) to eliminate known malicious software, and
each regex needs to be run over every field. Obviously, this is slow and
not secure. Just rejecting "current known bad" (which is at the time of
writing hundreds of strings and literally millions of combinations) is
insufficient if the input is a string. This strategy is directly akin to
anti-virus pattern updates. Unless the business will allow updating
"bad" regexes on a daily basis and support someone to research new
attacks regularly, this approach will be obviated before long.

### Sanitize

Rather than accept or reject input, another option is to change the user
input into an acceptable format

#### Sanitize with Whitelist

Any characters which are not part of an approved list can be removed,
encoded or replaced.

Here are some examples:

If you expect a phone number, you can strip out all non-digit
characters. Thus, "(555)123-1234", "555.123.1234", and "555\\";DROP
TABLE USER;--123.1234" all convert to 5551231234. Note that you should
proceed to validate the resulting numbers as well. As you see, this is
not only beneficial for security, but it also allows you to accept and
use a wider range of valid user input.

If you want text from a user comment form, it is difficult to decide on
a legitimate set of characters because nearly every character has a
legitimate use. One solution is to replace all non alphanumeric
characters with an encoded version, so "I like your web page", might
emerge from your sanitation routines as "I+like+your+web+page%21". (This
example uses [URL encoding](http://en.wikipedia.org/wiki/Url_encoding).)

You can also go one step further. Say you want to set up a site where
users can upload arbitrary files so they can share them or download them
again from another location. In this case validation is impossible
because there is no valid or invalid content. Because your only concern
is protecting your app from malicious input and you don't need to
actually do anything except accept, store and transmit the file, you can
encode the entire file in, say
[base 64](http://en.wikipedia.org/wiki/Base64).

#### Sanitize with Blacklist

Eliminate or translate characters (such as to HTML entities or to remove
quotes) in an effort to make the input "safe". Like blacklists, this
approach requires maintenance and is usually incomplete. As most fields
have a particular grammar, it is simpler, faster, and more secure to
simply validate a single correct positive test than to try to include
complex and slow sanitization routines for all current and future
attacks.

<code>

    public String quoteApostrophe(String input) {
        if (input != null)
            return input.replaceAll("[\']", "&rsquo;");
        else
            return null;
    }

</code>

### No validation

This is inherently unsafe and strongly discouraged. The business must
sign off each and every example of no validation as the lack of
validation usually leads to direct obviation of application, host and
network security controls.

`account.setAcctId(getParameter('formAcctNo'));`
`...`

`public setAcctId(String acctId) {`
`   cAcctId = acctId;`
`}`

## Prevent parameter tampering

There are many input sources:

  - HTTP headers, such as REMOTE_ADDR, PROXY_VIA or similar

<!-- end list -->

  - Environment variables, such as getenv() or via server properties

<!-- end list -->

  - All GET, POST and Cookie data

This includes supposedly tamper resistant fields such as radio buttons,
drop downs, etc - any client side HTML can be re-written to suit the
attacker

Configuration data (mistakes happen :))

External systems (via any form of input mechanism, such as XML input,
RMI, web services, etc)

All of these data sources supply untrusted input. Data received from
untrusted data sources must be properly checked before first use.

## Hidden fields

Hidden fields are a simple way to avoid storing state on the server.
Their use is particularly prevalent in "wizard-style" multi-page forms.
However, their use exposes the inner workings of your application, and
exposes data to trivial tampering, replay, and validation attacks. In
general, only use hidden fields for page sequence.

If you have to use hidden fields, there are some rules:

  - Secrets, such as passwords, should never be sent in the clear

<!-- end list -->

  - Hidden fields need to have integrity checks and preferably encrypted
    using non-constant initialization vectors (i.e. different users at
    different times have different yet cryptographically strong random
    IVs)

<!-- end list -->

  - Encrypted hidden fields must be robust against replay attacks, which
    means some form of temporal keying

<!-- end list -->

  - Data sent to the user must be validated on the server once the last
    page has been received, even if it has been previously validated on
    the server - this helps reduce the risk from replay attacks.

The preferred integrity control should be at least a HMAC using SHA-256
or preferably digitally signed or encrypted using PGP. IBMJCE supports
SHA-256, but PGP JCE support require the inclusion of the Legion of the
Bouncy Castle (http://www.bouncycastle.org/) JCE classes.

It is simpler to store this data temporarily in the session object.
Using the session object is the safest option as data is never visible
to the user, requires (far) less code, nearly no CPU, disk or I/O
utilization, less memory (particularly on large multi-page forms), and
less network consumption.

In the case of the session object being backed by a database, large
session objects may become too large for the inbuilt handler. In this
case, the recommended strategy is to store the validated data in the
database, but mark the transaction as "incomplete." Each page will
update the incomplete transaction until it is ready for submission. This
minimizes the database load, session size, and activity between the
users whilst remaining tamperproof.

Code containing hidden fields should be rejected during code reviews.

## ASP.NET Viewstate

ASP.NET sends form data back to the client in a hidden “Viewstate”
field. Despite looking forbidding, this “encryption” is simply
plain-text equivalent (base64 encoding) and has no data integrity
without further action on your behalf in ASP.NET 1.0. In ASP.NET 1.1 and
2.0, tamper proofing, called "enableViewStateMAC" is on by default using
a SHA-1 hash.

Any application framework with a similar mechanism might be at fault –
you should investigate your application framework’s support for sending
data back to the user. Preferably it should not round trip.

### How to determine if you are vulnerable

These configurations are set hierarchically in the .NET framework. The
machine.config file contains the global configuration; each web
directory may contain a web.config file further specifying or overriding
configuration; each page may contain @page directives specifying same
configuration or overrides; you must check all three locations:

  - If the enableViewStateMac is not set to “true”, you are at risk if
    your viewstate contains authorization state

<!-- end list -->

  - If the viewStateEncryptionMode is not set to “always”, you are at
    risk if your viewstate contains secrets such as credentials

<!-- end list -->

  - If you share a host with many other customers, you all share the
    same machine key by default in ASP.NET 1.1. In ASP.NET 2.0, it is
    possible to configure unique viewstate keys per application

### How to protect yourself

  - If your application relies on data returning from the viewstate
    without being tampered with, you should turn on viewstate integrity
    checks at the least, and strongly consider:

<!-- end list -->

  - Encrypt viewstate if any of the data is application sensitive

<!-- end list -->

  - Upgrade to the latest version of ASP.NET as soon as practical

<!-- end list -->

  - Move truly sensitive viewstate data to the session variable instead

### Selects, radio buttons, and checkboxes

It is a commonly held belief that the value settings for these items
cannot be easily tampered. This is wrong. In the following example,
actual account numbers are used, which can lead to compromise:

```

<html:radio value="<%=acct.getCardNumber(1).toString( )%>" property="acctNo">

<bean:message key="msg.card.name" arg0="<%=acct.getCardName(1).toString( )%>" />

<html:radio value="<%=acct.getCardNumber(1).toString( )%>" property="acctNo">

<bean:message key="msg.card.name" arg0="<%=acct.getCardName(2).toString( )%>" />
```

This produces (for example):

    <input type="radio" name="acctNo" value="455712341234">Gold Card

    <input type="radio" name="acctNo" value="455712341235">Platinum Card

If the value is retrieved and then used directly in a SQL query, an
interesting form of SQL injection may occur: authorization tampering
leading to information disclosure. As the connection pool connects to
the database using a single user, it may be possible to see other users'
accounts if the SQL looks something like this:

    String acctNo = getParameter('acctNo');

    String sql = "SELECT acctBal FROM accounts WHERE acctNo = '?'";

    PreparedStatement st = conn.prepareStatement(sql);

    st.setString(1, acctNo);

    ResultSet rs = st.executeQuery();

This should be re-written to retrieve the account number via index, and
include the client's unique ID to ensure that other valid account
numbers are exposed:

\<pre String acctNo = acct.getCardNumber(getParameter('acctIndex'));

String sql = "SELECT acctBal FROM accounts WHERE acct_id = '?' AND
acctNo = '?'";

PreparedStatement st = conn.prepareStatement(sql);

st.setString(1, acct.getID());

st.setString(2, acctNo);

ResultSet rs = st.executeQuery();

</pre>

This approach requires rendering input values from 1 to ... x, and
assuming accounts are stored in a Collection which can be iterated using
logic:iterate:

```

<logic:iterate id="loopVar" name="MyForm" property="values">

<html:radio property="acctIndex" idName="loopVar" value="value"/> 

<bean:write name="loopVar" property="name"/><br />

</logic:iterate>
```

The code will emit HTML with the values "1" .. "x" as per the
collection's content.

```

<input type="radio" name="acctIndex" value="1" />Gold Credit Card

<input type="radio" name="acctIndex" value="2" />Platinum Credit Card
```

This approach should be used for any input type that allows a value to
be set: radio buttons, checkboxes, and particularly select / option
lists.

### Per-User Data

In fully normalized databases, the aim is to minimize the amount of
repeated data. However, some data is inferred. For example, users can
see messages that are stored in a messages table. Some messages are
private to the user. However, in a fully normalized database, the list
of message IDs are kept within another table:

    +------------------------+
    |       MESSAGES         |
    +------------------------+
    |  msgid   |   message   |
    +------------------------+

If a user marks a message for deletion, the usual way is to recover the
message ID from the user, and delete that:

`DELETE FROM message WHERE msgid='frmMsgId' `

However, how do you know if the user is eligible to delete that message
ID? Such tables need to be denormalized slightly to include a user ID or
make it easy to perform a single query to delete the message safely. For
example, by adding back an (optional) uid column, the delete is now made
reasonably safe:

`DELETE FROM message WHERE uid='session.myUserID' and msgid='frmMsgId'; `

Where the data is potentially both a private resource and a public
resource (for example, in the secure message service, broadcast messages
are just a special type of private message), additional precautions need
to be taken to prevent users from deleting public resources without
authorization. This can be done using role based checks, as well as
using SQL statements to discriminate by message type:

`DELETE FROM message  `
`WHERE`
`uid='session.myUserID' AND`
`msgid='frmMsgId' AND`
`broadcastFlag = false;`

## URL encoding

Data sent via the URL, which is strongly discouraged, should be URL
encoded and decoded. This reduces the likelihood of cross-site scripting
attacks from working.

In general, do not send data via GET request unless for navigational
purposes.

## HTML encoding

Data sent to the user needs to be safe for the user to view. This can be
done using \<bean:write ...\> and friends. Do not use \<%=var%\> unless
it is used to supply an argument for \<bean:write...\> or similar.

HTML encoding translates a range of characters into their HTML entities.
For example, \> becomes \> This will still display as \> on the user's
browser, but it is a safe alternative.

## Encoded strings

Some strings may be received in encoded form. It is essential to send
the correct locale to the user so that the web server and application
server can provide a single level of canoncalization prior to the first
use.

Do not use getReader() or getInputStream() as these input methods do not
decode encoded strings. If you need to use these constructs, you must
decanoncalize data by hand.

## Data Validation and Interpreter Injection

This section focuses on preventing injection in ColdFusion. Interpreter
Injection involves manipulating application parameters to execute
malicious code on the system. The most prevalent of these is SQL
injection but it also includes other injection techniques, including
LDAP, ORM, User Agent, XML, etc. – see [Interpreter
Injection](Reviewing_Code_for_OS_Injection "wikilink") for greater
details. As a developer you should assume that all input is malicious.
Before processing any input coming from a user, data source, component,
or data service it should be validated for type, length, and/or range.
ColdFusion includes support for Regular Expressions and CFML tags that
can be used to validate input.

**SQL Injection**

[SQL Injection](SQL_Injection "wikilink") involves sending extraneous
SQL queries as variables. ColdFusion provides the <cfqueryparam> and
<cfprocparam> tags for validating database parameters. These tags nests
inside <cfquery> and <cfstoredproc>, respectively. For dynamic SQL
submitted in <cfquery>, use the CFSQLTYPE attribute of the
<cfqueryparam> to validate variables against the expected database
datatype. Similarly, use the CFSQLTYPE attribute of <cfprocparam> to
validate the datatypes of stored procedure parameters passed through
<cfstoredproc>.

You can also strengthen your systems against SQL Injection by disabling
the Allowed SQL operations for individual data sources. See the
**Configuration** section below for more information.

**LDAP Injection**

[LDAP injection](LDAP_injection "wikilink") is an attack used to exploit
web based applications that construct LDAP statements based on user
input. ColdFusion uses the <cfldap> tag to communicate with LDAP
servers. This tag has an ACTION attribute which dictates the query
performed against the LDAP. The valid values for this attribute are:
add, delete, query (default), modify, and modifyDN. <cfldap> calls are
turned into JNDI (Java Naming And Directory Interface) lookups. However,
because <cfldap> wraps the calls, it will throw syntax errors if native
JNDI code is passed to its attributes making LDAP injection more
difficult.

**XML Injection**

Two parsers exist for XML data – SAX and DOM. ColdFusion uses DOM which
reads the entire XML document into the server’s memory. This requires
the administrator to restrict the size of the JVM containing ColdFusion.
ColdFusion is built on Java therefore by default, entity references are
expanded during parsing. To prevent unbounded entity expansion, before a
string is converted to an XML DOM, filter out DOCTYPES elements.

After the DOM has been read, to reduce the risk of XML Injection use the
ColdFusion XML decision functions: isXML(), isXmlAttribute(),
isXmlElement(), isXmlNode(), and isXmlRoot(). The isXML() function
determines if a string is well-formed XML. The other functions determine
whether or not the passed parameter is a valid part of an XML document.
Use the xmlValidate() function to validate external XML documents
against a Document Type Definition (DTD) or XML Schema.

**Event Gateway, IM, and SMS Injection**

ColdFusion MX 7 enables Event Gateways, instant messaging (IM), and SMS
(short message service) for interacting with external systems. Event
Gateways are ColdFusion components that respond asynchronously to
non-HTTP requests – e.g. instant messages, SMS text from wireless
devices, etc. ColdFusion provides Lotus Sametime and XMPP (Extensible
Messaging and Presence Protocol) gateways for instant messaging. It also
provides an event gateway for interacting with SMS text messages.

Injection along these gateways can happen when end users (and/or
systems) send malicious code to execute on the server. These gateways
all utilize ColdFusion Components (CFCs) for processing. Use standard
ColdFusion functions, tags, and validation techniques to protect against
malicious code injection. Sanitize all input strings and do not allow
un-validated code to access backend systems.

**Best Practices**

  - Use the XML functions to validate XML input.

<!-- end list -->

  - Before performing XPath searches and transformations in ColdFusion,
    validate the source before executing.

<!-- end list -->

  - Use ColdFusion validation techniques to sanitize strings passed to
    xmlSearch for performing XPath queries.

<!-- end list -->

  - When performing XML transformations only use a trusted source for
    the XSL stylesheet.

<!-- end list -->

  - Ensure that the memory size of the Java Sandbox containing
    ColdFusion can handle large XML documents without adversely
    affecting server resources.

<!-- end list -->

  - Set the memory value to less than the amount of RAM on the server
    (-Xmx).

<!-- end list -->

  - Remove DOCTYPE elements from the XML string before converting it to
    an XML object.

<!-- end list -->

  - Using scriptProtect can be used to thwart most attempts of
    cross-site scripting. Set scriptProtect to All in the
    Application.cfc.

<!-- end list -->

  - Use <cfparam> or <cfargument> to instantiate variables in
    ColdFusion. Use this tag with the name and type attributes. If the
    value is not of the specified type, ColdFusion returns an error.

<!-- end list -->

  - To handle untyped variables use IsValid() to validate its value
    against any legal object type that ColdFusion supports.

<!-- end list -->

  - Use <cfqueryparam> and <cfprocparam> to valid dynamic SQL variables
    against database datatypes.

<!-- end list -->

  - Use CFLDAP for accessing LDAP servers. Avoid allowing native JNDI
    calls to connect to LDAP.

**Best Practice in Action**

The sample code below shows a database authentication function using
some of the input validation techniques discussed in this section.

    <cffunction name="dblogin" access="private" output="false" returntype="struct">

    <cfargument name="strUserName" required="true" type="string">

    <cfargument name="strPassword" required="true" type="string">

    <cfset var retargs = StructNew()>

    <cfif IsValid("regex", uUserName, "[A-Za-z0-9%]*") AND IsValid("regex", uPassword, "[A-Za-z0-9%]*")>

    <cfquery name="loginQuery" dataSource="#Application.DB#" >

    SELECT hashed_password, salt

    FROM UserTable

    WHERE UserName =

    <cfqueryparam value="#strUserName#" cfsqltype="CF_SQL_VARCHAR" maxlength="25">

    </cfquery>

    <cfif loginQuery.hashed_password EQ Hash(strPassword & loginQuery.salt, "SHA-256" )>

    <cfset retargs.authenticated="YES">

    <cfset Session.UserName = strUserName>

    <!-- Add code to get roles from database -->

    <cfelse>

    <cfset retargs.authenticated="NO">

    </cfif>

    <cfelse>

    <cfset retargs.authenticated="NO">

    </cfif>

    <cfreturn retargs>

    </cffunction>

## Delimiter and special characters

There are many characters that mean something special to various
programs. If you followed the advice only to accept characters that are
considered good, it is very likely that only a few delimiters will catch
you out.

Here are the usual suspects:

  - NULL (zero) %00

<!-- end list -->

  - LF - ANSI chr(10) "\\r"

<!-- end list -->

  - CR - ANSI chr(13) "\\n"

<!-- end list -->

  - CRLF - "\\n\\r"

<!-- end list -->

  - CR - EBCDIC 0x0f

<!-- end list -->

  - Quotes " '

<!-- end list -->

  - Commas, slashes spaces and tabs and other white space - used in CSV,
    tab delimited output, and other specialist formats

<!-- end list -->

  - \<\> - XML and HTML tag markers, redirection characters

<!-- end list -->

  - ; & - Unix and NT file system continuance

<!-- end list -->

  - @ - used for e-mail addresses

<!-- end list -->

  - 0xff

<!-- end list -->

  - ... more

Whenever you code to a particular technology, you should determine which
characters are "special" and prevent them appearing in input, or
properly escaping them.

## Further Reading

  - ASP.NET 2.0 Viewstate

<u><http://channel9.msdn.com/wiki/default.aspx/Channel9.HowToConfigureTheMachineKeyInASPNET2></u>

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Is the CSS Cheat Sheet in the current development guide? I wanted to
link to that and couldn't find it](Category:FIXME "wikilink")
[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Validation](Category:Validation "wikilink")
[Category:Encoding](Category:Encoding "wikilink")