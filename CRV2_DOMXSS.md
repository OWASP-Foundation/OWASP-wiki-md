XSS stands for Cross-site scripting. XSS is a common vulnerability found
in web sites. Cross-site scripting accounts for 60 to 80% of all
security vulnerabilities. This section od the Code Review Guide is
focused DOM-based XSS vulnerabilities instead of the more traditionally
cross-site scripting. The difference between the two is that traditional
XSS occur in server-side code response for preparing HTML response to be
served client-sided and DOM-XSS vulnerabilities occur in the content
processing on the client side typically done with client-side
JavaScript.

DOM-XSS is mitigation is hampered by a lack of standardization of
browsers and a large attack surface.

## Reducing the threat:

The most common way to reduce is with encoding/escaping of string input.
The code reviewer talk with development staff to see if any frameworks
were used to help eliminated common XSS vulnerabilities.

  - OWASP ESAPI (Java)
  - ValidateRequest (ASP.NET)
  - Anti-XSS library (ASP.NET)
  - AntiSamy (Java)
  - strip_tags, sanitize (Ruby on Rails)
  - Django template escaping (Python Django)
  - Coverity Security Library (Java)
  - xss validator (Node.js)
  - HTML Purifier
  - Google Gaja

As with standard XSS the code reviewer should always pay attention to
the following bullet points….

  - How the programmer is validating input data. Not validating data is
    the root of all evil.
  - Making sure data is escaped when the script writes out the page.
  - Code Reviewer should review methods that make it hard to escape data
    and require an understanding of each browers JavaScript engine. The
    code reviewer should red flag code that uses the following. These
    methods can be used securely but are prone to vulnerabilities. Best
    practice is not to use them.
      - Element's .innerHTML() and .outerHTML() methods.
      - Using user data in jQuery's element creation.
      - jQuery's append.
      - Using user data in a string passed to eval, setTimeout, an
        object's event handler, or javascript: url targets.
      - Using user data in strings that generate CSS.

## Microsoft ASPX .Net

  - On ASPX .Net pages code review should check to make sure web config
    file does not turn off page validation.
    <pages validateRequest="false" />
  - .Net framework 4.0 does not allow page validation to be turned off.
    Hence if the programmer wants to turn of page validation the
    developer will need to regress back to 2.0 validation mode.
    <httpRuntime requestValidationMode="2.0" />
  - Code reviewer needs to make sure page validation is never turned off
    on anywhere and if it is understand why and the risks it opens the
    organization to. \<%@ Page Language=”C\#” ValidationRequest=”false”

## OWASP Resources:

OWASP DOM BASED XSS [1](https://www.owasp.org/index.php/DOM_Based_XSS)

OWASP DOM BASED Cheat Sheet
\[www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet\]