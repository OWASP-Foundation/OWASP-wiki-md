<noinclude></noinclude> __NOTOC__

## The Presentation

![Geer.straight.vi11.jpg](Geer.straight.vi11.jpg
"Geer.straight.vi11.jpg")Dan Geer’s Milestones: The X Window System and
Kerberos (1988), the first information security consulting firm on Wall
Street (1992), convener of the first academic conference on electronic
commerce (1995), the “Risk Management is Where the Money Is” speech that
changed the focus of security (1998), the Presidency of USENIX
Association (2000), the first call for the eclipse of authentication by
accountability (2002), principal author of and spokesman for
“Cyberinsecurity: The Cost of Monopoly” (2003), co-founder of
SecurityMetrics.Org (2004), convener of MetriCon (2006-present), author
of “Economics & Strategies of Data Security” (2008), and author of
“Cybersecurity & National Policy” (2010). Creator of the Index of
Cyber Security (2011) and the Cyber Security Decision Market (2011). Six
times entrepreneur. Five times before Congress.


## Transcript

Application Security Matters Daniel E. Geer, Jr., Sc.D.

I am here today to talk about application security. By the time I'm
done, you may think that I have talked more around application security
than about it. Perhaps you are right, but bear with me. I am assuming
that each of you have heard all the exhortations to work smarter and
harder many times before, and have heard (and will be hearing) lot of
talks on secure methods as this meeting goes on.

Application security is a pervasive need because applications are
themselves now pervasive. Application security is a critical need
because applications are themselves now critical. Over the last three
years, much bile has been spilled in the press over institutions that
are too big to fail and how it must have been a conspiracy of dunces
that allowed those institutions to get that big. If application software
in the aggregate can be said to be an institution in and of itself, then
it is too big to fail. One only wonders what conspirators the press will
nominate when they get around to looking for a new set of dunces to
ridicule.

We are at or near the point where it is no longer possible to live your
life without having a critical dependence on software, even if you live
at the end of a dirt road but still occasionally buy nails or gasoline.

Everyone knows that the amount of data in the world is growing. Where
does that data come from? Data are the outputs of software, data are
nothing without software, and data volume is now so great that the data
that matter are too big to move -- meaning that your only knowledge of
those data will be what software tells you when you ask politely.
Data-centric activities that are too big to move seem naturally to be
too big to fail.

If biologic analogies move you, then I'd ask you to consider data as the
body and application software as the body's biggest organ, that is to
say application software is data's skin. It is the shape and color of
the skin that gets our attention when we are looking for a mate, and,
for many, how hard they are looking can be gauged by how much skin they
expose. The application software that is data's skin is likewise; the
most massaged data is the data with the most exposed application
software.

Many say that we know how to "build security in\[to\]" application
software, that it is simply some kind of weak will that explains why we
have insecure applications all around us. Others say that if and only if
the market likes the application's functionality is it worth
retrofitting some security into the application, that is to say that
security only matters once you have a customer base.

Applications are the only reason to have an Internet; without them, who
would care? At the same time, the Internet was not designed for security
-- and may I say "Thank God" for that. If the Internet had been designed
for security, we wouldn't be here not because the problem of application
security would have been solved at the outset but because the innovation
would not have come. The Internet was designed for resistance to random
faults, and that design worked. It worked so spectacularly that
innovation followed simply because the Internet did not depend on the
flawless functioning of every one of its moving parts. It was not
designed for resistance to targetted faults, which, as Laszlo Barabasi
showed, cannot be done at the same time as you are designing for
resistance to random faults. Further, there was no gatekeeper you had to
ask permission of to put new services on that Internet. There's no
government like no government.

The end-to-end principle was the single most important technical
decision made in building out the Internet. By putting no control policy
in the network, only transport functionality, the network became useful.
The present day drumbeat to put control policy into the network fabric
itself is so blatantly stupid that it isn't even wrong. Those who
propose making the network itself contain security policy are just
another breed of Communists, this time with the effete subtlety that
neither our Chief Executive nor our Congress has to nationalize critical
infrastructure, they just have to deputize it, by force and in private.

But, for the moment at least, the end-to-end principle generally holds.
It is, however, no longer the only principle we need as the nature of
applications on the Internet makes defining an "end" less clear than
once it had been. Under an end-to-end design rule, the two ends of any
conversation get to negotiate whatever security policy they like just as
they get to pick any network protocol that meets their needs.

That means application security is an end-to-end design issue, does it
not? Well of course it does, but those of us who want to retain the
freedom to tinker are running into a headwind and that headwind is the
increasing difficulty of defining what an "end" in "end-to-end" means.
The reasons for this are several, and all serious.

  - First, there are proxies; are they the end to which your security

regime guarantees trustworthy connection? If don't know about a certain
proxy exists, does that change your answer?

  - Second, what one sees on one's screen may be a complicated merging

of many applications and data sources; which one of them is the end? Are
they all ends? Does it matter that you can't tell where the bits came
from? Is plural marriage a good idea?

  - Third, in the original construction, the word "end" implicitly

meant "that which is trusted," and everthing between the ends was not
trusted. In applications today, this is not the case -- trust may be all
over the place, some of it misplaced, perhaps, but that is besides the
point.

Let me acknowledge here Marjory Blumenthal and Dave Clark whose thinking
on the end-to-end principle is especially instructive. As they pointed
out, the end-to-end principle made the assumption that the
communications system was not trustworthy whereas the endpoints were.
That the communications system might be unreliable was and is an
assumption that leads to good design choices. However, the idea that
endpoints are trustworthy needs some updating.

It may well be that the reframing should be not end-to-end but
trust-to-trust. In the original formulation, end-to-end meant
machine-to-machine or human-to-human. The idea was that the ends could
be trusted but the rest could not. Let's say that because there are new
attacks every day I don't trust my PC any more, then my PC can't be an
"end" in the end-to-end formulation. Put differently, what began as
"You're OK, I'm OK, but the network is dangerous" has become "I hope I'm
OK, I have to assume that you are hosed, and the network may make this
worse."

This, of course, brings us to the question of what is trust. My
definition of (a state of) "trust" is this: Confident anticipation
backed by effective recourse. The "confident anticipation" is the day to
day operational reality; I commit a job or some data to your computing
queue and I am confident that it will return in the manner I anticipate,
confident enough that I deploy no armed guards. The "effective recourse"
is that I actually do know enough about where that job or data is going
that should something go wrong I then would know what next to do to
force you to make me whole -- to get an effective recourse. This is the
antithesis of saying that everyone is my friend. Rudyard Kipling's poem
"If" is a jewel, but the cybersecurity practitioner's couplet is:

`    If neither foes nor loving friends can hurt you,`
`      If all men count with you, but none too much;`

Summing up what I have said so far, data is where the value is, winners
have the most data in motion whereas losers have too much, applications
are the skin on the data -- some more erotic than others, the Internet's
existence gives applications their universality and some applications
their raison d'etre, the end-to-end principle is about trust placement,
trust is not for sissies, and the central discipline of secure design is
that of choosing what failure modes you are prepared to tolerate.

At the same time, a design and its implementation can diverge. At least
since Hugh Thompson published his famous Venn diagram, we've known that
security flaw is in that part of the implementation that was not in the
design. It is from that realization that I give you what I know to be
the paramount rule of all security engineering: No Silent Failure.

We have nowhere to go but up with respect to a rule of "no silent
failure." The Verizon Data Breach Investigations Report shows that data
loss is overwhelmingly silent. Part of that silence is digital physics
-- if I steal your data, then you still have them, unlike when I steal
your underpants -- but the majority of that silence is that there is no
programmatic indicator of the data's cloning; it is like a (UNIX)
_fork_ operation, fast and cheap. \[As an historical aside, the late
Dennis Ritchie wrote that the "PDP-7's fork call required precisely 27
lines of assembly code."\]

But the most telling legacy of Dennis Ritchie was that C had data
structures, data structures that operated at a level that was just
barely high enough. I've come to view parsimony of expressiveness as a
talisman against silent failure. Let me quote Don Davis, whose code is
probably running on every computer in this room:

`    The network-security industry has produced lots of examples`
`    of over-rich expressiveness:  RACF, firewall rules, and .htaccess`
`    are my favorite examples.  I argue that in computer security`
`    applications, a language or UI should present a little _less_`
`    expressiveness than expert administrators will find necessary,`
`    so as not to help normal administrators to confuse themselves.`
`    The problem is that every security rule-set has to be long-lived`
`    and to change steadily.  If the rule-set's syntax allows for`
`    subtlety, then each rule-set's size and complexity tends only`
`    to grow, never to shrink.  This is because each security`
`    administrator will tend to avoid analyzing whatever subtleties`
`    have accumulated, and will instead blindly add special-case`
`    allowances and constraints, so as to avoid breaking whatever`
`    came before.  The typical result is an unwieldy rule-set that`
`    no human can understand, with unpredictable security holes.`
`    Here, as remedy, are two rules of thumb:  for security, avoid`
`    designing order-dependent syntax, and avoid recursive features,`
`    like groups of groups.  Such features seem useful and innocuous,`
`    but when administrators use them heavily, complexity mounts`
`    destructively.`

Don wrote that seven years ago. His distinction between programming
language and what an administrator uses may now be a distinction without
a difference, but that does not disable his point; it strengthens it.
PERL and Ruby and Java have too many ways to express the same thing, to
do the same thing, and they brag about how "there is always another
way." Each of the three are Turing complete. Greater expressiveness
seems to be the way things are going.

The work being done by Sergey Bratus, et al., at Dartmouth in the
"Langsec" group is instructive here. Quoting from their home page,

`    The Language-theoretic approach (LANGSEC) regards the Internet`
`    insecurity epidemic as a consequence of ad hoc programming of`
`    input handling at all layers of network stacks, and in other`
`    kinds of software stacks.  LANGSEC posits that the only path`
`    to trustworthy software that takes untrusted inputs is treating`
`    all valid or expected inputs as a formal language, and the`
`    respective input-handling routines as a recognizer for that`
`    language.  The recognition must be feasible, and the recognizer`
`    must match the language in required computation power.`

`    When input handling is done in ad hoc way, the de facto`
`    recognizer, i.e., the input recognition and validation code`
`    ends up scattered throughout the program, does not match the`
`    programmers' assumptions about safety and validity of data,`
`    and thus provides ample opportunities for exploitation.`
`    Moreover, for complex input languages the problem of full`
`    recognition of valid or expected inputs may be UNDECIDABLE,`
`    in which case no amount of input-checking code or testing will`
`    suffice to secure the program.  Many popular protocols and`
`    formats fell into this trap, the empirical fact with which`
`    security practitioners are all too familiar.`

`    Viewed from the venerable perspective of Least Privilege, ...`
`    computational power is privilege, and should be given as`
`    sparingly as any other kind of privilege to reduce the attack`
`    surface.  We call this ... the Minimal Computational Power`
`    Principle.`

`    We note that recent developments in common protocols run`
`    contrary to these principles.  In our opinion, this heralds a`
`    bumpy road ahead.  In particular, HTML5 is Turing-complete,`
`    whereas HTML4 was not.`

There is a parallel between Bratus' "weird machine" construct and my own
training in statistical computation. When you look at the numerical
stability of a statistical computation you posit that the result of the
computation is correct for some problem and you measure how different
the problem that you gave is from the problem whose solution you got. As
Young, Boebert, & Kain said, "If a program has not been specified, it
cannot be incorrect; it can only be surprising." Those "weird machines"
have not been specified, they've been discovered, and that includes
discovery of weird machines in standard protocols, which Marsh Ray and I
enumerated in our "Vulnerable Compliance" talk.

The Robustness Principle, as written by Jon Postel in RFC 793, is to "be
conservative in what you send, liberal in what you accept." That
principle explains why it is that browsers tolerate so much bad HTML
which, in turn, explains why so much bad HTML continues to be written.
Or Javascript. Or you-name-it. Both the Langsec folks and I think it is
time to simply repeal Postel's Law. Just as the most ready way to put
money on the bottom line is to not spend it, the most ready way for the
browser to be less vulnerable to input-based attacks is for it to be
unforgiving. This goes for server-side code, too, of course. Until that
repeal, Rik Farrow's comment that the market leading browser is the most
dangerous program ever written still stands.

There is a growing interest in DevOps. As a strategy, DevOps
intentionally merges programming and administration, though this merger
is not designed for limiting expressiveness but rather to "reduce the
scope of changes" based on "the idea that all elements of a technology
infrastructure can be controlled through code." If true, the latter --
that all elements of an infrastructure can be controlled through code --
makes cybersecurity the only game in town. As it happens, Sandy Clark's
thesis work under Matt Blaze analyzes frequent deployment as a security
tool, that is to say how releasing code often enough that your
opponents' ability to analyze your code is thwarted by what she calls
"the Honeymoon Effect" -- which can be restated as when attack
development has a cycle time then you just modify your apps using a
shorter cycle time. And then you win. Later today, Josh Corman will work
to convince you that it is possible to write and deploy secure code at,
as he says, ludicrous speed. Perhaps as you listen to Josh's talk you
can ask whether constant sprints at ludicrous speed are in fact (1)
inherent limitations on expressiveness thus precluding error, (2) proof
by demonstration of the Honeymoon Effect, (3) a way to simply minimize
the otherwise long wait for code fixes to vulnerabilities found in the
field, or (4) something else altogether.

This brings us to cloud computing which I can't help but think of as a
variation on the theme of timesharing. In a blog about how Seattle is
building a planet-wide dominance in cloud computing, the author made
this assertion:

`    [There is an] important, often overlooked difference between`
`    cloud computing and old-school time-share computing: minimal`
`    bureaucracy between users and the cloud.  Timeshare typically`
`    allocated scarce resources via a bureaucratic process.  In the`
`    cloud, anybody with $5 can be the IT manager of their own`
`    massive compute facility, at least for a little while.`

While it is completely unfair of me to pick on that one paragraph,
here's where an economist would say: Price Allocates Scarcity. It is not
as if cloud computing is forgoing bureaucracy out of some social
principle. But to the point of this meeting, I'd be very interested in
some one of you doing a thoughtful, real-numbers analysis of the impact
of cloud computing's cheapness on code bloat. Chris Wysopal, co-founder
of Veracode, has observed that the size of applications tends to rise
after they are moved into the cloud precisely because space becomes too
cheap to meter -- developers link against any library that contains even
one call they care about and, in any case, it's faster to just include
everything. Bloat like that doesn't matter to anyone except, perhaps, us
security people, and how we are supposed to measure it seems a research
grade problem to me.

Of course, the Software as a Service (SaaS) model has something
important going for it from our security point of view: when your users
stop using a copy of your software you get to stop pleading with them to
take their updates -- you can just force it down their throat. Think of
that as fluoridating the water supply instead of begging people to not
eat sweets. The security possibilities of Software as a Service are real
and unmistakable. Marcus Ranum's position these days is that if we were
really serious, then we would

`    Switch the whole planet from "you own this software" to "all`
`    software is a service" and put in place an app store model for`
`    everything (with the proviso that mission critical systems`
`    could opt out if payment was escrowed far enough in advance).`
`    Get the whole planet running a small common set of codebases`
`    instead of the chaos of crap we're wading around in.`

As it happens, I pretty much disagree with all of his comment but it
\*is\* a coherent idea that \*does\* lead in an identifiable direction
that \*can\* be imagined. It may even be the direction that we (the
capital-W "We") are going as by now everyone has seen the figures for
smartphone sales versus computer sales. Remember that a cell phone
network is not a public Internet and that a device that only works on
such a network is not a general purpose computer. This triplet of ideas,
that the smartphone is the new endpoint, that appstores are the only
suppliers, and that software is a service not a product leads to the end
of the general purpose computer as a consumer durable.

I've written about this as has Cory Doctorow; let me read a litte of
Cory's commentary from his speech to the Chaos Computer Congress this
past December in Berlin:

`    The triviality of [the] copyright [battles] tell you that when`
`    other sectors of the economy start to evince concerns about`
`    the Internet and the PC, that copyright will be revealed for`
`    a minor skirmish, and not a war.  Why would other sectors nurse`
`    grudges against computers?  Well, because the world we live`
`    in today is made of computers.  We don't have cars anymore,`
`    we have computers we ride in; we don't have airplanes anymore,`
`    we have flying Solaris boxes with a big bucketful of SCADA`
`    controllers; a 3D printer is not a device, it's a peripheral,`
`    and it only works connected to a computer; a radio is no longer`
`    a crystal, it's a general-purpose computer with a fast ADC and`
`    a fast DAC and some software.`

`    The grievances that arose from unauthorized copying are trivial,`
`    when compared to the calls for action that our new`
`    computer-embroidered reality will create.  Think of radio for`
`    a minute.  The entire basis for radio regulation up until today`
`    was based on the idea that the properties of a radio are fixed`
`    at the time of manufacture, and can't be easily altered.  You`
`    can't just flip a switch on your baby monitor, and turn it`
`    into something that interferes with air traffic control signals.`
`    But powerful software-defined radios can change from baby`
`    monitor to emergency services dispatcher to air traffic`
`    controller just by loading and executing different software,`
`    which is why the first time the ... FCC considered what would`
`    happen when we put SDRs in the field, they asked for comment`
`    on whether it should mandate that all software-defined radios`
`    should be embedded in trusted computing machines, ... whether`
`    every PC should be locked, so that the programs they run are`
`    strictly regulated by central authorities.`

Cory is laying out for us yet another evidence that cyber security, or
at least its tools, matter. In a sense, our longstanding wish to be
taken seriously has come; we will soon reflect on whether we really
wanted that.

Remember, security is about control and governments everywhere want more
of it. Michael Jay Gross goes further in his "World War 3.0" column.
Though he does not remind us that the Internet is a ecosystem of
applications, he does show that at the nation state level the coming
treatment of the Internet will embody the majority of the seven deadly
sins. As both Cory and Michael suggest, if you think security technology
is important now, you ain't seen nothing yet.

I would suggest that cyber security is like any other ecosystem and that
predators and prey evolve in response to each other. Under the usual
terminology of evolutionary biology, evolution shows itself as a series
of long quiet periods separated by shorter periods of change, what is
called "punctuated equilibria." Sentience on the part of the competing
life forms only makes the clock run faster; the overall dynamic remains
the same. There have been, to my count, three great punctuations that
bring us here today. You and I owe the existence of our field to the
first, which was the sudden appearance of a TCP/IP stack in Microsoft
Windows. That stack was all in all a good thing to have, but it exposed
an operating system designed for a single owner/operator on, at most, a
private net to a world in which every sociopath is your next door
neighbor. The attack rate had a sudden and profound acceleration
discontinuity much like that when they light the solid fuel on the Space
Shuttle.

The second punctuation came perhaps as much as five years ago when the
population of attackers changed over from braggarts to professionals.
Because braggarts are paid in bragging rights, their discoveries become
common knowledge quickly. Professionals, however, are paid in money and
their discoveries are intellectual property, ergo their discoveries do
not become common knowledge until they have been milked of all the
income they can produce. Put differently, the better our opponents are
the less we know about how they work -- a fact true both in
cybersecurity and in the intelligence game.

The third punctuation, in which we are presently swimming, is the very
thing that Cory and I talked about -- the death of the general purpose
computer. This death does very much make Marcus's prescription a likely
outcome, but let me remind you that this is absolutely an example of
trading freedom for security and if you are widely read, then you will
have absolutely zero confusion as to how that trade will eventually play
out whether your muse is Benjamin Franklin, Emiliano Zapata, or Edward
Gibbon.

If there is to be a fourth punctuation, it is the turning over of our
protections entirely to machines. I spoke about this at length in
February at the Suits and Spooks meeting and wrote about it in two
recent IEEE Security & Privacy columns. The core argument is simply that
when everything is connected all the time, the human cybersecurity
practitioner is largely a liability, not a failsafe.

The source of risk is dependence, especially dependence on expectations
of system state. As a term of biology, the virulence of a disease is a
measure of how fast it moves from me to you. Virulence in an infectious
organism is, interestingly, a marker for how good your immune system is
insofar as if your immune is quick and efficient at killing Microbe X,
then evolutionary selection pressure on Microbe X will cause it to move
faster (be more virulent) in proportion to how good your immune system
is.

Several years ago, I looked up the major virus attacks on cybersecurity
and, in particular, looked for the doubling time of the infected
population. I plotted the doubling time on a calendar timeline and found
a hyperbolic fall-off, i.e., virus pandemic events became ever rarer but
for those that did occur, their doubling times fell away as if on a
hyperbolic curve. This is exactly what one would expect in the biologic
world where an infectious agent and its target species co-evolve. On the
one hand, the immune system of the target gets better so episodes of
infection become locally rarer over time. Simultaneously, those episodes
that do occur involve a mutated infectious agent that displays much
higher virulence with each pandemic outbreak.

If you argue that evolution is a force that does not depend on the
choice of its participants to play ball but is, instead, operating
without either their cooperation or their sentience, then one must
conclude that computer infections will tend to follow the same general
life cycle of decreasing frequency balanced by increasing virulence.

In other words, by the time a truly virulent strain of something
appears, our dependence on the to-be-infected infrastructure will be so
complete as to guarantee collapse.

But let us flatly assume that Software as a Service is the future. As
someone who sees a lot of business plans, I can assure you that step 5
in nearly all of them involves renting space from Amazon, Microsoft, or
somebody and that nearly none of them include in their capital
requirements the cost of building out data centers. Software as a
Service is very much more likely to be closed source than open -- and
may I add that you will have little way to determine if a claim of
open-ness is valid when, for example, you don't have a way to compile
that source or look at the binaries that the SaaS vendor is actually
running.

Closed source can be helpful to security if the programmers take
security seriously, and harmful if they don't. While Eric Raymond is all
but entirely correct that "given enough eyeballs, all bugs are shallow,"
he is nevertheless wrong that this is a fact-of-Nature requirement on
how to build code if, in particular, the user cannot actually see the
code. SaaS, in other words, can single-handedly demote the decompiler as
the best attack tool and put the fuzzer in its place.

When you believe that your code won't actually be seen by its users
because they are only buying it as a service, your tendency will be to
compete not on ease of installation, update, field supportability or
integrability, but rather on performance and the latency of
re-configuration. Your code will get more idiosyncratic and possibly
more clever. Two engineers who have built big systems have something to
say about this; first, Mike O'Dell, the founding Chief Scientist of
UUNet and now a venture capitalist, said:

`    Left to themselves, creative engineers will deliver the most`
`    complicated system they think they can debug.`

while Brian Kernighan, the co-inventor of C, said:

`    Debugging is twice as hard as writing the code in the first`
`    place.  Therefore, if you write the code as cleverly as possible,`
`    you are, by definition, not smart enough to debug it.`

Mitja Kolsek suggests that the way to think about the execution space on
the web today is that the client has become the server's server. You are
expected to intake what amount to Remote Procedure Calls (RPCs) from
everywhere and everyone. You are supposed to believe that trust is
transitive. That is what Javascript is. That is what Flash is. That is
what HTML5 is. That is what every embedded Browswer Help Object (BHO)
is.

. If you grab .
s7.addthis.com/js/250/addthis_widget.js\#pubid=xa-4f27f6b13d07e361 .
you will get a file that in turn pulls down javascript from . hundreds
of sites including, for example, . vkontakte.ru, vkrugudruzei.ru,
vybrali.sme.sk

If I were to walk up to you and say that you must open your machine to
RPCs just because I say so, then you would kick me out of your office.
But that is precisely what is being asked -- to accept RPCs all day,
every day, so that the showmen in both industry and government can
deliver their vision of the all singing, all dancing "user experience."
A cavalcade of RPCs can certainly be configured to be not only
performance enhancing but security enhancing, but security enhancement
is not the default outcome.

If you think that this is a small matter, think again. According to the
HTTP Archive, over the course of 2011 the average size of a single web
page grew by 25% to 784KB and the average number of requests required to
load that page increased 13% to 87. More to my point, the average size
of the Javascript in that page increased by 45%, in one year(\!).
Because I personally refuse Javascript, I can very much confirm that for
me, the person who doesn't accept incoming RPCs, the WWW is palpably
shrinking. That is my fault, but I can at least report it.

Instead of calling me a crank, at least for the moment, remind yourself
that when, in the name of security, we "lock down" an operating system,
we do so by removing functions, by reducing the choice set of what might
be running, by shrinking the attack surface. The reason that the Web
browser is the leading entry point for malware is the number of choices
that a browser offers up to whomever is at the other end.

Lockdown is just one aspect of what someone might do in the name of
hardening. Let me make a point about that, however. Using the
terminology of metallurgy, we can harden in one of two ways. On the one
hand, we can pick a layer in the stack or wherever and case harden that.
If we make the whole product hard, it becomes brittle -- we have to make
only the surface hard. On the other hand, we can make the metal shatter
resistant but at the price of it being malleable enough that if I hit it
with a hammer it certainly will not shatter but it will ding. Which kind
of hardening we want depends on the kinds of impacts you expect it to be
exposed to when in actual use.

Auto-update of software is a great thing so long as it is capable of
dealing with local anomalies. Generally speaking, you get a better
result if you don't try to analyze too much, just replace the whole
software package. This is a strategy that is, to a degree, hardening of
the embrittlement sort as a regular auto-update that does what is in
effect synchronization means that both update and repair can use the
same tool and you don't really have to know whether you are updating or
repairing. However, if anyone else that doesn't like you ever gets
control of your auto-update mechanism, then it will be hard to ever pick
up the pieces well enough to truthfully say that you got back to where
you were before the strike.

Just don't forget that total cycle time for a round of updates matters.
The coming Smart Grid, is, after all, an application layered on top of
the biggest machine in the world. Kelly Ziegler's numbers indicate that
should it be necessary to do a total update of the firmware for all
households on a fully deployed Smart Grid it would take a year or so.
What might we do differently?

A strategy of intrusion tolerance is different. It begins with the
assumption that your software package will be dinged often but, if you
did a good job in design, the dings won't make the package unusable.
This is an uglier process in practice, but under some scenarios it is
more survivable. Any of you who work for large firms will have had some
visibility if not input into your disaster recovery plan. If that
includes your software base, which I hope it does, then the DR plan
probably includes mechanisms for diminished operation, which is
precisely what I am talking about. In a way, the Microsoft Address Space
Layout Randomization (ASLR) is exactly a strategy for intrusion
tolerance; you may still get dinged but the attacker will have less
probability of getting a shatter. Just an ugly ding.

Perhaps the most important thing you can do for us all is to ensure that
there is no silent failure. This means instrumentation, it means well
designed surveillance regimes, it means an attention to the kind of
metrics that come out of an airplane's black box, it means keeping
things simple enough that, well, there are fewer surprises, and it may
mean changing how you think about how you make tradeoffs. Repeating
Kernighan, if you write the code as cleverly as possible, you are, by
definition, not smart enough to debug it.

Finally, because security is not composable (and may never be), be very
careful where the code you reuse comes from. Every time I see a page
larded up with more domains than I have fingers, I plan never to visit
them again. I know you have to compete; I ask that you not end up in a
race to the bottom.

And, perhaps above all else, remember that all security technology is
dual use.

There is never enough time. Thank you for yours.

\-----------------8\<------------cut-here------------8\<-----------------

reference material

"Basics of the Unix Philosophy," www.faqs.org/docs/artu/ch01s06.html

"Build Security In," buildsecurityin.us-cert.gov

Barabasi L & Albert R, "Emergence of scaling in random networks,"
Science, v286 pp509-512, 15 October 1999.

Bratus S, Locasto ME, Patterson ML, Sassaman L, & Shubina A, "Exploit
Programming: from Buffer Overflows to Weird Machines and Theory of
Computation," USENIX Association ;login:, v36 n6, December 2011.

Clark DD & Blumenthal MS, "The End-to-End Argument and Application
Design: The Role of Trust," TPRC, 2007.

Clark S, Blaze B, Frei S & Smith J, "Familiarity Breeds Contempt: The
Honeymoon Effect and the Role of Legacy Code in Zero-Day
Vulnerabilities," ACSAC, 6-10 December 2010.

DARPA internet program, RFC 793, "Transmission Control Protocol
Specification," September 1981.

Davis, DT, personal communication, 27 January 2005.

Doctorow C, "Lockdown: The Coming War on General-Purpose Computing,"
keynote speech, Chaos Computer Congress, Berlin, 26 December 2011.

Farrow, R, "Internet Explorer is the most dangerous program ever
written," 30 June 2004.

Freedom to Tinker is hosted by Princeton's Center for Information
Technology Policy. freedom-to-tinker.com

Geer D, "People in the Loop: Are They a Failsafe or a Liability?,"
Invited Talk, Suits and Spooks, Washington DC, 8 February 2012. Geer D,
"Power. Law.," For Good Measure, IEEE Security & Privacy, v10 n1
pp94-95, January/February 2012. Geer D, "More or Less," Clear Text, IEEE
Security & Privacy, v10 n1 p96, January/February 2012.

Geer DE & Ray M, "Vulnerable Compliance," USENIX Security Symposium,
Washington, D.C., August 12, 2010.
www.usenix.org/events/sec10/tech/tech.html\#Geer

Gross MJ, "World War 3.0," Vanity Fair, May 2012.

Kolsek M, personal communication, 10 February 2012.

Nilsson E, "Seattle's Growing Advantage in The Cloud," 3 August 2010.
www.xconomy.com/seattle/2010/08/03/seattles-growing-advantage-in-the-cloud

Raymond E, "The Cathedral and the Bazaar," O'Reilly Media, 1999.

Ritchie DM, "The Evolution of the Unix Time-sharing System," Bell
Laboratories Technical Journal, v63 n6/2 pp1577-1593, October 1984.

Saltzer J, Reed D, & Clark DD, "End-to-End Arguments in System Design,"
ACM Transactions on Computer Systems, v2 n4 pp277-288, November 1984.

Thompson HH & Whittaker JA, "Testing for Software Security," Dr. Dobbs
Journal, v342 pp24-34, November 2002.

"Web Pages Are Getting More Bloated, and Here's Why,"
royal.pingdom.com/2011/11/21/web-pages-getting-bloated-here-is-why (
above based on "Trends," www.httparchive.org/trends.php )

"Verizon 2012 Data Breach Investigations Report," 22 March 2012.

Wysopal C, personal communication, 12 January 2012

Young WD, Boebert WE, & Kain RY "Proving a Computer System Secure,"
Scientific Honeyweller, v6 n2 pp18-27, July 1985.

Ziegler K, "Smart Grid, Cyber Security, and the Future of Keeping the
Lights On," USENIX Security Symposium, August 13, 2010.

-----

They that can give up essential liberty to obtain a little temporary
safety deserve neither liberty nor safety.

`           -- Benjamin Franklin`

Better to die on one's feet than to live on one's knees.

`           -- Emiliano Zapata`

In the end, more than freedom, they wanted security. They wanted a
comfortable life, and they lost it all -- security, comfort, and
freedom. When the Athenians finally wanted not to give to society but
for society to give to them, when the freedom they wished for most was
freedom from responsibility, then Athens ceased to be free and was never
free again.

`           -- Edward Gibbon`

<noinclude></noinclude>