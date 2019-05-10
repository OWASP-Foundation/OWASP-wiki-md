## Topic: Pulling the Plug: Security Risks in the Next Generation of Offline Web Applications

  - [Pulling the Plug: Security Risks in the Next Generation of Offline
    Web
    Applications](http://www.owasp.org/images/b/bc/Sutton_-_Pulling_The_Plug-Security_Risks_in_Next_Generation_Offline_Web_Apps_-_OWASP_LA_OC.pdf)

## Speaker: Michael Sutton

Michael Sutton,Vice President and security research at Zscaler, has
spent more than a decade in the security industry conducting
leading-edge research, building teams of world-class researchers and
educating others on a variety of security topics. As VP of Security
Research, Michael heads Zscaler Labs, the research and development arm
of the company. Zscaler Labs is responsible for researching emerging
topics in web security and developing innovative security controls,
which leverage the Zscaler in-the-cloud model. The team is comprised of
researchers with a wealth of experience in the security industry.

Prior to joining Zscaler, Michael was the Security Evangelist for SPI
Dynamics where, as an industry expert, he was responsible for
researching, publishing and presenting on various security issues. In
2007, SPI Dynamics was acquired by Hewlett-Packard. Previously, Michael
was a Research Director at iDefense where he led iDefense Labs, a team
responsible for discovering and researching security vulnerabilities in
a variety of technologies. iDefense was acquired by VeriSign in 2005.
Michael is a frequent speaker at major information security conferences;
he is regularly quoted by the media on various information security
topics, has authored numerous articles and is the co-author of Fuzzing:
Brute Force Vulnerability Discovery, an Addison-Wesley publication.

## Abstract: Pulling the Plug: Security Risks in the Next Generation of Offline Web Applications

As the line between desktop and web applications becomes increasingly
blurry in a web 2.0 world, browser functionality is being pushed well
beyond what it was originally intended for. Persistent client side
storage has become a requirement for web applications if they are to be
available both online and off. This need is being filled by a variety of
technologies such as Gears (formerly Google Gears) and the Database
Storage
\<<http://webkit.org/blog/126/webkit-does-html5-client-side-database-storage/>\>
functionality included in the emerging HTML 5
\<<http://dev.w3.org/html5/spec/Overview.html>\> specification. While
all such technologies offer great promise, it is clear that the vast
majority of developers simply do not understand their security
implications.

Researching a variety of currently deployed implementations of these
technologies has revealed a broad scope of vulnerabilities with
frightening implications. Now attackers can target victims not just
once, but every time they visit a site as the victim now carries and
stores the attack with them. Imagine a scenario whereby updated
confidential information is forwarded to an attacker every time a victim
interacts with a given web application. The attacker no longer needs to
worry about timing their attacks to ensure that the victim is
authenticated as the victim attacks himself\! Limited storage? Cookies
that expire? Not a problem when entire databases are accessible with
virtually unlimited storage and an infinite lifespan. Think these
attacks are theoretical? Think again. In this talk we dive into these
technologies and break down the risk posed by them when not properly
understood. We will then detail a variety of real-world vulnerabilities
that have been uncovered, including a new class of cross-site scripting
and client-side SQL injection.