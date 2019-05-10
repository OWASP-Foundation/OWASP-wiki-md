
[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

Deployment is the first and sometimes the only experience system
administrators will have with your application. Customers who buy or use
your application appreciate the lower costs of securely deployed
software – if their system administrators do not have to spend hours or
days securing your software, they are far more likely to choose your
software over an insecure competitor.

Ease of deployment is a key consideration for many highly available or
highly changeable systems. Systems have a special knack of buying the
farm at 3 am Monday morning before the busiest day of the year. If your
application can be trivially installed at 3 am by tired and emotional
system administrators, they will remember you fondly when the time comes
for new software or the next version. The worst case alternative is that
your customers may not be around if your software takes three days to
install.

Secure deployment is essential for high value systems. High value
systems require controls in excess of basic software. This chapter
guides you through packaging and deployment issues.

## Objective

To ensure that the application is deployed as easily and as securely as
possible.

## Platforms Affected

All.

## Best Practices

  - Software should have automated installers and provide automated
    uninstallers

<!-- end list -->

  - Software should deploy using a least privilege security model

<!-- end list -->

  - Software should not expose any secrets once installed

<!-- end list -->

  - Documentation should not contain any default accounts, nor should
    the installer contain any pre-chosen or default accounts

<!-- end list -->

  - Every configuration parameter must to be findable

## Release Management

Release management is a formal process designed to ensure that
applications are released in a tested and controlled fashion.

### How to identify if you are vulnerable

Is there release management in place? If so, does it cover?

  - Deployment testing

<!-- end list -->

  - Acceptance testing

### How to protect yourself

  - Read software quality assurance references

<!-- end list -->

  - Write deployment instructions

<!-- end list -->

  - Eliminate all steps that can be automated

<!-- end list -->

  - Implement a deployment acceptance test

## Secure delivery of code

Attackers have been known to send malicious code to end users, so it is
vital that your users and customers can obtain your software in a secure
fashion.

### How to identify if you are vulnerable

Secure delivery of code is relatively simple to test, and even easier to
rectify.

  - Pretend to be a normal customer. Obtain your software in the usual
    fashion.

<!-- end list -->

  - Was it obtained from a retailer or other distributor in hard format?
    If so, does the software contain instructions on how to validate it
    against legitimate deliveries?

<!-- end list -->

  - Does the media contain any viruses or harmful code?

<!-- end list -->

  - Was it obtained from a third party download site? If so, does it
    contain an accurate link back to your site?

### How to protect yourself

Secure

## Code signing

### How to identify if you are vulnerable

### How to protect yourself

## Permissions are set to least privilege

Application owner must to use a different user than sys admin. Only sys
admin have access to root password.

### How to identify if you are vulnerable

  - every employee can access with root/admin user
  - deployment procedures want system privileges
  - live application want system privileges to start

### How to protect yourself

  - create one user for every application
  - every application must uses least privileges
  - deploy and start command does not use root/admin privileges

## Automated packaging

### How to identify if you are vulnerable

### How to protect yourself

## Automated deployment

### How to identify if you are vulnerable

### How to protect yourself

## Automated removal

### How to identify if you are vulnerable

### How to protect yourself

## No backup or old files

### How to identify if you are vulnerable

### How to protect yourself

## Unnecessary features are off by default

### How to identify if you are vulnerable

### How to protect yourself

## Setup log files are clean

### How to identify if you are vulnerable

### How to protect yourself

## No default accounts

### How to identify if you are vulnerable

  - Identify the default user accounts that are standard with the
    product you are using.
  - Run periodic tests to ensure none of the accounts you identify are
    enabled or exist.

### How to protect yourself

  - Never generate common or default credentials.
  - Always remove any default user accounts from the server and
    applications prior to deployment.

## Easter eggs

Easter eggs are mostly small (but sometimes not) hidden features. Often
they will contain the developers' names or activate hidden advanced or
developer features, but occasionally, they are more like
mini-applications. For the most part, they have no business function.

*Figure 7 Adobe InDesign CS SVG Easter Egg*

Easter eggs are fairly popular with developers, but they are problematic
from a software engineering and legal view point. Unless easter eggs
have been sufficiently designed and tested, easter eggs can cause the
application to crash or misbehave. For example, Word 97 contained a
pinball game and Excel 97 contained a small flight simulator. If these
crashed with unsaved data, the application is not acting within design
parameters, opening up liability.

However, there is a case for including debug functionality, as long as
it is tested, not enabled by default, and is documented within the user
or administration manual.

### How to identify if you are vulnerable

### It’s almost impossible to prevent clever

### How to protect yourself

## Malicious software

The delivery of software is littered with examples of software delivered
with something more than the users bargained for.

Examples include:

  - Sony delivered First 4 Internet's XCP (Extended Copy Protection)
    rootkit on millions of audio disks, infecting at least half a
    million PCs. Major legal problems have ensued, and set copy
    prohibition technologies back at least five years

<!-- end list -->

  - Microsoft through a lack of a quality assured distribution process
    (now resolved), distributed viruses on multiple occasions, such as
    the Word macro viruses Concept and Wazzu

<!-- end list -->

  - Microsoft partner and premium support web sites were distributing
    Hotfixes with the FunLove virus in 2001

<!-- end list -->

  - Hewlett-Packard had the FunLove virus on their web site, in 2000 and
    also 2006. Though in 2006 it was a printer that was no longer made
    and the Korean version of Windows 95 drivers for it, so not as big a
    deal as in 2000

<!-- end list -->

  - Linux kernel with a backdoor was submitted to CVS tree in November
    2003. It was spotted (by Larry McVoy) because it had been placed
    directly into CVS, not via BitKeeper

These examples show that distributing malicious software can be highly
embarrassing, extremely expensive (in Sony’s case, hundreds of millions
of dollars) to resolve, and they are often truly trivial to prevent.

In the past, there has been a lot of confusion over the legal status of
'spyware' (e.g. software written so a boss can monitor his employees)
and 'adware' (e.g. software written to collect and send back how many of
a companies sites have been surfed to, or change keywords in search
results). Often they have been distributed with free software, and the
user has agreed in often vague and deliberately verbose legal
agreements, that they can be installed on their system. Usually the
adware is mentioned as a method to 'boost' the user's ability to use a
shopping network, or it's mentioned that information might be sent back
to 'assist in our marketing' or that of partners. This makes it sound as
if it's akin to Web cookies, and that there'll be very little effect on
system performance, and no privacy issues over what is sent back.
However now that the public are becoming more aware of adware, the legal
distinctions are clearer, and the IT security community are quickly
learning which companies that write adware are prepared to play ball,
make their warning notices more useful, make their software less covert,
etc. and which are continuing to write software that violates the user's
privacy and drains system resources.

In most countries, it is now illegal to create, distribute, and use
software that acts in a surreptitious and devious manner. Users will
remember any vendor attempting such criminal sabotage and never buy from
such vendors again. Sony is an excellent case of this; the rootkit
scandal has done their reputation a great deal of damage. In Australia,
such criminal acts are punishable with fines of up to $250,000 per
infected computer, and up to 10 years imprisonment. Similar statutes and
punishments exist in most countries.

'''OWASP is not a source of legal advice; if you think your software
flies close to the wind, you must seek competent legal opinion. Even
better, do not create or distribute such software. Karma will bite you
on the flip side. '''

### How to identify if you are vulnerable

Does your software contain any malicious code, which performs
unauthorized or damaging activity? This could be code like Sony’s root
kit. If so remove it.

Did you check your final software image for known:

  - viruses using at least one up to date virus scanner?

<!-- end list -->

  - spyware using at least one up to date spyware scanner?

You may also wish to check for rootkits as there are specific tools now
available to do that, at least on the Windows and Unix platforms.

Be aware that there are many free spyware scanners available which are
not to be trusted. They may surreptitiously install spyware, then when
they 'find' it, advise that you need to buy the commercial version to be
able to remove it. This situation will hopefully improve now that more
antivirus and security software companies are building integrated
solutions that detect spyware as well as viruses and worms. In the
meantime, stick with the more well-known spyware detection software.

Is it possible for an auditor to determine when this scan took place?

### How to protect yourself

Do not create or distribute malicious software – it is illegal in most
countries.

Scan your final distribution images and media with at least one up to
date virus scanner and at least one spyware checker. Document in your
manual the date of this scan and the software used.

## Further Reading

### Deploying applications

  - (PHP) Deploying PHP web applications with Ant:

<u><http://www.onlamp.com/pub/a/php/2005/12/20/php_ant.html></u>

  - (J2EE) Deploying for the web using Ant:

<u><http://www.onjava.com/pub/a/onjava/excerpt/AntTDG_chap8/index.html></u>

<u><http://www.onjava.com/pub/a/onjava/excerpt/AntTDG_chap8/index1.html></u>

  - (Apple MacOS X) Package Maker

<u><http://developer.apple.com/tools/installerpolicy.html></u>

  - (Many Linux distros) Redhat Package Manager (RPM)

<u><http://www.rpm.org/></u>

  - (Fedora and Red Hat Enterprise Linux) Yellowdog Update Manager (YUM)

<u><http://linux.duke.edu/projects/yum/></u>

  - (Debian, and MacOS X using Fink) Advanced Packaging Tool

<u><http://www.debian.org/doc/manuals/apt-howto/index.en.html></u>

  - (Solaris) Application Packaging Developer’s Guide

<u><http://docs.sun.com/app/docs/doc/806-7008/></u>

  - (Solaris) Blastwave is a project to encourage sharing of free
    software for Solaris 8, 9 and 10. Also called Community Software for
    Solaris (CSW); the end-user uses the pkg-get tool to install
    packages.

<u><http://www.blastwave.org/></u>

  - (FreeBSD) Ports and Packages Collection

<u><http://www.freebsd.org/ports/index.html></u>

  - (Win32, .NET, any framework where xcopy works as a deployment tool)

Microsoft Windows Installer XML (wix), a free Windows installer creator

<u><http://sourceforge.net/projects/wix></u>

### Examples of bad deployment practices

Sony’s root kit settlement will cost Sony more than $150 million and
seriously set back their anti-consumer copy prohibition agenda

  - Sony, Rootkits and Digital Rights Management Gone Too Far:

<u><http://www.sysinternals.com/blog/2005/10/sony-rootkits-and-digital-rights.html></u>

  - Sony has a voluntary recall program for XCP infected disks:

<u><http://cp.sonybmg.com/xcp/></u>

  - Settlement details of at least ten class action lawsuits against
    Sony:

<u><http://www.eff.org/IP/DRM/Sony-BMG/></u>

  - Microsoft distributes macro viruses on CD

<u><http://www.f-secure.com/v-descs/wazzu.shtml></u>

## Links

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Activity](Category:Activity "wikilink")
[Category:Deployment](Category:Deployment "wikilink")