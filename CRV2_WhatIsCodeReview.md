## What is Security Source Code Review?

Source code review is the practice of reviewing developed code for
vulnerabilities. There are many ways to review the security of an
application and it is recommended to perform more than one method to
help ensure more assessment coverage. Penetration testing is great at
finding certain bugs such as technical signature or API based issues.
Issues related to privacy, information leakage, denial of service are
more suited to code review. Source code review is also good practice as
you are finding issues early in the SDLC. Locating and fixing issues
early in your SDLC makes it cheaper in terms of effort and cost to
remediate. It also empowers developers to understand security bugs at
the source code level such that they may not repeat the same mistakes.

## What is static analysis?

Static Code Analysis is usually performed as part of a Source code
review and is carried out at the Implementation phase of SDLC. Static
Code Analysis commonly refers to the running of static code analysis
tools that attempts to highlight possible vulnerabilities whiting the
‘static’ (non-running) source code by using techniques such as Taint
Analysis, Data Flow Analysis, Control Flow Graph, and Lexical Analysis.
When the analysis is performed on a runtime environment, it is referred
to as Dynamic Code Analysis. Ideally, such tools would automatically
find security flaws with a high degree of confidence that what is found
is indeed a flaw. However, this is beyond the state of the art for many
types of application security flaws. Thus, such tools frequently serve
as aids for an analyst to help them zero in on security relevant
portions of code so they can find flaws more efficiently, rather than a
tool that simply finds flaws automatically.