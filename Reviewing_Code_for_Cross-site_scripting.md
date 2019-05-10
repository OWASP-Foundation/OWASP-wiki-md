## Overview

Cross-site scripting (XSS) attacks occur when an attacker uses a web
application to send malicious code, generally in the form of a browser
side script, to a different end user. Flaws that allow these attacks to
succeed are quite widespread and occur anywhere a web application
reflects user input without validation or encoding.

## Related Security Activities

### Description of Cross-site Scripting Vulnerabilities

See the OWASP article on [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink") Vulnerabilities.

### How to Avoid Cross-site scripting Vulnerabilities

See the [OWASP Development
Guide](:Category:OWASP_Guide_Project "wikilink") article on
[Phishing](Phishing "wikilink").

See the [OWASP Development
Guide](:Category:OWASP_Guide_Project "wikilink") article on [Data
Validation](Data_Validation "wikilink").

### How to Test for Cross-site scripting Vulnerabilities

See the [OWASP Testing
Guide](:Category:OWASP_Testing_Project "wikilink") article on how to
[Test for Cross site
scripting](Testing_for_Cross_site_scripting "wikilink") Vulnerabilities.

## Vulnerable Code example

If the text inputted by the user is reflected back without proper
encoding, the browser will interpret the inputted script as part of the
mark up, and execute the code accordingly.

To mitigate this type of vulnerability we need to perform a number of
security tasks in our code:

1.  Validate data
2.  Encode unsafe output

`import org.apache.struts.action.*; `
`import org.apache.commons.beanutils.BeanUtils; `
`import javax.servlet.http.HttpServletRequest; `
`import javax.servlet.http.HttpServletResponse; `

`public final class InsertEmployeeAction extends Action { `

`public ActionForward execute(ActionMapping mapping, ActionForm form,`
`    HttpServletRequest request, HttpServletResponse response) throws Exception{ `

`// Setting up objects and vairables.`

`Obj1 service = new Obj1(); `
`ObjForm objForm = (ObjForm) form; `
`InfoADT adt = new InfoADT (); `
`BeanUtils.copyProperties(adt, objForm); `

`   String searchQuery = objForm.getqueryString();`
`   String payload = objForm.getPayLoad();`
`try { `
`service.doWork(adt);  / /do something with the data`
`ActionMessages messages = new ActionMessages(); `
`ActionMessage message = new ActionMessage("success", adt.getName() ); `
`messages.add( ActionMessages.GLOBAL_MESSAGE, message ); `
`saveMessages( request, messages ); `
`request.setAttribute("Record", adt); `
`return (mapping.findForward("success"));`
`}`
`catch( DatabaseException de ) `
`{`
`ActionErrors errors = new ActionErrors(); `
`ActionError error = new ActionError("error.employee.databaseException" + “Payload: “+payload);`
`errors.add( ActionErrors.GLOBAL_ERROR, error ); `
`saveErrors( request, errors ); `
`return (mapping.findForward("error: "+ searchQuery)); `
`} `
`} `
`}`

The text above shows some common mistakes in the development of this
struts action class. First, the data passed in the HttpServletRequest is
placed into a parameter without being validated.

Focusing on XSS we can see that this action class returns a message,
ActionMessage, if the function is successful. If an error the code in
the Try/Catch block is executed, the data contained in the
HttpServletRequest is returned to the user, unvalidated and exactly in
the format in which the user inputted it.

`import java.io.*; `
`import javax.servlet.http.*; `
`import javax.servlet.*; `

`public class HelloServlet extends HttpServlet `
`{ `
`public void doGet (HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException `
`{ `

`String input = req.getHeader(“USERINPUT”);`

`PrintWriter out = res.getWriter(); `
`out.println(input);  // echo User input.`
`out.close();   `
`} `
`} `

Following is a second example of an XSS vulnerable function. Echoing
un-validated user input back to the browser provides a large
vulnerability footprint.

### .NET Example (ASP.NET version 1.1 ASP.NET version 2.0)

The server side code for a VB.NET application may have similar
functionality.

`' SearchResult.aspx.vb `
`Imports System `
`Imports System.Web `
`Imports System.Web.UI `
`Imports System.Web.UI.WebControls `

`Public Class SearchPage Inherits System.Web.UI.Page `

`Protected txtInput As TextBox `
`Protected cmdSearch As Button `
`Protected lblResult As Label Protected `

`Sub cmdSearch _Click(Source As Object, _ e As EventArgs) `
`   `
`// Do Search…..`
`   // …………`

`lblResult.Text="You Searched for: " & txtInput.Text `

`// Display Search Results…..`
`// …………`

`End Sub `
`End Class`

This is a VB.NET example of a vulnerable piece of search functionality
which echoes back the data inputted by the user. To mitigate against
this, we need proper data validation and in the case of stored XSS
attacks, we need to encode known bad input (as mentioned before). Note
that this code might not be vulnerable if the developers use a proper
declarative validation (ASPX regexp validator or routine, and
validateRequest not set to False).

### Classic ASP Example

Classic ASP is also XSS prone, just like most Web technologies.

```
 <%
    ...
    Response.Write "<div class='label'>Please confirm your data</div><br />"
    Response.Write "Name: " & Request.Form("UserFullName")
    ...
 %>

```

## Protecting against XSS

In the .NET framework there are some in-built security functions which
can assist in data validation and HTML encoding, namely, ASP.NET 1.1
'''request validation '''feature and **HttpUtility.HtmlEncode**.

Microsoft in their wisdom state that you should not rely solely on
ASP.NET request validation and that it should be used in conjunction
with your own data validation, such as regular expressions (mentioned
below).

The request validation feature is disabled on an individual page by
specifying in the page directive.

` `**`<%@``   ``Page``   ``validateRequest="false"``   ``%>`**

or by setting **ValidateRequest="false"** on the **@ Pages** element.

or in the **web.config** file:

You can disable request validation by adding a

` <`**`pages`**`> element with `**`validateRequest="false"`**

So when reviewing code, make sure the validateRequest directive is
enabled and if not, investigate what method of data validation is being
used, if any. Check that ASP.NET Request validation is enabled in
**Machine.config**. Request validation is enabled by ASP.NET by default.
You can see the following default setting in the **Machine.config**
file.

` '''<pages validateRequest="true" ... /> '''`

**HTML Encoding:**

Content to be displayed can easily be encoded using the HtmlEncode
function. This is done by calling:

` `**`Server.HtmlEncode(string)`**

Using the HTML encoder example for a form:

Text Box: \<%@ Page Language="C\#" ValidateRequest="false" %\>

<script runat="server">

` void searchBtn _Click(object sender, EventArgs e) { `
` Response.Write(HttpUtility.HtmlEncode(inputTxt.Text)); } `
` `

</script>

<html>

<body>

<form id="form1" runat="server">

` `<asp:TextBox ID="inputTxt" Runat="server" TextMode="MultiLine" Width="382px" Height="152px">` `
` `</asp:TextBox>` `
` `<asp:Button ID="searchBtn" Runat="server" Text="Submit" OnClick=" searchBtn _Click" />` `
` `

</form>

</body>

</html>

For Classic ASP pages the encoding function is used pretty much the same
as in ASP.NET

`Response.Write Server.HtmlEncode(inputTxt.Text)`

### Stored Cross Site Script

**Using HTML encoding to encode potentially unsafe output.**

Malicious scripts can be stored/persisted in a database and will not
execute until retrieved by a user. This has been seen in bulletin boards
and some early webmail applications. This incubated attack can sit
dormant for a long period of time until a user decides to view the page
where the injected script is present. At this point the script executes
on the user’s browser.

The original source of input for the injected script may be from another
vulnerable application, which is common in enterprise architectures.
Therefore the application at hand may have good input data validation
but the data persisted may not have been entered via this application
per se, but via another application.

In this case we cannot be 100% sure the data to be displayed to the user
is safe (as it could have found its way in via another path in the
enterprise). The approach to mitigate against this is to ensure that
data sent to the browser with the purpose of being displayed literally
is not going to be interpreted by the browser as mark-up.

We encode known bad to mitigate against this “enemy within”. This, in
effect, assures that the browser interprets any special characters as
data and markup. How is this done? HTML encoding usually means **\<**
becomes **\<**, **\>** becomes **\>**, **&** becomes **&**, and **"**
becomes **"**.

| From | To |
| ---- | -- |
| \<   |    |
| \>   |    |
| (    |    |
| )    |    |
| \#   |    |
| &    |    |
| "    |    |

So, for example, if the application has a string "

<script>

" and it wants a browser to display it as "

<script>

", it can first HTML-encode it to the form "\<script\>" before including
it in the web page that gets sent to the browser.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
.NET Project](Category:OWASP_.NET_Project "wikilink")