[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")

Contact author: [Eoin Keary](mailto:eoinkeary@owasp.org)

  -
    **NOTICE: PLEASE SEE [Reviewing code for XSS
    issues](Reviewing_code_for_XSS_issues "wikilink") as this page may
    not be up to date.**

## XSS attacks

Bad code example:

If the text inputted by the user is reflected back and has not been data
validated the browser shall interpret the inputted script as part of the
mark up and execute the code accordingly. To mitigate this type of
vulnerability we need to perform a number of security tasks in our code:

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
`saveErrors( request, errors ); return (mapping.findForward("error: "+ searchQuery)); `
`} `
`} `
`}`

The red text above shows some common mistakes in the development of this
struts action class. Firstly the data passed in the HttpServletRequest
is placed into a parameter without being data validated.

Focusing on XSS we can see that this action class returns either a
message, ActionMessage in the case of the function being successful. In
the case of an error the code in the Try/Catch block is executed and we
can see here that the data inputted by the user, the data contained in
the HttpServletRequest is returned to the user, unvalidated and exactly
in the format in which the user inputted it.

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

A second example of an XSS vulnerable function. Echoing un-validated
user input back to the browser would give a nice large vulnerability
footprint.

.NET Example (ASP.NET version 1.1 ASP.NET version 2.0):

The server side code for a VB.NET application may have similar
functionality

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

This is a VB.NET example of a Cross Site Script vulnerable piece of
search functionality which echoes back the data inputted by the user. To
mitigate against this we need proper data validation and in the case of
stored XSS attacks we need to encode known bad (as mentioned before).

In the .NET framework there are some in-built security functions which
can assist in data validation and HTML encoding, namley, ASP.NET 1.1
'''request validation '''feature and **HttpUtility.HtmlEncode**.

Microsoft in their wisdom state that you should not rely solely on
ASP.NET request validation and that it should be used in conjunction
with your own data validation, such as regular expressions (mentioned
below).

The request validation feature is disabled on an individual page by
specifying in the page directive

` `**`<%@``   ``Page``   ``validateRequest="false"``   ``%>`**

or by setting **ValidateRequest="false"** on the **@ Pages** element.

or in the **web.config** file:

You can disable request validation by adding a

` <`**`pages`**`> element with `**`validateRequest="false"`**

So when reviewing code make sure the validateRequest directive is
enabled an if not, investigate what method of DV is being used, if any.
Check that ASP.NET Request validation Is enabled in **Machine.config**
Request validation is enabled by ASP.NET by default. You can see the
following default setting in the **Machine.config** file.

` '''<pages validateRequest="true" ... /> '''`

HTML Encoding:

Content to be displayed can easily be encoded using the HtmlEncode
function. This is done by calling:

` `**`Server.HtmlEncode(string)`**

Using the html encoder example for a form:

Text Box: \<%@ Page Language="C\#" ValidateRequest="false" %\>

<script runat="server">

`void searchBtn _Click(object sender, EventArgs e) { `
`Response.Write(HttpUtility.HtmlEncode(inputTxt.Text)); } `

</script>

<html>

<body>

<form id="form1" runat="server">

<div>

<asp:TextBox ID="inputTxt" Runat="server" TextMode="MultiLine" Width="382px" Height="152px">` `
</asp:TextBox>` `
<asp:Button ID="searchBtn" Runat="server" Text="Submit" OnClick=" searchBtn _Click" />` `

</div>

</form>

</body>

</html>

**Stored Cross Site Script:** Using Html encoding to encode potentially
unsafe output.:

Malicious script can be stored/persisted in a database and shall not
execute until retrieved by a user. This can also be the case in bulletin
boards and some early web email clients. This incubated attack can sit
dormant for a long period of time until a user decides to view the page
where the injected script is present. At this point the script shall
execute on the users browser:

The original source of input for the injected script may be from another
vulnerable application, which is common in enterprise architectures.
Therefore the application at hand may have good input data validation
but the data persisted may not have been entered via this application
per se, but via another application.

In this case we cannot be 100% sure the data to be displayed to the user
is 100% safe (as it could of found its way in via another path in the
enterprise). The approach to mitigate against this si to ensure the data
sent to the browser is not going to be interpreted by the browser as
mark-up and should be treated as user data.

We encode known bad to mitigate against this “enemy within”. This in
effect assures the browser interprets any special characters as data and
markup. How is this done? HTML encoding usually means **\<** becomes
**\<**, **\>** becomes **\>**, **&** becomes **&**, and **"** becomes
**"**.

From To

\<      \<

\>      \>

(      (

)      )

1.        \#

&      &

"      "

So for example the text

<script>

would be displayed as

<script>

but on viewing the markup it would be represented by \<script\>

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")