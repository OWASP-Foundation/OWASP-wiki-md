__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

Capture the Flag Arena is a capture the flag game where teams compete
against each other in a closed network called the Arena.

Teams obtain points by protecting their services, by planting flags on
other teams’ servers, and by DOS'ing other teams’ services in the Arena.
There are a set of “reference” services provided by the Arena, thus
allowing for teams to be offensive only; however teams that elect to
defend services have the opportunity to collect more points than
possible through attacks alone.

The number of available teams will be limited by the amount of hardware
available. As competitors sign up to join the game they may choose to
join an existing team (if one is available) or they may choose to start
a new team (if one is available). A competitor may join the game only
once.

As the game progresses each team may elect to start supporting or to
cease supporting one or more services (DNS, HTTP, SSH, ...). A team may
select from different VMs with various services pre-packaged for the
competition. In order to be scored for running any services the team
must support DNS for their domain. Services are provided to teams on
VMs, which have vulnerabilities known to the judges. Such
vulnerabilities are not disclosed before-hand. The Arena provides top
level DNS. Second level domain name service is provided by the DNS
implementation running on a VM selected by the team.

The Arena scoring system checks scores of each service that can be
provided by a team. Defenders receive points for keeping a service
online. Attackers and defender receive points depending on the status of
the services.

Example of Scoring team 4: 1. scoring system gets page
<http://www1.team4.com/scorename1.txt> 2. if downloading the page is
successful them team 4 gets 1 point. 3. if the file matches the value
for team 4 then team 4 gets another point. 4. if the file matches the
value for another team then that team gets a point. 5. scoring system
gets page <http://www1.team4.com/scorename2.txt> 6. if the file matches
the value for team 4 then team 4 gets another point. 7. if the file
matches the value for another team then that team gets a point. There
may be multiple files per service. There may be multiple services per
VM. There may be multiple VMs per team.

Depending on the nature of the attack intended, an attacker may register
with a judge the intent to DOS another team's service(s) along with the
expected time of the outage (start time, length of outage). DOS attacks
are mutiple-point scores based on the amount of time of the outage. The
points are awarded to the attacker only of the stated result is
attained; otherwise the block of points is awarded to the defender.

As the game progresses the judges will release advisories to all
competitors regarding specific vulnerabilities in services and/or
servers that may have been provided during the game.

The scoring system will provide a live display of the score for both the
individual teams as well as for observers at the conference.

Join this live interactive tournament which is sure to be a fun,
challenging learning experience for all. Whether you are eager to prove
your AppSec knowledge and watch as you climb to the top of the Leader
board or simply want to learn more about how to code more securely –
everyone is welcome and there will be prizes / SWAG for the winner(s).
The tournament will be conducted using the Secure Code Warrior platform,
an innovative online, hands-on, gamified SaaS Learning Platform that
actively engages developers to Learn & Build their secure coding skills.
This approach is changing the way developers think and behave as they
build & test software.

Bring your laptop, choose your preferred language/framework, whether it
be C\# (.NET) MVC, C\# (.NET) Web Forms, Java Enterprise Edition, Java
Spring, Python Django, Ruby on Rails and more, and launch into the
AppSec Wars Challenge\! Who will prove to be The Secure Code Warrior?

Threat modeling is a way of thinking about what could go wrong and how
to prevent it. Instinctively, we all think this way in regards to our
own personal security and safety. When it comes to building software,
some teams either skip the important step of threat modeling in secure
software design or, they have tried threat modeling before but haven't
quite figured out how to connect the threat models to real world
software development and its priorities. Threat modeling should be part
of your secure software design process. Using threat modeling and some
principles of risk management, you can design software in a way that
makes security one of the top goals, along with performance,
scalability, reliability, and maintenance.

Objectives: Attendees will learn about Threat Modeling through
understanding concepts and hands-on demos:

1\. Introduction to Threat Modeling, including how to conduct a typical
Threat Modeling session 2. Understand practical strategies in finding
Threats 3. Determine proper Mitigations, and how to apply Risk
Management with the Mitigations 4. Review methods of documenting Threats
5. Hands-on demo of one or two Real World Threat Modeling case studies
6. Hands-on demos of the Microsoft Threat Modeling Tool 2016 and/or
OWASP Threat Dragon For some labs: Laptop recommended, but not required.
GitHub account recommended, but not required.

This workshop will serve as a beginner's guide to Mobile Application
Security. This will enable participants to perform penetration tests on
Android applications. Though the time limit doesn't alow us to cover all
the vulnerabilities ad test cases, it would focus on the methods which a
participant can then build up on.

Outline:

Introduction to Android Security

1\. Android Architecture 2. Most Common Vulnerabilities \[ OWASP Mobile
Top Ten \]

Performing Android Pen Test

1\. Setting up the environment. 2. Intercepting Android Traffic 3.
Common issues with interception and how to bypass them 4. Exploiting
vulnerabilities 5. Reverse Engineering Android Applications. Technical
Requirement: The participants need to bring laptops installed with
Android SDK, Geny Motion, Oracle Virtual Box, Burp Suite/ Charles Proxy.
\[Detailed instructions shall be provided prior to the workshop\]

Tools: Dex2jar, JD-GUI, JustTrustMe, Burpsuite etc.

PS: The workshop shall be detailed on a virtual mobile device. But the
methodology shall be good for physical android devices as well.