

## Description

A "positive" security model (also known as "whitelist") is one that
defines what is allowed, and rejects everything else. This should be
contrasted with a "negative" (or "blacklist") security model, which
defines what is disallowed, while implicitly allowing everything else.

The positive security model can be applied to a number of different
application security areas. For example, when performing input
validation, the positive model dictates that you should specify the
characteristics of input that will be allowed, as opposed to trying to
filter out bad input. In the access control area, the positive model is
to deny access to everything, and only allow access to specific
authorized resources or functions. If you've ever had to deal with a
network firewall, then you've probably encountered this application of
the positive model.

The benefit of using a positive model is that new attacks, not
anticipated by the developer, will be prevented. However, the negative
model can be quite tempting when you're trying to prevent an attack on
your site. Ultimately, however, adopting the negative model means that
you'll never be quite sure that you've addressed everything. You'll also
end up with a long list of negative signatures to block that has to be
maintained.

## Examples

### isAuthorized

`if(ESAPI.accessController().isAuthorizedForFunction(ADMIN_FUNCTION)) {`
`  doAdminFunction();`
`}`
`else {`
`  doNormalFunction();`
`}`

  -
    In this example, a validation happens that verifies if the active
    user is allowed to execute ADMIN_FUNCTIONS. If this is the case,
    the requested admin method doAdminFunction() will be executed,
    otherwise the default and non-administrative privileges requiring
    method doNormalFunction() is executed.

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Improper error handling](Improper_error_handling "wikilink")

## Related [Controls](Controls "wikilink")

  - [Authorization](Authorization "wikilink")
  - [Error handling](Error_handling "wikilink")
  - [Web Application Firewall](Web_Application_Firewall "wikilink")

## References

  - [:Category:OWASP Enterprise Security
    API](:Category:OWASP_Enterprise_Security_API "wikilink")

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")