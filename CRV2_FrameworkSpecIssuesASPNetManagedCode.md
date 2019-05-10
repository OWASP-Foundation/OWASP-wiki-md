# Code Review Manage Code

.NET Managed code is less vulnerable to common vulnerabilities found in
unmanaged code such as Buffer Overflows and memory corruption however
there could be issues in the code that can affect performance and
security. The following is a summary of the recommended practices to
look for during the code review. Also, it is worth mentioning some tools
that can make the work easier on this part and they can help you
understand and pin point flaws in your code

## Code Access Security

This supports the execution of semi-trusted code, preventing several
forms of security threats. The following is a summary of possible
vulnerabilities due to improper use of Code Access security:

| Vulnerability                           | Implications |
| --------------------------------------- | ------------ |
| Improper use of link demands or asserts |              |
| Code allows untrusted callers           |              |

(MSDN, 2013)

### Declarative security

Use declarative security instead of imperative whenever possible.
Example of declarative syntax(MSDN\[2\], 2013):

`[MyPermission(SecurityAction.Demand, Unrestricted = true)]`
` public class MyClass`
` {`
`  public MyClass()`
`  {`
`     //The constructor is protected by the security call.`
`  }`
`  public void MyMethod()`
`  {`
`     //This method is protected by the security call.`
`  }`
`  public void YourMethod()`
`  {`
`     //This method is protected by the security call.`
`  }`

}

## Unmanaged code

Even though C\# is a strong type language, it is possible to use
unmanaged code calls by using the ‘unsafe’ code. “Check that any class
that uses an unmanaged resource, such as a database connection across
method calls, implements the IDisposable interface. If the semantics of
the object are such that a Close method is more logical than a Dispose
method, provide a Close method in addition to Dispose”.

## Exception handling

Manage code should use exception handling for security purposes among
other reasons. Make sure that you follow these recommendations:

  - Avoid exception handling in loops, use try/catch block if it is
    necessary.
  - Identify code that swallows exceptions
  - Use exceptions handling for unexpected conditions and not just to
    control the flow in the application

## Tools

### FxCop

FxCop is an analysis tool that analyses binary assemblies, not source
code. The tool has a predefined set of rules and it is possible to
configure and extend them. Some of the available rules regarding
security are(CodePlex, 2010):

**`EnableEventValidationShouldBeTrue`**
`Verifies if the EnableEventValidation directive is disabled on a certain page`

**`ValidateRequestShouldBeEnabled`**
`Verifies if the ValidateRequest directive is disabled on a certain page.`

**`ViewStateEncryptionModeShouldBeAlways`**
`Verifies if the ViewStateEncryptionMode directive is not set to Never on a certain page.`

**`EnableViewStateMacShouldBeTrue`**
`Verifies if the EnableViewStateMac directive is not set to false on a certain page.`

**`EnableViewStateShouldBeTrue`**
`Verifies if the EnableViewState directive is not set to false on a certain page.`

**`ViewStateUserKeyShouldBeUsed`**
`Verifies if the Page.ViewStateUserKey is being used in the application to prevent CSRF.`

**`DebugCompilationMustBeDisabled`**
`Verifies that debug compilation is turned off. This eliminates potential performance and   `
`security issues related to debug code enabled and additional extensive error messages being    `
`returned.`

**`CustomErrorPageShouldBeSpecified`**
`Verifies that the CustomErrors section is configured to have a default URL for redirecting  `
`uses in case of error.`

**`FormAuthenticationShouldNotContainFormAuthenticationCredentials`**
`Verifies that no credentials are specified under the form authentication configuration.`

**`EnableCrossAppRedirectsShouldBeTrue`**
`Verifies that system.web.authentication.forms enableCrossAppRedirects is set to true. The    `
`settings indicate if the user should be redirected to another application url after the  `
`authentication process. If the setting is false, the authentication process will not`
`allow redirection to another application or host. This helps prevent an attacker to force the `
`user to  be redirected to another site during the authentication process. This attack is `
`commonly called Open redirect and is used mostly during phishing attacks.`

**`FormAuthenticationProtectionShouldBeAll`**
`Verifies that the protection attribute on the system.web.authentication.forms protection is  `
`set to All which specifies that the application use both data validation and encryption to \ `
`help protect the authentication cookie.`

**`FormAuthenticationRequireSSLShouldBeTrue`**
`Verifies that the requireSSL attribute on the system.web.authentication.forms configuration  `
`element is set to True which forces the authentication cookie to specify the secure attribute. `
`This directs the browser to only provide the cookie over SSL.`

**`FormAuthenticationSlidingExpirationShouldBeFalse`**
`Verifies that system.web.authentication.forms slidingExpiration is set to false when the  site `
`is being served over HTTP. This will force the authentication cookie to have a fixed timeout  `
`value instead of being refreshed by each request. Since the cookie will traverse over clear`
`text network and could potentially be intercepted, having a fixed timeout value on the cookie`
`will limit the amount of time the cookie can be replayed. If the cookie is being sent only`
`over HTTPS, it is less likely to be intercepted and having the slidingExpiration setting to`
`True will cause the timeout to be refreshed after each request which gives a better user  `
`experience.`

**`HttpCookiesHttpOnlyCookiesShouldBeTrue`**
`Verifies that the system.web.httpCookies httpOnlyCookies configuration setting is set to True  `
`which forces all cookies to be sent with the HttpOnly attribute.`

**`HttpCookiesRequireSSLShouldBeTrue`**
`Verifies that the system.web.httpCookies requireSSL configuration is set to True which forces`
`all cookies to be sent with the secure attribute. This indicates the browser to only provide`
`the cookie over SSL.`

**`TraceShouldBeDisabled`**
`Verifies that the system.web.trace enabled setting is set to false which disables tracing. It `
`is recommended to disable tracing on production servers to make sure that an attacker cannot`
`gain information from the trace about your application. Trace information can help an attacker`
`probe and compromise your application.`

**`AnonymousAccessIsEnabled`**
`Looks in the web.config file to see if the authorization section allows anonymous access.`

**`RoleManagerCookieProtectionShouldBeAll`**
`Verifies that the system.web.rolemanager cookieProtection is set to All which enforces the `
`cookie to be both encrypted and validated by the server.`

**`RoleManagerCookieRequireSSLShouldBeTrue`**
`Verifies that the system.web.rolemanager cookieRequireSSL attribute is set to True which`
`forces the role manager cookie to specify the secure attribute. This directs the browser to`
`only provide the cookie over SSL.`

**`RoleManagerCookieSlidingExpirationShouldBeTrue`**
`Verifies that the system.web.rolemanager cookieSlidingExpiration is set to false when the site `
`is being served over HTTP. This will force the authentication cookie to have a fixed timeout`
`value instead of being refreshed by each request. Since the cookie will traverse over clear `
`text network and could potentially be intercepted, having a fixed timeout value on the cookie `
`will limit the amount of time the cookie can be replayed. If the cookie is being sent only`
`over HTTPS, it is less likely to be intercepted and having the slidingExpiration setting to `
`True will cause the timeout to be refreshed after each request which gives a better user `
`experience.`

**`PagesEnableViewStateMacShouldBeTrue`**
`Verifies that the viewstate mac is enabled.`

**`PagesEnableEventValidationMustBeTrue`**
`Verifies that event validation is enabled.`

**`HttpRuntimeEnableHeaderCheckingShouldBeTrue`**
`Verifies that the system.web.httpRuntime enableHeaderChecking attribute is set to true. The `
`setting indicates whether ASP.NET should check the request header for potential injection `
`attacks. If an attack is detected, ASP.NET responds with an error. This forces ASP.NET to `
`apply the ValidateRequest protection to headers sent by the client. If an attack is detected `
`the application throws HttpRequestValidationException.`

**`PagesValidateRequestShouldBeEnabled`**
`Verify that validateRequest is enabled.`

**`PagesViewStateEncryptionModeShouldBeAlways`**
`Verifies that the viewstate encryption mode is not configured to never encrypt.`

**`CustomErrorsModeShouldBeOn`**
`Verifies that the system.web.customErrors mode is set to On or RemoteOnly. This disable `
`detailed error message returned by ASP.NET to remote users.`

**`MarkVerbHandlersWithValidateAntiforgeryToken`**
`Verifies that ValidateAntiforgeryTokenAttribute is used to protect against potential CSRF`
`attacks against ASP.NET MVC applications.`

### OWASP O2 platform(VisualStudio C\# REPL - O2 Platform (v5.1))

The O2 platform represents a new paradigm for how to perform, document
and distribute Web Application security reviews. O2 is designed to
Automate Application Security Knowledge and Workflows and to Allow
non-security experts to access and consume Security Knowledge. We
strongly recommend it to .NET developers since this tool helps you
identify current security issues in the framework.(Cruz, 2013)

O2 Platform is also available as a VisualStudio Extension which you can
download from VisualStudio Gallery (see VisualStudio C\# REPL - O2
Platform) or directly using VisualStudio's Extension Manager:
<http://visualstudiogallery.msdn.microsoft.com/295fa0f6-37d1-49a3-b51d-ea4741905dc2>

# References

MSDN 2013 "Code Access Security" available at
<http://msdn.microsoft.com/en-us/library/33tceax8.aspx> (Last viewed
25th July, 2013)

MSDN\[2\], 2013, "Declarative Security" available at
<http://msdn.microsoft.com/en-us/library/kaacwy28.aspx> (Last viewed
25th July, 2013)

CodePlex, 2010 "Fxcop ASP.NET Security Rules" Available at
<http://fxcopaspnetsecurity.codeplex.com/> (Last viewed 25th July, 2013)

Cruz, D. 2013 OWASP O2 Platform, available at
<https://www.owasp.org/index.php/OWASP_O2_Platform> (Last viewed 25th
July, 2013)