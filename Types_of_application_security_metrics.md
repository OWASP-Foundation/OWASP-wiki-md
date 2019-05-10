## Metrics Overview

![softwarefacts.jpg](softwarefacts.jpg "softwarefacts.jpg")
![Ingredients.png](Ingredients.png "Ingredients.png")

It's been said that you can't improve what you can't measure. We
currently don't have any good metrics for application security. Everyone
understands what we want to measure -- how secure is it? But we're
really not sure what low-level measurements we should be making, nor do
we know how to roll them up into something meaningful for the buyer or
user of software.

The difficulty of this problem is essentially the same as determining if
there are any loopholes in a legal contract. Like legalese, programming
languages are arbitrarily complex. A malicious developer, like a crafty
lawyer, will use all their skill to obfuscate their attack.

## Direct Metrics

Ideally, we could just measure the software itself. If we could count
all the vulnerabilities and determine their likelihood and impact, we'd
know how secure it is. Unfortunately, even the best static analysis
tools can't come close to doing this. Still, there are things we can
measure, and perhaps we can figure out which of these things directly
correlate with increased security.

  - How many lines of code?
  - What languages are used?
  - What libraries does this application use (and how)?
  - What type of network access is required (client, server, none)?
  - What security mechanisms are used?
  - What configuration files are associated with the application?
  - How are sensitive assets protected?
  - What vulnerabilities have been identified

## Indirect Metrics

If you can't measure the security of software directly, another option
is to measure the people, process, and technology that are associated
with creating the software in the first place?

  - Is there security documentation (design, test results,
    vulnerabilities)?
  - Is the documentation accurate and complete?
  - Is there a process for reporting security flaws?
  - Who developed this code (training, experience, background check)?
  - What assurance activities were performed (threat modeling, analysis,
    code review, test, evaluation)?
  - What was the outcome of those assurance activities?

[Category:OWASP Application Security Metrics
Project](Category:OWASP_Application_Security_Metrics_Project "wikilink")