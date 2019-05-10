## Summary

Stack traces are not vulnerabilities by themselves, but they often
reveal information that is interesting to an attacker. Attackers attempt
to generate these stack traces by tampering with the input to the web
application with malformed HTTP requests and other input data.

If the application responds with stack traces that are not managed it
could reveal information useful to attackers. This information could
then be used in further attacks. Providing debugging information as a
result of operations that generate errors is considered a bad practice
due to multiple reasons. For example, it may contain information on
internal workings of the application such as relative paths of the point
where the application is installed or how objects are referenced
internally.

## How to Test

### Black Box testing

There are a variety of techniques that will cause exception messages to
be sent in an HTTP response. Note that in most cases this will be an
HTML page, but exceptions can be sent as part of SOAP or REST responses
too.

Some tests to try include:

  - invalid input (such as input that is not consistent with application
    logic).
  - input that contains non alphanumeric characters or query syntax.
  - empty inputs.
  - inputs that are too long.
  - access to internal pages without authentication.
  - bypassing application flow.

All the above tests could lead to application errors that may contain
stack traces. It is recommended to use a fuzzer in addition to any
manual testing.

Some tools, such as [OWASP
ZAP](OWASP_Zed_Attack_Proxy_Project "wikilink") and Burp proxy will
automatically detect these exceptions in the response stream as you are
doing other penetration and testing work.

### Gray Box Testing

Search the code for the calls that cause an exception to be rendered to
a String or output stream. For example, in Java this might be code in a
JSP that looks like:

    <% e.printStackTrace( new PrintWriter( out ) ) %>

In some cases, the stack trace will be specifically formatted into HTML,
so be careful of accesses to stack trace elements.

Search the configuration to verify error handling configuration and the
use of default error pages. For example, in Java this configuration can
be found in web.xml.

## Tools

\[1\] ZAP Proxy
- https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project 

## References

  - \[1\] [RFC2616](http://www.ietf.org/rfc/rfc2616.txt?number=2616)
    Hypertext Transfer Protocol -- HTTP/1.1