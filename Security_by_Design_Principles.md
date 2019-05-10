[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink") __TOC__

Architects and solution providers need guidance to produce secure
applications by design, and they can do this by not only implementing
the basic controls documented in the main text, but also referring back
to the underlying “Why?” in these principles. Security principles such
as confidentiality, integrity, and availability – although important,
broad, and vague – do not change. Your application will be the more
robust the more you apply them.

For example, it is a fine thing when implementing data validation to
include a centralized validation routine for all form input. However, it
is a far finer thing to see validation at each tier for all user input,
coupled with appropriate error handling and robust access control.

In the last year or so, there has been a significant push to standardize
terminology and taxonomy. This version of the Development Guide has
normalized its principles with those from major industry texts, while
dropping a principle or two present in the first edition of the
Development Guide. This is to prevent confusion and to increase
compliance with a core set of principles. The principles that have been
removed are adequately covered by controls within the text.

## Asset classification

Selection of controls is only possible after classifying the data to be
protected. For example, controls applicable to low value systems such as
blogs and forums are different to the level and number of controls
suitable for accounting, high value banking, and electronic trading
systems.

## About attackers

When designing controls to prevent misuse of your application, you must
consider the most likely attackers (in order of likelihood and
actualized loss from most to least):

  - Disgruntled staff or developers

<!-- end list -->

  - “Drive by” attacks, such as side effects or direct consequences of a
    virus, worm, or Trojan attack

<!-- end list -->

  - Motivated criminal attackers, such as organized crime

<!-- end list -->

  - Criminal attackers without motive against your organization, such as
    defacers

<!-- end list -->

  - Script kiddies

Notice there is no entry for the term “hacker.” This is due to the
emotive and incorrect use of the word “hacker” by the media. However, it
is far too late to reclaim the incorrect use of the word “hacker” and
try to return the word to its correct roots. The Development Guide
consistently uses the word “attacker” when denoting something or someone
who is actively attempting to exploit a particular feature.

## Core pillars of information security

Information security has relied upon the following pillars:

  - [Confidentiality](:Category:Confidentiality "wikilink") – only allow
    access to data for which the user is permitted
  - [Integrity](:Category:Integrity "wikilink") – ensure data is not
    tampered or altered by unauthorized users
  - [Availability](:Category:Availability "wikilink") – ensure systems
    and data are available to authorized users when they need it

The following principles are all related to these three pillars. Indeed,
when considering how to construct a control, considering each pillar in
turn will assist in producing a robust security control.

## Security architecture

Applications without security architecture are as bridges constructed
without finite element analysis and wind tunnel testing. Sure, they look
like bridges, but they will fall down at the first flutter of a
butterfly’s wings. The need for application security in the form of
security architecture is every bit as great as in building or bridge
construction.

Application architects are responsible for constructing their design to
adequately cover risks from both typical usage, and from extreme attack.
Bridge designers need to cope with a certain amount of cars and foot
traffic but also cyclonic winds, earthquake, fire, traffic incidents,
and flooding. Application designers must cope with extreme events, such
as brute force or injection attacks, and fraud. The risks for
application designers are well known. The days of “we didn’t know” are
long gone. Security is now expected, not an expensive add-on or simply
left out.

Security architecture refers to the fundamental pillars: the application
must provide controls to protect the confidentiality of information,
integrity of data, and provide access to the data when it is required
(availability) – and only to the right users. Security architecture is
not “markitecture”, where a cornucopia of security products are tossed
together and called a “solution”, but a carefully considered set of
features, controls, safer processes, and default security posture.

When starting a new application or re-factoring an existing application,
you should consider each functional feature, and consider:

  - Is the process surrounding this feature as safe as possible? In
    other words, is this a flawed process?
  - If I were evil, how would I abuse this feature?
  - Is the feature required to be on by default? If so, are there limits
    or options that could help reduce the risk from this feature?

Andrew van der Stock calls the above process “Thinking Evil™”, and
recommends putting yourself in the shoes of the attacker and thinking
through all the possible ways you can abuse each and every feature, by
considering the three core pillars and using the STRIDE model in turn.

By following this guide, and using the STRIDE / DREAD threat risk
modeling discussed here and in Howard and LeBlanc’s book, you will be
well on your way to formally adopting a security architecture for your
applications.

The best system architecture designs and detailed design documents
contain security discussion in each and every feature, how the risks are
going to be mitigated, and what was actually done during coding.

Security architecture starts on the day the business requirements are
modeled, and never finishes until the last copy of your application is
decommissioned. Security is a life-long process, not a one shot
accident.

## Security principles

These security principles have been taken from the previous edition of
the OWASP Development Guide and normalized with the security principles
outlined in Howard and LeBlanc’s excellent *Writing Secure Code*.

### *[Minimize attack surface area](Minimize_attack_surface_area "wikilink")*

Every feature that is added to an application adds a certain amount of
risk to the overall application. The aim for secure development is to
reduce the overall risk by reducing the attack surface area.

For example, a web application implements online help with a search
function. The search function may be vulnerable to SQL injection
attacks. If the help feature was limited to authorized users, the attack
likelihood is reduced. If the help feature’s search function was gated
through centralized data validation routines, the ability to perform SQL
injection is dramatically reduced. However, if the help feature was
re-written to eliminate the search function (through better user
interface, for example), this almost eliminates the attack surface area,
even if the help feature was available to the Internet at large.

### *[Establish secure defaults](Establish_secure_defaults "wikilink")*

There are many ways to deliver an “out of the box” experience for users.
However, by default, the experience should be secure, and it should be
up to the user to reduce their security – if they are allowed.

For example, by default, password aging and complexity should be
enabled. Users might be allowed to turn these two features off to
simplify their use of the application and increase their risk.

### *Principle of [Least privilege](Least_privilege "wikilink")*

The principle of least privilege recommends that accounts have the least
amount of privilege required to perform their business processes. This
encompasses user rights, resource permissions such as CPU limits,
memory, network, and file system permissions.

For example, if a middleware server only requires access to the network,
read access to a database table, and the ability to write to a log, this
describes all the permissions that should be granted. Under no
circumstances should the middleware be granted administrative
privileges.

### *Principle of [Defense in depth](Defense_in_depth "wikilink")*

The principle of defense in depth suggests that where one control would
be reasonable, more controls that approach risks in different fashions
are better. Controls, when used in depth, can make severe
vulnerabilities extraordinarily difficult to exploit and thus unlikely
to occur.

With secure coding, this may take the form of tier-based validation,
centralized auditing controls, and requiring users to be logged on all
pages.

For example, a flawed administrative interface is unlikely to be
vulnerable to anonymous attack if it correctly gates access to
production management networks, checks for administrative user
authorization, and logs all access.

### *[Fail securely](Fail_securely "wikilink")*

Applications regularly fail to process transactions for many reasons.
How they fail can determine if an application is secure or not.

For example:

`isAdmin = true;`
`try {`
`  codeWhichMayFail();`
`  isAdmin = isUserInRole( “Administrator” );`
`}`
`catch (Exception ex) {`
`  log.write(ex.toString());`
`}`

If either `codeWhichMayFail()` or `isUserInRole` fails or throws an
exception, the user is an admin by default. This is obviously a security
risk.

### *[Don’t trust services](Don’t_trust_services "wikilink")*

Many organizations utilize the processing capabilities of third party
partners, who more than likely have differing security policies and
posture than you. It is unlikely that you can influence or control any
external third party, whether they are home users or major suppliers or
partners.

Therefore, implicit trust of externally run systems is not warranted.
All external systems should be treated in a similar fashion.

For example, a loyalty program provider provides data that is used by
Internet Banking, providing the number of reward points and a small list
of potential redemption items. However, the data should be checked to
ensure that it is safe to display to end users, and that the reward
points are a positive number, and not improbably large.

### *[Separation of duties](Separation_of_duties "wikilink")*

A key fraud control is separation of duties. For example, someone who
requests a computer cannot also sign for it, nor should they directly
receive the computer. This prevents the user from requesting many
computers, and claiming they never arrived.

Certain roles have different levels of trust than normal users. In
particular, administrators are different to normal users. In general,
administrators should not be users of the application.

For example, an administrator should be able to turn the system on or
off, set password policy but shouldn’t be able to log on to the
storefront as a super privileged user, such as being able to “buy” goods
on behalf of other users.

### *[Avoid security by obscurity](Avoid_security_by_obscurity "wikilink")*

Security through obscurity is a weak security control, and nearly always
fails when it is the only control. This is not to say that keeping
secrets is a bad idea, it simply means that the security of key systems
should not be reliant upon keeping details hidden.

For example, the security of an application should not rely upon
knowledge of the source code being kept secret. The security should rely
upon many other factors, including reasonable password policies, defense
in depth, business transaction limits, solid network architecture, and
fraud and audit controls.

A practical example is Linux. Linux’s source code is widely available,
and yet when properly secured, Linux is a hardy, secure and robust
operating system.

### *[Keep security simple](Keep_security_simple "wikilink")*

Attack surface area and simplicity go hand in hand. Certain software
engineering fads prefer overly complex approaches to what would
otherwise be relatively straightforward and simple code.

Developers should avoid the use of double negatives and complex
architectures when a simpler approach would be faster and simpler.

For example, although it might be fashionable to have a slew of
singleton entity beans running on a separate middleware server, it is
more secure and faster to simply use global variables with an
appropriate mutex mechanism to protect against race conditions.

### *[Fix security issues correctly](Fix_security_issues_correctly "wikilink")*

Once a security issue has been identified, it is important to develop a
test for it, and to understand the root cause of the issue. When design
patterns are used, it is likely that the security issue is widespread
amongst all code bases, so developing the right fix without introducing
regressions is essential.

For example, a user has found that they can see another user’s balance
by adjusting their cookie. The fix seems to be relatively
straightforward, but as the cookie handling code is shared among all
applications, a change to just one application will trickle through to
all other applications. The fix must therefore be tested on all affected
applications.

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[this link doesn't go to anything, we either need to remove the link or
add the content this is to link to. I removed the brackets from Script
kiddies](Category:FIXME "wikilink")
[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")