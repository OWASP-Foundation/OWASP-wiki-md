# Getting started in application security

Application security is simply everything involved in developing,
maintaining, and purchasing applications that your organization can
trust. However, application security is inextricably tied into almost
every aspect of your organizations' information technology, and can be
maddeningly difficult to tackle. This "Getting Started" page is intended
to provide a roadmap of the various topics in application security and
where OWASP materials can help you and your organization master them. As
the saying goes, when it comes to application security, there are really
two types of organizations - those who don't know their code is
insecure, and those that do.

# Searching for application security information

We are working hard to organize the world's application security
information. But it's fair to say we have a very long way to go. There
is a [simple search engine](Special:Search "wikilink") built into the
OWASP site.

As a last resort, you can also just [get a
list](Special:Allpages "wikilink") of all the pages if you know a word
in the title.

# How Can I Get Involved At OWASP?

  - Global Initiatives - The [OWASP Global
    Initiates](https://www.owasp.org/index.php/OWASP_Initiatives_Global_Strategic_Focus)
    program was established to provide easy access for volunteers
    interesting in helping advance OWASP. There are a variety of items
    that need volunteers - some with security focus, others that focus
    on the OWASP organization or an event.
  - Join a project - Everyone is welcomed to contribute to any of our
    open projects. Check out the [list of
    projects](https://www.owasp.org/index.php/Category:OWASP_Project)
    and join the mailing list to find out more.
  - Join your local [OWASP Chapter](OWASP_Chapter "wikilink") - Everyone
    is welcome to attend any of our local Chapter meetings which are
    FREE and OPEN to attend to anyone who wishes to listen to talks and
    participate in discussions on the topic of application security.
    Check out the [OWASP
    Chapters](https://www.owasp.org/index.php/OWASP_Chapter) in your
    area.
  - Become a [Member](Membership "wikilink") of OWASP - support the
    growth of OWASP and the development of new and improved OWASP
    Materials and projects, get discounts on major cyber security
    conference registration fees. Individual and Corporate
    [Membership](Membership "wikilink") is available:
    [1](https://www.owasp.org/index.php/Membership)
  - Edit a page - This is a wiki, if you see a page that needs some
    clarification or better information then please edit it. There are a
    variety of links to page that need some assistance within the
    [Maintenance
    Report](https://www.owasp.org/index.php/Special:SpecialPages)

# Why is application security so hard?

If you haven't read it lately, check out Fred Brooks' great article,
"[No Silver
Bullet](http://www.cs.nott.ac.uk/~cah/G51ISS/Documents/NoSilverBullet.html)".
In it, Brooks discusses both "accidental" and "essential" difficulties
of producing software. We created the accidental difficulties ourselves,
by making our languages, compilers, and environments more difficult than
they need to be. But the essential difficulties are fundamental problems
that will always be with us. Brooks considers four inherent properties
of software that help explain the difficulty of software security -
complexity, conformity, changeability, and invisibility.

# If you're wondering if your code has vulnerabilities...

If you're wondering whether your software really has application
security weaknesses, then the best thing to do is to find out. You can
do this in a number of ways, but the simplest is to do an [application
assessment](CLASP_Best_Practices#Perform_application_assessments "wikilink")
of a few of your applications. The review should analyze all the major
security areas by using a combination of [vulnerability
scanning](Vulnerability_Scanning "wikilink"), [code
review](:Category:OWASP_Code_Review_Project "wikilink"), [penetration
testing](:Category:OWASP_Testing_Project "wikilink"), and [static
analysis](Perform_source-level_security_review "wikilink"). Then based
on some actual results, which should verify areas that are well designed
and built as well as identify weaknesses, you can make an informed
decision about how to proceed.

# If you already know your code is vulnerable...

If you've already come to the conclusion that your project or
organization is not producing secure code, then you should consider what
[organizational improvements](:Category:Activity "wikilink") are most
likely to improve your ability. One popular place to start is
[instituting an awareness
program](CLASP_Best_Practices#Institute_awareness_programs "wikilink")
for developers and managers, as it is relatively inexpensive and has
immediate effects. However, you may want to consider doing an
[application security capability
appraisal](:Category:OWASP_CLASP_Project "wikilink") of your
organization to find out what changes are likely to be the most
effective. Also, you might consider defining a risk model, creating
organization roles and teams, establishing standards or coding
guidelines, or introducing some security activities into your software
development lifecycle before doing the training.

# About threats, vulnerabilities, and countermeasures

A good way to start learning about application security is by
understanding software [principles](:Category:Principle "wikilink"),
[threats](:Category:Threat_Agent "wikilink"),
[attack](:Category:Attack "wikilink"),
[vulnerabilities](:Category:Vulnerability "wikilink"), and
[countermeasures](:Category:Countermeasure "wikilink"). A good overview
of the most critical of these is the [OWASP Top
Ten](OWASP_Top_Ten_Project "wikilink") awareness document. This is a
short paper that describes the most critical vulnerabilities, how to
find them, and what to do to protect against them in your application.

Another great way to learn about application security is to study some
real vulnerabilities and learn how they work. OWASP has developed
[WebGoat](:Category:OWASP_WebGoat_Project "wikilink") to provide
hands-on examples of application security to learn from. WebGoat is a
full J2EE application and training environment that contains real
vulnerabilities to experiment with and learn from. [OWASP
ZAP](OWASP_Zed_Attack_Proxy_Project "wikilink") is a powerful web
application penetration testing tool that you can use to test
applications. For further reference, you can read all about each of the
[vulnerabilities](:Category:Vulnerability "wikilink") on the OWASP
website to learn more.

# What are the root causes of application vulnerabilities?

Once you've learned about risk model, you should think about how those
problems come into existence. Every application security problem has a
root cause somewhere in the organization. It may be that the project
didn't have the right [activities](:Category:Activity "wikilink") in
their development process, or it may be that the developers didn't have
the right training, or it might even be that the team didn't have the
right tools for the job. But every vulnerability is a reason to
investigate, find out why it happened, and make some organizational
changes. You can find more information about improving your capability
in the [Software Assurance Maturity Model(OWASP SAMM)
Project](:Category:Software_Assurance_Maturity_Model "wikilink").