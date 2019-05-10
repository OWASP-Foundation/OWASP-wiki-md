[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

## Introduction

Authorization issues cover a wide array of layers in a web application;
from the functional authorization of a user to gain access to a
particular function of the application is at the application layer to
the Database access authorization and least privilege issues at the
persistence layer. So what to look for when performing a code review?
From an attack perspective the most common issues are a result of
curiosity and also exploitation of vulnerabilities such as SQL
injection. **Example**: A Database account used by an application with
system/admin access upon which the application was vulnerable to SQL
injection would result in a higher degree of impact rather than the same
vulnerable application with a least privilege database account.

## How to locate the potentially vulnerable code

Business logic errors are key areas in which to look for authorization
errors. Areas wherein authorization checks are performed are worth
looking at. Logical conditional cases are areas for examination such as
malformed logic:

`if user.equals("NormalUser"){`
`   grantUser(Normal_Permissions);`
`}else{ //user must be admin/super`
`  grantUser("Super_Persmissions);`
`}`

For classic ASP pages authorization is usually performed using include
files that contains the access control validation and restrictions. So
you usually will look for something like

    <!--#include file="ValidateUser.inc"-->

We have an additional issue in this sentence a Information disclosure as
the inc file might be called directly and disclose application
functionality as ASP code will not be executed given that Inc extension
is not recognized.

## Vulnerable Patterns for Authorization issues

One area of examination is to see if the authorization model simply
relies on not displaying certain functions which the user has not
authorization to use, Security by obscurity in effect. If a crawl can be
performed on the application links may be discovered which are not on
the users GUI. Simple HTTP Get requests can uncover "Hidden" links.
Obviously a map on the server side should be used to see if one is
authorized to perform a task and we should not rely on the GUI "hiding"
buttons and links.

So disabling buttons on the client due to the authorization level of
user shall not prevent the user from executing the action relating to
the button.

`document.form.adminfunction.disabled=true;`

<form action="./doAdminFunction.asp">

By simply saving the page locally and editing the disabled=true to
disabled=false and adding the absolute form action one can proceed to
activate the disabled button.

## HotSpots

**The Database:** The account used by the application to access the
database. Ensure least privilege is in effect.

**ASP.NET:** (web.config)

The <authorization> element controls ASP.NET URL authorization and the
accessibility to gain access to specific folders, pages, and resources
by users/web clients. Make sure that only authenticated users are
authorized to see/visit certain pages.

`<system.web>`
` `<authorization>
`   `<deny users="?"/>`   <-- Anonymous users are denied access. Users must be authenticated.`
` `</authorization>
`</system.web>`

The roleManager Element in ASP.NET 2.0 is used to assist in managing
roles within the framework. It assists the developer as not as much
bespoke code needs to be developed. In web.config to see if it is
enabled check:

`<system.web>`
`..........`
`<roleManager enabled="true`

|false" <providers>...</providers> </roleManager>

`..........`
`</system.web>`

**Apache 1.3**

In Apache 1.3 there is a file called httpd. Access control can be
implemented from here in the form of the *Allow* and *Deny* directives.
*allow from address* is the usage where address is the IP address or
domain name to apply access to. Note this granularity is host level
granularity.

deny from 124.20.0.249 denies access to that IP.

Order ensures that the 'order'of access is observed.

Order Deny,Allow Deny from all Allow from owasp.org

Above, all is denied apart from owasp.org

To move the authorization to the user level in apache we can use the
*Satisfy* directive.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:Access
Control](Category:Access_Control "wikilink")