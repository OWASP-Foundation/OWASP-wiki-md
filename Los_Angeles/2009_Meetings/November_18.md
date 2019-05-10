## Topic: Watching Software Run

  - [Watching Software Run with Brian Chess, Fortify Founder and Chief
    Scientist](http://www.owasp.org/images/b/bc/Watching_software_run_11.18.09.pptx)

## Speaker: Brian Chess

Brian Chess is a founder of Fortify Software and serves as Fortify's
Chief Scientist, where his work focuses on practical methods for
creating secure systems. His book, Secure Programming with Static
Analysis, shows how static source code analysis is an indispensable tool
for getting security right. Brian holds a Ph.D. in computer engineering
from the University of California at Santa Cruz, where he studied the
application of static analysis to the problem of finding
security-relevant defects in source code. Before settling on security,
Brian spent a decade in Silicon Valley working at huge companies and
small startups. He has done research on a broad set of topics, ranging
from integrated circuit design all the way to delivering software as a
service.


## Abstract: Watching Software Run

Now more than ever before, computer systems are vulnerable because
software is vulnerable. No matter how good programmers get at making
secure software, it will never be perfect—we will always have to contend
with incomplete or inadequate code. Most efforts at living with bad code
have focused on shoring it up from the outside: limiting network access
(firewalls) or watching for suspicious behavior (intrusion detection).
This talk takes a different perspective: we’ll look at methods for
identifying and blunting the effects of software shortcomings from the
inside by watching the software run.

Modern languages like Java and C\# are good for more than just
programmers. They also provide a wealth of structured information when
they execute. We can apply many same techniques developed for outside-in
security, but at a finer granularity and with much more context. Along
the way there is a lot to talk about: Where web application firewalls
excel and where they fall down. Fuzzing vs. static analysis. The
disappointments of both aspect oriented programming and building
security in. Why nobody uses the Java Security model. Taking your
security with you into the cloud. The reason SQL injection won’t go
away. Revenge of the reference monitor. Why was Twitter’s security so
bad?