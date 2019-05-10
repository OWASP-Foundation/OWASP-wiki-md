**Introduction** Placement of security checks is a vital area of review
in an application design. Incorrect placement can render the applied
security controls null and void. It is important to study the
application design and spot the correctness of such checks in the
overall execution flow of the design. Many web application designs are
based on the concept of Model-View-Controller (MVC) that have a central
controller which listens to all incoming request and delegates control
to appropriate form/business processing logic. Ultimately the user is
rendered with a view. In such a layered design, when there are many
entities involved in processing a request, developers often go wrong in
placing the security controls at the right place. Most application
developers feel “view” is the right place to have the security checks
like authentication check etc. Image seven

**What is the flaw?** It thus seems logical that if you restrict the
users at the page/view level they won’t be able to perform any operation
in the application. But what if instead of requesting for a page/view an
unauthorized user tries to request for an internal action like to action
to add/modify any data in the application? It will get processed but the
resultant view will be denied to the user; because the flaw lies in just
having a view based access control in the applications. I am sure you
will agree that a lot of processing for a request is done before the
“view” comes into picture in any design. So the request to process any
action will get processed successfully without authorization. Consider a
MVC based given in the figure below. Observe in the figure that the
authentication check is present only in the view pages. Image eight
Observe that neither the controller servlet (central processing entity)
nor the action classes have any access control checks. So here, if the
user requests for an internal action like add user details, etc. without
authentication it will get processed, but the only difference is that
the user will be shown an error page as resultant view will be
disallowed to the user. Image nine Insecure POST-BACK’s in ASP.NET A
similar flaw is predominantly observed in ASP.NET applications where the
developers tend to mix the code for handling POSTBACK’s and
authentication checks. Usually it is observed that the authentication
check in the ASP.NET pages are not applied for POSTBACKs, as indicated
below. Here, if an attacker tries to access the page without
authentication an error page will be rendered. Instead, if the attacker
tries to send an internal POSTBACK request directly without
authentication it would succeed. A detailed explanation is present here.
Image ten Secure Design Recommendation: It is imperative to place all
validation checks before processing any business logic and in case of
ASP.NET applications independent of the POSTBACKs. Review criteria Check
if the placement of the security checks is correct. The security
controls like authentication check must be place before processing any
request.

**Authorisation in .NET MVC 4**

The usage of filters is recommended when authorisation is being
implemented in MVC 4 .NET MVC 3 introduced a method in global.asax
called RegisterGlobalFilters.The can be used to **DEFAULT DENY** access
to URL's in the application.

`   public static void RegisterGlobalFilters(GlobalFilterCollection filters)`
`   {`
`       filters.Add(new HandleErrorAttribute());`
`       `**`filters.Add(new``
 ``System.Web.Mvc.AuthorizeAttribute());`**
`   }`

Is is recommended when reviewing MVC3/4 .NET to take a look at how
authorisation is being implemented. The line above, **filters.Add(new
System.Web.Mvc.AuthorizeAttribute());** pretty much default denies
access to any request without a valid session. If this is implemented we
may need to provide unauthorised access to certain pages such as a
registration page, public welcome page or a login page. How do we do
this?

**AllowAnonymous** is used to provide access to public pages with no
valid session required. The code may look like this:

`   [AllowAnonymous]`
`   public ActionResult LogMeIn(string returnUrl)`

One must be careful that the pages which have AllowAnonymous enabled are
actually designed for public consumption.