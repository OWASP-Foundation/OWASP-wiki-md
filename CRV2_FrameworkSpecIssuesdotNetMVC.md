# ASP.NET Security in MVC

## Binding issues in MVC .NET

**A.K.A Over-Posting A.K.A Mass assignments**

In MVC framework, mass assignments is a mechanism that allow us to
update our models with data coming in a request in HTTP form fields. As
the data that needs to be updated comes in a collection of form fields,
a user could send a request and modify other fields in the model that
may not be in the form and the developer didn’t intend to be updated.

Depending on the models you create, there might be sensitive data that
you would not like to be modified. The vulnerability is exploited when a
malicious user modifys a model’s fields which are not exposed to the
user via the view and additional model parameters are added by the
malicious user to change hidden model values.

`   public class user`
`   {`
`       public int ID { get; set; }  <- exposed via view  `
`       public string Name { get; set; } <- exposed via view`
`       public bool isAdmin{ get; set; } <-hidden from view`
`   }`

Corresponding view (HTML)

`   ID: <%= Html.TextBox("ID") %> `
`    Name:  <%= Html.TextBox("Name")  %> `
`                    <-- no isAdmin here!`

The correspondig HTML for this model contain 2 fields: **ID** and
**Name**. If an attacker adds the **isAdmin** parameter to the form and
submitts they can change the model object above. So a malicious attacker
may change **isAdmin=true**

**Recommendations:**

  - \-1 Use a model which does not have values the user should not edit.
  - \-2 Use the bind method and whitelist attributes which can be
    updated.
  - \-3 Use the controller.UpdateModel method to exclude certain
    attribute updates.

## Anti-XSS

Traditional ASP.NET applications do not suffer from XSS attacks,
contrary to MVC ASP.NET applications. When MVC web apps are exposed to
malicious XSS code, they will not throw an error likethe following one:

![<File:Error_asp_validation.jpg>](Error_asp_validation.jpg
"File:Error_asp_validation.jpg")

To avoid this vulnerability, make sure that use use the following code
snippet:

`<%server.HtmlEncode(stringValue)%>`

The HTMLEncode method applies HTML encoding to a specified string. This
is useful as a quick method of encoding form data and other client
request data before using it in your Web application. Encoding data
converts potentially unsafe characters to their HTML-encoded
equivalent.(MSDN,2013)

### Razor Syntax MVC3

An option to for XSS protection is the use of Razor syntax for ASP.NET
MVC3 applications use the following code for this purpose:

`@message`

### MVC4 anti XSS feature

in ASP.NET MVC4 It is possible to override the standard HTML encoder by
using the XSS encoder For this, download the code, compile it and add
the library as a reference to the application.

`In the web.config, add the following line in the <system.web> section:`

<httpRuntime encoderType=
   "Microsoft.Security.Application.AntiXssEncoder, AntiXssLibrary"/>

### Sanitize object before saving to a database

The Anti XSS library contains a Sanitize object that can be called to
clean the HTML before is stored in a database in case the web
application is using a WYSIWYG editor

example:

` using Microsoft.Security.Application;`
` ...`
` ...`
` string wysiwygData = "before `

<script>

alert('bip ')

</script>

after ";

` string cleanData = Sanitizer.GetSafeHtmlFragment(wysiwygData);`

## Protection against SQL injections

The best solution to avoid this OWASP \#1 in the top ten list of
security vulnerabilities is to use Parameterized queries .Equivalent to
this solution, the use of Stored procedures is also a form of
parameterized queries, however the way you implement them could still be
prone to vulnerabilities

### Parameter collections

Parameter collections such as SqlParameterCollection provide type
checking and length validation. If you use a parameters collection,
input is treated as a literal value, and SQL Server does not treat it as
executable code, and therefore the payload can not be injected. Using a
parameters collection lets you enforce type and length checks. Values
outside of the range trigger an exception. Make sure you handle the
exception correctly. Example of the SqlParameterCollection:

`using System.Data; `
`using System.Data.SqlClient; `
`using (SqlConnection conn = new SqlConnection(connectionString)) `
`{ `
` DataSet dataObj = new DataSet(); `
` SqlDataAdapter sqlAdapter = new SqlDataAdapter( "StoredProc", conn); `
` sqlAdapter.SelectCommand.CommandType = CommandType.StoredProcedure; `
` //specify param type `
` sqlAdapter.SelectCommand.Parameters.Add("@usrId", SqlDbType.VarChar, 15); `
` sqlAdapter.SelectCommand.Parameters["@usrId "].Value = UID.Text; // Add data from user `
` sqlAdapter.Fill(dataObj); // populate and execute proc `
`} `

### Stored procedures don’t always protect against SQL injection

Even though Stored procedures are a form of Parametarized queries, they
do not offer total protectioon agains SQL injections. The following code
for example demonstrates this issue:

`CREATE PROCEDURE dbo.RunAnyQuery `
`@parameter NVARCHAR(50) `
`AS `
`EXEC sp_executesql @parameter `
`GO `

The above procedure shall execute any SQL you pass to it because is
using unfiltered content from the end user. The directive sp_executesql
is a system stored procedure in Microsoft® SQL Server™

Lets pass it.

`DROP TABLE ORDERS; `

Guess what happens? So we must be careful of not falling into the “We’re
secure, we are using stored procedures” trap\!

### Use an ORM(Object Relational Mapper)

ORM’s are a real blessing regarding protection against SQL injection. By
default, the use of ORM will automatically send all SQL request as
parameterized queries, however, it’s important to keep in mind that this
form of security can be easily bypassed if the developer uses
unparameterized HQL or Entity SQL queries dynamically with string
concatenations

## Request Validation feature against XSS attacks

The ASP .NET framework contains a validator framework, which has made
input validation easier and less error prone than in the past. This
feature was added in the ASP.NET version 1.1, in addition this feature
is enabled by default. Once a malformed request containing any HTML tags
in send, ASP.NET will simply display an error as shown in the following
figure

The validation solution for .NET also has client and server side
functionality akin to Struts (J2EE). What is a validator? According to
the Microsoft (MSDN) definition it is as follows:

`"A validator is a control that checks one input control for a specific type of error `
`condition and displays a description of that problem." `

The main point to take out of this from a code review perspective is
that one validator does one type of function. If we need to do a number
of different checks on our input we need to use more than one validator.
The .NET solution contains a number of controls out of the box:

  - RequiredFieldValidator – Makes the associated input control a
    required field.

<!-- end list -->

  - CompareValidator – Compares the value entered by the user into an
    input control with the value entered into another input control or a
    constant value.

<!-- end list -->

  - RangeValidator – Checks if the value of an input control is within a
    defined range of values.

<!-- end list -->

  - RegularExpressionValidator – Checks user input against a regular
    expression.

### Disadvantages

Unfortunately, this feature can also create issues when legitimate
requests are sent by users who need to submit data containing certain
kind of characters such as brackets.

Another disadvantage is that this does not avoid any attacks originated
from other application or if stored in the database, neither will offer
any protection when input is injected in HTML attributes.

### Use Microsft's Anti-XSS library

Unfortunately, HtmlEncode or validation feature is not enough to deal
with XSS, especially if the user input needs to be added to JavaScript
code, tag attributes, XML or URL. In this case a good option is the
Anti-XSS libray

## MVC’s CSFR anti-forgery system

This is one handy feature found in .NET which contra rest the \#8 owasp
top 10 security issue.

### Use Anti-forgery Helpers

There are 2 methods which a developer can use to avoid CSFR attacks,
these are Html.AntiForgeryToken() and the filter
\[ValidateAntiForgeryToken\]. To use these features, call the
AntiForgeryToken method from within your form, and add the
ValidateAntiForgeryTokenAttribute to the action method you want to
protect. A combination between the Html.AntiForgeryToken() and
Ajax.ActionLink is a recommended way to go in order to make sure that no
attacker can send a false deletion request

`$.ajaxPrefilter(`
`      function (options, localOptions, jqXHR) {`
`          if (options.type !== "GET") {`
`              var token = GetAntiForgeryToken();`
`              if (token !== null) {`
`                  if (options.data.indexOf("X-Requested-With") === -1) {`
`                      options.data = "X-Requested-With=XMLHttpRequest" + (options.data === "") ? "" : "&" + options.data;`
`                  }`
`                  options.data = options.data + "&" + token.name + '=' + token.value;`
`              }`
`          }`
`      }`
`      );`

#### Limitations

  - Users must accept cookies otherwise the \[ValidateAntiForgeryToken\]
    will deny their form’s posts
  - Works only with POST request
  - Can be bypassed if the application has XSS vulnerabilities since it
    will be possible to read _RequestVerificationToken value

## References

MSDN, 2013 - Server.HTMLEncode Method available at
<http://msdn.microsoft.com/en-us/library/ms525347%28v=vs.90%29.aspx>
(last viewed: 2nd July, 2013)

MSDN, 2013 HtmlHelper.AntiForgeryToken Method available at
<http://msdn.microsoft.com/en-us/library/dd470175%28v=vs.108%29.aspx>
(last viewed: 2nd July, 2013)

MSDN, 2013 Anti-Cross Site Scripting Library available at
<http://msdn.microsoft.com/en-us/security/aa973814.aspx> (last viewed:
2nd July, 2013)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")