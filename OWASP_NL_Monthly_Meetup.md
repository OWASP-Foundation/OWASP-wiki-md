  - [OWASP Netherland Wiki](Netherlands "wikilink")

The OWASP Monthly Meetup is a networking opportunity to get together
with your peers.

To visit OWASP - Chapter Netherlands Meetup, go here: [OWASP NL @
Meetup.com](https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/)

Dates / Locations:

# Upcoming Meetups

# Past Meetups

## January 17, 2019

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/257707239/>

  -
    18:30 - 19:00 Dinner
    19:00 - 19:15 Welcome, OWASP update
    19:15 - 20:00 Machine Learning vs. Cryptocoin Miners by Jonn
    Callahan
    20:00 - 2-:15: Break
    20:15 - 21:00 Running at Light Speed: Cloud Native Security Patterns
    by Jack Mannino
    21:00 - Closing

<!-- end list -->

  - Xebia
    Laapersveld 27
    1213 VB Hilversum

**Machine Learning vs. Cryptocoin Miners:**
With the advent of cryptocurrencies as a prevalent economic entity,
attackers have begun turning compromised boxes and environments into
cash via cryptocoin mining. This has given rise for the necessity to
detect compromised environments by analyzing network traffic logs for
evidence of cryptocoin miners operating within a given network. In this
talk, I'll be reviewing various ML and statistical analysis techniques
leveraged against VPC Flow Logs for this very purpose. It will not be a
deep dive of the math involved, but instead a general discussion of
these techniques and why I chose them.

  -
    [Download the presentation as
    PDF](Media:OWASP_MLvsCryptocoins_20190117.pdf "wikilink")
    [Link to the
    recording](https://www.youtube.com/watch?v=nO_HhyYWYqM&authuser=1)

**Running at Light Speed: Cloud Native Security Patterns**
No matter how fast you ship software, a good design is critical to
security. Cloud native systems are no exception. Containerized
microservices running on distributed management and orchestration
platforms, bring new challenges to address as well as classic software
problems that we’ve been dealing with for years. Secure software design
patterns can be used to model security controls at different trust
boundaries within your architecture, providing security in a repeatable
and consumable way. Using patterns such as the Service Mesh or
Ambassador pattern lets us focus on proper security control placement
and lifting security outside of the core services we’ve traditionally
bolted security onto later.

The goal of this presentation is to arm software developers and security
architects with reference architecture guidance that can be used in any
cloud native environment. The topics we’ll cover include multi-tenancy
considerations, authentication, authorization, encryption, and more. We
will focus on newer cloud native architecture patterns as well as some
classic software design patterns that are still applicable. At the end
of this presentation, you’ll have a greater understanding of cloud
native security design at an architectural level and you’ll be eager to
begin white-boarding your ideas.

  -
    [Download the presentation as
    PDF](Media:OWASP_Netherlands_-_Running_at_Light_Speed_-_20190117.pdf "wikilink")
    [Link to the
    recording](https://www.youtube.com/watch?v=EWHi8KgOZpw&authuser=1)

Speakers info: Jonn Callahan has worked in appsec for half a decade
across a wide variety of languages, technologies, and sectors. While
constantly looking for new things to play with, he rediscovered his love
for the universal language of math and, consequentially, the power of
statistical analysis and machine learning. He now seeks to dismantle the
black magic of these techniques, showing that they don't require an
advanced mathematics degree to be leveraged, as well as to find novel
ways to apply them within the security space Jack Mannino is the CEO of
nVisium. Passionate about security and impossible to keep away from a
keyboard, his expertise spans over 15 years of building, breaking, and
securing software. Jack founded nVisium in 2009, and since then has
helped the world's largest software teams enhance security across their
software portfolios. He has spoken at conferences globally on topics
such as secure design, mobile application security, and cloud-native
security.

## September 27, 2018

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/250034921/>

  -
    18:30 - 19:00 Dinner
    19:00 - 19:15 Welcome, OWASP update
    19:15 - 20:00 Serverless Security – Functions-as-a-Service (FaaS) by
    Niels Tanis - [Video](https://youtu.be/c5ZHPc_yG4g) -
    [PDF](Media:OWASP-meetup_20180927_-_WhenServerlessMetSecurity_-_Niels_Tanis.pdf "wikilink")
    20:15 - 21:00 Building a security test automation framework by
    Riccardo ten Cate - [Video](https://youtu.be/xWe816PXll4) -
    [PDF](Media:_OWASP-meetup_20180927_-_Building_a_security_test_automation_framework_-_Riccardo_ten_Cate.pdf "wikilink")
    21:00 - Closing

<!-- end list -->

  - Radboud University Nijmegen
    Faculty of Science, Huygensgebouw
    Heyendaalseweg 135
    6525 AJ Nijmegen

**Serverless Security – Functions-as-a-Service (FaaS)**
Serverless is a design pattern for writing scalable applications in
which Functions as a Service (FaaS) is one of the key building blocks.
Every mayor Cloud Provider has got his own FaaS available. On Microsoft
Azure there is Azure Functions, AWS has got Lambda and Cloud Functions
can be used on the Google Cloud. All of these have a lot of similarities
in the way they allow developers to create small event driven services.
From security perspective there are a lot of benefits when moving to a
serverless architecture. There is no need to manage any of the machines
and the underlying infrastructure. Dealing with updates, patches and
infrastructure is the responsibility of the platform provider. FaaS are
short lived processes which will be instantiated and destroyed in a
matter of milliseconds making it more resilient to denial-of-services
(DoS) and also makes it harder to attack and compromise. But will all of
this be sufficient to be ’secure’ or should we be worried about more?
With serverless there is still a piece of software that will be
developed, build, deployed and executed. It will also introduce a more
complex architecture with corresponding attack surface which also makes
it hard to monitor. What about the software supply chain and delivery
pipeline? There still will be a need to patch your software for
vulnerabilities in code and used 3rd party libraries. In this talk we
will identify the security area’s we do need to focus on when developing
serverless and define possible solutions for dealing with those
problems.

**Niels Tanis** has got a background in .NET development, pentesting and
security consultancy. He also holds the CSSLP certification and has been
involved in breaking, defending and building secure applications. He
joined Veracode in 2015 and right now he works as a security researcher
on a variant of languages and technologies related to Veracode’s Binary
Static Analysis service. He is married, father of 2 and lives in a small
village just outside Amersfoort, The Netherlands.

**Building a security test automation framework** Either to implement in
your SSDLC, or you just want to have a security test automation
framework to i.e periodically scan your infrastructure?

In this talk, I am going to present some best practices for how to build
a "security test automation framework". These best practices derived
directly from all the pitfalls I encountered from implementing these
type of solution for my customers.

This talk teaches how to create an agnostic and scalable solution with
Docker and Kubernetes. Dockerize your favorite security tooling Deploy
these containers in your Kubernetes cluster This talk teaches how to
manage your findings effectively with a vulnerability management
solution

  - Use Defect Dojo to manage your vulnerabilities
  - Use Defect Dojo for Delta reporting
  - Use Defect Dojo for false positive suppression

This talk teaches how to prevent key sprawl and manage your secrets with
a Keyvault

  - Store and manage your API keys
  - No more hardcoded secrets in your application
  - Even use it to build TOTP (Time based one time passwords)

This talk teaches you everything you need to know to get started with
security test automation and how to implement your favorite security
tooling into different CI/CD platforms (Jenkins, VSTS, Travis, etc) and
into their pipelines.

  - **Riccardo ten Cate**

As a penetration tester from the Netherlands Riccardo specializes in web
application security and has extensive knowledge in securing web
applications in multiple coding languages. Riccardo also has expertise
on implementing security test automation in CI/CD pipelines and is a
project leader of the OWASP Security knowledge framework.

## June 28, 2018

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/250034898/>

  -
    18:30 - 19:00 Dinner
    19:00 - 19:15 Welcome, OWASP update
    19:15 - 20:00: Building a Security ‘Culture’ by Gareth O’Sullivan
    20:15 - 21:00: Building secure software with OWASP tools and guides
    by Martin Knobloch
    21:00 - Closing

<!-- end list -->

  - Vergader Inn
    Croeselaan 207
    3521 BN Utrecht

'''Building a Security ‘Culture’ ''' Rushing Towards Digital
Transformation Breaches. Despite significant investments in security
technology and processes, attackers still gain access to protected data
on a regular basis. IT builds higher and higher walls around the
locations where data lives but attacks persist. Mass migration to cloud
computing has improved scalability, lowered costs, and freed IT from
having to manage the application environment. However, this means cloud
becomes a target for attackers, and it becomes more risky to store
sensitive data there. BYOD makes users’ devices a target as well.
Obviously from a security standpoint, the greater number of devices
there are to manage, the greater the risk of attack. What to do, and
where to start?

**Gareth O’Sullivan** Lead Technology Research Consultant at Genomics
Medicine Ireland, a company helping map the Irish Genome & recently
established as Managing Director of Progress Distribution Ireland a
leading EMEA Cyber Security distributor. Gareth is an IT Security
Executive with 20 years’ experience in the software industry, 13 of
which have been security focused. Previously Snr Director of Solutions
Architecture at WhiteHat Security covering EMEA plus similar roles in
the past with IBM & Watchfire. Technical, Compliance and Commercially
focused so enjoy engaging with technology but also like to build teams,
conducting business development, sales channel development & pipeline
generation.

**Building secure software with OWASP tools and guides** All know the
OWASP TopTen, some one or more other projects. The problem is, where the
wiki is good to archive the project information, it is hard to find
information if you don't know what you are looking for. Therefore, only
a few have a broader understanding of projects (being tools or guides)
you can use in your software development lifecycle, even before, to
create more secure software. This talk is highlighting various OWASP
projects taking you from CISO policies, security requirements to
building and secure software and verifying the security level.

**Martin Knobloch** is security consultant at Xebia.com. His main
working area is (software) security in general, from awareness to
implementation. In his daily work, he is responsible for education in
application security matters, advise and implementation of application
security measures. With his background in Java Development, he
understands the complexity of Enterprise software development, Agile
Scrum environments and continuous delivery / deployment.

## April 12, 2018

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/248338412/>

  -
    18:30 - 19:00 Dinner
    19:00 - 19:15 Welcome, OWASP update & Inspire introduction
    19:15 - 20:00: Adding Privacy by Design in Secure Application
    Development by Sebastien Deleersnyder
    20:15 - 21:00: Smashing Ethereum Smart Contracts for Fun and ACTUAL
    Profit by Bernhard Mueller
    21:00 - Closing

<!-- end list -->

  - Inspire
    Voetiusstraat 2
    3512 JM Utrecht

**Adding Privacy by Design in Secure Application Development** The
General Data Protection Regulation (GDPR) is coming. One monumental
change is the introduction of Privacy by Design. In this presentation we
will focus on the Privacy by Design (PbD) implications for developers.
Two cornerstones for a successful implementation of PbD will be pitched:
1) the integration of GDPR in a Secure Development Lifecycle approach 2)
threat modeling and GDPR risk patterns

  -
    **[Download the presentation as
    PDF](Media:TOREON_Adding_Privacy_by_Design_in_Secure_Application_Development_v20180412.pdf "wikilink")**

**Sebastien Deleersnyder** is Co-founder & managing partner application
security at Toreon.com. Sebastien has helped various companies improve
their ICT-, Web- and Mobile Security, including BNP Paribas Fortis, Atos
Worldline, KBC, Nationale Nederlanden (ING), Isabel, Fluxys, OLAF, EU
Council, TNT Post, Flemish Community, Agfa-Gevaert and ING Insurance
International. Sebastien is the Belgian OWASP Chapter Leader, co-project
leader of the OWASP SAMM project, served on the OWASP Foundation Board
member (2007-2013) and performed several presentations and trainings on
Web Application, Mobile and Web Services Security. Ethereum is an open
software blockchain platform that enables developers to build and deploy
decentralized apps. Over the past couple of years, its cryptocurrency
Ether has taken the number two spot in market cap second to Bitcoin.

**Smashing Ethereum Smart Contracts for Fun and ACTUAL Profit** In
Ethereum, state transitions are mediated by code (a.k.a “smart
contracts”) running in the Ethereum Virtual Machine (EVM) which boasts
a turing-complete instruction set, allowing for near-unlimited use cases
including (but not limited to) crypto kitties. However, with great
flexibility comes great potential for vulnerabilities. And in accordance
to Murphy’s law, disaster has stricken several times, resulting in
hundreds of millions worth of Ether being stolen or stuck in limbo for
all eternity. In this talk, I will investigate recent incidents, and
shed light on the various types of flaws that occur in Ethereum smart
contracts. I’ll show how to explore the blockchain and reverse engineer
smart contract binary code using Mythril, the “nmap of Ethereum”. I’ll
also demonstrate the use of symbolic analysis to detect different types
of vulnerabilities, including those resulting from inter-contract calls.
Finally, I’ll show how to autogenerate Ethereum exploits using the Z3
solver.

  -
    **[Download the presentation as
    PDF](https://conference.hitb.org/hitbsecconf2018ams/materials/D1T2%20-%20Bernhard%20Mueller%20-%20Smashing%20Ethereum%20Smart%20Contracts%20for%20Fun%20and%20ACTUAL%20Profit.pdf)**

**Bernhard Mueller** is a security engineer at Consensys and a hacker
with a decade-long track record. He has found dozens of zero day flaws
in widely used software, published attacks on core Internet protocols,
and written award-winning papers. He is also a winner of BlackHat’s
“Best Research” Pwnie Award.

## March 8, 2018

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/248125406/>

  -
    18:00 - 18:45 Registration & Pizzas
    18:45 - 19:00 Welcome & OWASP update
    19:00 - 19:15 TNO introduction
    19:15 - 20:00 Faalkaart by Elger Jonker
    20:00 - 20:15 Break
    20:15 - 21:00 Second talk by Edwin van Andel
    21:00 - 21:30 Networking and discussion

<!-- end list -->

  - TNO
    Eemsgolaan 3
    Groningen

## February 8, 2018

<https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/247313273/>

  -
    18:30 - Start
    18:45 - Order food/dinner
    19:30 - Presentation about Faalkaart by Elger Jonker.
    20:30 - Meet'n' greet - Time to meet your peers\!
    21:00 - Closing

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## December 7, 2017

OWASP Netherlands Meetup\!
[registration](https://www.meetup.com/nl-NL/OWASP-Chapter-Netherlands-Meetup/events/244959136/)

## November 9, 2017

OWASP Netherlands Meetup\!
[registration](https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/243179151/)

  -
    18:30 - Doors open / buffet (sponsored by Xebia)
    19:15 - Talk:
      -
        In de Ict-industrie zit naarstig te wachten op het eigen
        incident dat een groot verschil gaat maken in het denken over
        beveiliging. De OWASP TOP-10 is het triest bewijs dat veel
        organisaties, maar bitter weinig leren van beveiliging. Hoe
        anders is dat in transport geweest toen het denken radicaal
        omsloeg na de ondergang van de Titanic. Gaat nu opnieuw
        logistiek opnieuw voor de omslag in denken zorgen of wachten we
        op een andere ramp? Want dat technologie juist in die industrie
        een alles veranderende rol staat spelen, kan tot weinig
        discussie leiden. En als de verandering komt hoe ziet dan de
        wereld eruit? Is OWASP klaar voor zo’n nieuwe situatie?
        **Brenno de Winter** (1971) schreef zijn eerste
        computerprogramma op vijfjarige leeftijd en is sindsdien altijd
        met technologie bezig geweest. Hij is al jaren bezig met
        beveiliging. Tijdens zijn jaren als journalist schreef hij menig
        verhaal dat een fundamentele discussie startte of het nu ging
        over het kraken van de OV-chipkaart, Diginotar, de duizenden
        lekken die rond lektoner naar voren kwamen of falend beleid. Als
        boekenschrijver schreef hij diverse titels en werkt hij aan eend
        methodiek om meer ‘zeewaardig te worden’ op beveiligingsgebied.
    20:15 - Meet'n' greet
      -
        Time to meet your peers\!
    21:30 Closing

Where:

`   Xebia`
`   Wibautstraat 200, 1091 GS Amsterdam`

## October 5, 2017

OWASP Netherlands Meetup\!
[registration](https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/242139520/)

  -
    18:30 - Doors open / buffet (sponsored by Xebia)
    19:15 - Talk: OWASP Global and Netherlands update
    :\*Looking back on the past AppSec-US
    :\*Looking forward to the BeNeLux-Day 2017
    20:15 - Meet'n' greet
      - Time to meet your peers\!
    21:30 Closing

Where:

  -
    Xebia
    Wibautstraat 200, 1091 GS Amsterdam== September 7, 2017 ==

OWASP Netherlands Meetup\!
[registration](https://www.meetup.com/OWASP-Chapter-Netherlands-Meetup/events/242773196/)

  -
    18:30 - Doors open / buffet (sponsored by Xebia)
    19:15 - Talk: OWASP Security Knowledge Framework, 2.0
      - Glenn and Riccardo ten Cate will talk about the OWASP Security
        Knowledge Framework (SKF) and the new features of the 2.0
        release
    20:15 - Meet'n' greet
      - Time to meet your peers\!
    21:30 Closing

Where:

  -
    Xebia
    Wibautstraat 200, 1091 GS Amsterdam

## June 8, 2017

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/240446300/>

  -
    18:30 - Start
    19:00 - Order food
    20:00 - Discussions/networking/updates

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## April 6, 2017

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/238715293/>

  -
    18:30 - Start
    19:00 - Order food
    20:00 - Discussions/networking/updates

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## December 1, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632198/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## November 3, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632193/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## October 6, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632186/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## September 1, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632177/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## August 4, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/kkcwnlyvlbgb/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## June 2, 2016

<https://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632164/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## May 12th, 2016

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228094227/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## April 7th, 2016

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228632149/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## March 3rd, 2016

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228104950/>

  -
    18:30 - ? chat, brainstorming etc.

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## February 4th, 2016

Kick-Off BBQ, location to be announced to whom has registered:

  -
    <http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/228093822/>

## December 3rd, 2015

  -
    18:30 - ? chat, brainstorming etc. / bijkletsen

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## November 5th, 2015

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/226036523/>

  -
    18:30 - ? chat, brainstorming etc. / bijkletsen

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## October 1st, 2015

  -
    18:30 - 19:00 walk-in / in-loop
    19:00 - 19:30 announcements / aankondigingen
    19:30 - ? chat, brainstorming etc. / bijkletsen

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## September 3rd, 2015

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/224672626/>

  -
    18:30 - 19:00 walk-in / in-loop
    19:00 - 19:30 announcements / aankondigingen
    19:30 - ? chat, brainstorming etc. / bijkletsen

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>

## August 6th, 2015

<http://www.meetup.com/OWASP-Chapter-Netherlands-Utrecht-Meetup/events/224046536/>

  -
    6:30 - 7:00 walk-in / inloop
    7:00 - 7:30 kennismaking / introductions
    7:30 - 8:00 aankondigingen / announcements
    8:00 - 8:30 Vragen / Q & A, einde

<!-- end list -->

  - Restaurant De Branding
    Croeselaan 303
    3521 BT Utrecht
    030-2900299
    <http://www.restaurantdebrandingutrecht.nl/>