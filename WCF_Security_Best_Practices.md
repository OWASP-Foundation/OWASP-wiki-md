From [WCF 3.5 Security
Guidelines](http://www.codeplex.com/WCFSecurity/Wiki/View.aspx?title=Guidelines)
(@Codeplex by J.D. Meier , Jason Taylor , Prashant Bansode , Carlos
Farre, Madhu Sundararajan, Steve Gregersen.)

**Design Considerations**

  - Design your service as a wrapper
  - If you are coming from ASMX then use basicHttpBinding to support
    your existing clients
  - If you are coming from DCOM then, use netTcpBinding
  - If your clients are deployed within intranet then choose transport
    security
  - If your clients are deployed over the internet then choose message
    security
  - Know your Authentication options
  - Know your binding options
  - If you need to Interop with non MS clients, use basicHttpBinding or
    wsHttpBinding
  - If your non-MS clients understand WS stack, use wsHttpBinding

**Auditing and Logging**

  - Use WCF auditing to audit your service
  - If non-repudiation is important, consider setting
    SuppressAuditFailure property to false
  - Use message logging to log operations on your service
  - Instrument for user management events
  - Instrument for significant business operations
  - Protect log files from unauthorized access
  - Do not log sensitive information

**Authentication**

  - Know your authentication options
  - Use Windows Authentication when you can
  - If you support non-WCF clients using windows authentication and
    message security, consider using the Kerberos direct option
  - If your users are in AD, but you can’t use windows authentication,
    consider using username authentication
  - If you are using username authentication, use Membership Provider
    instead of custom authentication
  - If your users are in a SQL membership store, use the SQL Membership
    Provider
  - If your users are in a custom store, consider using username
    authentication with a custom validator
  - If your clients have certificates, consider using client certificate
    authentication
  - If your partner applications need to be authenticated when calling
    WCF services, use client certificate authentication.
  - If you are using username authentication, validate user login
    information
  - Do not store passwords directly in the user store
  - Enforce strong passwords
  - Protect access to your credential store
  - If you are using Windows Forms to connect to WCF, do not cache
    credentials

**Authorization**

  - If you store role information in Windows Groups, consider using the
    WCF PrincipalPermissionAttribute class for roles authorization
  - If you use ASP.NET roles, use the ASP.NET Role Provider
  - If you use windows groups for authorization, use ASP.NET Role
    Provider with AspNetWindowsTokenRoleProvider
  - If you store role information in SQL, consider using the SQL Server
    Role Provider for roles authorization
  - If you store role information in ADAM, use the Authorization Store
    Role Provider for roles authorization
  - If you need to authorize access to WCF operations, use declarative
    authorization
  - If you need to perform fine-grained authorization based on business
    logic, use imperative authorization

**Binding**

  - If you need to support clients over the internet, consider using
    wsHttpBinding.
  - If you need to expose your WCF service to legacy clients as an ASMX
    web service, use basicHttpBinding
  - If you need to support remote WCF clients within an intranet,
    consider using netTcpBinding.
  - If you need to support local WCF clients, consider using
    netNamedPipeBinding.
  - If you need to support disconnected queued calls, use
    netMsmqBinding.
  - If you need to support bidirectional communication between WCF
    Client and WCF service, use wsDualHttpBinding.

**Configuration Management**

  - Use Replay detection to protect against message replay attacks
  - If you host your service in a Windows service, expose a metadata
    exchange (mex) binding
  - If you don’t want to expose your WSDL, turn off HttpGetEnabled and
    metadata exchange (mex)
  - Manage bindings and endpoints in config not code
  - Associate names with the service configuration when you create
    service behavior, endpoint behavior, and binding configuration
  - Encrypt configuration sections that contain sensitive data

**Exception Management**

  - Use structured exception handling
  - Do not divulge exception details to clients in production
  - Use a fault contract to return error information to clients
  - Use a global exception handler to catch unhandled exceptions

**Hosting**

  - If you are hosting your service in a Windows Service, use a least
    privileged custom domain account
  - If you are hosting your service in IIS, use a least privileged
    service account
  - Use IIS to host your service unless you need to use a transport that
    IIS does not support

**Impersonation and Delegation**

  - Know the impersonation options
  - If you have to flow the original caller, use constrained delegation
  - Consider LogonUser when you need to impersonate but you don’t have
    trusted delegation
  - Consider S4U when you need a Windows token and you don’t have the
    original caller’s credentials
  - Use programmatic impersonation to impersonate based on business
    logic
  - When impersonating programmatically be sure to revert to original
    context
  - Only impersonate on operations that require it
  - Use OperationBehavior to impersonate declaratively

**Input/Data Validation**

  - If you need to validate parameters, use parameter inspectors
  - If your service has operations that accept message or data
    contracts, use schemas to validate your messages
  - If you need to do schema validation, use message inspectors
  - Validate operation parameters for length, range, format and type
  - Validate parameter input on the server
  - Validate service responses on the client
  - Do not rely on client-side validation
  - Avoid user-supplied file name and path input
  - Do not echo untrusted input

**Proxy Considerations**

  - Publish your metadata over HTTPS to protect your clients from proxy
    spoofing
  - If you turn off mutual authentication, be aware of service spoofing

**Deployment considerations**

  - Do not use temporary certificates in production
  - If you are using a custom domain account in the identity pool for
    your WCF application, create an SPN for Kerberos to authenticate the
    client.
  - If you are using a custom service account and need to use trusted
    for delegation, create an SPN
  - If you are hosting your service in a Windows Service, using a custom
    domain identity, and ASP.NET needs to use constrained trusted for
    delegation when calling the service, create an SPN
  - Use IIS to host your service unless you need to use a transport that
    IIS does not support
  - Use a least privileged account to run your WCF service
  - Protect sensitive data in your configuration files