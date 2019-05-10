Now it's time to tell about the hackathon, where 15 OWASP volunteers
from 10 different companies gathered on Wed September 27th to find out
how to add security into devops process in real life. This was done as
a  DevSecOps mini hackathon. While normally hackathons may last even
two full days, this lasted only 12 hours. It was organized at Nixu’s
office in the beautiful Keilaniemi area. We had really enthusiastic
athmosphere\!

Many of the participants already had former experience of the CI tools
and Docker, while the others had experience on some of the security
testing tools, which was a nice starting point for the hackathon. At
least the organizers who prepared the environment definitely learned a
lot while preparing the hackathon setup\! It was a great experience\!
Even if e.g. Docker, Jenkins and the basics of CI were familiar in
theory level for most of the participants, it was exciting to dive much
deeper into the practical challenges of these tools\!

## Goal

Initially, we had prepared a CI setup for OWASP Juice Shop application.
Juice Shop is a web application that intentionally contains typical web
application vulnerabilities, and has a nice set of unit tests and
end-to-end tests. (The project is located here:
https://www.owasp.org/index.php/OWASP_Juice_Shop_Project) This
project was forked into own repository under owasp-helsinki GitHub group
and a Jenkins pipeline was created to build and deploy the Juice Shop as
a Docker container.

We had three tracks in the hackathon:

1.  Application security testing
2.  Platform hardening and testing
3.  Vulnerability management

The main goal of the hackathon was to add security to CI pipeline, by
using open source tools. The maturity and applicability of these tools
for automated use in a CI pipeline was initially unknown. Many of these
tools are developed under an OWASP project. Each track was responsible
of investigating and configuring the tools relevant to their track, and
see how applicable they are.

## Setup

### AWS infrastructure

We had six Amazon AWS Medium EC2 instances that was accessible from the
hackathon Wi-Fi network.

The following diagram describes the setup:
![Hackathon_setup.png](Hackathon_setup.png "Hackathon_setup.png")

Every track had two instances. One instance was for running Jenkins
pipeline defined in GitHub and running the target Juice Shop Docker
image from Docker Hub. The other was for installing the required testing
tools. We wanted to keep the jenkins/deployment environment stable and
to allow flexible installation for the tools.

We shared owasp-hackathon SSH private key and a proper config file for
all participants. Network access to the servers was limited only to the
wi-fi network of the hackathon venue. Accesses from all servers to all
servers were opened at AWS level both from their private and public
IP-addresses, as the traffic was initially blocked. It was also
noteworthy to see that even though the servers were opened at the same
time, the public IP-addresses were in totally different B-class
networks\!

### CI Pipeline

The pipeline was made using Jenkins Pipelines (JenkinsFile), which
contained initially few stages (more info here:
<https://www.owasp.org/index.php/OWASP_Helsinki_DevSecOps_Hackathon>).

Basically the pipeline had initially 5 stages. Stages are the different
phases in Jenkins pipeline, that can be considered as "scripts" and
measured independently.

## Schedule

The event was basically divided into two parts: before-pizza and
after-pizza.

12:00 - 12:30 Introduction to environment, tracks & goals

12:30 - 17:00 Track work

17:00 - 17:30 Preparation of track presentations

17:30 - 18:00 Pizza & beverages

18:00 - 18:30 Tracks presents their results and the next steps

19:00 - 21:30 Track work continues

21:30 - 22:00 Preparation of track presentations

22:00 - 22:45 Tracks presents results

22:45 - 23:00 Final wrap-up

After the first section, the tracks gave a presentation of the
achievements and their intended next steps. Around 22:30 we started to
go through the final achievements and had a quick wrap-up of the
results.

## Achievements

The following simplified diagram summarizes the achievements of the
hackathon. We did not have time to bundle every possible security
testing tool to the pipeline, but each track chose the optimal location
for each stage for the tools.
![Oversimplified_hachathon_pipeline.png](Oversimplified_hachathon_pipeline.png
"Oversimplified_hachathon_pipeline.png")

Here is more complex, and more accurate version of the Pipeline diagram
with all the stages that were in the final pipeline.
![Hackathon_pipeline_final.png](Hackathon_pipeline_final.png
"Hackathon_pipeline_final.png")

As we can see, this diagram looks much more complex than the one we
initially had in mind before the hackathon (presented here:
<https://www.owasp.org/index.php/OWASP_Helsinki_DevSecOps_Hackathon>).
But the same basic stages are there, but split in more specific
locations based on the tool's applicability.

The tracks contributed (at least some) of their work to OWASP Helsinki's
GitHub repository.

<https://github.com/owasp-helsinki/>

The testing images of juice-shop were pushed to Docker Hub under
/helsinkiowasp

### Track 1 achievements: Platform security hardening and testing

Track 1 splitted into two branches, one for hardening the Docker image
and one for testing the Docker image hardening. The hardening branch
started with a nice script for hardening the web server, blocking all
unnecessary and possibly harmful URLS. This branch also applied the
hardening recommendations given in the previous OWASP Helsinki Chapter
meeting (slides here
[<https://www.owasp.org/index.php/File:Owasp-Helsinki-20170613-Docker-Security.pdf>)](https://www.owasp.org/index.php/File:Owasp-Helsinki-20170613-Docker-Security.pdf%29)

Testing branch chose Clair as their tool for testing the vulnerabilities
in the docker container. Clair assumed the target to be in a Docker Hub
or similar public location, and the team spent time to make it available
for local testing. In the end it was also realized that the images can
be pushed to Docker Hub with a tag (e.g. "testing"), to prevent the
image to be run in any real environment.

(MORE INFORMATION TO BE INSERTED HERE)

### Track 2 achievements: Application security testing

Track 2 started to implement OWASP Dependency Check utility, that checks
the versions of the used libraries and reports if there are any known,
publicly disclosed, vulnerabilities. They installed the Jenkins OWASP
Dependency Check Plugin.

Dependency Check scan was added as part of a build process in the
Jenkinsfile. The analyzer was configured to read the npm's package.json
file. The detailed analysis report was seen in the HTML report (but was
not analysed further for detailed findings). Getting the check work as a
Jenkins plugin in the pipeline involved setting up a missing directory
for a feature that was not needed in the first place, but could not be
disabled.

OWASP Zed Attack Proxy (ZAP) was integrated to the build pipeline in two
phases. First, because ZAP doesn't really know a whole lot about the
target application, it needs to be taught how to log in and navigate the
functionality. For that the team used Juice Shop's end-to-end tests, so
that the testing was done with ZAP acting as a passive proxy, recording
the traffic. That involved reconfiguring end to end test to use ZAP as a
proxy, but unfortunately that did break some of the test cases for
unknown reason. Juice Shop does use socket.io in communications, and
finding correct ZAP configs (connection timeouts etc) might have fixed
that.

Second, Jenkins plugin for ZAP was used to scan the target application.
For that the recorded ZAP session was imported to Jenkins ZAP plugin.

One possible concern with the setup was that the target application used
JWT for maintaining authentication, but the expiration time for tokens
turned out to be long enough so that they were still fresh after running
the first phase. (I.e. security scanning could use the same tokens as
end-to-end test.)

Something to look at to make ZAP work more reliably, could be
<https://github.com/continuumsecurity/bdd-security>, which was not
assessed during this hackathon.

Plugin installations and configuring was done directly at Jenkins, which
ran in a container, so it was not a persistent way to store them.

### Track 3 achievements: Vulnerability management

The goal of this track was to apply vulnerability management practices.

Track started by investigating the Defect Dojo tool. It was quite
straightforward to understand the data model, which contained:

  - product type (e.g. for grouping critical business applications)
  - product (separate applications / systems)
  - engagements (for linking various testing activities to specific
    product)
  - test (to describe specific type of test done during an engagement)
  - finding (an issue found during the test)

They created a business critical product type, and created a product
called "Juice Shop". First they played with different engagements and
tests to find the proper way of using the system in vulnerability
management. Then the importing capabilities were tested from ZAP tool.
This worked well, but importing an OWASP Dependency checker file crashed
the system, which was probably due to a newer file format that the
system expected. Creating findings manually worked well.

Lot of time was spent trying to figure out how to import files via the
API. Eventually, a nice script was pointed in the Defect Dojo slack
channel:
<https://github.com/aaronweaver/defectdojo_api/blob/master/examples/dojo_ci_cd.py>.
There was not enough time to make this work properly in the pipeline, as
the proper way of usage of that (API keys, etc) was found too late.
However, this probably could take it a bit further.

JIRA integration took a lot of time. The JIRA instance itself was easy
to run as a docker container, short configuration. Defect Dojo had
generally a good documentation and also instructions to setup JIRA
bidirectional integration. However, we had already created the product.
Enabling JIRA did not enable JIRA configuration options for the existing
Juice Shop project. After a long struggle, we asked for help at the
Slack channel again. Got some answers from the developer, and then we
tried to create a new project, and voilá, the JIRA options appeared to
this new product. However, we could not get any JIRA issues to be
created, and thus could not test the JIRA webhook based JIRA→DefectDojo
integration.

This track was evaluating this pipeline with Defect Dojo / JIRA etc.
form NIST vulnerability management program perspective. They found that
quite many areas are actually not covered by these tools, but a quite
good coverage can be achieved by applying some processes especially to
JIRA -\> Developers, Admins and Decision makers. Initial slideset on
this topic was created, but it will probably still evolve.

Possible observations/bugs were detected during the hackathon:

  - Crashes when importing OWASP Dependency Check files
  - If JIRA integration is enabled later, the products created before
    JIRA integration cannot be configured to use JIRA
  - JIRA import does not start for ZAP file import
  - JIRA issues were not created, even though the Celery started
    processing a new issue. No error messages or whatsoever could be
    found.
  - Uploading Threat modeling documentation crashed the system
  - Scanning DefectDojo with ZAP made the system very unstable, and we
    had to reinstall it.

## Lessons learned

The most obvious thing we learned was that the tools we tested are not
yet mature to be easily bundled into a CI pipeline. We had many
experienced people trying to make these tools work. Even though the
tools generally had quite good documentation, our use cases seemingly
were not the typical use case scenarios. Therefore, at the current
state, we think that implementing security into the CI pipeline with the
open source tools that were used in this hackathon, may be slow and
expensive. Many of the features are not very well documented, and they
contain bugs that are time consuming to debug.

During this hackathon, we did not get the whole "ideal" process working,
so we don't know what kind of practical challenges it might have.
However, some thoughts rose into mind:

  - There is a lot of noise and false positives in the vulnerability
    scanner results. This should be reduced so that the accuracy of the
    tools used in the CI/CD-pipeline should be maximized by using lot of
    effort in proper configuration. Instead of getting maximum amount of
    findings, concentrate on getting real findings.
  - Communication to the business people may be tricky, as these tools
    cannot tell the business impacts of the identified vulnerabilities,
    which may slow down the decision process.

Generally this hackathon was considered to be a success what comes to
learning. We had a question round in the end, and every participant had
a good learning experience, both security tools and the world of CI
pipelines and Docker. CI pipelines generally are becoming more and more
familiar concept, but security testing bundled to that is still
something not many are actively doing. This hackathon was a journey to
find out reasons why, and even in this short time we were able to
conclude that this area still requires more development and community
work to make this more practical and straightforward to start be used
daily as a part of CI.

If you have been building or seen working pipelines with these tools (or
some other) bundled, please let us know how well it has worked. We know
that there are also commercial vendors that are actively making their
tools CI/CD compliant, and we are also interested in hearing of success
stories related to any free or commercial tools, with practical examples
how they are used, and how well they work.

## Future work

It would be really nice to see the whole pipeline with all stages
working, as there are not many good real life practical examples
available. Many high level diagrams have been seen in many
presentations.

During the hackathon we found an OWASP project AppSec Pipeline which
looks interesting:
<https://www.owasp.org/index.php/OWASP_AppSec_Pipeline#tab=Main> This
definitely is worth looking a bit futher, even though the latest
activities seemed to be from 2015.

If anyone has pointers to good and practical CI/CD-pipelines with
security tools bundled in, we are interested to hear about those\!

The following action points were left open:

  - Investigate more Engagement survey addon for Defect Dojo, that
    allows inputting more specific background information about the
    engagement for the record
  - If this pipeline finally starts working, we could start including
    other tools and make practical Jenkins pipelines / stages available
    for easy installation, and practical instructions on how to start
  - Code analysis tools should be bundled there too
  - Should we organize a new Hackathon? This was considered a really
    good way of learning - and many participants were eager to join then
    next time, so definititely yes\!