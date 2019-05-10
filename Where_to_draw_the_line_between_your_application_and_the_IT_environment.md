If you are performing an application security verification according to
the [OWASP Application Security Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
verification requirements, you will need to figure out where your
application ends and the IT environment begins.

![Asvs_app_itenv_line.gif](Asvs_app_itenv_line.gif
"Asvs_app_itenv_line.gif") OWASP ASVS is not intended to be used to
perform security assessments of any nature of IT environment components
such as application servers, web servers, and operating systems. That
said, the line between your application and the IT environment is not
quite as straightforward as it might appear.

If your application calls an IT environment component to perform a
security function, either performing a security check (e.g. access
control check) or resulting in a security effect (e.g. audit record
generation), you will need to examine this functionality according to
OWASP ASVS detailed verification requirements. For example, let us say
that an authentication server in the IT environment is being relied on
by your application. If you are performing an ASVS Level 2B or higher
verification, to pass requirement V2.6 (“Verify that all authentication
decisions are logged”), you will need to examine the authentication
server to the extent it can be determined that all authentication
decisions are logged. Examining administrative documentation can provide
insight in these types of situations. Obtaining source code for IT
environment components in these situations is not typically necessary.

Similarly, if no management interfaces were built into your application,
and administrators must use IT environment components to manage your
application’s security functions, you will need to examine this
functionality according to OWASP ASVS detailed verification
requirements. For example, let us say that no management interfaces were
built into your application. If you are performing an ASVS Level 4
verification, to pass requirement V12.4 (“Verify that the configuration
store can be output in a human-readable format to facilitate audit”),
you will need to examine application server, web server, and/or
operating system management interfaces to the extent it can be
determined that your application’s configuration store can be output in
a human-readable format. Examining administrative documentation can
provide insight in these types of situations. Obtaining source code for
IT environment components in these situations is not typically
necessary.

Helpful hints:

  - Use the results of your OWASP ASVS Level 1 security architecture
    assessment as input into figuring out where your application ends
    and the IT environment begins. Please see the ASVS article [How to
    perform a security architecture review at Level
    1](How_to_perform_a_security_architecture_review_at_Level_1 "wikilink").

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")