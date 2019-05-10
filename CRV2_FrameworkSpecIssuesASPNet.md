# ASP.NET Security

Securing web applications in ASP.NET requires an integration of
configurations between the .NET framework and IIS. ASP.NET applications
contains a web.config file where you can define many access and
privileges for example, but they alone are not sufficient to protect the
resources of your application. IIS plays a major role in protecting the
website’s assets contained in it too. It is important to understand the
interaction between these components in order to implement proper
security

## Integrating Authentication with IIS

![<File:Iis.png>](Iis.png "File:Iis.png")

Enable and configure the necessary type of authentication based on the
security level required by your application. ASP.NET membership and
ASP.NET login controls implicitly work with forms authentication.

The authentication methods used in IIS 7 are the following:

  - Anonymous
  - ASP.NET impersonation
  - Basic
  - Client certificate mapping,
  - Digest
  - Forms
  - Windows Integrated Security (NTLM or Kerberos)

ASP.NET configuration works only for its resources. Keep in mind that if
you need to configure access to resources of files contained in your
application such as .txt, .gif, .jpg, these are done through the IIS
permissions. For example, even though the ASP.NET resources in a
directory might be forbidden by a Web.config file, users can still
seethe files located in that directory if directory browsing is turned
on and no other restrictions are in place.

## Reference

<http://msdn.microsoft.com/en-us/library/bwd43d0x%28v=vs.85%29.aspx>