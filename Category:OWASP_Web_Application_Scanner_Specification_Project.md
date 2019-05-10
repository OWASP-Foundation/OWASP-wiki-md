[Click here to see (& edit, if wanted) the project's
template.](:Key_Project_Information:OWASP_Web_Application_Scanner_Specification_Project "wikilink")

## About

This project will attempt to outline some of the shortcomings of
currently available web application vulnerability scanners and offer a
plan for comparing and/or building web application vulnerability
scanners.

## Goals & Roadmap

In the near future, we will be focused on the following goals...

`       1. Clean up feature redundancy  `

`       2. Further categorize and document modules`

`       3. Add to platform specific checks (ex. file extensions, )`
`       `
`       4. Adding additional "check" modules`

## Content



<FONT FACE="Times, serif"><FONT SIZE=3><B>Dynamic Analysis of Web
Application Security in Respect to Current Web Application Vulnerability
Scanners: Specification of Needs in Comparison to Current
Offerings</B></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>Introduction/Scope:</B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>There will always be a "gap"
between the types of attacks that can be performed and those which can
be found by an automated scanner. This paper will attempt to outline
some of those shortcomings and offer a plan for comparing/building a web
application vulnerability scanner.</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Need for analysis by attack
type</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Coverage and integration with
other tools and/or scripting support</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Need to assist "technical"
attacker to perform "custom" checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Support for "custom"
reporting</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>_____________________________________________________________________________________</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>General
Topics:</B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Automated vs. Manual Discovery
– The Need for Integration Between Tools</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Application Security – The
Need for Automated Testing Tools </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Integrated Threat Modeling
Feature – Identifying API Exposures and Assigning Risk</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>_____________________________________________________________________________________</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>[OWASP_Web_Application_Scanner_Specification_Project_Baseline](OWASP_Web_Application_Scanner_Specification_Project_Baseline "wikilink")</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>Ideal Baseline - Needs For
Scanner: </B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Integration with Std. VA
scanner</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Integration with HTTP
Proxies</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Exportable Storage of
Results</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • XML Format</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Database Formats</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Search Engine Harvester
Modules</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ability to Document/Flag Good
and Bad Results</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Limit scan to specified
IPs/Hosts, Domains, and Ports Discovered on Host running HTTP(s)
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • checksum content b/t ports,
hosts, etc. for same content</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Be able to accurately
reproduce results (ex. -- reply request and show in
browser)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Spidering and Resource
Identification </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • User defined optimization of
scan threads, timeouts, etc</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Virtual host identification -
edit cost, diff btw pages –</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HDM idea - Intranet hostname
exposure, etc.....over 512 bytes, insane overhead</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DNS grinding, etc
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> •
<http://www.owasp.org/index.php/Testing_for_Application_Discovery_(OWASP-IG-005)></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Auth vs UnAuth forced Browsing
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • checkout step bypass,
etc</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Accurately identify
directories and files present (and supported extensions)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ability to add checks for
permeation based dir checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • User is able to specify and
retest extra files, dirs, and attacks as well as add to test
"template"</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • (retest/add this dir for all
vulns/files, retest this dir for XSS, rerun all SQL injection,
etc)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ability to specify custom HTTP
requests and form templates based on HTTP requests and
errors</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Fuzzer </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ability to model after
"stored" requests,</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • pop out?</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HTTP</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • WSDL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Iteration based fuzzing and
discovery - ie, Pornzilla</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookies/Session testing and
analysis </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • automated analysis and manual
analysis replay idea (my idea kinda......need to
elaborate)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Platform Specific tests and
customization/AI (MS, .Net, Java, Apache)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Path, Error Path and Verbose
errors Identification </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Tomcat</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ASP.NET</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • CFM</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JSP</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Request
Comparison</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookies</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Collection</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Encoder/Decoder</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Comparison</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Authentication Tester/Brute
Forcer</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Form</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Basic</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • NTLM</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookies/Sessions</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • SSL/Encryption strength
analysis</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Easy "dictionary"
customization</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Application
Servers/Frameworks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache Tomcat</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ruby on Rails</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Django</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JavaScript Framework
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Dojo</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • script.aculo.us</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Prototype</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DWR</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • GWT</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Sajax </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Endpoint
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • 3rd Party
Resources</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • RSS</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Atom</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Misc. Web Service
oriented</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Admin Console
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JBoss</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JRun</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Services</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • SOAP</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • WSDL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • UDDI/Endpoint Discovery
Protocols</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • WS-Security</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ReST</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Flash/Flex</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Java</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ActiveX</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • User identification (error
messages, user dirs, etc) and customization (ex. add to BF
dictionary)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DB Platform
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MSSQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MySQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Sybase</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MS Access</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Oracle</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DB2</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DB/XML store of files/dirs -
grepable</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>_____________________________________________________________________________________</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>Platform and Resource
Requirements:</B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DB Platform
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MSSQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MySQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Sybase</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MS Access</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Oracle</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DB2</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Platform
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • IIS</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Tomcat</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ASP.NET</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • CFM</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JSP</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ActiveX</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Java Applets</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Javascript and JS
Frameworks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Flex</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Flash</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ReST</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • SOAP/WSDL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • WEBrick</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Django (python)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>_____________________________________________________________________________________</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>Modules:</B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • XSS </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • DOM Injection
Attacks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Stored</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Reflected</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Injection
Attacks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • SQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • XML/XPATH/XMLRCP/SOAP -
DOM-based XSS - Difficult - can't grep sourcd</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JSON (Javascript Object
Notation) </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Link Injection/Insertion (eg.
OWA)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Dir Traversal</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • File Include</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • XSRF</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HTTP Response
Splitting</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookie Collector and
Checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookies Enabled
(Y/N)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Flags Set in
Cookies</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HTTPOnly</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Secure</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Domain</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Path</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Expires</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Cookie
Randomization</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • GUI plotting</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Platform Specific
Checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • IIS</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • IPP</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • IDA/IDQ</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • FrontPage</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Anon</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Files/Extensions</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MSSQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Microsoft .NET</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • .NET

`Version Enumeration`</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ViewState</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Decoder</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Value collection</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Value comparison</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Identification of Repeating VS
Unique Values</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Identification of Possibly
Sensitive Values</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Changes in Relation to
Application Logic</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • userdir</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • MySQL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Docs</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Modules
installed</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • OpenSSL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ModSSL</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Expect</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ModSecurity</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Mod_jk</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache Tomcat</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • mgmt/admin
interface</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Docs</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • General platform and
hardware/device specific checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Parameter identification
(Identify inputs)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Identify ALL Resources that
appear to accept "user-defined" input</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HTTP OPTIONS</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • HTTP Track/XST</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Comments</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Internal IP
Disclosure</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Mgmt Interface Scanner
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /jmx-console</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /web-console</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Conf File Scanner
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /WEB-INF/web.xml</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /robots.txt</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /.htaccess</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /jmx-console site enumeration
(not just identify presence of web console)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • /web-console site enumeration
(not just identify presence of web console)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • File Include/Insertion Scanner
(esp PHP)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Authentication
Scanner</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Basic/NTLM
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Form-based Authentication
Identification</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Username
Enumeration</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • User-dir</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Page Scraping </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Site Mirroring</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Google – Email Scraper
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Brute-Forcer</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Dictionary
attacker</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Easy "dictionary"
customization</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Default Password
Tester</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • By Platform</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Source Code Disclosure (eg.
%00, %20)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Page pattern matcher (Page
Structure VS <Diff> Page Content)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Incorrect usage of
eval()</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • OS command shell</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Software Version
Identification </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • regex values</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • window

<Title>

names</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • comments </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • base platform</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Hidden Fields/Links
Enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • File Upload
Enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Log File Scanner</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Temp Files</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Search Function for associated
Vulns and software versions</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ability to Reference Common
Security Sites for Vulnerability Information</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Path Case-sensitivity
enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Encodings
Supported</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Servlet Mapper</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Local Search Engine
Enumeration</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Google File/DIR
mapper</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • BackEnd DB Type
Enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Application logic
enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • ActiveX, Java object
enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • LDAP Checks</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • File Ext and Dir Mapper
</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • System Platform Type/Version
Enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Supported File Types
Enumerator</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Unmapped File
Extensions</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Identifying "sensitive"
data</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Framework and Application
Fingerprinting </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Flash/Flex </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • J2EE</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JBoss

</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • JRun</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Apache
Foundation</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Web Server</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Tomcat</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Axis </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Ruby on Rails</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Zend</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Django </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Jakarta Struts (and other MVC
architectures)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Exposed Source-Code analysis
(VM-like environment to run in)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • FireBug
(pop-out?)</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3>_____________________________________________________________________________________</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3><U><B>Reporting/Results:</B></U></FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • Database/XML compatible
storage </FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • data correlation with other
(HTTP) tools</FONT></FONT>

<FONT FACE="Times, serif"><FONT SIZE=3> • AUTO TXT, DB, SQL, source file
ARCHIVER/STORED DIRECTORY</FONT></FONT>





<FONT FACE="Times, serif"><FONT SIZE=3> </FONT></FONT>







[Web Application Scanner Specification
Project](Category:OWASP_Project "wikilink") [Category:OWASP
Document](Category:OWASP_Document "wikilink") [Category:OWASP Alpha
Quality Document](Category:OWASP_Alpha_Quality_Document "wikilink")