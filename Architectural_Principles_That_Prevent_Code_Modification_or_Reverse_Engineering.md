__NOTOC__ ![MainProjectIcon.png](MainProjectIcon.png
"MainProjectIcon.png") This content is part of a much bigger project. To
return to the main umbrella project, visit the [Reverse Engineering and
Code Modification Prevention
Project](https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project).

__TOC__

# Introduction

## Relevant Audiences

This guide is relevant to technical audiences that are responsible for
designing or proposing the technical architecture behind software that
is hosted in an untrustworthy environment. Untrustworthy environments
are those not under a developer’s control. Although this guide
identifies risks that apply to all untrustworthy environments (e.g.,
firmware, thick-clients, cloud), specific examples and attacks are
provided using mobile devices.

Often, relevant technical audiences have the following role titles:

  -
    \* Enterprise Architect;
    \* Solution Architect;
    \* Security Architect;
    \* Software Architect;
    \* Infrastructure Security Specialist Architect;
    \* Web Application Security Architect; or
    \* Lead Software Engineer

The relevant audience is interested in exploring architectural features
of software that should be included to mitigate mobile application
operational risks related to application integrity violation.

## Goals of this Guide

This guide helps Architects formulate appropriate application solutions
that mitigate operational risks specific to mobile device applications.
These risks are outlined in a related OWASP project titled, ["Technical
Risks of Reverse Engineering and Unauthorized Code
Modification"](http://www.owasp.org/index.php/Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification).

This project has several different goals that are outlined below:

### Integrity Risk Education

Software Architects must take into account many different competing
design factors when proposing a technical architecture for a mobile
device application. When considering the security of the application’s
solution, architects must propose various controls that will mitigate
several different types of operational risk. Relevant technical risks
that stem from mobile device applications include: hardware
infrastructure, code, and application integrity. This section of the
guide highlights application integrity risks that an architect should be
aware of when designing mobile device application solutions.

### Architectural Solution Components

To reduce application integrity risks to an acceptable level, an
architect must integrate particular security controls at the right
locations within the mobile device application. This section of the
document highlights a catalog of potential architectural controls that
are relevant to mitigating application integrity violation risks. As
part of the architectural formulation process, the architect must choose
particular technologies to leverage in the final solution. These choices
can have varying impacts on the following aspects of the mobile device
application: performance; scalability; and maintenance. This section of
the guide highlights the potential impacts of integrity security
controls on the final solution.

# Integrity Risk Education

## Evolution of Application Security Threat Landscape

Historically, organizations offered their customers web applications
that exposed an interface to some necessary business services. The
services expose high-value functionality that allows an organization to
deliver value to its clients. Attackers had a specific set of threats or
goals that they realized by exploiting vulnerabilities that the
organization exposed through the application’s presentation layer.
Security practitioners address these specific sets of vulnerabilities
through the web application or the associated infrastructure security
disciplines.

Often, attackers launch successful attacks by providing malicious input
that they fed into the web application’s presentation layer. Classic
attack vectors used by attackers that use this technique include: SQL
Injection, Cross-Site (XSS) Scripting, and URL parameter tampering
vulnerabilities. Often, security professionals detect the presence of
these vulnerabilities through source code analysis or penetration
testing. In response to the detection, security professionals recommend
to the organization that its Software Engineers should mitigate these
vulnerabilities by applying secure coding techniques and adding
appropriate data validation security controls to the affected
application. Generally, this is sage advice and it works well for
traditional web-based applications. In this common scenario, this advice
is enforceable because the organization is hosting the web application
in a highly controlled (more trustworthy) environment where only the
organization’s Software Engineers can modify the application’s
underlying code.

In present day, consumers have demanded much more convenient access to
functionality than what organizations could traditionally offer through
web applications accessible via desktop browsers. In response to these
demands, organizations began augmenting the user experience with mobile
applications.

In making the switch to mobile applications, organizations are now
deploying more of the presentation layer and business layer of the
application on a mobile device instead of on their own servers. As a
result, they lose a lot more control over who gets to see or modify
their application’s code. Before the switch, most of the application’s
presentation and business layer functionality was hidden within the
organization’s trusted server environments. Outside users or attackers
did not get much of an opportunity to see executing code in action. With
the recent move towards mobile applications, an attacker can now see,
touch, and directly modify the application’s presentation and business
layer code within the attacker’s mobile computing environment. This
capability allows the attacker to realize the same traditional business
threats as before (with web applications) but in genuinely new and
unconventional ways.

In general, attackers have far more security expertise than the
computing industry and are quite successful in exploiting mobile
application integrity risks. Most mobile application Software Engineers
are not producing mobile applications that will defend themselves
against reverse engineering by the attacker.

## Application Integrity Threats

Attackers can now leverage reverse-engineering / code modification
attack techniques inside mobile device applications to realize the
following threats:

:; Spoofing Identity

  -

      -
        Attackers may attempt to modify the mobile application code on a
        victim’s device to force the application to transmit a user’s
        authentication credentials (username and password) to a third
        party malicious site. Hence, the attacker can masquerade as the
        user in future transactions;

:; Tampering

  -

      -
        Attackers may wish to alter higher-level business logic embedded
        within the application to gain some additional value for free.
        For instance, an attacker may alter digital rights management
        code embedded in a mobile application to attain digital assets
        like music for free;

:; Repudiation

  -

      -
        Attackers may disable logging or auditing controls embedded
        within the mobile application to prevent an organization from
        verifying that the user performed particular transactions;

:; Information Disclosure

  -

      -
        Attackers may modify a mobile application to disclose highly
        sensitive assets contained within the mobile application. Assets
        of interest include: digital keys, certificates, credentials,
        metadata, and proprietary algorithms;

:; Denial of Service

  -

      -
        Attackers may alter a mobile device application and force it to
        periodically crash or permanently disable itself to prevent the
        user from accessing online services through their device; and

:; Elevation of Privilege

  -

      -
        Attackers may modify a mobile application and redistribute it in
        a repackaged form to perform actions that are outside of the
        scope of what the user should be able to do with the app.

## Steps to Conduct an Attack

<table>
<tbody>
<tr class="odd">
<td><p>Unprotected mobile apps can easily be cracked open, analyzed, modified, and exploited by hackers. In addition to exploiting flaws, attackers can directly access the binary and compromise its integrity with various tools and techniques:</p>
<p>:* Decompilers and disassemblers;</p>
<p>:* Jailbreaking / Rooting, Encryption removal; and</p>
<p>:* Code editors and exploit creation.</p>
<p>Safe coding alone cannot prevent these attacks as code written with secure coding techniques can be reverse-engineered and modified. To realize mobile app integrity threats, the attacker will execute the steps highlighted in the graph to the left in order to conduct a reverse engineering attack against the mobile device app.</p></td>
<td><figure>
<img src="Binary_Attack_Overview_Process_Graph.png" title="Binary_Attack_Overview_Process_Graph.png" alt="Binary_Attack_Overview_Process_Graph.png" width="400" /><figcaption>Binary_Attack_Overview_Process_Graph.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Attacks using this technique are now fairly common and achievable.
Studies show that today's mobile banking apps were largely not protected
against reverse-engineering or tampering attacks. These apps revealed
highly sensitive information that should not be disclosed, and their
operations and data were exposed in the clear, wide open to examination
and manipulation.

### Survey Phase

Figure 1 illustrates the general steps that an attacker must
successfully execute in order to gather intelligence about the app they
wish to integrity-attack: ![surveyPhase.png](surveyPhase.png
"surveyPhase.png")

For an iOS mobile app, the attacker will need to compromise their own
iOS device and trick it into downloading and executing malicious tools
that allow the attacker to inspect other apps on the iOS device. This
occurs during the ‘Exploit Phone’ and ‘Install Inspection Tools’ phases
depicted by Figure 1. After the attacker has successfully compromised
their own iOS device and installed the necessary exploit tools, the
attacker proceeds to download the legitimate app. Figure 1 depicts this
act in the ‘Download App to Phone’ state. For an Android app, the
attacker does not necessarily need to compromise their device. Instead,
the attacker can try running the inspection tools directly within an
Android emulator and explore the attack surface of the app from within
it. If this does not work, the attacker can then compromise their device
and inspect using the same tools.

After the attacker has downloaded the app, the attacker will explore the
exposed functionality of the app. Often, the attacker will pay attention
to sensitive data that is processed by the app. Once the attacker has
examined any exposed functionality or data provided by the user of the
mobile device app, the attacker will need to understand how these assets
are processed by the underlying code. Figure 1 depicts this in ‘Examine
Internals’ phase.

Often, the attacker will go back and forth between discovering new
features of the app and exploring its underlying design at the same
time: ![surveyExamine.png](surveyExamine.png "surveyExamine.png")

### Examine Internals Phase

Once the attacker has established a threat and a goal in mind, the
attacker will need to understand how the app works in order to
compromise these assets. Figure 3 depicts this phase of the mobile
device compromise: ![fsmExamine.png](fsmExamine.png "fsmExamine.png")

On some platforms (Android), an app can simply be opened directly for
further inspection. On other platforms (iOS), an attacker will use one
of many automated and fairly inexpensive tools to decrypt and then open
the app. Figure 3 depicts this within the ‘Run Exploits’ and ‘Decrypt
Application’ processes.

After obtaining the original binary, the attacker can choose to perform
static analysis. Figure 3 depicts this within the ‘Static Code Analysis’
process. Furthermore, the attacker may also engage in dynamic analysis
to observe the runtime behavior of the app. This is depicted as the
‘Dynamic Code Analysis’ process in Figure 3. In both states, the
attacker needs to acquire particular intelligence about the app in order
to violate its integrity. Desirable intelligence includes how data flows
through the app. As well, an attacker will want to know more about how
the app’s code changes control flow paths along various points of
interaction with the end user. In acquiring this intelligence, the
attacker can learn how to alter the flow of sensitive data, bypass
important functionality and modify the behavior of the app.

Upon detailed analysis, the attacker may discover new product features
or abilities that were not exposed through the user interface. For
example, an attacker may discover and enable diagnostic features that
disclose sensitive information about how the app works. Figure 3 depicts
this as a return to the ‘Survey Phase’ states.

Often, the attacker will spend a lot of time going back and forth
between formulating a payload and examining the internals of the app.
Figure 4 depicts this back-and-forth relationship between these two
phases of the operation: ![fsmExaminePatch.png](fsmExaminePatch.png
"fsmExaminePatch.png")

### Patch / Deploy Phase

An attacker may decide that this phase is unnecessary in order for them
to achieve their goals. For example, an attacker may choose to lift
algorithms, extract keys, or gain other sensitive information through
the previous phase using static analysis or dynamic analysis tools.

If the attacker intends on altering the behavior of the app, the
attacker must formulate a malicious payload that will alter the app’s
control or dataflow. The attacker then inserts the payload into the
binary and may execute it only on their mobile device, or they may
choose to distribute the modified binary to a wider audience.

These steps are depicted in the following figure:
![fsmPatchDeploy.png](fsmPatchDeploy.png "fsmPatchDeploy.png")

During this phase, the attacker spends a lot of time experimenting with
code modifications or additions and observing how the app responds. Once
the attacker is satisfied that the modified code behaves accordingly,
the attacker has many different distribution options.

Conventionally, the attacker inserts malicious code into the legitimate
app and redistributes it within a third-party store for distribution.
The victim downloads the modified app through the third-party app store
and executes it locally on their mobile device. At this point, the
attacker has successfully conducted an integrity attack and some sort of
fraud against the user of the app.

Alternatively, the attacker may wish to conduct fraud against the
organization that owns the app rather than the users of the app. In this
scenario, the attacker modifies the app on their device with the goal of
exploiting a server-side vulnerability. The attacker does not have to
distribute any code to a third-party site in order to conduct fraud
against the organization.

## App Modification Threat Examples

It is very common for an attacker to disable security controls and
policies or modify critical functionality. According to Forrester
Research, “Tampering and logic fraud rates are seen increasingly within
mobile environments.”

Common attack targets include:

:\* Security controls and policies;

:\* Credentials;

:\* Cryptography keys;

:\* Communication interception; and

:\* Modification of business logic and restricted functionality.

According to a 2012 study conducted by North Carolina State University,
app-repackaging attacks were the most common form of attack executed by
a hacker. Through repackaging, the attacker installs a malicious payload
through disassembly, payload insertion, and re-assembly. This malware
may infect other apps on the same device without the owner’s knowledge.

The NC study concludes that common malicious payloads include:

:\* Remote control through command-and-control botnets - 93%;

:\* Information stealing (user accounts; sensitive date) – 51%;

:\* Financial charging – 45%; and

:\* Privilege escalation – 37%.

# Architectural Solution Components

Mobile app threats are similar to threats seen within traditional web
applications. To mitigate such threats within traditional web
applications, the organization should include appropriate web
application security controls that are built using secure coding
techniques. Mobile device apps are similar enough to traditional web
applications that the organization should apply the same secure coding
techniques for mobile device apps. However, mobile device apps are
hosted within an untrustworthy environment. As such, they require
additional security controls to mitigate the added risks associated with
integrity violation.

The primary goal of including integrity controls is to disrupt or
prevent the steps necessary to conduct a successful integrity attack
against a mobile app. Each subsection below outlines the relevant
controls that must be put in place to prevent such an attack. Impacts on
the confidentiality, integrity, and availability of the solution are
also considered below.

## Controls

This section of the guide outlines the specific integrity controls that
an architect should consider when choosing to protect the integrity of a
mobile app.

### AntiDebug Controls

Within the ‘Examine Internals’ phase of an attack (outlined in “Steps to
Conduct an Attack” section of this document), the attacker may choose to
examine the app while it is executing to gain a better understanding of
the app’s code structure and control flow. The attacker may choose to do
so by inserting a debugger into the app’s process. This control prevents
the attacker from injecting a debugger into the process and conducting
dynamic code analysis:

![fsmExamineInternals_NoDynamicAnalysis.png](fsmExamineInternals_NoDynamicAnalysis.png
"fsmExamineInternals_NoDynamicAnalysis.png")

In order to prevent modification of code or data at runtime, other
controls are necessary to detect and react to such violations. These
controls are explored below.

### Checksum Control

During the ‘Patch and Deploy’ phase of an attack, the attacker will need
to inject malicious code and test that the app behaves “correctly”. The
checksum integrity control compares a selected region of code at runtime
to what it knows at build time. If the two are not equal, the integrity
control has successfully identified an unexpected code change. It is
then up to the app to decide how to react to such an unexpected change:

![fsmPatchAndDeploy_NoTest.png](fsmPatchAndDeploy_NoTest.png
"fsmPatchAndDeploy_NoTest.png")

### Static Damage Control

Within the ‘Examine Internals’ phase of an attack (outlined in “Steps to
Conduct an Attack” section of this document), an attacker may wish to
gain further intelligence about the app’s control flow via static
analysis tools like IDA Pro or Hopper. At build time, a Static Damage
control “damages” a region of code and stores it in some other location
in the binary. When an attacker attempts to perform static analysis
against the code region they will be misled by the protected region. The
organization can choose to replace the protected region with encrypted
code or unencrypted but unrelated (and misleading) code. At runtime, the
organization must then leverage Dynamic Repair controls to replace the
protected code with a known good copy prior to execution. This control
prevents static analysis of sensitive code:

![fsmExamineInternals_NoStaticAnalysis.png](fsmExamineInternals_NoStaticAnalysis.png
"fsmExamineInternals_NoStaticAnalysis.png")

During the ‘Patch and Deploy’ phase of an attack, the attacker will need
to inject malicious code and test that the application behaves
correctly. The Dynamic Repair control prevents the attacker from
applying and executing malicious code at runtime. This control is
typically used in unison with a Static Damage control. The Static Damage
control is responsible for preventing static analysis. At runtime, the
“damaged” code must be repaired in order to execute the correct code.
The Dynamic Repair control replaces the “damaged” code in memory with
the known good copy of the code just before execution. This good copy
prevents the execution of any modified code inserted by the attacker.
After the code executes, it is important to “re-damage” code in memory
using a Dynamic Damage Control.

The Dynamic Repair control prevents an attacker from inserting modified
code into protected code regions:

![fsmPatchAndDeploy_NoModify.png](fsmPatchAndDeploy_NoModify.png
"fsmPatchAndDeploy_NoModify.png")

### Dynamic Damage Control

During runtime, an attacker may wish to attach a debugger to a process
to see what unencrypted code looks like in memory. For example,
ClutchMod is a particularly useful tool to examine unencrypted code in
the memory of iOS devices. Dynamic Damage controls will replace
protected code in memory with other code segments in a way similar to
the way Static Damage controls work on disk. After a Dynamic Repair
control repairs code to a known good state and the code executes, a
Dynamic Damage control is responsible for replacing the good code with
another copy of the “damaged” or misleading code stored in the binary.

Dynamic Damage controls prevent an attacker from inspecting code or data
within the app’s memory at runtime:

![fsmExamineInternals_NoDynamicAnalysis.png](fsmExamineInternals_NoDynamicAnalysis.png
"fsmExamineInternals_NoDynamicAnalysis.png")

### Obfuscation Control

Within the ‘Examine Internals’ phase of an attack (outlined in “Steps to
Conduct an Attack” section of this document), an attacker may wish to
gain further intelligence about the application’s code by looking at the
code while it is not executing. To do so, the attacker may choose to
engage in static code analysis. The obfuscation control is responsible
making code difficult to understand during static code analysis. Code
can be made harder to understand through a number of different
techniques. These techniques include: polymorphic obfuscation,
method-inlining, insertion of opaque predicates, instruction
substitution, and instruction block chopping.

Effective obfuscation forces the attacker to perform dynamic analysis
instead:

![fsmExamineInternals_NoStaticAnalysis.png](fsmExamineInternals_NoStaticAnalysis.png
"fsmExamineInternals_NoStaticAnalysis.png")

### Renaming Control

Within the ‘Examine Internals’ phase of an attack (outlined in “Steps to
Conduct an Attack” section of this document), an attacker may wish to
gain further intelligence about the application by looking at the
application’s user-specified symbols while the application is not
executing. To do so, the attacker may choose to engage in static code
analysis. The renaming control is responsible for making user-specified
symbols (code or data) difficult to understand through static code
analysis. It is different from an Obfuscation control in that its scope
is severely reduced to just user-supplied class fields and methods
directly exposed through the binary. This has the advantage of reduced
impact on size and performance in comparison to applying traditional
obfuscation techniques. However, it has the disadvantage of shallow
obfuscation.

This control strives to prevent static analysis:

![fsmExamineInternals_NoStaticAnalysis.png](fsmExamineInternals_NoStaticAnalysis.png
"fsmExamineInternals_NoStaticAnalysis.png")

### String Damage Control

Within the ‘Examine Internals’ phase of an attack (outlined in “Steps to
Conduct an Attack” section of this document), an attacker may wish to
gain further intelligence about the application’s internal data by
looking at the application’s string table. To do so, the attacker may
choose to engage in static code analysis. The String Damage control is a
form of obfuscation that is severely reduced in scope to that of the
string table. It is similar to a Static Damage control in that it
encrypts static data. However, it focuses exclusively on the string
table and prevents an attacker from inspecting the string contents at
runtime. At runtime, it must also use a corresponding Dynamic Repair
Guard to replace “damaged” strings with known good strings just before
consumption.

A String Damage control is responsible for making an app’s internal data
difficult to understand and associate with sensitive methods during
static code analysis:

![fsmExamineInternals_NoStaticAnalysis.png](fsmExamineInternals_NoStaticAnalysis.png
"fsmExamineInternals_NoStaticAnalysis.png")

### Jailbreak / Root Detection Controls

During the ‘Patch and Deploy’ phase of an attack, the attacker may need
to inject malicious code and test that the app behaves as the attacker
intends. The attacker may need to do this on a mobile device that the
attacker has compromised. For iOS devices, the Jailbreak control will
prevent the attacker from injecting and executing malicious code within
the mobile app:

![fsmPatchAndDeploy_NoTest.png](fsmPatchAndDeploy_NoTest.png
"fsmPatchAndDeploy_NoTest.png")

The victim may run the legitimate version of the app on a Jailbroken
device. In such a scenario, the device’s overall security has been
compromised. It may be possible to compromise the legitimate app due to
its dependencies for security features contained within its environment.
The Jailbreak control prevents the app from running at all within the
untrustworthy environment.

## Technical Impacts of Controls

Each section below outlines the impacts on a solution that may result
from the inclusion of integrity security controls in the final solution.

### Performance

When an integrity control is inserted into a mobile application, the
mobile application will have additional overhead in performing its
functionality. When an integrity control is invoked by the application,
the application must execute the code associated with that instance of
the integrity control. The amount of resource consumption is dependent
upon a number of different factors: the algorithm behind the control,
invocation location, probability of execution, and protection ranges
associated with each control.

### Algorithm Choice

For example, a checksum integrity control is responsible for verifying
that a protected range of code or data has not been modified in memory
or on disk. For example, hash algorithms used to perform a checksum are
varied in terms of performance. Secure Hash Algorithm (SHA) families of
hash functions require more resources than simple arithmetic algorithms
based on XOR.

### Invocation Location

The choice of where to invoke an integrity control can have a big impact
on an application’s performance. For example, an architect may decide to
invoke a checksum integrity control within a segment of code that is
executed with high frequency. In doing so, the application may
unnecessarily perform an integrity check too often and negatively impact
performance greatly.

### Probability of Execution

The choice of frequency of integrity control invocation can have a big
impact on performance. For example, an architect may have no choice but
to place a checksum integrity guard invocation within a segment of code
that is executed frequently. In such a case, the architect should reduce
the likelihood that the integrity control will actually perform the
check upon invocation by the application.

### Protection Range

Some integrity controls protect ranges of code or data within an
application. For example, a checksum integrity control can protect the
entire application or a specific set of code modules within said
application. In this example, the checksum integrity control must
perform a hash over the entire range. As the range expands, it will take
more time and effort to computer the hash. Hence, the architect can
choose to reduce the range of coverage to only critical areas in order
to minimize performance impact.

## Confidentiality, Integrity, and Availability Impacts

Often, security architects have to describe how their security solution
impacts the CIA model. This is required because each control may have
security impacts on maintaining the confidentiality, integrity, and
availability of the application’s code and data.

The following table clarifies how each integrity control contributes to
the overall security posture of the application:

|                                                                                     |                                         |
| ----------------------------------------------------------------------------------- | --------------------------------------- |
| colspan="5"                                                                         | CIA Impacts per Integrity Control       |
| style="color: \#fbede4; background-color: \#eb9b64; vertical-align:top; width: 25%" | **Integrity Control**                   |
| style="color: \#e88a49; background-color: white"                                    | **AntiDebug Control**                   |
| style="color: \#e88a49; background-color: \#fbede4"                                 | **Checksum Control**                    |
| style="color: \#e88a49; background-color: white"                                    | **Static Damage Control**               |
| style="color: \#e88a49; background-color: \#fbede4"                                 | **Dynamic Damage Control**              |
| style="color: \#e88a49; background-color: white"                                    | **Obfuscation Control**                 |
| style="color: \#e88a49; background-color: \#fbede4"                                 | **Renaming Control**                    |
| style="color: \#e88a49; background-color: white"                                    | **String Damage**                       |
| style="color: \#e88a49; background-color: \#fbede4"                                 | **Jailbreak / Root Detection Controls** |

# Guiding Architectural Principles of Integrity Design

When trying to prevent reverse-engineering or unauthorized code
modification into your mobile app solution, there are ten critical
design principles that should be applied to your solution. Together,
these architecture features will make is very painful, if not
impossible, for an attacker to inject or modify mobile app code through
binary attacks.

Examine your app's architecture and see verify that it is honoring these
integrity principles. If you follow these principles, you will do a
reasonable job of making it very painful for an attacker to
reverse-engineer or modify your binary.

|                                                                                   |                                                    |
| --------------------------------------------------------------------------------- | -------------------------------------------------- |
| colspan="2"                                                                       | Architectural Features of Code Integrity Solutions |
| style="color: \#bfd4e7; background-color: \#407fb6; vertical-align:top;"          | **Principle to Follow**                            |
| style="color: \#00549e; width: 30%; background-color: white; vertical-align:top;" | **Defence in Depth**                               |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Positive Security Model**                        |
| style="color: \#00549e; width: 30%; background-color: white; vertical-align:top;" | **Avoid Integrity Information Leakage**            |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Least Privilege**                                |
| style="color: \#00549e; width: 30%; background-color: white; vertical-align:top;" | **Avoid Integrity Security by Obscurity Alone**    |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Simplicity**                                     |
| style="color: \#00549e; width: 30%; background-color: white; vertical-align:top;" | **Detect Integrity Violation Incidents**           |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Don’t Trust Infrastructure**                     |
| style="color: \#00549e; width: 30%; background-color: white; vertical-align:top;" | **Establish Secure Defaults**                      |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Don’t Trust Local Resources**                    |
| style="color: \#00549e; background-color: white; vertical-align:top;"             | **Avoid Binary Signatures**                        |
| style="color: \#00549e; background-color: \#f2f6fa; vertical-align:top;"          | **Create Unpredictable Defenses**                  |

# Conclusions

With the rise in automated tools like Dendroid, mobile app developers
must now take into account a whole host of new risks that relate to
hosting code in an uncontrolled environment. If you are hosting code in
an untrustworthy environment, you are susceptible to these risks
<sup>[1]([#ReferenceItem1 "wikilink")\]</sup>
<sup>[2]([#ReferenceItem2 "wikilink")\]</sup>
<sup>[3]([#ReferenceItem3 "wikilink")\]</sup>
<sup>[4]([#ReferenceItem4 "wikilink")\]</sup>. In this guide, we focused
mainly on mobile solutions. However, there are plenty of other
uncontrolled environments that expose the same risks (firmware, desktop
software, and many others).

This guide helps Security Architects understand the security features
that should include when trying to flesh out a solution that should
detect, react, and alert to unauthorized code modifications or reverse
engineering within the mobile app.

For more information about what these controls mitigate against, check
out the deep dive on technical risks that is hosted in the umbrella
project. You can find the technical risk paper
[here](https://www.owasp.org/index.php/Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification).
This paper goes into some of the more technical, low-level aspects of
coding techniques that will enforce these controls.

# External References

<span id="ReferenceItem1">\[1\] Arxan Research: [State of Security in
the App Economy,
Volume 2](https://www.arxan.com/assets/1/7/State_of_Security_in_the_App_Economy_Report_Vol._2.pdf),
November 2013:

  -
    *“Adversaries have hacked 78 percent of the top 100 paid Android and
    iOS apps in 2013.”*</span>

<span id="ReferenceItem2">\[2\] HP Research: [HP Research Reveals Nine
out of 10 Mobile Applications Vulnerable to
Attack](http://www8.hp.com/us/en/hp-news/press-release.html?id=1528865#.UuwZFPZvDi5),
18 November 2013:

  -
    *"86 percent of applications tested lacked binary hardening, leaving
    applications vulnerable to information disclosure, buffer overflows
    and poor performance. To ensure security throughout the life cycle
    of the application, it is essential to build in the best security
    practices from conception."*</span>

<span id="ReferenceItem3">\[3\] North Carolina State University:
[Dissecting Android Malware: Characterization and
Evolution](http://www.csc.ncsu.edu/faculty/jiang/pubs/OAKLAND12.pdf), 7
September 2011:

  -
    *“Our results show that 86.0% of them (Android Malware) repackage
    legitimate apps to include malicious payloads; 36.7% contain
    platform-level exploits to escalate privilege; 93.0% exhibit the
    bot-like capability.”*</span>

<span id="ReferenceItem4">\[4\] InfoSecurity Magazine: [Two Thirds of
Personal Banking Apps Found Full of
Vulnerabilities](http://www.infosecurity-magazine.com/view/36376/two-thirds-of-personal-banking-apps-found-full-of-vulnerabilities/),
January 3 2014:

  -
    *“But one of his more worrying findings came from disassembling the
    apps themselves ... what he found was hardcoded development
    credentials within the code. An attacker could gain access to the
    development infrastructure of the bank and infest the application
    with malware causing a massive infection for all of the
    application’s users.”*</span>