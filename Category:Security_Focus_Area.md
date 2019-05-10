## What is a Security Focus Area (SFA)?

The [Honeycomb Project](:Category:OWASP_Honeycomb_Project "wikilink")
has many individual articles detailing the basic building blocks of
application security, including
[principles](:Category:Principle "wikilink"),
[threats](:Category:Threat "wikilink"),
[attacks](:Category:Attack "wikilink"),
[vulnerabilities](:Category:Vulnerability "wikilink"),
[countermeasures](:Category:Countermeasure "wikilink"). Generally, a
single application security issue will involve several of each type of
building block. For example, SQL Injection might involve several
different threats and attacks, a few related vulnerabilities, and
several countermeasures.

To help navigate these articles, we have created these "Security Focus
Areas" (SFAs) as a guide that pulls together and creates a roadmap for a
single application security issue. The articles in other OWASP projects
([Top 10](Top_10 "wikilink"), [Guide](Guide "wikilink"), [Testing
Guide](Testing_Guide "wikilink"), [Code Review](Code_Review "wikilink"),
etc.) tend to be more comprehensive guidelines to various security
areas. These articles are either trying to raise the awareness of a SFA
(such as these articles in Top 10), or describe the systematic security
approaches on how to identify, analyze, remediate or prevent these
problems.

## What goes into a SFA?

Each SFA provides:

  - A short, management-level introduction to the area
  - A roadmap to the threat modeling elements for this area with
    emphasis on helping readers evaluate the likelihood and impact of a
    successful exploit in their application
  - Links to guidelines for testing, code reviewing, and architecting
    this area
  - Other articles covering this topic

Therefore a SFA category acts as a roadmap to guide you through articles
in this area. It helps you to obtain a high-level overview of the
problem quickly and enables you to dive down into the details easily
when needed.

## What makes a good SFA?

Here are some criteria for a SFA:

  - It should be a specific topic instead of a big/generic title
      - For example, "SQL Injection" instead of "Injection Flaws"
  - It should be a well-known and commonly used topic area
  - It should overlap as little as possible with other SFA's

## How to add a new SFA

Create an Category:SecurityFocusAreaName and add
\[\[Category:Security_Focus_Area|Category:Security Focus Area\]\] at
the bottom. A SFA article should follow the structure in
[SFA](SFA "wikilink"). **Note:** we should create a template for the
header of an SFA.

## How you can help?

  - If you find articles related to an existing SFA, please link to them
    in the SFA article.
  - If you feel the need to create a new SFA, please consider the
    criteria listed in "what makes a good SFA" section.

## The current list of SFAs

  - [Phishing](Phishing "wikilink")
  - [Cross-Site Scripting](Cross-Site_Scripting "wikilink")
  - [Buffer Overflow](Buffer_Overflow "wikilink")
  - [SQL Injection](SQL_Injection "wikilink")

__NOTOC__