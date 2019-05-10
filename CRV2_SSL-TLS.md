**Ensuring SSL with MVC.NET**

The SSL/TLS protocol allows client-server applications to communicate
across a network in a way designed to prevent eavesdropping and
tampering. Any application that needs to send private sensitive
information back and forth between server and client browser needs to
use a protocol that prevents eavesdropping and tampering.

When reviewing MVC .NET is is important to make sure the application
transmitts and recieved over a secure link. It is not recommended to
only have the login pages over SSL and then default to clear. We also
need to protect our session cookie as it is pretty much as useful as a
users credentials.

`   public static void RegisterGlobalFilters(GlobalFilterCollection filters)`
`   {`
`       ......`
`       ......`
`       `**`filters.Add(new``   ``RequireHttpsAttribute());`**`    `
`   }`

In the global.asax file we can review the RegisterGlobalFilters method.
The attribute RequireHttpsAttribute() can be used to make sure the
application runs over SSL/TLS It is recommended that this is enabled for
SSL/TLS sites.