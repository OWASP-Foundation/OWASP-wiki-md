## Brief Summary


Proper scoping as well as gathering pre-engagement information is very
important to properly execute web services testing. Many modern web
services include custom authentication as well as very complex designs
and architectures.
\== Scoping Questions ==
The following scoping questions need to be asked prior to any web
service test. Answers to these questions are typically completed by
developers responsible for the design, coding and architecture of the
web service.

  - What type of web service framework is being used? Examples include
    Windows Communication Foundation (WCF), Apache Axis/Axis2, Zend.

<!-- end list -->

  - What type of web services are they? (ex: SOAP, REST or WCF)

<!-- end list -->

  - What type of data do the web services provide? What is the
    importance of this data from a business perspective?

<!-- end list -->

  - Is BPEL being used?

<!-- end list -->

  - How many web services are there, and how many web methods for each
    service exist?

<!-- end list -->

  - Are you able to provide any developer documentation showing the
    schema of the web service as well as any documentation on APIs if
    they are being used?

<!-- end list -->

  - Can you provide all DISCO/UDDIs if being used specific to any
    directory listing of your web service (if publicly available)?

<!-- end list -->

  - Does the web service use SSL?

<!-- end list -->

  - Does the web service use WS-Security?

<!-- end list -->

  - Can you provide all WSDL paths and endpoints? How many WSDL paths
    are there?

<!-- end list -->

  - Are you using non-SOAP web services such as JSON (RESTful services)?

<!-- end list -->

  - What type of authentication does the web service use? Examples
    include: None, HTTP Basic Authentication, NTLM Authentication, NTLM
    off of Windows (via Ado), Parameter Based Authentication,
    username/password as parameters (in each call, header/body, etc),
    custom built or other authentication, and certificate based.

<!-- end list -->

  - If authentication is used, will you be able to provide credentials
    for testing the web service?

<!-- end list -->

  - Does the Web Service accept attachments via SOAP requests?

<!-- end list -->

  - Will you be able to provide multiple sample SOAP requests that can
    be used to demonstrate the full functionality of the web service?

<!-- end list -->

  - Does the web service have a custom front end that uses the web
    service i.e., Java app, custom coded desktop application, Microsoft
    Silverlight? Can you provide the jar, XAP, or installation files?



## References

**Whitepapers**
\* Tom Eston, Josh Abraham, Kevin Johnson "Don't Drop the SOAP: Real
World Web Service Testing"
<http://securestate.com/Insights/Documents/WhitePapers/Dont-Drop-the-SOAP-Whitepaper.pdf>