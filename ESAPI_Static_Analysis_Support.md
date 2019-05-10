There are a number of activities related to static analysis tools and
ESAPI.

  - Claim: Use of ESAPI 'should' make it easier to analyze applications
    for security using analysis tools. To facilitate this we should:
      - Develop markup for ESAPI for each of the major static analysis
        tools (open source AND commercial)
          - This will allow the existing rules provided by the tools to
            be run against the application, while recognizing what ESAPI
            does, like validate, encode, etc.
          - If a tool can recognize ESAPI-based validation/encoding and
            other controls, it might help to reduce the number of false
            positives
          - If there is a [mapping](CWE_ESAPI "wikilink") from CWE names
            to associated ESAPI controls, then a tool could use its CWE
            results to suggest which controls to focus on first.


\* Fact: There are coding rules we would like developers to follow to
build secure apps that are not currently being checked for, possibly
because developers don't have the capability to do some of these things
today. ESAPI is intended to make it far easier for developers to adopt
new secure coding practices and we would like to check to make sure they
are following these new best practices

  -   - OWASP should develop its own 'rules' on what it thinks
        applications should do to use ESAPI correctly, which won't
        currently be represented in existing tool rulesets
      - OWASP should also develop its own 'rules' on what it thinks that
        applications should do to be secure, that don't necessarily
        depend on the use of ESAPI. These rules would be applicable to
        all applications, regardless of whether they are using ESAPI or
        not.


We might want to start with something open source like FindBugs and do
the above for it first (if it can handle what we want to do), and then
encourage the major static analysis tool vendors to implement equivalent
API markup and rules for their tool. There is already precedent for
publication of rules for commercial tools (see CERT C Secure Coding
standard pack for Fortify and others)