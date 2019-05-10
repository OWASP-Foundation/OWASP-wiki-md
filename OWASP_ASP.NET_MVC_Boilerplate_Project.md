# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

## ASP.NET MVC Boilerplate Project

The default ASP.NET MVC project template uses insecure defaults and
omits many security features altogether. ASP.NET MVC Boilerplate is a
Visual Studio project template that enables security features by default
and adds liberal comments and links to further resources to help
developers (Who often do not have a lot of knowledge on the subject) get
started. ![New_Project.png](New_Project.png "New_Project.png")

## Description

A professional ASP.NET MVC template for building secure, fast, robust
and adaptable web applications or sites. It provides the minimum amount
of code required on top of the default MVC template provided by
Microsoft to provide security by default.
![Preview_Image.png](Preview_Image.png "Preview_Image.png")

### Better Defaults

The default MVC template provided by Microsoft is not as secure as it
could be. There are various settings (Mostly in the web.config file)
which are insecure by default. For example, it leaks information about
which version of IIS you are using and allows external scripts to access
cookies by default\! ASP.NET MVC Boilerplate makes everything secure by
default.

### TLS and HTTPS

Setting up TLS, so that your site runs over HTTPS is very difficult in
ASP.NET MVC as it requires several steps to do it correctly. ASP.NET MVC
Boilerplate makes this easy with step by step instructions and links.

### HTTP Headers

Several HTTP headers are also used to provide better security using the
[NWebSec](https://nwebsec.codeplex.com/) NuGet packages:

1.  [Content Security Policy
    (CSP)](https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Introducing_Content_Security_Policy).
2.  [Strict-Transport-Security
    (HSTS)](https://developer.mozilla.org/en-US/docs/Web/Security/HTTP_strict_transport_security)
3.  [Public-Key-Pins
    (HPKP)](https://developer.mozilla.org/en-US/docs/Web/Security/Public_Key_Pinning)
4.  [X-Content-Type-Options](http://rehansaeed.com/nwebsec-asp-net-mvc-security-through-http-headers/)
5.  [X-Download-Options](http://rehansaeed.com/nwebsec-asp-net-mvc-security-through-http-headers/)
6.  [X-Frame-Options](http://rehansaeed.com/nwebsec-asp-net-mvc-security-through-http-headers/)

### Subresource Integrity (SRI)

ASP.NET MVC Boilerplate has [Subresource Integrity
(SRI)](http://rehansaeed.com/subresource-integrity-taghelper-using-asp-net-core/)
implemented by default using a custom ASP.NET MVC 6 TagHelper.

### Detailed Comments

ASP.NET MVC Boilerplate provides detailed comments and links to official
documentation explaining all of the security features.

### Security Check-List

ASP.NET MVC Boilerplate provides a check-list of steps the developer
needs to take to secure the site.

### Fingerprint Resistant

ASP.NET MVC Boilerplate attempts to thwart fingerprinting tools by
removing the IIS and .NET version HTTP headers and also changing several
defaults including session and anti-forgery cookie names.

### Dynamic IP Security

ASP.NET MVC Boilerplate enables IIS Dynamic IP Security to limit the
maximum number of concurrent requests to thwart DDOS attacks.

## Licensing

This program is free software: you can redistribute it and/or modify it
under the terms of the [GNU Affero General Public
License 2.0](https://github.com/RehanSaeed/ASP.NET-MVC-Boilerplate/blob/master/LICENSE)
as published by the Free Software Foundation 2015.

## Project Resources

  - [GitHub Project Home
    Page](https://github.com/RehanSaeed/ASP.NET-MVC-Boilerplate) where
    you can view source code, log issues and view the change log.
  - [Visual Studio
    Gallery](https://visualstudiogallery.msdn.microsoft.com/6cf50a48-fc1e-4eaf-9e82-0b2a6705ca7d)
    where you can install the project template, rate/review it.
  - [My RehanSaeed.com](http://rehansaeed.com/asp-net-mvc-boilerplate/)
    blog where I post articles detailing features of the project. The
    project template itself links to many of the articles so that
    developers can get detailed information if they need it.

## Project Leader

[Muhammad Rehan Saeed](http://rehansaeed.com)

## Classifications

![Project_Type_Files_CODE.jpg](Project_Type_Files_CODE.jpg
"Project_Type_Files_CODE.jpg")
![Owasp-incubator-trans-85.png](Owasp-incubator-trans-85.png
"Owasp-incubator-trans-85.png")
![Owasp-builders-small.png](Owasp-builders-small.png
"Owasp-builders-small.png") ![Agplv3-155x51.png](Agplv3-155x51.png
"Agplv3-155x51.png")

## News and Events

Read all of the blog articles about this project
[here](http://rehansaeed.com/asp-net-mvc-boilerplate/).

## Roadmap

As ASP.NET MVC evolves and many of the JavaScript libraries release new
updates, this project template needs constant updates. It is intended
that this project template remain as current as possible. I would like
to add more security features to the site template and add more
documentation and helper comments.

## Getting Involved

All are welcome to get involved. Simply visit the GitHub site and raise
a pull request for your code.

# Minimum Viable Product

A Visual Studio Project Template which you can download
[here](https://visualstudiogallery.msdn.microsoft.com/6cf50a48-fc1e-4eaf-9e82-0b2a6705ca7d)

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")