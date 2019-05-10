[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__
Contact author: [Eoin Keary](mailto:eoin.keary@owasp.org)

One key area in web application security is the validation of data
inputted from an external source. Many application exploits a derived
from weak input validation on behalf of the application. Weak data
validation gives the attacked the opportunity to make the application
perform some functionality which it is not meant to do.

## Canonicalization of input.

Input can be encoded to a format that can still be interpreted correctly
by the application but may not be an obvious avenue of attack.

The encoding of ASCII to Unicode is another method of bypassing input
validation. Applications rarely test for Unicode exploits and hence
provides the attacker a route of attack.

The issue to remember here is that the application is safe if Unicode
representation or other malformed representation is input. The
application responds correctly and recognises all possible
representations of invalid characters.

Example:

The ASCII:

<script>

*(If we simply block “\<” and “\>” characters the other representations
below shall pass data validation and execute).*

URL encoded: %3C%73%63%72%69%70%74%3E

Unicode Encoded: &\#60&\#115&\#99&\#114&\#105&\#112&\#116&\#62

The OWASP Guide 2.1 delves much more into this subject.

## Data validation strategy

A general rule is to accept only “**Known Good**” characters, i.e. the
characters that are to be expected. If this cannot be done the next
strongest strategy is “**Known bad**”, where we reject all known bad
characters. The issue with this is that today’s known bad list may
expand tomorrow as new technologies are added to the enterprise
infrastructure.

There are a number of models to think about when designing a data
validation strategy, which are listed from the strongest to the weakest
as follows.

1.  **Exact Match** (Constrain)
2.  **Known Good** (Accept)
3.  **Reject Known bad** (Reject)
4.  **Encode Known bad** (Sanitise)

In addition there must be a check for maximum length of any input
received from an external source, such as a downstream service/computer
or a user at a web browser.

**Rejected Data must not be persisted to the data store unless it is
sanitised. This is a common mistake to log erroneous data but that may
be what the attacker wishes your application to do.**

  - **Exact Match**: (preferred method) Only accept values from a finite
    list of known values.

E.g.: A Radio button component on a Web page has 3 settings (A, B, C).
Only one of those three settings must be accepted (A or B or C). Any
other value must be rejected.

  - **Known Good**: If we do not have a finite list of all the possible
    values that can be entered into the system we uses known good
    approach.

E.g.: an email address, we know it shall contain one and only one @. It
may also have one or more full stops “.”. The rest of the information
can be anything from \[a-z\] or \[A-Z\] or \[0-9\] and some other
characters such as “_ “or “–“, so we let these ranges in and define a
maximum length for the address.

  - **Reject Known bad**: We have a list of known bad values we do not
    wish to be entered into the system. This occurs on free form text
    areas and areas where a user may write a note. The weakness of this
    model is that today known bad may not be sufficient for tomorrow.

<!-- end list -->

  - **Encode Known Bad**: This is the weakest approach. This approach
    accepts all input but HTML encodes any characters within a certain
    character range. HTML encoding is done so if the input needs to be
    redisplayed the browser shall not interpret the text as script, but
    the text looks the same as what the user originally typed.

**HTML-encoding and URL-encoding user input when writing back to the
client**. In this case, the assumption is that no input is treated as
HTML and all output is written back in a protected form. This is
sanitisation in action.

## Good Patterns for Data validation

### Data Validation examples

A good example of a pattern for data validation to prevent OS injection
in PHP applications would be as follows:

` $string = preg_replace("/[^a-zA-Z0-9]/", "", $string);`

This code above would replace any non alphanumeric characters with “”.
**preg_grep()** could also be used for a ***True*** or ***False**''
result. This would enable us to let “***only known good**''” characters
into the application.

Using regular expressions is a common method of restricting input
character types. A common mistake in the development of regular
expressions is not escaping characters, which are interpreted as control
characters, or not validating all avenues of input.

Examples of regular expression are as follows:

<u><http://www.regxlib.com/CheatSheet.aspx></u>

` ^[a-zA-Z]$    Alpha characters only, a to z and A to Z (RegEx is case sensitive).`
` ^[0-9]$   Numeric only (0 to 9).`
` [abcde]   Matches any single character specified in set`
` [^abcde]  Matches any single character not specified in set`

### Framework <Example:(Struts> 1.2)

In the J2EE world the struts framework (1.1) contains a utility called
the commons validator. This enables us to do two things.

1.  Enables us to have a central area for data validation.
2.  Provides us with a data validation framework.

What to look for when examining struts is as follows:

The struts-config.xml file must contain the following:

` `<plug-in className="org.apache.struts.validator.ValidatorPlugIn">
`   `<set-property property="pathnames" value="/technology/WEB-INF/
    validator-rules.xml, /WEB-INF/validation.xml"/>
` `</plug-in>

This tells the framework to load the validator plug-in. It also loads
the property files defined by the comma-separated list. By default a
developer would add regular expressions for the defined fields in the
validation.xml file.

Next we look at the form beans for the application. In struts, form
beans are on the server side and encapsulate the information sent to the
application via a HTTP form. We can have concrete form beans (built in
code by developers) or dynamic form beans. Here is a concrete bean
below:

` package com.pcs.necronomicon`
` import org.apache.struts.validator.ValidatorForm;  `
` public class LogonForm extends ValidatorForm {`
`   private String username;`
`   private String password;    `
`   public String getUsername() {`
`     return username;`
`   }    `
`   public void setUsername(String username) {`
`     this.username = username;`
`   }  `
`   public String getPassword() {`
`     return password;`
`   }`
` public void setPassword(String password) {`
`     this.password = password;`
`   }`
` }`

Note the LoginForm extends the ValidatorForm, this is a must as the
parent class (ValidatorForm) has a validate method which is called
automatically and calls the rules defined in validation.xml

Now to be assured that this form bean is being called we look at the
struts-config.xml file: It should have something like the following:

<form-beans>
`  `<form-bean name="logonForm"
             type=" com.pcs.necronomicon.LogonForm"/>
</form-beans>

Next we look at the validation.xml file. It should contain something
similar to the following:

<form-validation>
` `<formset>
`   `

<form name="logonForm">

`     `<field property="'''username'''"
            depends="'''required'''">
`       `<arg0 key="prompt.username"/>
`     `</field>
`   `

</form>

` `</formset>
</form-validation>

Note the same name in the validation.xml, the struts-config.xml, this is
an important relationship and is case sensitive.

The field “username” is also case sensitive and refers to the String
username in the LoginForm class.

The “depends” directive dictates that the parameter is required. If this
is blank the error defined in **Application.properties**. This
configuration file contains error messages among other things. It is
also a good place to look for information leakage issues:

1.  Error messages for Validator framework validations

` errors.required={0} is required.`
` errors.minlength={0} cannot be less than {1} characters.`
` errors.maxlength={0} cannot be greater than {2} characters.`
` errors.invalid={0} is invalid.`
` errors.byte={0} must be a byte.`
` errors.short={0} must be a short.`
` errors.integer={0} must be an integer.`
` errors.long={0} must be a long.0.   `
` errors.float={0} must be a float.`
` errors.double={0} must be a double.`
` errors.date={0} is not a date.`
` errors.range={0} is not in the range {1} through {2}.`
` errors.creditcard={0} is not a valid credit card number.`
` errors.email={0} is an invalid e-mail address.`
` prompt.username = User Name is required.`

The error defined by arg0, prompt.username is displayed as an alert box
by the struts framework to the user. The developer would need to take
this a step further by validating the input via regular expression:

`     `<field property="username"
            depends="required,mask">
`       `<arg0 key="prompt.username"/>
`        `<var>
`           `<var-name>`mask`</var-name>
`           `<var-value>`^[0-9a-zA-Z]*$`</var-value>
`       `</var>
`     `</field>
`    `

</form>

`  `</formset>
` `</form-validation>

Here we have added the Mask directive, this specifies a variable <var>.
and a regular expression. Any input into the username field which has
anything other than A to Z, a to z or 0 to 9 shall cause an error to be
thrown. The most common issue with this type of development is either
the developer forgetting to validate all fields or a complete form. The
other thing to look for is incorrect regular expressions, so learn those
RegEx’s kids\!\!\!

We also need to check if the jsp pages have been linked up to the
validation.xml finctionaltiy. This is done by <html:javascript> custom
tag being included in the JSP as follows:

` `<html:javascript formName="logonForm" dynamicJavascript="true" staticJavascript="true" />

### Framework example:(.NET)

The ASP .NET framework contains a validator framework, which has made
input validation easier and less error prone than in the past. The
validation solution for .NET also has client and server side
functionalty akin to Struts (J2EE). What is a validator? According to
the Miscosoft (MSDN) definition it is as follows:

***"A validator is a control that checks one input control for a
specific type of error condition and displays a description of that
problem."***

The main point to take out of this from a code review perspective is
that one validator does one type of function. If we need to do a number
of different checks on our input we need to use more than one validator.

The .NET solution contains a number of controls out of the box:

  - RequiredFieldValidator – Makes the associated input control a
    required field.
  - CompareValidator – Compares the value entered by the user into an
    input control with the value entered into another input control or a
    constant value.
  - RangeValidator – Checks if the value of an input control is within a
    defined range of values.
  - RegularExpressionValidator – Checks user input against a regular
    expression.

The following is an example web page (.aspx) containing validation:

<html>

<head>

<title>

Validate me baby\!

</title>

</head>

<body>

` `<asp:ValidationSummary runat=server HeaderText="There were errors on the page:" />`  `
` `

<form runat=server>

Please enter your User Id

<tr>

<td>

`         `<asp:RequiredFieldValidator runat=server
              ControlToValidate=Name ErrorMessage="User ID is required.">` *`
`         `</asp:RequiredFieldValidator>
`     `

</td>

<td>

User ID:

</td>

<td>

<input type=text runat=server id=Name>

</td>

` `<asp:RegularExpressionValidator runat=server display=dynamic
              controltovalidate="Name"
              errormessage="ID must be 6-8 letters."
              validationexpression="[a-zA-Z0-9]{6,8}" />`  `
`   `

</tr>

` `<input type=submit runat=server id=SubmitMe value=Submit>
` `

</form>

</body>

</html>

Remember to check to regular expressions so they are sufficient to
protect the application. The “runat” directive means this code is
executed at the server prior to being sent to client. When this is
displayed to a users browser the code is simply HTML.

## Length Checking

Another issue to consider is input length validation. If the input is
limited by length this reduces the size of the script that can be
injected into the web app.

Many web applications use operating system features and external
programs to perform their functions. When a web application passes
information from an HTTP request through as part of an external request,
it must be carefully data validated for content and min/max length.
Without data validation the attacker can inject Meta characters,
malicious commands, or command modifiers, masquerading, as legitimate
information and the web application will blindly pass these on to the
external system for execution.

Checking for minimum and maximum length is of paramount importance, even
if the code base is not vulnerable to buffer overflow attacks.

If a logging mechanism is employed to log all data used in a particular
transaction we need to ensure that the payload received is not so big
that it may affect the logging mechanism. If the log file is sent a very
large payload it may crash or if it is sent a very large payload
repeatedly the hard disk of the app server may fill causing a denial of
service. This type of attack can be used to recycle to log file, hence
removing the audit trail. If string parsing is performed on the payload
received by the application and an extremely large string is sent
repeatedly to the application the CPU cycles used by the application to
parse the payload may cause service degradation or even denial of
service.

## Never Rely on Client-Side Data Validation

*Client-side validation can always be bypassed.* ''Server-side code
should perform its own validation. What if an attacker bypasses your
client, or shuts off your client-side script routines, for example, by
disabling JavaScript? '' *Use client-side validation to help reduce the
number of round trips to the server but do not rely on it for security.*
**Remember: Data validation must be always done on the server side.**
**A code review focuses on server side code. Any client side security
code is not and cannot be considered security.**

Data validation of parameter names:

When data is passed to a method of a web application via HTTP the
payload is passed in a “key-value” pair such as '' UserId =3o1nk395y''
'' password=letMeIn123''

Previously we talked about input validation of the payload (parameter
value) being passed to the application. But we also may need to check
that the parameter name (*UserId*,*password* from above) have not been
tampered with. Invalid parameter names may cause the application to
crash or act in an unexpected way. The best approach is “Exact Match” as
mentioned previously.

## Web services data validation

The recommended input validation technique for web services is to use a
schema. A schema is a “map” of all the allowable values that each
parameter can take for a given web service method. When a SOAP message
is received by the web services handler the schema pertaining to the
method being called is “run over” the message to validate the content of
the soap message. There are two types of web service communication
methods; XML-IN/XML-OUT and REST (Representational State Transfer).
XML-IN/XML-OUT means that the request is in the form of a SOAP message
and the reply is also SOAP. REST web services accept a URI request (Non
XML) but return a XML reply. REST only supports a point-to-point
solution wherein SOAP chain of communication may have multiple nodes
prior to the final destination of the request. Validating REST web
services input it the same as validating a GET request. Validating an
XML request is best done with a schema.

<?xml version="1.0"?>

<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" ns="http://server.test.com" targetNamespace="http://server.test.com" elementFormDefault="qualified" attributeFormDefault="unqualified">
<xsd:complexType name="AddressIn">
<xsd:sequence>
`   `<xsd:element name="addressLine1" type="HundredANumeric" nillable="true"/>
`   `<xsd:element name="addressLine2" type="HundredANumeric" nillable="true"/>
`   `<xsd:element name="county" type="TenANumeric" nillable="false"/>
`   `<xsd:element name="town" type="TenANumeric" nillable="true"/>
`   `<xsd:element name="userId" type="TenANumeric" nillable="false"/>
</xsd:sequence>
</xsd:complexType>
<xsd:simpleType name="HundredANumeric">
`   `**<xsd:restriction base="xsd:string">**
`       `<xsd:minLength value="1"/>
`       `<xsd:maxLength value="100"/>
`       `<xsd:pattern value="[a-zA-Z0-9]"/>
`   `</xsd:restriction>
`   `</xsd:simpleType>
`   `<xsd:simpleType name="TenANumeric">
`       `**<xsd:restriction base="xsd:string">**
`           `<xsd:minLength value="1"/>
`           `<xsd:maxLength value="10"/>
`           `<xsd:pattern value="[a-zA-Z0-9]"/>
`       `</xsd:restriction>
`   `</xsd:simpleType>
</xsd:schema>

Here we have a schema for an object called AddressIn. Each of the
elements have restrictions applied to them and the restrictions (in red)
define what valid characters can be inputted into each of the elements.
What we need to look for is that each of the elements have a restriction
applied to the as opposed to the simple type definition such as
**xsd:string**. This schema also has the <xsd:sequence> tag applied to
enforce the sequence of the data that is to be received.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
Code Review Project](Category:OWASP_Code_Review_Project "wikilink")
[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
Code Review Project](Category:OWASP_Code_Review_Project "wikilink")
[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
Code Review Project](Category:OWASP_Code_Review_Project "wikilink")