# Adding two-factor authentication to ASP.NET using Google Authenticator

## Description

If you wish to add two factor authentication to your ASP.NET site you
can use [ASP.NET's Microsoft's Identity
Framework](http://www.asp.net/identity) and [Google's
"Authenticator"](https://en.wikipedia.org/wiki/Google_Authenticator)
app. A pre-prepared [NuGet
Package](https://www.nuget.org/packages/AddTwoFactorToMvc) by [Lachlan
Barclay](http://lachlanbarclay.net) is available which contains all the
code you need.

If you are adding two-factor authentication to an existing site or
codebase, start by creating a brand new project and adding the
already-prepared NuGet package. This will add all of the necessary code,
web pages, references and dependencies. Once you have that working you
can go ahead and add the code to your existing codebase.

### Create your sample application

The first step is to create a new ASP.NET MVC web application, making
sure to set authentication to none. (In this example I am creating a
fictitious "Movie Manager" application". )

![New Project](Auth2.png "New Project")

From this screen you can click “Ok” – and then on the next screen turn
off authentication by clicking “Change Authentication” and selecting “No
Authentication”:

![change authentication](dotnet-2fa-auth3.png "change authentication")

![change authentication 2](dotnet-2fa-auth4.png
"change authentication 2")

You should now have a very basic MVC app:

![basic MVC app](dotnet-2fa-auth5.png "basic MVC app")

## Adding the NuGet package

You can now add the NuGet package “AddTwoFactorToMvc” which will install
all of the code that you need. Note that this package contains no DLL
files, just code.

To install the package you need to open the "Package Manager Console" by
going to Tools -\> NuGet Package Manager -\> Package Manager Console:

![Opening the package manager](nuget-packagemanagerconsole.png
"Opening the package manager")

you can then enter the following command:

`install-package AddTwoFactorToMvc`

![Adding NuGet package](dotnet-2fa-auth6.png "Adding NuGet package")

the following files and directories should have been added to your
solution:

### Files Added by NuGet Package

| File                                       | Description                                                                        |
| ------------------------------------------ | ---------------------------------------------------------------------------------- |
| Content\\authenticator-iphone-sample.png   | Example image showing how to use the authenticator app                             |
| Controllers\\AccountController.cs          | Controller for managing all the account pages like registration, login, logout etc |
| Controllers\\ManageController.cs           | Controller for managing all of the “manage my account” pages                       |
| Scripts\\qrcode.js                         | Javascript library for generating QR codes                                         |
| TwoFactor\\database-scripts\\twofactor.sql | SQL script for creating tables in the DB                                           |
| TwoFactor\\readme.txt                      | Instructions for installing TwoFactor                                              |
| Views\\Account\\\*.cshtml                  | Pages handling registration, login, logout etc                                     |
| Views\\Manage\\\*.cshtml                   | Pages for the user to manage their account                                         |
| Views\\Shared\\_LoginPartial.cshtml       | Partial control used to display Registration/Login links                           |

### Directories Added

| Directory                      | Description                                     |
| ------------------------------ | ----------------------------------------------- |
| TwoFactor\\classes\\auth       | Contains the code for two factor authentication |
| TwoFactor\\classes\\common     | Common code used across multiple pages          |
| TwoFactor\\classes\\models     | ApplicationDb and ApplicationUser models        |
| TwoFactor\\classes\\viewmodels | Viewmodels for Account and Manage pages         |

All of these files should be added to your source control system.

You should also see an installation/configuration page that will tell
you how to get started. There are just three steps needed:

1.  Database Configuration
2.  SMTP Configuration
3.  Adding the Login Bar to your master page

## Database Configuration

The first step will be to create a SQL Server DB that will be used to
store the member’s credentials. You can do this very simply by using the
following script:

`CREATE DATABASE [moviemanager]`
`GO`

you will also need to create a user that your ASP.NET application uses
to connect to the DB as:

`USE [master]`
`GO`
`CREATE LOGIN [moviemanageruser] WITH PASSWORD=N'moviemanagerpassword', `
`   DEFAULT_DATABASE=[moviemanager], CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF`
`GO`
`USE [moviemanager]`
`GO`
`CREATE USER [moviemanageruser] FOR LOGIN [moviemanageruser]`
`GO`
`ALTER ROLE [db_owner] ADD MEMBER [moviemanageruser]`
`GO`

You will need to add a connection string to your web.config:

<configuration>
` ...`
<connectionStrings>
`   `<add name="DefaultConnection"
         connectionString="Server=localhost;database=moviemanager;User Id=moviemanageruser;password=moviemanagerpassword"
         providerName="System.Data.SqlClient" />
</connectionStrings>

Once the tables have been created, we need to add the columns necessary
for two factor authentication by running the following script file:

`TwoFactor\database-scripts\update-existing-db.sql`

### Db Owner?

You may have noticed that we have added the **db_owner** role to the
**moviemanageruser** account. This is a very bad practice when it comes
to security, as it means that if someone can find a way to execute SQL
via a security hole on your website, they will have full access to your
entire DB. They can read your data, update your data, or worse of all,
delete your entire database.

We need to give the user account full access so that the entity
framework can do its thing and create all of the tables necessary. Once
they have been set up, we can lower the permissions level needed. I will
write another post on this soon.

## Configuring SMTP

Whenever a user registers on your site, you need to send them an email
so they can confirm that they own that email address. You’ll need to
enter your SMTP server’s details so that this email can be sent. If you
open this file you can edit the following file:

`TwoFactor\classes\common\SendEmail.cs`

With these contents:

`namespace MovieManager`
`{`
`    public class Emailer`
`    {`
`       const string smtpServerName = "localhost";`
`       const string replyToEmail = "donotreply@yourcompany.com";`

`       public void sendEmail(string email, string subject, string body)`
`       {`
`            using (MailMessage mail = new MailMessage(`
`                replyToEmail, `
`                email, `
`                subject, `
`                body))`
`            { `
`                mail.IsBodyHtml = true;`

`                using (SmtpClient client = new SmtpClient())`
`                {`
`                    client.Port = 25;`
`                    client.DeliveryMethod = SmtpDeliveryMethod.Network;`
`                    client.Host = smtpServerName; `

`                    client.Send(mail);`
`                }`
`            }`
`        }`
`    }`
`} `

For development purposes you can simply comment out the
client.send(mail), as you will be able to approve the registered email
address manually.

## Adding the Login Bar

You will also need to add the “Register / Login / Manage My Account”
links to your site:

![Login Bar](dotnet-2fa-auth7.png "Login Bar")

these have been bundled into a partial view named:

`Views\Shared\LoginPartial.cshtml `

which has been added to your project by the NuGet package. You’ll need
to add a call to @Html.Partial() to render it, which I suggest putting
into your Views\\Shared\\_Layout.cshtml page:

<body>

`  ...`
`  @Html.Partial("_LoginPartial")`
`  ...`

</body>

## Testing

You can now go ahead and test your two factor authentication\! Simply
register on your site:

![Registering](dotnet-2fa-auth8.png "Registering")

After you click “Register”, you will need to verify your email. If you
are working on a Debug build, you can just click on the link provided
which will verify your email automatically:

![Registering Ok](dotnet-2fa-auth9.png "Registering Ok")

Your email should now be confirmed:

![Confirming](dotnet-2fa-auth10.png "Confirming")

And you can now login:

![Logging back in](dotnet-2fa-auth11.png "Logging back in")

voila\!

![Login Bar](dotnet-2fa-auth12.png "Login Bar")

Now you need to enable two factor authentication, just like an ordinary
user would. Click on your user account:

![Clicking on username](dotnet-2fa-auth13.png "Clicking on username")

and click “Enable” for google’s authenticator:

![Enabling 2FA on account](dotnet-2fa-auth14.png
"Enabling 2FA on account")

you will now need to scan the QR code using Google’s Authenticator app,
and enter the 6 digits provided:

![Entering validation code](dotnet-2fa-auth15.png
"Entering validation code")

now log out, and log back in again, this time you should see the
following:

![Logging in with 2FA](dotnet-2fa-auth16.png "Logging in with 2FA")

enter the verification code shown on your mobile and you have
successfully logged in\!

## Points To Note

1.  Your database user still has **db_owner** permission. You need to
    lower this.
2.  You need to encourage your users to use a complex password. You can
    add a “password strength meter”, using something like [JQuery
    Password Strength
    Meter](https://github.com/ablanco/jquery.pwstrength.bootstrap), or
    you can add links to KeePass & LastPass.
3.  At no point is any data (password or otherwise) transferred to or
    from google’s servers. The joy of the authenticator app is that you
    are (essentially) storing a password on your mobile, and your
    application knows how to work out if the one-time 30 second code is
    currently valid. There is no need to transmit the password over the
    wire.
4.  Calling it "two factor authentication" is bad. Why? Most users see
    that phrase and go “I don’t know what that is, I’m not interested”.
    Calling it something like [Login
    Approvals](https://www.facebook.com/notes/facebook-engineering/introducing-login-approvals/10150172618258920)
    like facebook have is a much friendlier approach, and you will
    probably see much higher adoption\!
5.  Adding functionality that says “you have recently logged in from a
    new/unknown device, if you don’t recognise it let us know” would be
    a great extra layer of security. A free system like
    [MaxMind](http://dev.maxmind.com/geoip/legacy/geolite) might be
    useful, or a paid system like [IpInfo](http://ipinfo.io) might help.
6.  If you are developing an internal enterprise system, training your
    users on basic security principles is definitely necessary. No
    sharing of passwords, lock your computer when you leave your desk,
    don’t plug in random USB sticks, etc etc.
7.  Protecting yourself from the [top 10 most common security
    vulnerabilities](https://www.owasp.org/index.php/Top_10_2013-Top_10)
    will go a long way to making your app more secure. No point in
    adding 2FA if your site is very easily hacked.

## Other References

[Two factor Auth using SMS and Email with ASP.NET
Identity](http://www.asp.net/identity/overview/features-api/two-factor-authentication-using-sms-and-email-with-aspnet-identity)
[Another take on Google
Authenticator](http://www.jerriepelser.com/blog/using-google-authenticator-asp-net-identity)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")