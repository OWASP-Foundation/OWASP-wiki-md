## Introduction

Securing resources in ASP.NET applications is a combination of
configuration settings in the Web.config file but also, its important to
remember that the IIS configurations play also a big part on this. It's
an integrated approach which provides a total framework of security. The
following highlights the most important aspects of ASP.NET configuration
settings within the web.config file. For a total overview see chapter
ASP.NET security
(https://www.owasp.org/index.php/CRV2_FrameworkSpecIssuesASPNet)

## Secure Configuration Values

Sensitive Information saved in config files should be encrypted.
Encryption keys stored in the machineKey element for example or
connectionstrings with username and passwords to login to database.

## Lock ASP.NET Configuration settings

You can lock configuration settings in ASP.NET configuration files
(Web.config files) by adding an allowOverride attribute to a location
element

## Configure directories using Location Settings

Through the <location> element you can establish settings for specific
folders and files. The Path attribute is used to specify the file or
subdirectory. This is done in the Web.config file example:

<location path="." >
`   <section1 .../>`
`   <section2 ... />`
` `</location>
` `<location path="Default Web Site" >
`   <section1 … />`
`   <section2 … />`
` `</location
  <location path="Default Web Site/MyApplication/Admin/xyz.html" >
`   <section1 ... />`
`   <section2 ... />`
` `</location>

## Configure exceptions for Error Code handling

Showing and handling the correct error code when a user sends a bad
request or invalid parameters is an important configuration subject.
Logging these errors are also an excellent help when analyzing potential
attacks to the application.

It is possible to configure these errors in the code or in the
Web.Config file

The HttpException method Describes an exception that occurred during the
processing of HTTP requests.For example:

`if (string.IsNullOrEmpty(Request["id"]))`
`    throw new HttpException(400, "Bad request");`

or in the Web.config file:

<configuration>
` <system.web>`
`   `<customErrors mode="On" defaultRedirect="ErrorPage.html"
                 redirectMode="ResponseRewrite">
`     `<error statusCode="400" redirect="BadRequest.html" />
`     `<error statusCode="404" redirect="FileNotFound.html" />
`   `</customErrors>
` </system.web>`
</configuration>

## Input validation

Anything coming from external sources can be consider as input in a web
application. Not only the user inserting data through a web form, but
also data retrieved from a web service or database, also headers sent
from the browsers fall under this concept. A way of defining when input
is safe can be done through outlining a trust boundary.

Defining what is known as trust boundary can help us to visualize all
possible untrusted inputs. One of those are user input.ASP.NET has
different types of validations depending on the level of control to be
applied. By default, web pages code is validated against malicious
users. The following is a list types of validations used (MSDN, 2013):

| Type of validation    | Control to use | Description                |
| --------------------- | -------------- | -------------------------- |
| Required entry        |                | RequiredFieldValidator     |
| Comparison to a value |                | CompareValidator           |
| Range checking        |                | RangeValidator             |
| Pattern matching      |                | RegularExpressionValidator |
| User-defined          |                | CustomValidator            |

## References

MSDN, 2013 "Securing ASP.NET Configurations" available at
<http://msdn.microsoft.com/en-us/library/ms178699%28v=vs.100%29.aspx>
(Last Viewed, 25th July 2013)