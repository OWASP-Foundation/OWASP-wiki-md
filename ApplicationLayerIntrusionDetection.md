**Application Layer Intrusion Detection**

Today’s applications are responsible for securely performing critical
operations for individuals and businesses around the world. From
transferring money, to managing health records, web enabled applications
handle immense amounts of sensitive data each day. Despite the critical
role they play, the security defenses within these applications are
seriously lacking. The attackers are organized, motivated, and backed by
a network of resources and talent. If our applications have any hope of
standing up to such formidable opponents, then we need to move beyond
just attempting to design our applications securely. We need to
implement robust attack detection within the application to identify
malicious users before they are successful in their attack. Just like in
the real world, we would prefer to detect and prevent an attack instead
of just responding after a compromise has occurred.

How do we bridge the technology gap to implement appropriate security
controls in our critical applications? The first step is to realize that
in order to detect and respond to malicious activity at the application
layer we need to be able to monitor and understand a user’s actions
within the application. Security approaches of previous years are not
sufficient. A firewall provides no protection; its purpose is to allow
users to access the application. Nor does a network based IDS system
since it will have no insight to our application specific traffic.
Antivirus is also out of the question since this is a signature based
approach that knows nothing of custom web application vulnerabilities.

We need to move into the application layer to understand our attackers.
One potential solution is a web application firewall (WAF). A WAF is
able to detect generic application attacks such as basic SQL injection
attacks or common actions of a known attack sequence. While some
detection is better than none, a generic product could never fully
understand the intricacies of each custom web application. This approach
is just not sufficient to properly protect critical applications that
process sensitive financial data or personal user information. Imagine
trying to design an effective building alarm system without any
knowledge of how the building is designed or even where the doors and
windows are located.

The solution is to design and integrate a detection and response system
into the application itself. Within the application we have a full
understanding of the user initiating an action, the target of that
action and whether that action should be allowed for that user. Inside
the application our protection system can identify advanced attacks that
are attempting to exploit specific features of our application. Within
the application we can easily identify attempts to circumvent security
controls or use the application in an unintended manner. After we have
determined that a particular user has malicious intent and is attempting
to identify weaknesses in our system, we can immediately respond and
block the user from future access to the application, or take whatever
other action is appropriate. Once locked out, such users can no longer
login and are limited to attacking the perimeter of an application,
which often contains limited functionality and is typically well
secured. Alternatively, some organizations may wish to forego an
automated lockout response and instead generate an attack alert and
allow their security-monitoring center to perform an immediate
investigation and decide upon the appropriate response.

The rigor of response is a decision for each organization in relation to
their tolerance for risk and specific needs for an application. However,
it is clear that this level of detection capability is a must for any
organization wishing to prevent skilled and persistent attackers from
compromising their critical applications.

**OWASP AppSensor**

OWASP is committed to the protection of applications through application
attack detection and automated response. The OWASP AppSensor project has
been established in response to the clear need for guidance and
knowledge in this area.

AppSensor provides the following:

  - Recommendations for what application actions should be detected as
    malicious along with suggested responses
  - Guidance on designing and implementing an attack detection and
    response system within an application
  - A Java reference implementation that you can integrate into your
    application as the basis for your Application Layer Intrusion
    Detection and Response mechanism

Find out more at: [The OWASP AppSensor
Project](:Category:OWASP_AppSensor_Project "wikilink")