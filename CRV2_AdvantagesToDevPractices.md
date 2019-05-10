## Advantages of Code Review to Development Practices

Integrating code review into your companies development processes can
have many benefits that will be explored below. Some of these benefits
depend upon the tools you use to perform code reviews, how well that
data is backed up, and how well those tools are used. The days of
bringing developers into a room and displaying code on a projector,
whilst recording the review results on a printed copy and behind us,
many tools exist to make code review more efficient and to track the
review records/decisions. When the code review process is structured
correctly, the act of reviewing code can provide educational, auditable
and historical benefits to any organization.

The following provides a list of benefits that a code review procedure
can add to development team.

### Provides an Historical Record

If any developer has joined a company, or moved teams within a company,
and had to maintain or enhance a piece of code written years ago, one of
the biggest frustrations can be the lack of context the new developer
has on the code. Various schools of opinion exist on code documentation,
both within the code (comments) and external to the code
(design/functional docs, wikis, etc), opinions ranging from
zero-documentation tollerance through to near-NASA level documentation
where the size of the documentation far exceeds the size of the code
module.

If you think about the discussions that occur during a code review, many
of these discussions, if recorded, would provide valuable information
(context) to module maintainers and new programmers. From the writer
describing the module along with some of their design decisions, to each
reviewers comments, stating why they think one SQL query should be
restructured, or an algorithm changed, there is a development story
unfolding in front of the reviewers eyes which can (and should) be used
by future coders on the module, who are probably not involved in the
review meetings.

Capturing those review discussions in a review tool automatically, and
storing them for future reference, will provide the development
organization with a history of the changes on the module which can be
queried at a later time by new developers. These discussions can also
contain links to any architectural/functional/design/test
specifications, bug or enhancement numbers, etc.

### Verification Change has been Tested

When a developer is about to submit code into the repository, how do you
know they have sufficiently tested it? Adding a description of the tests
they have run (manually or automated) against the changed code can give
reviewers (and managment) confidence that the change will work and not
cause any regressions. Also by declaring the tests the writer has ran
against their change, the author is allowing reviewers to suggest
further testing that may have been missed by the author.

In a development scenario where automated unit or component testing
exists, the coding guidelines can require the developer include those
unit/component tests in the code review. This again allows reviewers
within this type of automated environment to ensure the correct
unit/component tests are going to be included in the environment,
keeping the quality of the continious intergration.

### Coding Education for Junior Developers

After you learn the basics of a language and read a few of the best
practices book, how can you get good on-the-job skills to learn more?
Besides buddy coding (which rarely happens and is never cost effective)
and training sessions (brown bag sessions on coding, tech talks, etc)
the design and code decisions discussed during a code review can be a
learning experiance for junior developers. Many experianced developers
may admit to this being a two way street, where new developers can come
in with new ideas or tricks that the older developers can learn from.
Altogether this cross polination of experiance and ideas can only be
beneficial to a development organization.

### Familiarization with Code Base

When a new feature is developed, it is often integrated with the main
code base, and here code review can be a conduit for the wider team to
learn about the new feature and how it's code will impact the wider
product. This helps prevent functional duplication where separate teams
end up coding the same small piece of functionality.

This also applies for development environments with silo'ed teams. Here
the code review author can reach out to other teams to gain their
insight, and allow those other teams to review their code, and everyone
then learns a bit more about the company's code.

### Pre-warning of Integration Clashes

In a busy code base there will be times (especially on core code) where
multiple developers can be writing code affecting the same module. Many
people have had the experiance of cutting the code and running the
tests, only to discover upon submission that some other change has
modified the functionality, requiring the author to recode and retest
some aspects of their change. Spreading the word on upcoming changes via
code reviews gives a greater chance of a developer learning that a
change is about to impact their upcoming commit, and development
timelines, etc, can be updated accordingly.

### Coding Guidelines Touchpoint

Many development environments have coding guidelines which new code must
adhere to. Coding guidelines can take many forms, but it's worth
pointing out that security guidelines can be a particularly relevant
touchpoint within a code review as unfortunately, though typically, the
security issues are understood by a subset of the development team.
Therefore it can be possible to include teams with various technical
expertise into the code reviews, i.e. someone from the security team (or
that person in the corner who knows all the security stuff) can be
invited as a technical subject expert to the review to check the code
from their particular angle. This is where the OWASP top 10 could be
enforced.