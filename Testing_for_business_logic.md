## Summary

Testing for business logic flaws in a multi-functional dynamic web
application requires thinking in unconventional methods. If an
application's authentication mechanism is developed with the intention
of performing steps 1, 2, 3 in that specific order to authenticate a
user. What happens if the user goes from step 1 straight to step 3? In
this simplistic example, does the application provide access by failing
open; deny access, or just error out with a 500 message?

There are many examples that can be made, but the one constant lesson is
"think outside of conventional wisdom". This type of vulnerability
cannot be detected by a vulnerability scanner and relies upon the skills
and creativity of the penetration tester. In addition, this type of
vulnerability is usually one of the hardest to detect, and usually
application specific but, at the same time, usually one of the most
detrimental to the application, if exploited.

The classification of business logic flaws has been under-studied;
although exploitation of business flaws frequently happens in real-world
systems, and many applied vulnerability researchers investigate them.
The greatest focus is in web applications. There is debate within the
community about whether these problems represent particularly new
concepts, or if they are variations of well-known principles.

Testing of business logic flaws is similar to the test types used by
functional testers that focus on logical or finite state testing. These
types of tests require that security professionals think a bit
differently, develop abused and misuse cases and use many of the testing
techniques embraced by functional testers. Automation of business logic
abuse cases is not possible and remains a manual art relying on the
skills of the tester and their knowledge of the complete business
process and its rules.

## Business Limits and Restrictions

Consider the rules for the business function being provided by the
application. Are there any limits or restrictions on people's behavior?
Then consider whether the application enforces those rules. It's
generally pretty easy to identify the test and analysis cases to verify
the application if you're familiar with the business. If you are a
third-party tester, then you're going to have to use your common sense
and ask the business if different operations should be allowed by the
application.

Sometimes, in very complex applications, the tester will not have a full
understanding of every aspect of the application initially. In these
situations, it is best to have the client walk the tester through the
application, so that they may gain a better understanding of the limits
and intended functionality of the application, before the actual test
begins. Additionally, having a direct line to the developers (if
possible) during testing will help out greatly, if any questions arise
regarding the application's functionality.

## Description of the Issue

Automated tools find it hard to understand context, hence it's up to a
person to perform these kinds of tests. The following two examples will
illustrate how understanding the functionality of the application, the
developer's intentions, and some creative "out-of-the-box" thinking can
break the application's logic. The first example starts with a
simplistic parameter manipulation, whereas the second is a real world
example of a multi-step process leading to completely subvert the
application.

**Example 1**:

Suppose an e-commerce site allows users to select items to purchase,
view a summary page and then tender the sale. What if an attacker was
able to go back to the summary page, maintaining their same valid
session and inject a lower cost for an item and complete the
transaction, and then check out?

**Example 2**:

Holding/locking resources and keeping others from purchases these items
online may result in attackers purchasing items at a lower price. The
countermeasure to this problem is to implement timeouts and mechanisms
to ensure that only the correct price can be charged.

**Example 3**:

What if a user was able to start a transaction linked to their
club/loyalty account and then after points have been added to their
account cancel out of the transaction? Will the points/credits still be
applied to their account?

## Business Logic Test Cases

Every application has a different business process, application specific
logic and can be manipulated in an infinite number of combinations. This
section provides some common examples of business logic issues but in no
way a complete list of all issues.

**Business Logic exploits can be broken into the following categories**:

[4.12.1 Test business logic data validation
(OTG-BUSLOGIC-001)](Test_business_logic_data_validation_\(OTG-BUSLOGIC-001\) "wikilink")

In business logic data validation testing, we verify that the
application does not allow users to insert “unvalidated” data into the
system/application. This is important because without this safeguard
attackers may be able to insert “unvalidated” data/information into the
application/system at “handoff points” where the application/system
believes that the data/information is “good” and has been valid since
the “entry points” performed data validation as part of the business
logic workflow.

[4.12.2 Test Ability to forge requests
(OTG-BUSLOGIC-002)](Test_Ability_to_forge_requests_\(OTG-BUSLOGIC-002\) "wikilink")

In forged and predictive parameter request testing, we verify that the
application does not allow users to submit or alter data to any
component of the system that they should not have access to, are
accessing at that particular time or in that particular manner. This is
important because without this safeguard attackers may be able to
“fool/trick” the application into letting them into sections of thwe
application of system that they should not be allowed in at that
particular time, thus circumventing the applications business logic
workflow.

[4.12.3 Test Integrity Checks
(OTG-BUSLOGIC-003)](Test_integrity_checks_\(OTG-BUSLOGIC-003\) "wikilink")

In integrity check and tamper evidence testing, we verify that the
application does not allow users to destroy the integrity of any part of
the system or its data. This is important because without these safe
guards attackers may break the business logic workflow and change of
compromise the application/system data or cover up actions by altering
information including log files.

[4.12.4 Test for Process Timing
(OTG-BUSLOGIC-004)](Test_for_Process_Timing_\(OTG-BUSLOGIC-007\) "wikilink")

In process timing testing, we verify that the application does not allow
users to manipulate a system or guess its behavior based on input or
output timing. This is important because without this safeguard in place
attackers may be able to monitor processing time and determine outputs
based on timing, or circumvent the application’s business logic by not
completing transactions or actions in a timely manner.

[4.12.5 Test Number of Times a Function Can be Used Limits
(OTG-BUSLOGIC-005)](Test_number_of_times_a_function_can_be_used_limits_\(OTG-BUSLOGIC-007\) "wikilink")

In function limit testing, we verify that the application does not allow
users to exercise portions of the application or its functions more
times than required by the business logic workflow. This is important
because without this safeguard in place attackers may be able to use a
function or portion of the application more times than permissible per
the business logic to gain additional benefits.

[4.12.6 Testing for the Circumvention of Work Flows
(OTG-BUSLOGIC-006)](Testing_for_the_Circumvention_of_Work_Flows_\(OTG-BUSLOGIC-009\) "wikilink")

In circumventing workflow and bypassing correct sequence testing, we
verify that the application does not allow users to perform actions
outside of the “approved/required” business process flow. This is
important because without this safeguard in place attackers may be able
to bypass or circumvent workflows and “checks” allowing them to
prematurely enter or skip “required” sections of the application
potentially allowing the action/transaction to be completed without
successfully completing the entire business process, leaving the system
with incomplete backend tracking information.

[4.12.7 Test Defenses Against Application Mis-use
(OTG-BUSLOGIC-007)](Test_defenses_against_application_mis-use_\(OTG-BUSLOGIC-011\) "wikilink")

In application mis-use testing, we verify that the application does not
allow users to manipulate the application in an unintended manner.

[4.12.8 Test Upload of Unexpected File Types
(OTG-BUSLOGIC-008)](Test_Upload_of_Unexpected_File_Types_\(OTG-BUSLOGIC-015\) "wikilink")

In unexpected file upload testing, we verify that the application does
not allow users to upload file types that the system is not expecting or
wanted per the business logic requirements. This is important because
without these safeguards in place attackers may be able to submit
unexpected files such as .exe or .php that could be saved to the system
and then executed against the application or system.

[4.12.9 Test Upload of Malicious Files
(OTG-BUSLOGIC-009)](Test_Upload_of_Malicious_Files_\(OTG-BUSLOGIC-016\) "wikilink")

In malicious file upload testing, we verify that the application does
not allow users to upload files to the system that are malicious or
potentially malicious to the system security. This is important because
without these safeguards in place attackers may be able to upload files
to the system that may spread viruses, malware or even exploits such as
shellcode when executed.

## Tools

While there are tools for testing and verifying that business processes
are functioning correctly in valid situations these tools are incapable
of detecting logical vulnerabilities. For example, tools have no means
of detecting if a user is able to circumvent the business process flow
through editing parameters, predicting resource names or escalating
privileges to access restricted resources nor do they have any mechanism
to help the human testers to suspect this state of affairs.

The following are some common tool types that can be useful in
identifying business logic issues.

'''HP Business Process Testing Software '''
\*<http://www8.hp.com/us/en/software-solutions/software.html?compURI=1174789#.UObjK3ca7aE>

**Intercepting Proxy - To observe the request and response blocks of
HTTP traffic.**

  - Webscarab -
    <https://www.owasp.org/index.php/Category:OWASP_WebScarab_Project>

<!-- end list -->

  - Burp Proxy - <http://portswigger.net/burp/proxy.html>

<!-- end list -->

  - Paros Proxy - <http://www.parosproxy.org/>

**Web Browser Plug-ins - To view and modify HTTP/HTTPS headers, post
parameters and observe the DOM of the Browser**

  - Tamper Data (for Internet Explorer) -
    <https://addons.mozilla.org/en-us/firefox/addon/tamper-data/>

<!-- end list -->

  - TamperIE (for Internet Explorer) - <http://www.bayden.com/tamperie/>

<!-- end list -->

  - Firebug (for Internet Explorer) -
    <https://addons.mozilla.org/en-us/firefox/addon/firebug/> and
    <http://getfirebug.com/>

**Miscellaneous Test Tools**

  - Web Developer toolbar -
    <https://chrome.google.com/webstore/detail/bfbameneiokkgbdmiekhjnmfkcnldhhm>

The Web Developer extension adds a toolbar button to the browser with
various web developer tools. This is the official port of the Web
Developer extension for Firefox.

  - HTTP Request Maker -
    <https://chrome.google.com/webstore/detail/kajfghlhfkcocafkcjlajldicbikpgnp?hl=en-US>

Request Maker is a tool for penetration testing. With it you can easily
capture requests made by web pages, tamper with the URL, headers and
POST data and, of course, make new requests

  - Cookie Editor -
    <https://chrome.google.com/webstore/detail/fngmhnnpilhplaeedifhccceomclgfbg?hl=en-US>

Edit This Cookie is a cookie manager. You can add, delete, edit, search,
protect and block cookies

  - Session Manager -
    <https://chrome.google.com/webstore/detail/bbcnbpafconjjigibnhbfmmgdbbkcjfi>

With Session Manager you can quickly save your current browser state and
reload it whenever necessary. You can manage multiple sessions, rename
or remove them from the session library. Each session remembers the
state of the browser at its creation time, i.e. the opened tabs and
windows. Once a session is opened, the browser is restored to its state.

  - Cookie Swap -
    <https://chrome.google.com/webstore/detail/dffhipnliikkblkhpjapbecpmoilcama?hl=en-US>

Swap My Cookies is a session manager, it manages your cookies, letting
you login on any website with several different accounts. You can
finally login into Gmail, yahoo, hotmail, and just any website you use,
with all your accounts; if you want to use another account just swap
profile\!

  - HTTP Response Browser -
    <https://chrome.google.com/webstore/detail/mgekankhbggjkjpcbhacjgflbacnpljm?hl=en-US>

Make HTTP requests from your browser and browse the response (HTTP
headers and source). Send HTTP method, headers and body using
XMLHttpRequest from your browser then view the HTTP status, headers and
source. Click links in the headers or body to issue new requests. This
plug-in formats XML responses and uses Syntax Highlighter \<
<http://alexgorbatchev.com/> \>.

  - Firebug lite for Chrome -
    <https://chrome.google.com/webstore/detail/bmagokdooijbeehmkpknfglimnifench>

Firebug Lite is not a substitute for Firebug, or Chrome Developer Tools.
It is a tool to be used in conjunction with these tools. Firebug Lite
provides the rich visual representation we are used to see in Firebug
when it comes to HTML elements, DOM elements, and Box Model shading. It
provides also some cool features like inspecting HTML elements with your
mouse, and live editing CSS properties.

## References

**Whitepapers**

  - Business Logic Vulnerabilities in Web Applications -
    <http://www.google.com/url?sa=t&rct=j&q=BusinessLogicVulnerabilities.pdf&source=web&cd=1&cad=rja&ved=0CDIQFjAA&url=http%3A%2F%2Faccorute.googlecode.com%2Ffiles%2FBusinessLogicVulnerabilities.pdf&ei=2Xj9UJO5LYaB0QHakwE&usg=AFQjCNGlAcjK2uz2U87bTjTHjJ-T0T3THg&bvm=bv.41248874,d.dmg>

<!-- end list -->

  - The Common Misuse Scoring System (CMSS): Metrics for Software
    Feature Misuse Vulnerabilities - NISTIR 7864 -
    <http://csrc.nist.gov/publications/nistir/ir7864/nistir-7864.pdf>

<!-- end list -->

  - Designing a Framework Method for Secure Business Application Logic
    Integrity in e-Commerce Systems, Faisal Nabi -
    <http://ijns.femto.com.tw/contents/ijns-v12-n1/ijns-2011-v12-n1-p29-41.pdf>

<!-- end list -->

  - Finite State testing of Graphical User Interfaces, Fevzi Belli -
    <http://www.slideshare.net/Softwarecentral/finitestate-testing-of-graphical-user-interfaces>

<!-- end list -->

  - Principles and Methods of Testing Finite State Machines - A Survey,
    David Lee, Mihalis Yannakakis -
    <http://www.cse.ohio-state.edu/~lee/english/pdf/ieee-proceeding-survey.pdf>

<!-- end list -->

  - Security Issues in Online Games, Jianxin Jeff Yan and Hyun-Jin Choi
    - <http://homepages.cs.ncl.ac.uk/jeff.yan/TEL.pdf>

<!-- end list -->

  - Securing Virtual Worlds Against Real Attack, Dr. Igor Muttik, McAfee
    -
    <https://www.info-point-security.com/open_downloads/2008/McAfee_wp_online_gaming_0808.pdf>

<!-- end list -->

  - Seven Business Logic Flaws That Put Your Website At Risk – Jeremiah
    Grossman Founder and CTO, WhiteHat Security -
    <https://www.whitehatsec.com/resource/whitepapers/business_logic_flaws.html>

<!-- end list -->

  - Toward Automated Detection of Logic Vulnerabilities in Web
    Applications - Viktoria Felmetsger Ludovico Cavedon Christopher
    Kruegel Giovanni Vigna -
    <https://www.usenix.org/legacy/event/sec10/tech/full_papers/Felmetsger.pdf>

<!-- end list -->

  - 2012 Web Session Intelligence & Security Report: Business Logic
    Abuse, Dr. Ponemon -
    <http://www.emc.com/collateral/rsa/silvertail/rsa-silver-tail-ponemon-ar.pdf>

<!-- end list -->

  - 2012 Web Session Intelligence & Security Report: Business Logic
    Abuse (UK) Edition, Dr. Ponemon -
    <http://buzz.silvertailsystems.com/Ponemon_UK.htm>

**OWASP Related**

  - Business Logic Attacks – Bots and Bats, Eldad Chai -
    <http://www.imperva.com/resources/adc/pdfs/AppSecEU09_BusinessLogicAttacks_EldadChai.pdf>

<!-- end list -->

  - OWASP Detail Misuse Cases -
    <https://www.owasp.org/index.php/Detail_misuse_cases>

<!-- end list -->

  - How to Prevent Business Flaws Vulnerabilities in Web Applications,
    Marco Morana -
    <http://www.slideshare.net/marco_morana/issa-louisville-2010morana>

**Useful Web Sites**

  - Abuse of Functionality -
    <http://projects.webappsec.org/w/page/13246913/Abuse-of-Functionality>

<!-- end list -->

  - Business logic - <http://en.wikipedia.org/wiki/Business_logic>

<!-- end list -->

  - Business Logic Flaws and Yahoo Games -
    <http://jeremiahgrossman.blogspot.com/2006/12/business-logic-flaws.html>

<!-- end list -->

  - CWE-840: Business Logic Errors -
    <http://cwe.mitre.org/data/definitions/840.html>

<!-- end list -->

  - Defying Logic: Theory, Design, and Implementation of Complex Systems
    for Testing Application Logic -
    <http://www.slideshare.net/RafalLos/defying-logic-business-logic-testing-with-automation>

<!-- end list -->

  - Prevent application logic attacks with sound app security practices
    -
    <http://searchappsecurity.techtarget.com/qna/0,289202,sid92_gci1213424,00.html?bucket=NEWS&topic=302570>

<!-- end list -->

  - Real-Life Example of a 'Business Logic Defect -
    <http://h30501.www3.hp.com/t5/Following-the-White-Rabbit-A/Real-Life-Example-of-a-Business-Logic-Defect-Screen-Shots/ba-p/22581>

<!-- end list -->

  - Software Testing Lifecycle -
    <http://softwaretestingfundamentals.com/software-testing-life-cycle/>

<!-- end list -->

  - Top 10 Business Logic Attack Vectors Attacking and Exploiting
    Business Application Assets and Flaws – Vulnerability Detection to
    Fix -
    <http://www.ntobjectives.com/go/business-logic-attack-vectors-white-paper/>
    and
    <http://www.ntobjectives.com/files/Business_Logic_White_Paper.pdf>

**Books**

  - The Decision Model: A Business Logic Framework Linking Business and
    Technology, By Barbara Von Halle, Larry Goldberg, Published by CRC
    Press, ISBN1420082817 (2010)