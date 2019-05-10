**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Paolo Perego

**Project coordinator**: Dinis Cruz

**Project Progress**: 100% Complete, [Progress
Page](SpoC_007_-_Orizon_Project_-_Progress_Page "wikilink")

## Paolo Perego - OWASP Orizon Project

### Executive Summary

Owasp Orizon \[16\] Project born in 2006 as answer to the lack of common
engine and library usable by opensource code review related tools.

I'm proposing that, during the Spring of Code 2007 period, I'll complete
static analisys API and java source code enforment objects.

Sometimes a complete code review approach is not suitable for most
customers who wants to harden their code which is being approaching
release stage. For such a reason, I started writing Java objects that
embeds most of the security checks against common web vulnerabilities
(XSS, SQL injection, Session handling, ...) so that source code can be
hardened with a small effort in terms of code rewriting.

I do believe that a common set of API and a common safe coding best
practices library is one of the most important goals to bring
application security to the developers.

### Objectives and Deliverables

Completing the static code review API section:

  - improving programming language to XML translator
  - improving security best practices code review scan library
  - improving secure coding fashion best practices library
  - writing the pattern matching scan using the aformentioned libraries

Writing the java source code enforment objects

  - writing an object to handle form data values to avoid XSS
  - writing an object to handle form data values to avoid SQL Injection
  - writing an object to handle HttpRequest and HttpSession objects

### Why I should be sponsored for the project

Owasp Orizon is the first Owasp project I'm involved in. I'm also
contributor of Owasp Italian chapter managed by Matteo Meucci and I'm
talking at various speeches about application security and safe coding
best practices.

I'm a security consultant working in ethical hacking and we're
approaching code review and safe topics right now. I'm a developer too
so I understand also the "dark side" of the problem developing code with
security in mind.

I work using the "release early release often" paradigm so to be
concrete and let other people having something usable to work with.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**