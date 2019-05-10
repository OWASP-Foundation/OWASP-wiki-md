## Overview

This CLASP Resource is meant as a set of basic principles for all
members of your application-security project.

## Ethics in Secure-Software Development

Software development organizations should behave ethically as a whole,
but should not expect that their individual components will.

In so far as security goes, it is ethical not to expose a user to
security risks that are known and will not be obvious to the user,
without clearly informing the user of those risks (and preferably,
mitigation strategies).

It is also ethical to provide users with a specific privacy policy for
use of their personal information in a timely manner so that they can
act to avoid undesired use of that information, if they so desire.
Additionally, if you change a privacy policy, the user should be given
the explicit choice either to accept the change or to have his personal
data expunged.

Additionally, if you have a system that is compromised on which user
data resides, it is ethical to inform users of the breach in privacy. If
the data resides in the state of California, this is required by law.
Similar regulations may apply in other jurisdictions.

Do not expect that all other people on the development team will be
ethical. Insiders play a significant factor in over 50% of corporate
security breaches. Particularly at risks are those employees that are
silently disgruntled or have recently left the company.

## Insider Threats as the Weak Link

Most development organizations overlook “insider” risks — i.e., those
users with inside access to the application, whether it be in deployment
or development. For example, when planning for deployments it is easy to
assume “a firewall will be there,” although, even when true, there are
many techniques for circumventing a firewall.

Most development organizations completely ignore the risks from the guy
in the next cube or on the next floor, the risks from the secretaries
and the janitors, the risks from those who have recently quit or been
fired. This, despite yearly numbers from the Computer Crime and Security
Survey performed by the Computer Security Institute and the FBI, which
shows that over half of all security incidents have an inside angle.

This suggests that trusting the people around you isn’t good enough. Not
only might people be disgruntled or susceptible to bribe that you may
not expect, but people are often susceptible to accidentally giving
insider help by falling victim to social engineering attacks.

Social engineering is when an attacker uses his social skills (generally
involving deception) to meet his security ends. For example, he may
convince technical support that he is a particular user who has
forgotten his password, and get the password changed over the phone.
This is why many people have moved to systems where passwords can be
reset automatically only using a “secret question” — although secret
questions are a bit too repetitive... if someone is being targeted, it
is often easy to figure out the mother’s maiden name, the person’s
favorite color, and the name of his or her pets.

## Assume the Network is Compromised

There are many categories of attack that can be launched by attackers
with access to any network media that can see application traffic. Many
people assume wrongly that such attacks are not feasible, assuming that
it is “difficult to get in the middle of network communications,”
especially when most communications are from ISP to ISP.

One misconception is that an attacker actually needs to “be in the
middle” for a network attack to be successful. Ethernet is a shared
medium, and it turns out that attacks can be launched if the bad guy is
on one of the shared segments that will see the traffic. Generally, the
greatest risk lies in the local networks that the endpoints use.

Many people think that plugging into a network via a switch will prevent
against the threat on the local network. Unfortunately, that is not
true, as switches can have their traffic intercepted and monitored using
a technique called ARP spoofing. And even if this problem were easily
addressed, there are always attacks on the physical media that tend to
be easy to perform.

As for router infrastructure, remember that most routers run software.
For example, Cisco’s routers run IOS, an operating system written in C
that has had exploitable conditions found in it in the past. It may
occasionally be reasonable for an attacker to truly be “in the middle.”

Another misconception is that network-level attacks are difficult to
perform. There are tools that easily automate them. For example,
“dsniff” will automate many attacks, including man-in-the-middle
eavesdropping and ARP spoofing.

Well known network-level threats include the following:

  - *Eavesdropping* — Even when using cryptography, eavesdropping may be
    possible when not performing proper authentication, using a
    man-in-the-middle attack.
  - *Tampering* — An attacker can change data on the wire. Even if the
    data is encrypted, it may be possible to make significant changes to
    the data without being able to decrypt it. Tampering is best
    thwarted by performing ongoing message authentication (MACing),
    provided by most high-level protocols, such as SSL/TLS.
  - *Spoofing* — Traffic can be forged so that it appears to come from a
    different source address than the one from which it actually comes.
    This will thwart authentication systems that rely exclusively on IP
    addresses and/or DNS names for authentication.
  - *Hijacking* — An extension of spoofing, in which established
    connections can be taken over, allowing the attacker to enter an
    already established session without having to authenticate. This can
    be thwarted with ongoing message authentication, which is provided
    by most high-level protocols, such as SSL/TLS.
  - *Observing* — It is possible to give away security-critical
    information even when a network connection is
    confidentiality-protected through encryption. For example, the mere
    fact that two particular hosts are talking may give away significant
    information, as can the timing of traffic. These are generally
    examples of covert channels (non-obvious communication paths), which
    tend to be the most difficult problem in the security space.

## Minimize Attack Surface

For a large application, a rough yet reliable metric for determining
overall risk is to measure the number of input points that the
application has — i.e., attack surface. The notion is that more points
of entry into the application provides more avenues for an attacker to
find a weakness.

Of course, any such metric must consider the accessibility of the input
point. For example, many applications are developed for a threat model
where the local environment is trusted. In this case, having a large
number of local input points such as configuration files, registry keys,
user input, etc., should be considered far less worrisome than making
several external network connections.

Collapsing functionality that previously was spread across several ports
onto a single port does not always help reduce attack surface,
particularly when the single port exports all the same functionality,
with an infrastructure that performs basic switching. The effective
attack surface is the same unless the actual functionality is somehow
simplified. Since underlying complexity clearly plays a role, metrics
based on attack surface should not be used as the only means access
control should be mandatory of analyzing risks in a piece of software.

## Secure-by-Default

A system’s default setting should not expose users to unnecessary risks
and should be as secure as possible. This means that all security
functionality should be enabled by default, and all optional features
which entail any security risk should be disabled by default.

It also means that — if there is some sort of failure in the system —
the behavior should not cause the system to behave in an insecure manner
(the “fail-safe” principle). For example, if a connection cannot be
established over SSL, it is not a good idea to try to establish a
plaintext connection.

The “secure-by-default” philosophy does not interact well with usability
since it is far simpler for the user to make immediate use of a system
if all functionality is enabled. He can make use of functionality which
is needed and ignore the functionality that is not.

However, attackers will not ignore this functionality. A system released
with an insecure default configuration ensures that the vast majority of
systems-in-the-wild are vulnerable. In many circumstances, it can even
become difficult to patch a system before it is compromised.

Therefore, if there are significant security risks that the user is not
already accepting, you should prefer a secure-by-default configuration.
If not, at least alert the user to the risks ahead of time and point him
to documentation on mitigation strategies.

Note that, in a secure-by-default system, the user will have to
explicitly enable any functionality that increases his risk. Such
operations should be relatively hidden (e.g., in an “advanced”
preference pane) and should make the risks in disabling the
functionality readily apparent.

## Defense-in-Depth

The principle of defense-in-depth is that redundant security mechanisms
increase security. If one mechanism fails, perhaps the other one will
still provide the necessary security. For example, it is not a good idea
to rely on a firewall to provide security for an internal-use-only
application, as firewalls can usually be circumvented by a determined
attacker (even if it requires a physical attack or a social engineering
attack of some sort).

Implementing a defense-in-depth strategy can add to the complexity of an
application, which runs counter to the “simplicity” principle often
practiced in security. That is, one could argue that new protection
functionality adds additional complexity that might bring new risks with
it. The risks need to be weighed. For example, a second mechanism may
make no sense when the first mechanism is believed to be 100% effective;
therefore, there is not much reason for introducing the additional
solution, which may pose new risks. But usually the risks in additional
complexity are minimal compared to the risk the protection mechanism
seeks to reduce.

## Principles for Reducing Exposure

Submarines employ a trick that makes them far less risky to inhabit.
Assume that you are underwater on a sub when the hull bursts right by
you. You actually have a reasonable chance of survival, because the ship
is broken up into separate airtight compartments. If one compartment
takes on water, it can be sealed off from the rest of the compartments.

Compartmentalization is a good principle to keep in mind when designing
software systems. The basic idea is to try to contain damage if
something does goes wrong. Another principle is that of least privilege,
which states that privileges granted to a user should be limited to only
those privileges necessary to do what that user needs to do. For
example, least privilege argues that you should not run your program
with administrative privileges, if at all possible. Instead, you should
run it as a lesser user with just enough privileges to do the job, and
no more.

Another relevant principle is to minimize windows of vulnerability. This
means that — when risks must be introduced — they should be introduced
for as short a time as possible (a corollary of this is “insecure
bootstrapping”). In the context of privilege, it is could to account for
which privileges a user can obtain, but only grant them when the
situation absolutely merits. That supports the least privilege principle
by granting the user privileges only when necessary, and revoking them
immediately after use.

When the resources you are mitigating access in order to live outside
your application, these principles are usually easier to apply with
operational controls than with controls you build into your own
software. However, one highly effective technique for enforcing these
principles is the notion of privilege separation. The idea is that an
application is broken up into two portions, the privileged core and the
main application. The privileged core has as little functionality as
absolutely possible so that it can be well audited. Its only purposes
are as follows:

  - Authenticate new connections and spawn off unprivileged main
    processes to handle those connections.
  - Mediate access to those resources which the unprivileged process
    might legitimately get to access. That is, the core listens to
    requests from the children, determines whether they are valid, and
    then executes them on behalf of the unprivileged process.

This technique compartmentalizes each user of the system into its own
process and completely removes all access to privileges, except for
those privileges absolutely necessary, and then grants those privileges
indirectly, only at the point where it is necessary.

## The Insecure-Bootstrapping Principle

Insecure bootstrapping is the principle that — if you need to use an
insecure communication channel for anything — you should use it to
bootstrap a secure communication channel so that you do not need to use
an insecure channel again.

For example, SSH is a protocol that provides a secure channel after the
client and server have authenticated each other. Since it does not use a
public key infrastructure the first time the client connects, it
generally will not have the server credentials. The server sends its
credentials, and the client just blindly accepts that they’re the right
ones. Clearly, if an attacker can send his own credentials, he can
masquerade as the server or launch a man-in-the-middle attack.

But, the SSH client remembers the credentials. If the credentials remain
the same, and the first connection was secure, then subsequent
connections are secure. If the credentials change, then something is
wrong — i.e., either an attack is being waged, or the server credentials
have changed — and SSH clients will generally alert the user.

Of course, it is better not to use an insecure communication channel at
all, if it can be avoided.

## Input Validation

If a program is liberal in what it accepts, it often risks an attacker
finding an input that has negative security implications. Several major
categories of software security problems are ultimately input validation
problems — including buffer overflows, SQL injection attacks, and
command-injection attacks.

Data input to a program is either valid or invalid. What defines valid
can be dependent on the semantics of the program. Good security practice
is to definitively identify all invalid data before any action on the
data is taken. And, if data is invalid, one should act appropriately.

#### Where to perform input validation

There are many levels at which one can perform input validation. Common
places include:

  - *Use* — all places in the code where data (particularly data of
    external origin) gets used.
  - *Unit boundaries* — i.e., individual components, modules, or
    functions;
  - *Trust boundaries* — i.e., on a per-executable basis.
  - *Protocol parsing* — When the network protocol gets interpreted.
  - *Application entry points* — e.g., just before or just after passing
    data to an application, such as a validation engine in a web server
    for a web service.
  - *Network* — i.e., a traditional intrusion detection system (IDS).

Validating at use is generally quite error-prone because it is easy to
forget to insert a check. This is still true, but less so when
validating at unit boundaries. Going up the line, validation becomes
less error prone. However, at higher levels, it gets harder and harder
to make accurate checks because there is less and less context readily
available to make a decision with.

At a bare minimum, input validation should be performed at unit
boundaries, preferably using a structured technique such as
design-by-contract. Validating at other levels provides defense-in-depth
to help handle the case where a check is forgotten at a lower level.

#### Ways in which data can be invalid

At a high level, invalid data is anything that does not meet the
strictest possible definition of valid. It does not just encompass
malformed data, it encompasses missing data and out-of-order data (e.g.,
data used in a capture-replay attack).

There are four different contexts in which data can be invalid:

  - *Sender* — Data is invalid if it did not originate from an authentic
    source.
  - *Tokens* — Data in network protocols are generally broken up into
    atomic units called tokens, which often map to concrete data types
    (e.g., numbers, zip codes, and strings). An invalid token is one
    that is an invalid value for all token types known to a system.
  - *Syntax* — Protocols accept messages as valid based on a protocol
    syntax, which is usually defined in terms of tokens. An invalid
    message is one that should not be accepted as part of the protocol.
  - *Semantics* — Even when a message satisfies syntax requirements, it
    may be semantically invalid.

#### How to determine input validity

Data validity must be evaluated in each of the four contexts described
above. For example, a valid sender can send bad tokens. Good tokens can
be combined in syntactically invalid ways. And, otherwise valid messages
can make no valid sense in terms of the program’s semantics.

At a high-level, there are three approaches to providing data validity:

  - *Black-listing* — Widely considered bad practice in all cases, one
    validates based on a policy that explicitly defines bad values. All
    other data is assumed to be valid, but in practice, it often is not
    (or should not be).
  - *White-listing* — One validates based on a precise description of
    what valid data entails (a policy). If the policy is correct, this
    prevents accidentally allowing maliciously invalid data. The risks
    are that the policy will not be correct, which may result not only
    in allowing bad data but also in disallowing some valid data.
  - *Cryptographic validation* — One uses cryptography to demonstrate
    validity of the data.

Handling each input validation context involves a separate strategy:

  - The sender can, in the general case, only be validated adequately
    using cryptographic message authentication.
  - Tokens are generally validated using a simple state machine
    describing valid tokens (often implemented with regular
    expressions).
  - Syntax is generally validated using a standard language parser, such
    as a recursive decent parser or a parser generated by a parser
    generator.
  - Semantics are generally validated at the highest boundary at which
    all of the semantic data needed to make a decision is available.
    Message-ordering omission is best validated cryptographically along
    with sender authentication.

Protocol-specific semantics are often best validated in the context of a
parser generated from a specification. In this case, semantics should be
validated in the production associated with a single syntactic rule.
When not enough semantic data is available at this level, semantic
validation is best performed using a design-by-contract approach.

#### Actions to perform when invalid data is found

There are three classes of action one can take when invalid data is
identified:

  - *Error* — This includes fatal errors and non-fatal errors.
  - *Record* — This includes logging errors and sending notifications of
    errors to interested parties.
  - *Modify* — This includes filtering data or replacing data with
    default values.

These three classes are orthogonal, meaning that the decision to do any
one is independent from the others. One can easily perform all three
classes of action.