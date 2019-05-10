*This article is for the OWASP Top 10 2004*

## Description

Attackers use buffer overflows to corrupt the execution stack of a web
application. By sending carefully crafted input to a web application, an
attacker can cause the web application to execute arbitrary code –
effectively taking over the machine. Buffer overflows are not easy to
discover and even when one is discovered, it is generally extremely
difficult to exploit. Nevertheless, attackers have managed to identify
buffer overflows in a staggering array of products and components.
Another very similar class of flaws is known as format string attacks.
Buffer overflow flaws can be present in both the web server or
application server products that serve the static and dynamic aspects of
the site, or the web application itself. Buffer overflows found in
widely used server products are likely to become widely known and can
pose a significant risk to users of these products. When web
applications use libraries, such as a graphics library to generate
images, they open themselves to potential buffer overflow attacks.

Buffer overflows can also be found in custom web application code, and
may even be more likely given the lack of scrutiny that web applications
typically go through. Buffer overflow flaws in custom web applications
are less likely to be detected because there will normally be far fewer
hackers trying to find and exploit such flaws in a specific application.
If discovered in a custom application, the ability to exploit the flaw
(other than to crash the application) is significantly reduced by the
fact that the source code and detailed error messages for the
application are normally not available to the hacker.

## Environments Affected

Almost all known web servers, application servers, and web application
environments are susceptible to buffer overflows, the notable exception
being Java and J2EE environments, which are immune to these attacks
(except for overflows in the JVM itself).

## Examples and References

  - OWASP Guide to Building Secure Web Applications and Web Services,
    [Data Validation](Data_Validation "wikilink")

## How to Determine If You Are Vulnerable

For server products and libraries, keep up with the latest bug reports
for the products you are using. For custom application software, all
code that accepts input from users via the HTTP request must be reviewed
to ensure that it can properly handle arbitrarily large input.

## How to Protect Yourself

Keep up with the latest bug reports for your web and application server
products and other products in your Internet infrastructure. Apply the
latest patches to these products. Periodically scan your web site with
one or more of the commonly available scanners that look for buffer
overflow flaws in your server products and your custom web applications.
For your custom application code, you need to review all code that
accepts input from users via the HTTP request and ensure that it
provides appropriate size checking on all such inputs. This should be
done even for environments that are not susceptible to such attacks as
overly large inputs that are uncaught may still cause denial of service
or other operational problems.

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")