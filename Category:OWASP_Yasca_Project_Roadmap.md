### The Goal of Yasca

The primary goal of Yasca is to assist **developers** in performing a
**security-oriented code review**. This is accomplished through the
following main features:

  - an extensible architecture that other products can be integrated
    into,
  - a single view of all results, with details down to the line of code
    (where possible), and
  - a growing set of "open source" rules that anyone can add to.

A secondary goal is to support both the open source and enterprise
development communities by delivering a high-quality product that can be
relied upon and extended to meet evolving needs.

### The Roadmap

#### Version 1.0

The initial public release of Yasca was made available in October 2008.
It offered integration with PMD, FindBugs, J-Lint, and antiC, as well as
a limited set of custom rules and report generators.

#### Version 1.1

This version was released on December 19, 2008, with the following
changes:

  - Update of all integrated components
      - PMD to version 4.2.4
      - FindBugs to version 1.3.6 (with FB-Contrib as well)
      - PHP to version 5.2.8
  - Addition of new custom rules
  - Minor bug fixes

#### Version 1.2

Version 1.2 was released on January 16, 2009, with the following
enhancements:

  - Ability to flag findings to be ignored in subsequent scans
  - New plugins for PHP and C/C++
  - Inclusion of Pixy, a scanner for PHP 4 source code
  - Minor bug fixes

#### Version 2.0

Version 2.0 released on 2009-05-07

`   Redesign separating Yasca-Core from plugin packages.`
`   Added ClamAV plugin`
`   Added RATS plugin`
`   Added new minor plugins and many new rulesets.`

Version 2.01 released on 2009-05-18

`   Fixed a few bugs related to calling external plugins.`
`   Added a few minor plugins, including one that finds banned functions (via Microsoft SDL)`

#### Version 3.0

While no decisions have been finalized, some ideas for consideration
include:

  - Better error handling
      - Automatic disabling of certain plugins based on the type of
        project (i.e. don't use PMD to scan C only projects)
  - Integration of OunceOpen tools
  - Integration of other OWASP projects ([Open
    Review](:Category:OWASP_Open_Review_Project "wikilink"), [Code
    Review](:Category:OWASP_Code_Review_Project "wikilink"), and
    [Orizon](:Category:OWASP_Orizon_Project "wikilink"))

[Category:OWASP Yasca Project](Category:OWASP_Yasca_Project "wikilink")