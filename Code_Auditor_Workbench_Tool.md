Following this thread [Code Review project and
Code-Scanning-Tool(s)](http://lists.owasp.org/pipermail/owasp-testing/2007-January/001324.html)
here are some ideas of what such tool could do:

My conjecture is that static analysis only goes so-far in terms of
helping in a audit. It's nice, it's flashy, it's expensive, SPI, Fortify
and the like are spending millions investing in the technology, it looks
good to managers (I just bought a 60k security tool for my coders, I'm a
cool manager it's all secure now\!) - but it's not the static analysis
portion of a review that will help me secure a system. (Sure, it helps
me find low hanging fruit, but not the real interesting stuff).

Please tell me what static code review tool will bark at me if I forget
to add my custom authentication function or functions (which is most
common) at the top of each JSP? Not many do stuff like that well.

Also, most Java code audits that I am a part of is done by a team of 2
of more coders. (In fact, I say never do at a code review alone\! Bring
your friends\!)

So my vision is having some kind of web 2.0-like mashup:

1.  integrated IM
2.  integrated commenting system
3.  code demarcation/labeling tool
4.  a built in programmable checklist (like, this JSP needs to be
    "checked" for manual review of input validation, authentication,
    access control, or my applet checklist would be (no business logic,
    no protected information, etc) - the checklist changes depending on
    what I'm auditing. Cost limitations almost always necessitate I
    limit scope of my audit.
5.  integrated documentation features so I can build my audit
    documentation "on the fly" during the audit process within the
    workbench in a Wiki-fashion so the whole team could work on the doc
    together at the same time. (For example, this feature would
    automatically create shell documentation every time I label code as
    a "critical" problem.
6.  It would be nice if this workbench could import reports from those
    static analyzers (but they have a history of not playing well with
    the other tools)
7.  Lately I've been asked to create system documentation during the
    audit process (can you believe that some very large systems that I
    audit have no system documentation? oh my\! shocking\!) so perhaps
    enhanced technical documentation functionality would help.