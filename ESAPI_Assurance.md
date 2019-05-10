## Building an Assurance Case for ESAPI

  - [Arguing Security - Creating Security Assurance
    Cases](https://buildsecurityin.us-cert.gov/daisy/bsi/articles/knowledge/assurance/643-BSI.html)

<!-- end list -->

  - summary: make Claims, provide supporting Evidence, and make
    Arguments for how the evidence supports the claims

<!-- end list -->

  - Highest level claim is "The system is Acceptably Secure" but how to
    break this down into sub-claims that map to the provided evidence?
    e.g. absence of specific vulns (as investigated by manual testing or
    tool scans)

<!-- end list -->

  - Hey\! How about an explicit threat model??? Especially, what are our
    assumptions.

<!-- end list -->

  - claims could be summarized using a [Software Facts
    Label](http://swaconsortium.org/projects/softwareFacts/softwareFacts.html)

<!-- end list -->

  - each language (Java, ASP, etc.) may need separate claims

<!-- end list -->

  - list the third-party software

<!-- end list -->

  - discuss coding practices that were followed, skill levels of
    developers, amount of independent review

<!-- end list -->

  - publish scanning tool results. "Tool X, using rule set R on date D,
    was run against ESAPI version Y using configuration Z, and found
    this set of results with this amount of code coverage."

## Coding Practices

  - was OWASP Top Ten followed?

<!-- end list -->

  - how was performance and security balanced?

<!-- end list -->

  - what is the level of training of the developers? amount of
    experience in web development?

<!-- end list -->

  - were tools part of the whole process or run at the end?

<!-- end list -->

  - how was code repository prevented from unauthorized alterations?

<!-- end list -->

  - practices for code check-in and independent review - how is
    introduction of Trojans avoided?

<!-- end list -->

  - what threat level is being accounted for (e.g. will this only work
    against script kiddies)? was threat modeling used? (No; I wish\!)