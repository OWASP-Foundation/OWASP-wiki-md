# GA (General Availability) Planning

  - Proposed General Availability Criteria:

<!-- end list -->

1.  100% Unit tests pass.
2.  All classes must have unit tests.
3.  Test coverage must test 100% of the "sunny day" paths and at least
    80% of the total paths. (This will require using some sort of code
    coverage during unit testing.)
4.  At least 3 independent adoptions of the previous beta RC for the
    given release must provide their approval.
5.  All public features must be documented in terms of:
    1.  API documentation (e.g., Javadoc)
    2.  Document when this feature should be considered / used
    3.  Example(s) showing how this feature should be used
6.  Once all these things are completed, we open it up to a formal vote
    by the ESAPI-Users group and then it is only made GA if they
    approve. (I would say by at least 60%, but your opinion may vary.)

If not obvious, the reason for adding \# 4 & 6 is that generally UAT is
done by individual clients using said software. In this case, unless we
can get the unanimous ESAPI community consensus on a UAT (e.g., if the
ESAPI-Users wrote up a formal test plan that needed to be tested
against) this is probably the best we can do.

  - Other Suggestions (Mike B):

This is in my mind further rationale for perhaps even stopping with new
features and starting backfilling documentation and tests if needed. I
urge people to examine the ESAPI for PHP adapter that one can download
from its Google Code repository, and to read the ESAPI design patterns
doc, and to re-read Jeff's recent email with some hints about rolling
out controls in phases etc., and to dig a little bit in the ESAPI book
draft there are a small number of "nuggets" along these lines, in e.g.
the user/auth sections for this kind of higher-level guidance e.g. step
one map current wrappers to ESAPI interfaces, then start extending user,
then ... Anecdotally for example I can report that taking the extended
factory pattern adapter route, and building it out in a phased approach,
where I as the security guy own the wrapper code, and then the
development team uses it according to a cookbook that I write and
maintain for them, COMPLETELY puts the security guy in control in terms
of determining the quality of the ESAPI security control that's about to
be rolled out. I write a new wrapper function for something, and then I
add 6-12 proper security function tests (i.e. a few expected successes,
then a whole bunch of expected failures) for each with test data that is
customer-specific. If ESAPI's broken or not quite there yet, I don't put
the wrapper function into the adapter until it's right.

  - Other Suggestions (Ed S):

Open source projects need to "Release Early, Release Often"
(http://catb.org/esr/writings/homesteading/cathedral-bazaar/ar01s04.html).
If we wait until it's perfect it will never happen (I have plenty of
code rotting on my disk to prove this).

  - Other Suggestions (Beef):

I think that where we are right now is acceptable, and if anything,
taking it back to a pre 1.0 release level would have the same basic
effect without the negative stigma that goes along with labeling
software as "beta" quality.

My alternate proposal would be to prefix the current ESAPI version with
a 0.

So esapi 0.1.4.2 and esapi 0.2.0 respectively.

This allows us the luxery of time before a full 1.0 GA release of the
API and carries a positive stigma with the development world. Plenty of
libraries are in use and have been in use for years before they ever get
to a 1.0 release. Had those same libraries been labeled beta, I highly
doubt they would have gotten the adoption and implementation rates that
they did (an example would be just about an utility that has ever been
released for \*nix)

  - More Comments (from Mike B)

There needs to be at least one "release" version, however you want to do
it. The cat's out of the bag, having two "major.minor" releases (1.4 and
2.0) already in the wild. So, plan on a 3.0 if there are major things
that you think are still lacking. It'd be great to have such a product
roadmap or have this survive that long before someone productizes
this/something equivalent and this project becomes marginalized.
Hopefully there will be a surge of open source resources before that
happens, a la Red Hat model.

Not having at least one "good" (before jump on the use of this word,
please read next paragraph after carefully reading this one) baseline
takes the legs out from under this project. The argument that any use of
any variation or extension or adaptation of ESAPI is at least designed
for/based on a proven stable definitive solution goes away. The basic
argument in my neck of the woods against using OWASP documents and tools
in general is that customers don't ask for them, and the basic
explanation of why customers don't ask for them is that the perception
is they are all just kind of fun science experiments with perhaps little
bits of helpful things here and there, but that's it. Not trying to be
harsh or mean, I have had this feedback nearly verbatim many times, and
there were those earlier emails on this list saying that it's important
to listen to feedback.

So, adoption is really based on perception, not technical merit.
Technical stuff can always be fixed, can always add another function or
some such. The business (no-technical) stuff can't, can't make someone
like something or someone. This toolkit is so specialized, this is WAY
more specialized that even OpenSSL which keeps being mentioned, there is
never going to be the same uptake as some generic library or widget,
holding it to that sort of a measure is a standard that's not
achievable. I wrote earlier, you guys aren't realizing how much magic
there is in what you've got so far. The current Java should be a 5.x
release or something, not exaggerating too terribly much. In my mind, so
what if it's not super-pretty for example from a generic design patterns
point of view. The goal of ESAPI is to help guard against data spills by
making it as easy as possible on the developer. Most of the "problems"
that I see on the lists are with ESAPI are due to lack of instruction,
of written down knowledge that can be transferred. A lot of the more
detailed problems talked about on this list, most new adopters won't hit
those for quite some time, if ever. When to use it. How to plan for its
use. How to roll it out. How to select combinations of controls to
target a level of assurance. What combinations of platforms will it work
on. On and on. Commercial products have ideas of "supported
configurations", where only usages according to their documentation are
supported by the company. Do that here and I guarantee that (1)any
immediate problems will be found faster than they are now, and
(2)problems will taper off dramatically.

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")