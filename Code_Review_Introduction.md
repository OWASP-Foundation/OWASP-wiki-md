__TOC__

## Introduction

Code review is probably the single-most effective technique for
identifying security flaws. When used together with automated tools and
manual penetration testing, code review can significantly increase the
cost effectiveness of an application security verification effort.

This guide does not prescribe a process for performing a security code
review. Rather, this guide focuses on the mechanics of reviewing code
for certain vulnerabilities, and provides limited guidance on how the
effort should be structured and executed. OWASP intends to develop a
more detailed process in a future version of this guide.

Manual security code review provides insight into the “real risk”
associated with insecure code. This is the single most important value
from a manual approach. A human reviewer can understand the context for
certain coding practices, and make a serious risk estimate that accounts
for both the likelihood of attack and the business impact of a breach.

### Why Does Code Have Vulnerabilities?

MITRE has catalogued almost 700 different kinds of software weaknesses
in their CWE project. These are all different ways that software
developers can make mistakes that lead to insecurity. Every one of these
weaknesses is subtle and many are seriously tricky. Software developers
are not taught about these weaknesses in school and most do not receive
any training on the job about these problems.

These problems have become so important in recent years because we
continue to increase connectivity and to add technologies and protocols
at a shocking rate. Our ability to invent technology has seriously
outstripped our ability to secure it. Many of the technologies in use
today simply have not received any security scrutiny.

There are many reasons why businesses are not spending the appropriate
amount of time on security. Ultimately, these reasons stem from an
underlying problem in the software market. Because software is
essentially a black-box, it is extremely difficult to tell the
difference between good code and insecure code. Without this visibility,
buyers won’t pay more for secure code, and vendors would be foolish to
spend extra effort to produce secure code.

One goal for this project is to help software buyers gain visibility
into the security of software and start to effect change in the software
market.

Nevertheless, we still frequently get pushback when we advocate for
security code review. Here are some of the (unjustified) excuses that we
hear for not putting more effort into security:

*“We never get hacked (that I know of), we don’t need security”*

*“We have a firewall that protects our applications”*

''"We trust our employees not to attack our applications" ''

Over the last 10 years, the team involved with the OWASP Code Review
Project has performed thousands of application reviews, and found that
every single application has had serious vulnerabilities. If you haven’t
reviewed your code for security holes, the likelihood that your
application has problems is virtually 100%.

Still, there are many organizations that choose not to know about the
security of their code. To them, we offer Rumsfeld’s cryptic explanation
of what we actually know. If you’re making informed decisions to take
risk in your enterprise, we fully support you. However, if you don’t
even know what risks you are taking, you are being irresponsible both to
your shareholders and your customers.

''"...we know, there are known knowns; there are things we know we know.
We also know there are known unknowns; that is to say we know there are
some things we do not know. But there are also unknown unknowns -- the
ones we don't know we don't know." '' - Donald Rumsfeld

### What is Security Code Review?

Security code review is the process of auditing the source code for an
application to verify that the proper security controls are present,
that they work as intended, and that they have been invoked in all the
right places. Code review is a way of ensuring that the application has
been developed so as to be “self-defending” in its given environment.

Security code review is a method of assuring secure application
developers are following secure development techniques. A general rule
of thumb is that a penetration test should not discover any additional
application vulnerabilities relating to the developed code after the
application has undergone a proper security code review.

All security code reviews are a combination of human effort and
technology support. At one end of the spectrum is an inexperienced
person with a text editor. At the other end of the scale is a security
expert with an advanced static analysis tool. Unfortunately, it takes a
fairly serious level of expertise to use the current application
security tools effectively.

Tools can be used to perform this task but they always need human
verification. Tools do not understand context, which is the keystone of
security code review. Tools are good at assessing large amounts of code
and pointing out possible issues, but a person needs to verify every
single result to determine if it is a real issue, if it is actually
exploitable, and calculate the risk to the enterprise.

Human reviewers are also necessary to fill in for the significant blind
spots where automated tools simply cannot check.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")