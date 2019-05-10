This is the OWASP Testing Guide Project Roadmap for v4.
You can download the stable version v3
[here](http://www.owasp.org/images/5/56/OWASP_Testing_Guide_v3.pdf)
Back to the OWASP Testing Guide Project:
<http://www.owasp.org/index.php/OWASP_Testing_Project>

  - **Introduction and Project purpose for v4**

The OWASP Testing Guide v3 includes a "best practice" penetration
testing framework which users can implement in their own organizations
and a "low level" penetration testing guide that describes techniques
for testing most common web application and web service security issues.
Nowadays the Testing Guide has become the standard to perform a Web
Application Penetration Testing and many Companies all around the world
have adopted it. It is vital for the project mantaining an updated
project that represents the state of the art for WebAppSec.

  - **Project Deadlines**
      - 17th July 2010: Start a brainstorming for the new index starting
        from "Release Description",
      - 15th August 2010: Create the new index and the new team,
      - 15th September 2010: Starting writing articles,
      - 1st October 2010: Starting writing
      - 1st November 2010:Starting the first review phase,
      - 15th November 2010: Starting writing articles II phase,
      - 1st December 2010: Starting the second review phase,
      - 15th December 2010: Create the RC1,
      - 15th January 2011: Release the version 4.

<!-- end list -->

  - **Main goals**
      - Review all the control numbers to adhere to the OWASP Common
        numbering
      - Allignment with ASVS
      - Review all the sections in v3,
      - Create a more readable guide, eliminating some sections that are
        not really useful,
      - Insert new testing techniques: HTTP Verb tampering, HTTP
        Parameter Pollutions, etc.,
      - Rationalize some sections as Session Management Testing,
      - Create a new section: Client side security and Firefox
        extensions testing.
      - Developing 02 test cases for the black box testing

<!-- end list -->

  - **Project Roadmap**

\- 1st phase: Brainstorming
18th July 2010: starting a brainstorming with the OWASP Leaders and
project contributors to share goals and project's objectives.
The following are the main improvements we have to realize: - Inserting
new testing techniques, OWASP Top10 update: HTTP Verb tampering, HTTP
Parameter Pollutions, URL Redirection, Insecure Direct Object
References, Insecure Cryptographic Storage, Failure to Restrict URL
Access, Insufficient Transport Layer Protection, Unvalidated Redirects
and Forwards.
\- Review and improve all the sections in v3
\- Create a more readable guide, eliminating some sections that are not
really useful, Rationalize some sections as Session Management Testing
\- Create a new section: Client side security and Firefox extensions
testing
\- Create a test case for each test to perform using O2 platform
\- 2nd phase: Set-up the team
15th August: Introduce the new project to the OWASP mailing list seeking
for contributors. We need to involve also the final users of the Testing
Guide (for example Banking Companies to understand how they would like
to improve that).

\- 3rd phase: Create a new Index
15th September: creating a new table of contents of the OTGv4 assigning
a task for each contributor. Here is the v3 Index:
<http://www.owasp.org/index.php/OWASP_Testing_Guide_v3_Table_of_Contents>

\- 4th phase: Writing and reviewing
1st October 2010: Starting writing
1st November 2010:Starting the first review phase
15th November 2010: Starting writing articles II phase
1st December 2010: Starting the second review phase
15th December 2010: Create the RC1
15th January 2011: Release the version 4.

-----

  - **OTGv4 Diary**

**18th July 2010**

  - Start 1st phase: brainstorming

Now, we are at the 1st phase, and I think this phase it's the most
important to create a solid project as we saw from the last versions.
This time I found really important to open a debate about the following
item.

\- OWASP vulnerabilities - The OWASP Testing Guide checklist represents
the set of controls to test:
<http://www.owasp.org/index.php/Testing_Checklist> We divided it into 10
categories (Information Gath, Config. Mng, Authentication, etc...). For
each category we tell what test to perfom. The last column tells you
what vulnerability you can find if the test demonstrate a weakness of
the application. Now I see that the list of vulnerabilities is not
alligned with all the OWASP Guides. Imo the point is that is
foundamental to create a list of OWASP Vulnerabilities shared between
the OWASP projects. Why? Because the OWASP DevGuide, Code Review and
Testing Guide should be linked to this common KB: in this way the 3
projects are linked between the others and Companies can uderstand for
each vuln how to protect from this vuln (Dev), how to review that code
(CR), and how to test the app running (TG). Then because it is very
important for the Companies have a full list of the possible WebAppSec
vulns (I think there is a lack now).

At this time we have:
<http://www.owasp.org/index.php/Category:Vulnerability> But this list
does not represents what I mean. I would like to start from the OWASP
Testing Guide checklist and collect all the vulnerabiities we can find
from the last column, add the new ones. Then maybe Eoin's team should
add the white box vulnerabilities: we know some are the same of the
black box assessment, but others can be found only perfoming a Code
Review, for example "Backdoor in the code". Then the Dev Guide team
should point to this set of vulnerabilities telling how to write code to
protect the application for each vulnerability.

[Category:OWASP Testing
Project](Category:OWASP_Testing_Project "wikilink")