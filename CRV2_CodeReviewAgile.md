## Code Reviewing an Agile Project

If you are going to review an Agile Team project code, the best thing
that you can do is give this guide to that Team as early as possible and
most of your work will be done for you. Or better yet, integrate
yourself to the Team.

Code review must be done at least at the end of every user story and be
very fast in order to not introduce delays and detect any error as soon
as possible. It's better to do that in every commit to the code
repository. That is the reason that peer review is the prefered method
for agile code review. Nevertheless, as security review requieres some
extra specialization, perhaps the best way is to integrate the security
code reviewier with the Team.

These are some simple steps on how to integrate code reviews in an agile
project:

  - Configure your Continous Integration system to run static code
    analysis tools.
  - Train your team on this guide.
  - Train your team on OWASP TopTen.
  - Use this guide when doing Peer Review.
  - Determine the frequency of the review. A good place is at the end of
    every loop.
  - Keep in mind that besides the code, there is the test code.

## Some definitions about Agile

The Agile name is an umbrella for quite a lot of practices that range
from programming, to testing, to project management and everything in
between. There are many flavors of agile, perhaps as many as
practitioners. It is like an heterogeneous reference framework and you
are free to use what you want.

Agile has some key practices that could affect the way the code is
reviewed. First, when the review is done and then, the code itself.

Agile Development(AD) is well suited for code review, as two of its
practices are "pair programming" and "peer review". AD incorporates code
review in itself, in what traditionally was seem as another phase.

Agile blurs the difference between developing and testing, and so does
with code review. It is not an external activity. Agile tries to keep
the code testing and review as near as possible to the development
phase, there is no such thing as the develop, test, code review cycle.

It is a common practice to define short development cycles. At the end
of each one, all the code must be production quality code. Its
funtionality may be incomplete, but it must add some value. That affects
the review process as it must be continuous.

### Pair Programming

This technique is quite controversial, but when it is adopted it has the
benefits of making better code, as there is one programmer supervising
cooperatively the other one's work. If both programmers know this guide,
they will apply it continuously. In pair program there are 2 roles, the
programmer (pig) and the supervisor (chicken). Basically, what the
supervisor does is control the work of the programmer. In this process,
a code review might be part of it and it can be easily integrated since
the major responsibility of the supervisor is to regulate the
programmer’s work.

### Continuous Integration

It is a practice from eXtreme Programming (link to the book) based upon
that team programming is not a divide and conquer problem but a divide,
conquer and integrate problem and that integrate could be the hardest
step. In order to mitigate the impact, the integration should be as
frequently as there are commits to the repository. An automated task
becomes aware of any change and triggers the build and test process. If
there is any error, the committer get notified so he or she can fix it
before it accumulates with other errors.

### Peer Review

This one is enforced by the usage of tools like Jenkins that ask another
user for a code review before commiting to the versioning system.

### Testing

The role of testers... some people thinks that there is almost no place
for the traditional tester role. Automated testing requires a tester to
define the tests but not to execute them. This tester must be almost a
programmer or work with a programmer.

In AD, test is so fundamental, that the xDD pervades Agile, test first,
test earlier.

Agile projects tend to use a lot of automated testing, in order to
review an Agile Project, you will have to extend the review to the
tests.

Some guide taken from (I can't remember but searching...)

  - Are there enough tests?
  - Is the code covered by the tests? Code coverage measure main value
    is to find unused code.
  - Are there the trivial tests? They are as needed as any other test.
  - Are there commented out tests? Commented out tests means that some
    one made a test that the code could not pass or take a long time to
    run.
  - Are boundary conditions tested? These are the tests around maximum
    and minimum values or near a change in a condition.
  - Are bugs exhaustively tested? That is, is an off-by-one bug is
    found, are there boundary tests for that condition?
  - Are the test automatic? If the tests requiere manual intervention,
    they will not be run.
  - Do the tests conform to F.I.R.S.T.?

` Fast: a slow test is a candidate for removal, as it slows down the "make test, implement, test, refactor" cycle.`
` Independent: one test can not depend on the execution of another one, the order should not matter.`
` Repeatable: one test should give always the same result in any environment if nothing has changed in the code.`
` Self-validating: the result of a test should be Pass or Fail, nothing else. There should not be any manual intervention needed.`
` Timely: the test should be written before the code. That can not be detected with code review, but you can always see the logs of the versioning system.`

### Refactoring

Refactoring is the art of changing the code with out changing its
behavior. In order to refactor, there must exists a rich battery of
tests.

The problem with refactoring, is that thanks to the heavy testing, you
can trust that the interface does not change, but behind it, the code
can be very volatile. You have to review the code continously, another
argument for peer review and automatic static analysis.

## References and sources

Clean Code: A handbook for Agile Software Craftsmanship - Robert C.
Martin

Extreme Programming Explained: embrace change - Kent Beck with Cynthia
Andres

<http://groups.yahoo.com/group/foro-agiles/>

<http://martinfowler.com/articles/continuousIntegration.html>

<http://martinfowler.com/bliki/TestCoverage.html>

not used <http://refactoring.com/>

not used <http://dddcommunity.org/>

# I am not sure about keeping the following sections

### Clean Code and "Smells"

The agile community is very committed to code quality. A by product is
the concept of Clean Code and its smells, its very handy to be familiar
with this topic, ...

## The Agile Ecosystem

`   bdd----------------------------------------------------------------------+`
`    `

| |

`   tdd-------------------------------------------------------------+        `

|

| | |

`    +----+-->   pair programming --------+--> peer review -----> continuous integration`
`         `

| ( collective ownership ) |

`         +-->  individual programming ---+`

### The XDD

There are many agile practices related to what drives the development of
a project, what they have in common is that they could generate testing
code. As a security practicioner, there are two aspects of interest.
One, sometimes useful is called "test coverage" and it is automatically
calculated. 100% code coverage does not mean a good coverage neither a
60% a bad one. It is very difficult to measure the second aspect, the
quality of the test. There is possitive testing, that aims at the added
value of every piece of software and negative testing, related to bugs
and security.

#### Test Driven Development

TDD is the practice of making the test before coding, it is the extremme
application of the "test early" principle. The idea is that the code
always will be tested as the test predates the code itself. A very
important side effect is that it forces to simplify the code to make it
testeable. It could be very low level with very isolated components,
called "unit testing" and high level, when it tests clusters of
interrelated components, called "functional testing".

To read more about code coverage:
[1](https://www.owasp.org/index.php/Code_Review_Coverage)

#### Behavior Driven Development

This practice builds upon TDD, providing an interface to non-specialists
users, shaping the tests around full blown scenarios. As TDD, it
generates testing code.

#### Domain Driven Design

This practice consist of... It does not generate code itself, but the
architecture. It is very popular among the Agile people, so it is very
important to be familiar with. Perhaps the most useful concept is
"ubiquitous language".