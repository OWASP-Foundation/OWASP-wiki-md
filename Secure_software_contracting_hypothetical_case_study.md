## Let's Sue the Idiots -- Security, Software, Contracts, and Lawyers

  - By Jeff Williams (Aspect Security, Inc.)
  - Posted January 13, 2004

## Introduction

What would you do if you outsourced your web application development to
a software shop, only to find out years later that the code they
produced is full of security holes? What would you do if you were a
developer who wrote the code? Sound familiar? In many organizations, the
knee-jerk reaction is to sue the developers on a breach of contract or
negligence theory, but that's about the biggest mistake you can make.
This column discusses how these disputes happen, how the contracts work,
some of the arguments on both sides, and suggests a middle ground that
will hopefully help guide you through a delicate situation.

`What do you do when you realize software you wrote might have vulnerabilities?`

## Just Another Outsourced Web Application

Imagine the plight of the National Widgets. Two years ago, National
contracted with the talented Front End Associates to build a web site
for their users. The contract detailed the work to be performed, the
schedule, and many functional requirements - but was completely silent
on security. Front End built the site and National deployed it about 18
months ago without incident. The site has been working well and National
has provided strong references for Front End.

Recently, some National employees raised the possibility of security
problems, so National went to Front End and asked them whether the
application is secure. The Front End sales team started dancing and said
that they were confident that they met their contractual obligation and
would be happy to submit a proposal to respond to these 'new'
requirements. National was unsure about the original contract and went
to their lawyers to see if the original contract required security.

## Send In the Lawyers\!

The lawyers got very excited about the issue, and started making
statements about the standard of care, rights, duties, and res ipsa
loquitur. National never did get a clear answer about whether the
contract did or didn't require security. So they just went back to Front
End and asked them to fix the problems for free. And that's where the
situation started to unhinge.

Front End said that they didn't believe that there were any security
problems in their code. Before delivery, they had hired a security
testing company to do a security audit of their application. The company
they hired claimed to specialize in penetration testing to test and
prepare a report. Unfortunately, all the company did was to run a few
scanning tools like nmap and nessus. They cleaned up the tool output and
delivered the report. National laughed when Front End brought up the
report, and asked them to produce the application security test results
for the application they developed. Confronted with this, Front End
rapidly backed down and again claimed that there were no security
problems with their code, and even if there were, they weren't required
to build secure code.

National responded that the requirement to build secure code is obvious,
and that any vendor who knowingly built insecure code is clearly
negligent. Then, obviously grasping, they started throwing around terms
like implied warrantee, strict liability, and class action. They even
called the OWASP Top Ten the de facto standard for web application
security and mentioned that even the U.S. Federal Trade Commission is
going after companies that don't meet the standard.

## Everybody Hires Experts

Quietly, Front End began to worry that their code did have security
problems. So they hired their own experts. They found a firm that
specialized in web application security to review their code and do some
application penetration testing. These experts found quite a lot of
problems in the first few days, and called Front End to let them know
how it was going. A senior manager at Front End called the experts back
after a few days to let them know that they would not require a written
report for their findings. Rather they would prefer to receive all the
findings orally during teleconferences.

In the meantime, National decided that the first order of business was
to prove that there were indeed serious security problems with their
code. So they hired their own web application security experts and
arranged for an application security review. These experts started with
the standard web application vulnerability scanning tools, but only
found a few problems. The experts wanted to do a code review, and asked
National to send a copy of the source code for the application. But
National never asked for, and did not have a copy of the source code for
their application. When they asked Front End for a copy, they were
delayed and ultimately refused, mentioning trade secret and copyright
issues. Fortunately for National, the code was written in Java and was
not obfuscated. So the experts thumbed their noses at the Digital
Millennium Copyright Act (DMCA), decompiled the code with Jad, and
performed their code review anyway. They also did some penetration
testing along with the code review to validate their findings.

Unfortunately (but not surprisingly), the review found serious problems
in six of the Top Ten categories. Several of the problems were
design-level problems and would require quite a few man-months of effort
to fix. So, National went back to Front End, showed them the findings,
and asked them again to fix the problems for free. Front End, now quite
worried, responded that they would take the matter up with their lawyers
and left the meeting. Not surprisingly, the lawyers never did respond to
National.

## Bad to Worse

So, National felt obligated to file suit against Front End, claiming
that Front End had not performed the work required under the contract
and that they should fix the problems and pay National's legal fees.
Front End responded with a motion to dismiss, based on the fact that the
code was developed over two years prior, that they had been paid, and
that the code had therefore been fully accepted by National. They also
argued in the alternative that they could not be held liable for not
meeting requirements that did not exist at the time of contracting.

Both sides have now invested many tens of thousands of dollars in legal
fees, lost productivity, and reputation damage. In addition to actual
litigation costs, both parties spent a significant amount of time
answering interrogatories, producing documents, getting ready for
depositions, and in trial. Many of the original developers of the
National application left Front End as the environment had changed
dramatically, and they did not want to be blamed for the debacle.

## A Better Way?

This miserable story is a good example of how NOT to handle this issue.
There are clearly many companies who are in this situation, and the
legal system is not a good way out. There is some right and wrong on
both sides, so let's look at a better way to clean up this mess, and
then we'll conclude with some ideas about preventing these problems from
happening in the future.

First, everyone on both sides needs to understand that building a secure
web application takes more effort than just building one that looks
pretty. If you're the customer, you should stop feeling ripped off. If
you and the builder had discussed the issue, the price would have almost
certainly been higher. You should also take into account that the vast
majority of developers do not have a strong understanding of security,
so it is not reasonable to expect vulnerability-free code without paying
for it. At the end of the day, you probably got what you paid for. If
you suspect security problems in your applications, don't ignore them.

But, if you're the developer, don't pretend to be innocent here. If the
customer had asked whether the code would have vulnerabilities you would
have almost certainly said no. And you wouldn't have added very much, if
anything, to your bid. You know that you really should have taken the
time to do the security requirements and get it built and tested
properly. Most of these vulnerabilities have been well understood for
many years, and they are not difficult to avoid. If you uncover or even
suspect vulnerabilities in code your company wrote, the responsible
thing to do is to let your customers know. In fact, you may have a legal
obligation to warn your customer - just as if you had sold them a car
with faulty brakes. Most buyers will respect the fact that you've come
forward with this information and work with you to resolve the issues.

`Nobody wins if you end up in court.`
`Do your homework and work it out.`

The only equitable thing for parties in this situation is to figure out
a way to share the costs involved with fixing the problems. If you find
yourself in this situation, the first thing to do is to meet with the
other party to discuss your concerns and suggest a plan for resolving
any possible issues. The fact is that there are vulnerabilities in the
software that neither party thought of when you were agreeing to do the
work. Agree on an independent third party to perform an accurate
assessment of what the application is going to take to fix. Sharing the
costs of this review is reasonable, since both parties will benefit from
the findings. The meeting should also include a careful review of the
contract language to see if there are any terms that assign
responsibility in this situation.

To ensure completeness, the third party review should include code
analysis and some penetration testing. It's reasonable for the review to
focus on the OWASP Top Ten, in order to keep the findings grounded in a
reasonable minimum standard for web applications. The report should
include detailed descriptions of any findings, focused on exactly what
is wrong with the code. The reviewers will need access to the code to
make these judgments and will need strong code review skills. In
addition, the third party should estimate the risk associated with the
flaw in the specific context of the customer's enterprise.

Once you have a justifiable list of problems from an independent third
party, both parties should meet again to create a plan for getting them
fixed. The purpose of the meeting should be to identify which problems
the developer will fix, how difficult the fixes will be, and who is
going to pay for the fixes. Remember that if you can't find some common
ground here, both parties will end up in court and only the lawyers will
win.

## What Would Happen in Court?

This is a difficult question, since there are so many variables at work.
But my best guess is that a court would end up splitting the difference
anyway. Most courts are not going to understand the technical issues
with these vulnerabilities, so they will look to external standards and
industry practice. This will end up as a battle of expert witnesses,
some saying that these vulnerabilities have been well understood for 25
years, the others arguing that most developers do not understand
security and that there are no standards. Ultimately, the court is not
going to be able to decide who is responsible for what. They might
decide for the developer, thinking that it is unfair to hold developers
to requirements that are not explicitly stated and are not industry
practice. On the other hand, they could easily hold for the customer, on
the theory that the developer either knew or should have known about
these vulnerabilities, and therefore should have taken measures to
prevent them in their software.

`Either way, the cost of fixing these problems will`
`be dwarfed by the cost of litigating the issue.`
`So get with your partner and work it out. `

## What Should Happen When the Contract Is Silent

When contracts are silent on an issue, the law fills in the missing
terms with what it thinks the parties would have intended. These
"default" terms come from statutes, the UCC, trade practices, and many
other sources. But application security is new enough and moving fast
enough that it's anybody's guess what sources a court might lean on to
decide a case. So just for a moment, let's put on a lawmaker hat and try
to decide what ought to happen.

Would the world be a better place if the default contractual term were
zero security? No, this can't be the right answer. This would mean that
unless you specifically call it out, developers have no responsibility
to make their code secure. Developers would have no responsibility to
avoid well understood vulnerabilities. This puts all the burden on the
buyer, who is not in a very good position to know what vulnerabilities
might occur. So this approach would be extremely economically
inefficient.

But imagine the opposite extreme, where the developer is required to
produce a perfectly secure application if the contract is silent. This
can't be the right answer either. In general, putting liability on the
party in the best position to avoid the problem will produce the most
efficient results. However, since creating perfectly secure code is
virtually impossible, this would create unlimited liability for software
builders. Obviously, this would have a dramatic effect on the ability of
software makers to practice their craft. Therefore, courts should read
in some basic security requirements into contracts that are silent on
the issue. The list should include requirements that both parties would
have agreed to if the topic had been discussed. Well understood security
vulnerabilities like those in the OWASP Top Ten are a reasonable
starting point. But it would be far better if the buyer and builder work
out the real security requirements for the project and capture them in
the contract, rather than relying on what a court might dream up if you
ignore the issue.

## Next Time?

Hopefully, most readers are not currently in this situation, and would
just like to prevent it from happening in the future. The right way is
to set up specific contractual terms about how good the security needs
to be for the project.

Dave Thomas has written that quality should be a part of the
requirements that you negotiate with the customer up front. NASA spends
something like $1,000 per line of code. For you non-math majors, that's
a million dollars for even a trivial 1000 line program. And although
they have a fantastic record on software quality, they still
occasionally lose a probe or crash a rocket because of software
problems.

Security, like quality, is something that software builders and buyers
should discuss, as there are legitimate business reasons for web
applications with differing levels of security. Buyers, of course, are
initially going to expect software without any vulnerabilities. This, of
course, is not realistic. Builders, at least if history is any guide,
are going to want to build software that meets the functional
requirements and not worry about security at all. Leaving security out
of the negotiation entirely is also not appropriate, as the default
legal rules are quite unclear.

The software builder and buyer need to have a frank discussion that
addresses questions like:

  - What types of incidents would be considered serious (e.g.
    disclosure, corruption, denial of service)?
  - Do all the developers have to be trained in security?
  - Do you want a documented security policy and/or security
    requirements for the application?
  - Do you want detailed documentation of the security design and
    mechanisms?
  - Do you want a security review of the design?
  - Do you want penetration testing done before deployment?
  - Do you want the code reviewed by security experts?
  - Who takes the risk on fixing security problems discovered down the
    road?

Buyers should expect that there will be some additional charges for
increased security, and that they can get a cheaper price if they
decline these security services. As a contractual starting point, you
may want to consider the draconian Code Integrity Warranty that puts all
the burden on the developers for any bug of any kind that affects
security. At least the terms are very clear, but the potential liability
for developers is staggering.

## Conclusions

So, if you're outsourcing software development, talk with your
developers. Make sure they understand your security needs. Make sure it
gets in the contract. You may have to answer some hard questions about
just how much security you're willing to pay for. If you're a software
developer, be clear about what security you are providing, then do it.
Make sure you understand whose responsibility it will be if a security
vulnerability is uncovered after the software is in production.

[Category:OWASP Legal Project](Category:OWASP_Legal_Project "wikilink")