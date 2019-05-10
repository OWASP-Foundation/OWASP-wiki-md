''' 4.2 Information Gathering '''

-----

The first phase in security assessment is focused on collecting as much
information as possible about a target application. Information
Gathering is the most critical step of an application security test. The
security test should endeavour to test as much of the code base as
possible. Thus mapping all possible paths through the code to facilitate
thorough testing is paramount.

This task can be carried out in many different ways.

By using public tools (search engines), scanners, sending simple HTTP
requests, or specially crafted requests, it is possible to force the
application to leak information, e.g., disclosing error messages or
revealing the versions and technologies used.

[4.2.5 Application Discovery
(OWASP-IG-005)](Testing_for_Application_Discovery_\(OWASP-IG-005\) "wikilink")
\[rename to "Enumerate applications on webserver"\]
Application discovery is an activity oriented to the identification of
the web applications hosted on a web server/application server.
This analysis is important because often there is not a direct link
connecting the main application backend. Discovery analysis can be
useful to reveal details such as web applications used for
administrative purposes. In addition, it can reveal old versions of
files or artifacts such as undeleted, obsolete scripts, crafted during
the test/development phase or as the result of maintenance.

[4.2.1 Spiders, Robots and Crawlers
(OWASP-IG-001)](Testing:_Spiders,_Robots,_and_Crawlers_\(OWASP-IG-001\) "wikilink")
\[rename to "Review webserver metafiles" \] This phase of the
Information Gathering process consists of browsing and capturing
resources related to the application being tested.

[4.2.x Review webpage comments and
metadata(OWASP-IG-00x)](Testing:_Review_webpage_comments_and_metadata_\(OWASP-IG-00x\) "wikilink")
Review the webpage metadata, HTML, JavaScript comments for sensitive
information and disabled links/scripts.

[4.2.3 Identify application entry points
(OWASP-IG-003)](Testing:_Identify_application_entry_points_\(OWASP-IG-003\) "wikilink")
Enumerating the application and its attack surface is a key precursor
before any attack should commence. This section will help you identify
and map out every area within the application that should be
investigated once your enumeration and mapping phase has been completed.

[4.2.x Identify application exit/handover points
(OWASP-IG-00x)](Testing:_Identify_application_exit/handover_points_\(OWASP-IG-00x\) "wikilink")
Identify the functional exit points of the application and points where
the application hands over to another application that may, or may not,
be within scope of testing (e.g. handover to a payment gateway).

[4.2.x Map paths through the application
(OWASP-IG-00x)](Testing:_Map_paths_through_the_application_\(OWASP-IG-00x\) "wikilink")
Enumerating the application and its attack surface is a key precursor
before any attack should commence. This section will help you identify
and map out every area within the application that should be
investigated once your enumeration and mapping phase has been completed.

[4.2.x Testing Web Server Fingerprint
(OWASP-IG-00x)](Testing_for_Web_Server_Fingerprint_\(OWASP-IG-00x\) "wikilink")
Application fingerprint is the first step of the Information Gathering
process; knowing the version and type of a running web server allows
testers to determine known vulnerabilities and the appropriate exploits
to use during testing.

[4.2.4 Testing Web Application Fingerprint
(OWASP-IG-004)](Testing_for_Web_Application_Fingerprint_\(OWASP-IG-004\) "wikilink")
Application fingerprint is the first step of the Information Gathering
process; knowing the version and type of a running web server allows
testers to determine known vulnerabilities and the appropriate exploits
to use during testing.

[4.2.6 Analysis of Error Codes
(OWASP-IG-006)](Testing_for_Error_Codes_\(OWASP-IG-006\) "wikilink")
During a penetration test, web applications may divulge information that
is not intended to be seen by an end user. Information such as error
codes can inform the tester about technologies and products being used
by the application.
In many cases, error codes can be easily invoked without the need for
specialist skills or tools, due to bad exception handling design and
coding.

[4.2.2 Search Engine Discovery/Reconnaissance
(OWASP-IG-002)](Testing:_Search_engine_discovery/reconnaissance_\(OWASP-IG-002\) "wikilink")
Search engines, such as Google, can be used to discover issues related
to the web application structure or error pages produced by the
application that have been publicly exposed.

Clearly, focusing only on the web application will not be an exhaustive
test. It cannot be as comprehensive as the information possibly gathered
by performing a broader infrastructure analysis.