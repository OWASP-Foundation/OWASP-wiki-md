## Status Update - Lead Change, Copyright & License Issues (Oct. 31, 2013)

**Overall**: This project was identified as orphaned in 2009, and the
last change to the application was made in 2006. At this point it is
antiquated, relying on an obsolete version of the .NET framework.

**Lead Change**: I (Adam Caudill) have agreed to assume the lead of this
project, and will try to make it relevant again. How this project will
evolve going forward is still up in the air (see below for the main
complicating factor), and it will take some time to get the project to a
point where it's running smoothly.

**Copyright & License**: While the stated intention of the submitted
application was that it was an open-source project, the FAQ.html and
license.txt files indicate otherwise; the FAQ.html makes it very clear
that this is *not* an open-source project. As such, the existing code
can not be used going forward - to progress with this project will
require a complete rewrite, and a move to an OSI license.

**License Going Forward**: All future work will be licensed under the
Apache 2.0 license.

**Language & Platform Choice**: The current application is built on an
obsolete version of the .NET framework, though primarily targets the
Mono implementation. I am debating what would be most friendly for users
of the new version - Ruby, or .NET/Mono as the old version was. Ruby has
a better open-source ecosystem, though isn't ideal for Windows users
that typically prefer GUI-based tools.

If the decision to use Ruby is made, consideration needs to be given to
what will be needed for Windows users to get the application running
quickly and painlessly as possible.

**Github Repo**: I will be submitting the request for a Github repo to
be created soon, once a few more decisions are made. Once the repo is
available, the initial work will be in building out the Wiki with
details on design and implementation - that design work will be
completed prior to the start of development.

**Versioning**: The current application is versioned as "0.0.0.0" - the
new application will start at version "0.1.0"

\--[Adam Caudill](User:Adam_Caudill "wikilink")
([talk](User_talk:Adam_Caudill "wikilink")) 12:27, 31 October 2013 (CDT)