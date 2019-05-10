

## Description

Detecting intrusions requires three elements:

  - the capability to log security-relevant events
  - procedures to ensure the logs are monitored regularly
  - procedures to properly respond to an intrusion once detected

You should log all security relevant information. Perhaps you can detect
a problem by reviewing the logs that you couldn't detect at runtime. But
you must log enough information. In particular, all use of security
mechanisms should be logged, with enough information to help track down
the offender. Additionally, the logging functionality in the application
should also provide a method of managing the logged information. If the
security analyst is unable to parse through the event logs to determine
which events are actionable, then logging events provide little to no
value.

Detecting intrusions is important because otherwise you give the
attacker unlimited time to perfect an attack. If you detect intrusions
perfectly, then an attacker will only get one attempt before he is
detected and prevented from launching more attacks. Remember, if you
receive a request that a legitimate user could not have generated - it
is an attack and you should respond appropriately. Logging provides a
forensic function for your application/site. If it is brought down or
hacked, you can trace the culprit and check what went wrong. If the user
uses an anonymizing proxy, having good logs will still help as "what
happened" is logged and the exploit can be fixed more easily.

Don't rely on other technologies to detect intrusions. Your code is the
only component of the system that has enough information to truly detect
attacks. Nothing else will know what parameters are valid, what actions
the user is allowed to select, etc. It must built into the application.

## Examples

### Short example name

  -
    This is a place holder. A better example of logging using the ESAPI
    will go here.

`public void testLogHTTPRequest() throws ValidationException, IOException, AuthenticationException {`
`       System.out.println("logHTTPRequest");`
`       String[] ignore = {"password","ssn","ccn"};`
`       TestHttpServletRequest request = new TestHttpServletRequest();`
`       // FIXME: AAA modify to return the actual string logged (so we can test)`
`       Logger.getLogger("logger", "logger").logHTTPRequest(Logger.SECURITY, request, Arrays.asList(ignore) );`
`       request.addParameter("one","one");`
`       request.addParameter("two","two1");`
`       request.addParameter("two","two2");`
`       request.addParameter("password","jwilliams");`
`       Logger.getLogger("logger", "logger").logHTTPRequest(Logger.SECURITY, request, Arrays.asList(ignore) );`
`   } `

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")

TBD

## Related [Controls](Controls "wikilink")

  - [Controls 1](Controls_1 "wikilink")

TBD

## References

  - [ESAPI Logging and Intrusion
    Detection](ESAPI_Secure_Coding_Guideline#Logging_and_Intrusion_Detection "wikilink")

## Categories

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[need content here](Category:FIXME "wikilink") [need content
here](Category:FIXME "wikilink")
[Category:Principle](Category:Principle "wikilink")