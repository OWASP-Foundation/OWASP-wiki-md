Full descriptions of all the talks at [AppSec Israel
2016](AppSec_Israel_2016 "wikilink") are below, together with each of
the speakers' biographies.

The [full schedule can be found and subscribed to
here](https://appsecil2016.sched.org/).

Pictures from the event [can be found
here](https://drive.google.com/drive/folders/0B0_K8tApcXxmVzBkcDNFUmt5S0U).

__TOC__

The AppSec Israel conference is proudly being sponsored by:

## Technical Tracks

### Bot Extension - Abusing Google Chrome Extensions for Bot Attacks

**תוספי בוט - שימוש בתוספי כרום למטרת התקפות בוטים**
''''' Tomer Cohen, Head of R\&D security, Wix.com '''''
Chrome extensions have opened a variety of opportunities for users as
well as developers, expanding the limits of what we've known as browsing
experience. Attacker have also spotted the wide usage of such
extensions, and abuse people's trust in Chrome Web Store to distribute
malicious extensions. This allows them to run web-based bot attacks
straight from victims' browsers, including DDoS campaigns and cross-site
requests resulting in impersonation of users in third-party websites.

Furthermore, the detection of such bot attack by a third-party is more
complex than in regular distributed attacks, since real humans actually
use the Chrome tab abused to attack the victim third-party.

The lecture will include an intro on Chrome Extension architecture
followed by techniques to abuse this architecture in order to run bot
attacks, as well as distribute a malicious extensions to big crowds of
victims.


<u>Speaker Bio</u>

Worked as a security consultant in several places, one of the founders
of Magshimim Cyber Training Program.


<u>Technical Level:</u> Intermediate / Advanced
<u>Language:</u> Hebrew



### Could a few lines of code \<F\!\#ck\> it all up??

''*' Amit Ashbel, Director of Product Marketing & Cyber Security
Evangelist, Checkmarx **''
*** Erez Yalon, Application Security Lead, Checkmarx '''''
([download
presentation](Media:AppSecIL2016_AFewLinesOfCode-JS_AmitAshbel-ErezYalon.pptx "wikilink"))

March 2016. An anonymous open source developer decides to remove his
code (left-pad) from a public repository.

Shortly thereafter, several large organizations felt the impact of his
actions. Facebook, AirBnB and others experienced errors impacting the
functionality of their services. Packages using “left-pad” wouldn’t
properly execute.

Today, we embrace both the open source community and the growth of open
source projects, modules and packages but... Dependencies and recursive
dependencies might become a risk or even a new attack vector which we
didn’t foresee.

Could there be other cases of common and popular open source packages
depending on open source modules that might not be there tomorrow or,
even worse, could they be maliciously modified?

Join us for an insightful session that will reveal our research on this
topic where you will learn:

  - Which common open source packages might not be there tomorrow and
    how this can affect you?
  - How packages you use could be maliciously modified impact on your
    app Discuss the risks introduced by hybrid application development
  - How intertwined and complex dependencies have become


<u>Speaker Bio</u>

Amit has been with the security community for more than a decade where
he has taken on multiple tasks and responsibilities, including technical
and Senior Product lead positions. Amit adds valuable product knowledge
including experience with a wide range of security platforms and
familiarity with emerging threats. Amit also speaks at high profile
events and conferences such as BlackHat, Defcon, OWASP and others.


<u>Speaker Bio</u>

Erez Yalon heads the security research group at Checkmarx. With vast
defender and attacker experience and as an independent security
researcher, he brings invaluable knowledge and skills to the table. Erez
is responsible for maintaining Checkmarx’s top notch vulnerability
detection technology where his previous development experience with a
variety of coding languages comes into play.


<u>Technical Level:</u> Introduction
<u>Language:</u> Hebrew



### Crippling HTTPS with unholy PAC

**איך להרוס HTTPS עם PAC"ל חבלה**
''''' Amit Klein, VP Security Research, SafeBreach '''''
([download
presentation](Media:AppSecIL2016_CripplingHTTPSwithUnholyPAC_AmitKlein.pdf "wikilink"))

You're in a potentially malicious network (free WiFi, guest network, or
maybe your own corporate LAN). You're a security conscious netizen so
you restrict yourself to HTTPS (browsing to HSTS sites and/or using a
"Force TLS/SSL" browser extension). All your traffic is protected from
the first byte. Or is it?

We will demonstrate that, by forcing your browser/system to use a
malicious PAC (Proxy AutoConfiguration) resource, it is possible to leak
HTTPS URLs. We will explain how this affects the privacy of the user and
how credentials/sessions can be stolen. We will present the concept of
"PAC Malware" (a malware which is implemented only as JavaScript logic
in a PAC resource) that features: a 2-way communication channel between
the PAC malware and an external server, contextual phishing via
messages, denial-of-service options, and sensitive data extraction from
URI's. We present a comprehensive browser PAC feature matrix and
elaborate more about this cross-platform (Linux, Windows, Mac) and
cross-browser (IE, Chrome, Safari) threat.


<u>Speaker Bio</u>

Amit Klein is a world renowned information security expert, with 25
years in information security and over 30 published technical papers on
this topic. Amit is VP Security Research at SafeBreach, responsible for
researching various infiltration, exfiltration and lateral movement
attacks. Before SafeBreach, Amit was CTO for Trusteer (acquired by IBM)
for 8.5 years. Prior to Trusteer, Amit was chief scientist for Cyota
(acquired by RSA) for 2 years, and prior to that, director of Security
and Research for Sanctum (acquired by Watchfire, now part of IBM
security division) for 7 years. Amit has a B.Sc. from the Hebrew
University (magna cum laude, Talpiot program), recognized by InfoWorld
as a CTO of the year 2010, and has presented at HITB, RSA, OWASP,
CertConf, BlueHat, CyberTech, APWG and AusCERT.


<u>Technical Level:</u> Intermediate
<u>Language:</u> Hebrew



### Don't Feed the Hippos\!

''''' Martin Knobloch, Principal Consultant, Nixu '''''
([download
presentation](Media:AppSecIL2016_DontFeedTheHippos_MartinKnobloch.pdf "wikilink"))

The security community is trying to solve insecurity caused by bugs and
flaws in software for many years now, but with what success?

We almost never look in successes and failures experiences in other
areas, but we could really learn from. This talk is inspired by Ernesto
Sirolli’s TED talk “Want to help someone? Shut up and listen\!” about
failures in the aid program’s around the world. Listening to Ernesto
Sirolli, you cannot miss the similarity with the security community
trying to tell developers how to write secure code. This talk points out
common failures of the security community when communicating with
developers, trying to solve their problems without understanding what
their problems really are.

Using the hippo-analogy for security failures, during the talks those
‘(in-)secure hippos’ are identified, advice on how to avoid them are
provided, by anecdotes and best practices from the experience of the
past 10 years in the security field as a consultant.


<u>Speaker Bio</u>

Martin is Principal Consultant at Nixu BeNeLux
(https://www.nixu.com/en/nixubenelux). His main working area is
(software) security in general, from awareness to implementation. In his
daily work, he is responsible for education in application security
matters, advise and implementation of application security measures.

With his background in Java Development, he understands the complexity
of Enterprise software development, Agile Scrum environments and
continuous delivery / deployment.

Martin got involved in OWASP in 2006. He became a member of the OWASP
Netherland Chapter board in 2007. He has contributed to several OWASP
projects and is co-organizer of the OWASP BeNeLux-Day conference since
2008. Martin has been chair of the Global Education Committee from 2008
until the ending of the Global Committees.

Futher, Martin is the conference chair of the OWASP AppSec-Eu/Research
2015 conference in Amsterdam, the Netherlands and involved in the
AppSec-Eu 2016 among other activities as CfT Co-Chair.

Martin is a frequent speaker at universities, hacker spaces and various
conferences.


<u>Technical Level:</u> Intermediate / Advanced
<u>Language:</u> English



### Hacking HTTP/2 - New attacks on the Internet’s Next Generation Foundation

''*' Nadav Avital, Application Security Research Team Leader, Imperva
**''
*** Noam Mazor, Security Research Engineer, Imperva '''''
HTTP/2 is the emerging network protocol for the Internet, facilitating
leaner and faster web browsing by introducing several new mechanisms
which can be seen as a single transition layer for web traffic. The
adoption of HTTP/2 is lightning fast, and even though only a year has
passed since its publication, HTTP/2 is already supported by all
significant players in the field including browsers, web servers and
Content Delivery Networks.

In the presentation we will overview the HTTP/2 attack surface - stream
multiplexing, flow control, HPACK compression and server push, with a
focus on how the way HTTP/2 servers implement these mechanisms can make
or break your security posture. We will continue with presenting new
classes of vulnerabilities that have been introduced by the mechanisms
used with HTTP/2, and explaining how these vulnerabilities can be used
for mounting effective attacks against web servers like Apache, IIS,
Ngnix, Jetty and nghttp. We will explain in detail several serious
zero-day vulnerabilities, such as CVE-2016-1546, CVE-2016-0150 and
CVE-2016-1544, and end with discussing several approaches for mitigating
attacks of these types.

Those attending this session will understand that:

  - As an emerging technology that introduces novel and flexible
    mechanisms, HTTP/2 also induces new risks.
  - HTTP/2 implementations are still not “security mature.” Therefore it
    is almost certain that scrutiny of HTTP/2 implementations will
    increase in coming years, resulting in the discovery of new
    vulnerabilities, exploits and security patches. With HTTP/2 gaining
    more popularity, this trend will intensify.
  - An effective security strategy for newly adopted technologies must
    rely on supplemental solutions rather than patching


<u>Speaker Bio</u>

Nadav Avital is an expert in Web Application Security. He leads an
Imperva team who captures and analyzes hacking activities and then
create mitigation strategies. These efforts result in research for new
technologies and protocols. Nadav has more than 10 years industry
experience in coding and creating security tools. He holds B.Sc. in
Computer Science.


<u>Speaker Bio</u>

Noam Mazor worked in Imperva as security research engineer in the Web
Application Security team. Noam has experience in analyzing hacking
activities, creating mitigation and researching vulnerabilities. He
holds BSc in Computer Science and is currently a MSc student in Tel Aviv
University.


<u>Technical Level:</u> Intermediate
<u>Language:</u> Hebrew



### Hacking The IoT (Internet of Things) - PenTesting RF Operated Devices

**האקינג של מערכות IoT מבוססות RF**
''''' Erez Metula, Application Security Expert, AppSec Labs (Founder)
'''''
([download
presentation](Media:AppSecIL2016_HackingTheIoT-PenTestingRFDevices_ErezMetula.pdf "wikilink"))

We often encounter IoT (Internet of Things) systems during our work as
penetration testers and security consultants. We know how to assess the
security of the server side API, the associated mobile apps, the web
apps and so on - but what about the device itself (the "thing")?
Moreover, what happens if the device is not using traditional HTTP/S
request, or does not even "speak" plain old TCP/IP?

During this talk, we'll go over the obstacles we have to face when
analyzing unknown, custom RF based communication that drives the target
IoT system we're pentesting. We'll talk about and see in action tools
that will allow us to capture RF traffic, analyze it, brute force it,
replay it, and of course forge it. It's like plain old appsec hacking
tricks, but at the RF level. So let's hack some physical things
belonging to the real world\!


<u>Speaker Bio</u>

Erez Metula is the founder and Chairman of AppSec Labs, a leading
company in the field of application security.

He is the author of the book "Managed Code Rootkits", and is a world
renowned application security expert.

Erez has extensive hands-on experience performing security assessments,
code reviews and secure development trainings for worldwide
organizations, and had previously talked at international security
conferences such as BlackHat, Defcon, OWASP, RSA, SOURCE, CanSecWest and
more. Erez had helped companies from all sizes, from startups to Fortune
500 organizations.

Erez focuses on advanced application security topics and has performed
extensive ground breaking research on mobile application security.

Erez holds an MSc in computer science and he is CISSP.


<u>Technical Level:</u> Advanced
<u>Language:</u> Hebrew



### Integrating Security in Agile projects (real case study)

''*' Elena Kravchenko, ADM BU Security Lead, Security & Trust Office,
HPE Software **''
*** Efrat Wasserman, ADM Senior Program manager, SRL, HPE Software
'''''
([download
presentation](Media:AppSecIL2016_IntegratingSecurityInAgile_ElenaKravchenko-EfratWasserman.pptx "wikilink"))

There are many different security development lifecycles (SDLC)
frameworks in the modern world. However, a fully implemented SDLC
program is often represented as heavy, time-consuming and not suitable
to Agile development methodology. We’d like to break the myth and show
how a very comprehensive security program, managed by a dedicated
security office, can be successfully integrated in agile development
project on a real case example.

We’ll shortly describe the main challenges, and the techniques and
procedures helping to overcome the challenges. We’ll present the
Security Lifecycle Management (SLM) Framework developed and used in HPE
SW in the last three years, and describe how it integrated into
development of new SaaS based fully agile developed product, with
emphasis on main activities and roles. As a part of the presentation we
would like to highlight the importance of the proper program management
and role of the PMO and how it became a key success factor in the
effective security program implementation.


<u>Speaker Bio</u>

Elena has a MSc in Applied Mathematics from Leningrad State University,
and over 25 years of software engineering experience in different roles,
including Software Design Engineer, Technical Lead, Customer Oriented
Development Engineer, and Software System Architect.

Currently a part of HPE Software ITOM and ADM Security and Trust Office
as the Security Lead for HPE’s Application Delivery Management (ADM)
Business Unit.


<u>Speaker Bio</u>

Efrat has earned a BSc in Computer Science and Mathematics, and a MBA in
Business Management and Marketing. She has over 17 years in Software
Development, and 9 years as a Program manager.

Currently Senior Program Manager in HPE SW responsible for lifecycle of
SaaS product


<u>Technical Level:</u> Intermediate
<u>Language:</u> Hebrew



### Law and the Israeli Cybersecurity Industry

''''' Eli Greenbaum, Partner, Yigal Arnon & Co. '''''
From an international perspective, Israel provides a unique laboratory
for studying the effect of law and regulation on cybersecurity research
and development. This presentation will provide an introduction to
specific laws and regulations concerning cybersecurity research and ask
whether these laws have in actual practice influenced the growth of the
cybersecurity ecosystem in Israel. More specifically, how have industry
players, including startups, multinationals and the military, reacted to
the unique legal framework that Israel provides for cybersecurity
activities?


<u>Speaker Bio</u>

Eli Greenbaum is partner in the law firm of Yigal Arnon & Co.,
specializing in technology, intellectual property and cybersecurity. He
received his Masters degree in Applied Physics from Columbia University
and his law degree from Yale Law School. Eli has published widely in the
intersection between technology and the law, including in the Harvard
Journal of Law and Technology and the Cardozo Law Review. Eli clerked
from Justice Miriam Naor of the Supreme Court of Israel and Judge David
Cheshin of the District Court of Jerusalem.


<u>Technical Level:</u> Introduction
<u>Language:</u> English



### Java Hurdling: Obstacles and Techniques in Java Client Penetration-testing

''''' Tal Melamed, Technical Leader, AppSec Labs '''''
([download
presentation](Media:AppSecIL2016_JavaHurdling_TalMelamed.pdf "wikilink"))

Testing Java client applications is not always straightforward as
testing web applications. Even under experienced hands, there might be
obstacles coming your way; what if you cannot use a proxy? How do you
MitM? What if you just can't? How do you modify the app to your benefit?

Fortunately, Java is still Java. This lecture is based on a true story,
and will follow an interesting case of pen-testing a known product; what
tools and techniques can be used in order to jump over hurdles, all the
way to the finish line.

The lecture aims to enrich the pentester's toolbox as well as mind, when
facing Java client applications; MitM-ing, run-time manipulations and
patching the code are only some of the discussed cases.

In addition, a newly developed proxy for intercepting and tampering with
TCP communication over TLS/SSL and bypassing certificate-pinning
protections, will be introduced during the lecture.


<u>Speaker Bio</u>

Tal is an Application Security Expert. As AppSec Labs' Technical Leader,
he is leading a variety of security projects for Android, iOS, WP, Web
and Client applications.

Prior to working at AppSec Labs, Tal has worked at Amdocs, CheckPoint
and RSA, having more than a decade of experience in the Information
Security field.

Tal is a lead Trainer, a neat developer, and a security dreamer;
breaking, building, defending & training since '99.


<u>Technical Level:</u> Intermediate / Advanced
<u>Language:</u> Hebrew



### NodeJS Security Done Right​ - The tips and tricks they won’t teach you in school​

''''' Liran Tal, R\&D Team Leader, Hewlett Packard Enterprise '''''
([download
presentation](Media:AppSecIL2016_NodeJS-Security_LiranTal.pdf "wikilink"))

NodeJS, and JavaScript at large are quickly taking over software whether
it is GitHub’s statistics for projects growth, the IoT industry, ChatOps
projects written in JavaScript and Enterprises adoption is growing as
well.

With this trend, it is imperative to review OWASP security practices and
learn how to harden NodeJS Web Applications.​ ​ We will begin with a
quick NodeJS intro and a few fail stories of how things can go wrong. ​

We will quickly dive into hands-on practical implementation of security
measures to adopt in your current or future NodeJS project. Next I will
show how to leverage widely adopted security tools for integration in
the build and CI/CD process to audit and test for security
vulnerabilities, as well as leveraging successful enterprise-level open
source npm libraries to enhance your web application’s security.​ ​ In
summary: in this session I will demonstrate:​

  - Securing ExpressJS by adopting mature and commonly used npm
    libraries​
  - Secure code guidelines for JavaScript software developers​
  - Integrating NodeJS security measures as part of your build CI/CD
    DevOps process​

​ To empower others and make a lasting impression for Open Source
awareness and Security involvement: In the closing minutes of this
presentation I will ask a volunteer from the audience to commit a
Pull-Request that enhances security for a NodeJS project on GitHub.​


<u>Speaker Bio</u>

Liran is a top contributor to the open source MEAN.io, and core team
member of the MEAN.js full stack JavaScript framework. He is also an
author of several Node.js npm packages, as well as actively contributing
to many open source projects on GitHub. Being an avid supporter and
contributor to the open source movement, in 2007 he has redefined
network RADIUS management by establishing daloRADIUS, a world-recognized
and industry-leading open source project (http://www.daloradius.com).

Liran is currently leading the R\&D Engineering team for Hewlett Packard
Enterprise content Marketplace, built on a microservices architecture
for a combined technology stack of Java, NodeJS, AngularJS, MongoDB and
MySQL. He loves mentoring and empowering team members, drive for better
code methodology, and seek out innovative solutions to support business
strategies.

He enjoys spending his time with his beloved wife Tal, and his son Ori.
Amongst other things, his hobbies include playing the guitar, hacking
all things Linux and continuously experimenting and contributing to open
source projects.


<u>Technical Level:</u> Introduction
<u>Language:</u> Hebrew



### Putting the "I" in Code Review - Turning Code Review Interactive

''''' Tamir Shavro, Seeker R\&D Manager, Synopsys '''''
([download
presentation](Media:AppSecIL2016_InteractiveCodeReview_TamirShavro.pdf "wikilink"))

Everybody knows that manual code review can be a tedious and lengthy
effort, with complexity growing exponentially with the size of the code.
However, understanding code flow and focusing on relevant parts can
become much easier when employing interactive debugging techniques. This
allows combining the best of penetration testing and code review
benefits to achieve maximum results in the most efficient manner. In
this talk we will explain and demonstrate this eye-opening technique for
effectively performing a manual code review on a live system using a
debugger and provide a quick starter kit for implementing this
technique.


<u>Speaker Bio</u>

Tamir Shavro has been involved both in complex R\&D endeavors and in the
security field in the past 18 years. As the Chief Architect & VP RnD of
Seeker (acquired by Synopsys in 2015), Tamir has been the driving force
behind the development of the Seeker technology.

Prior to Seeker he worked as a Senior Security Consultant in Hacktics,
where he was involved in advance application security projects. He was
previously a Captain in the IDF Intelligence Corps, involved in various
development leadership and architecture roles.


<u>Technical Level:</u> Advanced
<u>Language:</u> Hebrew



### Signoff or Sign-Out

''''' Ofer Maor, Director of Security Strategy, Synopsys '''''
Software Signoff is an inevitable step in maturing our software
development processes in order to deliver better and safer software.
Like with other engineering disciplines before, the growing concerns for
safety, security and standards is driving the industry to do better. In
this talk we will explain what Software Signoff means and why
organizations must adopt it before it is too late.


<u>Speaker Bio</u>

Ofer Maor is a security expert and entrepreneur with over 20 years of
experience in information and application security. Ofer has been
involved in application security from its early days, through research,
penetration testing, consulting, and product development. As the founder
and CTO of Seeker, Ofer pioneered IAST, the next generation of
application security testing technology, currently used by some of the
largest organizations in the world to continuously improve their
software security. Ofer joined Synopsys when it acquired Seeker in July
2015. Prior to Seeker, Ofer was the Founder and CTO of Hacktics. He led
Imperva's Application Defense Center research group and has also served
as the Chairman of OWASP Israel and in the OWASP Global Membership
Committee.


<u>Technical Level:</u> Intermediate
<u>Language:</u> Hebrew



### The Dark Side of Search Engine Optimization

**הצד האפל של קידום אתרים במנועי חיפוש**
''''' Or Katz, Principal Security Researcher, Akamai '''''
([download
presentation](Media:AppSecIL2016_DarkSideSearchEngineOptimizations_OrKatz.pdf "wikilink"))

Search engines optimization (SEO) is a technique being used by web sites
owners in order to improve visibility and traffic to their web site.
Legitimate SEO activity will use optimization techniques such as:
changing structure and textual usage of the web site pages, publication
in social media and web forums that will referrer relevant users.

The ultimate goal of SEO campaign is to promote web site ranking in the
leading search engines, having the promoted web site returned in the
primary result page once searching for relevant terms and keywords.

In the presentation I’m going to present what happens when threat actors
get into the world of SEO campaigns abuse SEO optimization techniques
and moreover, use all kind of attack techniques such as SQL injection
and open redirects in order to manipulate search engines ranking.

I will also evaluate some of the SEO attacks and the manipulating
techniques, try to determine who are the victims in this story, check if
these attacks achieved their goal and supply more interesting insights
on the world of “Blackhat SEO”.


<u>Speaker Bio</u>

Or is an application security veteran, with years of experience at
industry leading vendors, currently serves as principal security
researcher for Akamai's Cloud Security Intelligence platform. Or is a
frequent speaker in conferences such as RSA, AppSec and CSA. Or has
published several innovative articles and white papers on web
applications threat intelligence and defensive techniques.


<u>Technical Level:</u> Intermediate
<u>Language:</u> Hebrew



### The Threat of Advanced Cross-Site Search Attacks

**האיום של התקפות Cross-Site Search מתקדמות**
''''' Dr. Nethanel Gelernter, Cyberpion & The College of Management
Academic Studies '''''
([download
presentation](Media:AppSecIL2016_AdvancedCrossSiteSearch_NethanelGelernter.pdf "wikilink"))

Cross-site search (XS-search) is a practical timing side-channel attack
that allows the extraction of sensitive information from web-services.
The attack exploits inflation techniques to efficiently distinguish
between search requests that yield results and requests that do not.
This work focuses on the response inflation technique that increases the
size of the response; as the difference in the sizes of the responses
increases, it becomes easier to distinguish between them. We begin with
browser-based XS-search attack and demonstrate its use in extracting
users' private data from Gmail and Facebook. The browser-based XS-search
attack exploits the differences in the sizes of HTTP responses, and
works even when significant inflation of the response is impossible.
This part also involves algorithmic improvements compared to previous
work. When there is no leakage of information via the timing side
channel it is possible to use second-order (SO) XS-search, a novel type
of attack that allows the attacker to significantly increase the
difference in the sizes of the responses by planting maliciously crafted
record into the storage. SO XS-search attacks can be used to extract
sensitive information such as email content of Gmail and Yahoo\! users,
and search history of Bing users.


<u>Speaker Bio</u>

Nethanel Gelernter received a PhD in Computer Science from Bar-Ilan
University (Israel). His research mainly focuses on web application
security, and in particular in exploring new attack vectors and threats
in the web. Currently, he is leading the cyber security research and
studies in the College of Management Academic Studies in Israel. Beyond
the academic world, Nethanel provides consulting services, and he
recently founded Cyberpion, a company that investigates unknown attack
vectors and develops countermeasures against them.


<u>Technical Level:</u> Advanced
<u>Language:</u> Hebrew



### The Unwanted Sons - Formalizing and Demonstrating WAF Bypass Methods for the REST of the Top 10

**צאצאים לא רצויים - פירמול לטכניקות חדשות למעקף WAF לשאר ההתקפות
הנפוצות של OWASP TOP 10**
''''' Shay Chen, CEO, Effective Security '''''
([download
presentation](Media:AppSecIL2016_TheUnwantedSons-WAFBypassTechniques_ShayChen.pptx "wikilink"))

The once uncommon application-level protection mechanisms are EVERYWHERE
these days, and sooner or later, you'll have to face them.

Web Application Firewalls (WAF) and Intrusion Detection Systems (IDS),
Filters and RASP Modules, all common and widespread countermeasures you
have to face on a regular basis, with the power to turn a typical
assessment into a nightmare, and make automated tools practically
useless.

While the attack vectors are well covered in CWE, CAPEC, TECAPI RvR,
WASC, OWASP Top 10 and Testing Guide, all you have to cover evasion
techniques is a couple of cheat sheets focused on a limited set of
attacks.

Sure, there are numerous XSS and SQL Injection evasion cheat sheets, but
what about Path Traversal, Remote File Inclusion, OS Command Injection?
What about Forced Browsing? What about other attacks?

Formalizing evasion techniques and methods for the REST of the common
attack vectors makes a LOT of sense, for manual pen-testing and
automated tools - and THIS is phase one, aimed to cover the rest of the
unattended top 10.


<u>Speaker Bio</u>

Shay Chen is the CEO of Effective Security, an information-security
boutique company specializing in information security assessments and in
automating security processes of vulnerability management and SDLC.

He has over twelve years in information technology and security, a
strong background in software development, and a stream of previously
published vulnerabilities, attack vectors, benchmarks and hacking
methodologies.

Shay is an experienced speaker, and regularly instructs a wide variety
of security related courses in Conferences and Enterprises. Before
moving into the information security field, he was involved in various
software development projects in ERP, mobile & enterprise environments.


<u>Technical Level:</u> Intermediate / Advanced
<u>Language:</u> Hebrew



### The Ways Hackers Are Taking To Win The Mobile Malware Battle

''''' Yair Amit, CTO & Co-founder, Skycure '''''
([download
presentation](Media:AppSecIL2016_WhyHackersAreWinningMobileMalwareBattle-YairAmit.pdf "wikilink"))

In the proverbial game of cat-and-mouse between endpoint security
vendors and malware writers, malware attacks have recently grown more
sophisticated. More enterprises are losing ground to hackers, who are
able to outmaneuver static and runtime solutions by constantly changing
their attack strategies. The team that uncovered iOS malicious profiles,
WiFiGate, HTTP Request Hijacking, No iOS Zone and Invisible Profiles are
taking it upon themselves to coach developers and organizations on how
to regain control, and turn the tables on the hackers behind
next-generation mobile malware.

In his presentation, Yair will discuss cutting-edge techniques used by
malware writers to circumvent mobile security paradigms such as
app-sandboxing and containers. Mr. Amit will then break down the current
set of techniques (signatures, static analysis & dynamic analysis) used
to identify malware on mobile devices, and identify the pros and cons of
these approaches. He will also explain why attackers constantly succeed
in fooling these technologies, and explore the problem of false
positive/false negative tradeoffs in such solutions.

During a live, interactive demo, Yair will create a mobile malware on
stage, meant to be undetected by static and runtime analysis
technologies.


<u>Speaker Bio</u>

Yair Amit is co-founder and CTO at Skycure, leading the company’s
research and vision and overseeing its R\&D center. Yair has been active
in the security industry for more than a decade with his research
regularly covered by media outlets and presented in security conferences
around the world. Prior to co-founding Skycure, Yair managed the
Application Security and Research Group at IBM, joining through the
acquisition of Watchfire. At IBM, Yair led the research and
implementation of IBM’s next-generation application security technology.
Yair holds a BSc, summa cum laude, from Tel Aviv University in
bioinformatics.


<u>Technical Level:</u> Intermediate / Advanced
<u>Language:</u> Hebrew