## Brief Summary

Evaluating the strength of a “Multiple Factors Authentication System”
(MFAS) is a critical task for the Penetration tester. Banks and other
financial institutions are going to spend considerable amounts of money
on expensive MFAS; therefore performing accurate tests before the
adoption of a particular solution is absolutely suggested. In addition,
a further responsibility of the Penetration Testers is to acknowledge if
the currently adopted MFAS is effectively able to defend the
organization assets from the threats that generally drive the adoption
of a MFAS.

## Description of the Issue

Generally, the aim of a two factor authentication system is to enhance
the strength of the authentication process \[1\]. This goal is achieved
by checking an additional factor, or “something you have” as well as
“something you know”, making sure that the user holds a hardware
device of some kind in addition to the password. The hardware device
provided to the user may be able to communicate directly and
independently with the authentication infrastructure using an additional
communication channel; this particular feature is something known as
“separation of channels”.

Bruce Schneier in 2005 observed that some years ago “the threats were
all passive: eavesdropping and offline password guessing. Today, the
threats are more active: phishing and Trojan horses” \[2\]. Actually the
common threats that a MFAS in a Web environment should correctly address
include:

1.  Credential Theft (Phishing, Eavesdropping, MITM e.g. Banking from
    compromised network)
2.  Weak Credentials (Credentials Password guessing and Password
    Bruteforcing attacks)
3.  Session based attacks (Session Riding, Session Fixation)
4.  Trojan and Malware attacks (Banking from compromised clients)
5.  Password Reuse (Using the same password for different purposes or
    operations, e.g. different transactions)

The optimal solution should be able to address all the possible attacks
related to the 5 categories above. Since the strength of an
authentication solution is generally classified depending on how many
“authentication factors” are checked when the user gets in touch with
the computing system, the typical IT professional’s advise is: “If you
are not happy with your current authentication solution, just add
another authentication factor and it will be all right”. \[3\]
Unfortunately, as we will see in the next paragraphs, the risk
associated with attacks performed by motivated attackers cannot be
totally eliminated; in addition some MFAS solutions are more flexible
and secure compared to the others.

Considering the *5-Threats (5T)* above we could analyze the strength of
a particular MFAS solution, since the solution may be able to *Address*,
*Mitigate* or *Not Remediate* that particular Web Attack.

## Gray Box testing and example

A minimum amount of information about the authentication schema in use
is necessary for testing the security of the MFAS solution in place.
This is the main reason why the “Black Box Testing” section has been
omitted. In particular, a general knowledge about the whole
authentication infrastructure is important because:

  - MFAS solutions are principally implemented to authenticate disposal
    operations. Disposal actions are supposed to be performed in the
    inner parts of the secure website.
  - Attacks carried out successfully against MFAS are performed with a
    high degree of control over what is happening. This statement is
    usually true because attackers can “grab” detailed information about
    a particular authentication infrastructure by harvesting any data
    they can intercept through Malware attacks. Assuming that an
    attacker must be a customer to know how the authentication of a
    banking website works is not always correct; the attackers just need
    to get control of a single customer to study the entire security
    infrastructure of a particular website (Authors of SilentBanker
    Trojan \[4\] are known for continuously collecting information about
    visited websites while infected users browse the internet. Another
    example is the attack performed against the Swedish Nordea bank in
    2005 \[5\]).

The following examples are about a security evaluation of different
MFAS, based upon the *5T* model presented above.

The most common authentication solution for Web applications is User ID
and password authentication. In this case, an additional password for
authorizing wire transfers is often required. MFAS solutions add
“something you have” to the authentication process. This component is
usually a:

  - One-time password (OTP) generator token.
  - Grid Card, Scratch Card or any information that only the legitimate
    user is supposed to have in his wallet
  - Crypto devices like USB tokens or smart cards, equipped with X.509
    certificates.
  - Randomly generated OTPs transmitted through a GSM SMS messages
    \[SMSOTP\] \[6\]

The following examples are about the testing and evaluation of different
implementations of MFAS similar to the ones above. Penetration Testers
should consider all possible weaknesses of the current solution to
propose the correct mitigating factors if the infrastructure is already
in place. A correct evaluation may also permit one to choose the right
MFAS for the infrastructure during a preliminary solution selection.

A mitigating factor is any additional component or countermeasure that
might result in reduced likelihood of exploitation of a particular
vulnerability. Credit cards are a perfect example. Notice how little
attention is paid to cardholder authentication. Clerks barely check
signatures. People use their cards over the phone and on the Internet,
where the card's existence isn't even verified . The credit card
companies spend their security dollar “controlling” the transaction, not
the cardholder \[6\]. The transactions could be effectively controlled
by behavioral algorithms that automatically fill up a risk score chart
while the user uses his own credit card. Anything that is marked as
suspected could be temporarily blocked by the circuit.

Another mitigating factor is also informing the customer about what is
happening through a separate and secure channel. The Credit Card
industry uses this method for informing the user about credit card
transactions via SMS messages. If a fraudulent action is taken, the user
knows immediately that something has gone wrong with his credit card.
Real time information through separate channels can also have a higher
accuracy by informing the user about transactions, before those
transactions are successful.

Common **"User ID, password, and Disposal password"** usually protect
from (3), partially from (2). They usually do not protect from (1), (4)
and (5). From a Penetration tester's point of view, for correctly
testing this kind of authentication system, we should concentrate on
what the solution should protect from.

In other words, the adopters of a “User ID, Password, and Disposal
password” authentication solution should be protected from (2) and from
(3). A penetration tester should check if the current implementation
effectively enforces the adoption of strong passwords and if it is
resilient to Session Based attacks (e.g. Cross Site Request Forgeries
attacks in order to force the user to submitting unwanted disposal
operations).

  - Vulnerability Chart for “UserID + Password + Disposal Password”
    based authentication:
    \**Known Weaknesses:* 1, 4, 5
    \**Known Weaknesses (Details):* This technology doesn’t protect from
    (1) because the password is static and can be stolen through blended
    threat attacks \[8\] (e.g. MITM attack against a SSLv2 connection).
    It doesn’t protect from (4) and (5) because it’s possible to submit
    multiple transactions with the same disposal password.
    \**Strengths (if well implemented):* 2, 3
      - *Strengths (Details):* This technology protects from (2) only if
        password enforcement rules are in place. It protects from (3)
        because the need for a disposal password does not permit an
        attacker to abuse the current user session to submit disposal
        operations. \[9\]


Now let’s analyze some different implementations of MFASs:

**"One Time Password Tokens"** protect from (1), (2) and (3) if well
implemented. Do not always protect from (5). Almost never protect from
(4).
\*Vulnerability Chart for "One Time Password Tokens" based
authentication:
\*\**Known Weaknesses:* 4, sometimes 5
\*\**Known Weaknesses (Details):* OTP tokens do not protect from (4),
because Banking Malware is able to modify the Web Traffic in real-time
upon pre-configured rules; examples of this kind include malicious codes
SilentBanker, Mebroot, and Trojan Anserin . Banking Malware works like a
web proxy interacting with HTTPS pages. Since Malware takes total
control over a compromised client, any action that a user performs is
registered and controlled: Malware may stop a legitimate transaction and
redirect the wire transfer to a different location. Password Reuse (5)
is a vulnerability that may affect OTP tokens. Tokens are valid for a
certain amount of time e.g. 30 seconds; if the authentication does not
discard tokens that have been already used, it could be possible that a
single token may authenticate multiple transactions during its 30 second
lifetime.
\*\**Strengths (if well implemented):* 1,2,3
\*\**Strengths (Details):* OTP tokens mitigate effectively (1), because
token lifetime is usually very short. In 30 seconds the attacker should
be able to steal the token, enter the banking website and perform a
transaction. It could be feasible, but it’s not usually going to happen
in large-scale attacks. They usually protect from (2) because OTP HMAC
are at least 6 digits long. Penetration Testers should check that the
algorithm implemented by the OTP tokens under the test is safe enough
and not predictable. Finally, they usually protect from (3) because the
disposal token is always required. Penetration testers should verify
that the procedure of requesting the validation token could not be
bypassed.
**"Grid Cards, Scratch Cards and any information that only the
legitimate user is supposed to have in his Wallet"** should protect from
(1), (2), (3). Like OTP tokens, they cannot protect from (4). During
testing activities grid cards in particular have been found vulnerable
to (5). Scratch card are not vulnerable to password reuse, because any
code can be used just one time.
The penetration tester, during the assessment of technologies of this
kind, should pay particular attention to Password Reuse attacks (5) for
grid cards. A grid card based system commonly would request the same
code multiple times. An attacker would just need to know a single valid
disposal code (e.g one of those inside the grid card), and to wait until
the system requests the code that he knows. Tested grid cards that
contain a limited number of combinations are usually prone to this
vulnerability. (e.g., if a grid card contains 50 combinations the
attacker just needs to ask for a disposal, filling up the fields,
checking the challenge, and so on. This attack is not about bruteforcing
the disposal code, it’s about bruteforcing the challenge). Other common
mistakes include a weak password policy. Any disposal password contained
inside the gridcard should have a length of at least 6 numbers. Attacks
could be very effective in combination with blended threats or Cross
Site Request forgeries.

**"Crypto Devices with certificates (Token USB, Smart Cards)"** offer a
good layer of defense from (1), (2). It’s a common mistake to believe
that they would always protect from (3), (4) and (5). Unfortunately
technologies offer the best security promises and at the same time some
of the worst implementations around. USB tokens vary from vendor to
vendor. Some of them authorize a user when they are plugged in, and do
not authorize operations when they are unplugged. It seems to be a good
behavior, but what it looks like is that some of them add further layers
of implicit authentication. Those devices do not protect users from (3)
(e.g. Session Riding and Cross Site Scripting code for automating
transfers).

**Custom “Randomly generated OTPs transmitted through a GSM SMS messages
\[SMSOTP\]”** could protect effectively from (1), (2), (3) and (5).
Could also mitigate effectively (4) if well implemented. This solution,
compared to the previous one, is the only one that uses an independent
channel to communicate with the banking infrastructure. This solution is
usually very effective if well implemented. By separating the
communication channels, it’s possible to inform the user about what is
going on.

Ex. of a disposal token sent via SMS:
"This token: 32982747 authorizes a wire transfer of $ 1250.4 to bank
account 2345623 Bank of NY". The previous token authorizes a unique
transaction, that is reported inside the text of the SMS message. In
this way, the user can control that the intended transfer is effectively
going to be directed to the right bank account.

The approach described in this section is intended to provide a simple
methodology to evaluate Multiple Factor Authentication Systems. The
examples shown are taken from real-case scenarios and can be used as a
starting point for analyzing the efficacy of a custom MFAS.

## References

**Whitepapers**
\[1\] \[Definition\] Wikipedia, Definition of Two Factor
Authentication
<http://en.wikipedia.org/wiki/Two-factor_authentication>

\[2\] \[SCHNEIER\] Bruce Schneier, Blog Posts about two factor
authentication 2005,
<http://www.schneier.com/blog/archives/2005/03/the_failure_of.html>
<http://www.schneier.com/blog/archives/2005/04/more_on_twofact.html>

\[3\] \[Finetti\] Guido Mario Finetti, "Web application security in
un-trusted client scenarios"
<http://www.scmagazineuk.com/Web-application-security-in-un-trusted-client-scenarios/article/110448>

\[4\] \[SilentBanker Trojan\] Symantec, Banking in Silence
<http://www.symantec.com/connect/blogs/banking-silence>

\[5\] \[Nordea\] Finextra, Phishing attacks against two factor
authentication, 2005
<http://www.finextra.com/fullstory.asp?id=14384>

\[6\] \[SMSOTP\] Bruce Schneier, “Two-Factor Authentication with Cell
Phones”, November 2004,
<http://www.schneier.com/blog/archives/2004/11/twofactor_authe.html>

\[7\] \[Transaction Authentication Mindset\] Bruce Schneier, "Fighting
Fraudulent Transactions"
<http://www.schneier.com/blog/archives/2006/11/fighting_fraudu.html>

\[8\] \[Blended Threat\] <http://en.wikipedia.org/wiki/Blended_threat>

\[9\] \[GUNTEROLLMANN\] Gunter Ollmann, “Web Based Session Management.
Best practices in managing HTTP-based client sessions”,
<http://www.technicalinfo.net/papers/WebBasedSessionManagement.html>