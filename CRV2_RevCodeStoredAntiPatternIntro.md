## Stored Cross Site Script (XSS) across Web Applications

This is one of the most common vulnerabilities found accordingly with
OWASP Top 10 2013. When executing a Code review regarding stored XSS,
it’s essential to understand the code containing XSS vulnerability,
which in essence it will be JavaScript code inserted in an input field
of a web form . The malicious user attempts to submit and save this code
in the database or store system of the web application in question.

The following sections focus on showing what components in the
applications must be reviewed in order to determine if they have been
properly configured or coded to avoid XSS attacks. Most of the attacks
occur due to bad configurations or missing mechanisms to validate input,
once a submission is done by a bad-intended user.

## Using in-built resources available

The XSS Cheat Sheets is a valuable resource to the code reviewer, to
understand and control vulnerabilities related to XSS. Understand what
kind of code is been injected and prepare the correct mechanisms to
validate characters and code that can be recognized as XSS. Remember,
many frameworks and applications already contain security libraries and
components that can be used by the developer to achieve this, however if
the developer is ignorant regarding the correct implementation or use of
these instruments, the application will be vulnerable for this and many
more type of vulnerabilities.

Read also the related chapters regarding understanding XSS
vulnerabilities

<https://www.owasp.org/index.php/Reviewing_Code_for_Cross-Site_Scripting>

<https://www.owasp.org/index.php/Overall_approach_to_content_encoding_and_anti_XSS>