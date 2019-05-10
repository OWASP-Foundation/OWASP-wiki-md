**AoC Candidate:** Rogan

**Project coordinator:** Andrew van der Stock

**Project Progress:** xx% Complete - [Progress
Page](OWASP_Autumn_of_Code_2006_-_Projects:_WebScarab_NG_-_Progress "wikilink")

## Background and Motivation

**History Behind Project**

WebScarab was originally designed by a group of people from the
webappsec list, with the lofty ambition of being a complete open-source
web application vulnerability scanner. Unfortunately, in code terms, it
got no further than checking in some slightly-modified code from the
WebSphinx spider project before interest waned, and the project
stagnated. While participating in the WebScarab design process, Rogan
Dawes was also working on a proxy-based tool called Exodus, both from a
need for such a tool, and in a desire to learn how to program in Java.
After the initial WebScarab effort stagnated, Rogan volunteered to
rewrite Exodus, and donate it to OWASP to replace the then-existing
spider code. This offer was accepted, and the current WebScarab was
born.

**Problem to be Addressed**

However, WebScarab still had its own share of problems. In the main,
those problems were as a result of its user interface, although there
were also some fairly fundamental design flaws too

The original WebScarab is a very rough tool. It has a large amount of
functionality, but in many cases, that functionality is only understood
by its author, and a very few others. This is because WebScarab does not
follow any published/recognised Human Interface Guidelines, and so that
functionality is not obvious, or even "discoverable" in many cases.

WebScarab NG is intended to be a substantial rewrite of the original
WebScarab code, focusing on providing a clean user interface that is
intuitive for a newcomer to start using, but still powerful enough to
serve the needs of the hardcore web application testers.

**Benefit to OWASP Members and Community**

The benefits to OWASP members, and the broader web application security
community should be obvious. Improved tools can ultimately translate
into more secure web applications.

## Goals and Deliverables

**Plan of Approach**

I have already got some fundamental parts of WebScarab NG written.
Specifically, WebScarab NG is already usable as an Intercepting Proxy. I
intend to start work on the remaining items as described in the
deliverables next.

**Deliverables**

The output of this project will be a WebScarab NG implementation, based
on the Spring Rich Client platform, supporting at least the following
features:

  - Intercepting Proxy, with the ability to control the proxy using a
    "stays on top" toolbar

<!-- end list -->

  - Spider

<!-- end list -->

  - Form extractor, that will present any forms identified in the HTML
    code for editing and submission by the operator

<!-- end list -->

  - Manual request (replay and/or create from scratch)

<!-- end list -->

  - Significantly improved session id analysis plugin (dynamic
    partitioning of session identifiers AFTER they have been collected)

<!-- end list -->

  - Improved scripting interface and hooks into functions

<!-- end list -->

  - Integrated search and compare functionality

## Risks and Rewards

**Main Risks**

**Rewards of Successful Project**