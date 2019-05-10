<noinclude></noinclude> __NOTOC__

## The Presentation

Industrial control systems (ICS), embedded systems such as weapons
systems, medical devices, avionics, etc., can be characterized as
logical/physical systems in which software, firmware, or hardware logic
directly interfaces with and, often, controls the physical processes of
the electrical or mechanical components of the systems. The physical
elements of such systems often implement processes on which human
physical well-being relies. Because of the potential consequences (loss
of life or limb, damage to health or environment, etc.) should such
systems fail, the main imperative for both the logical and physical
components of these systems has traditionally been safety, which in
system engineering terms is an extreme manifestation of quality and
dependability. Also, because many logical/physical systems, or
components thereof, have "real time" requirements, another imperative
for such systems is performance. Because logical/physical systems have
traditionally operated either stand-alone or have been connected only to
self-contained, wholly isolated (non-Internet connected), dedicated
networks, little if any attention has been paid to their security for
most of their history. In the late 20th and 21st centuries, however,
this isolation has gradually eroded, to the extent that a new term has
been adopted for logical/physical systems that now use the Internet or
another public network (e.g., the cellular telephone network) to enable
communications among system elements: cyber-physical systems.
Coincidental with their increasing "cyberization" has been the same
trend in the engineering of such systems that has long been the norm for
conventional information and communications technology (ICT) systems:
the minimization of wholly proprietary, custom-built software and
hardware elements and the maximization of commodity technologies and
components. This shift means that many of the elements from which
cyber-physical systems are built are readily available for inspection
and study, so that those of their flaws and defects, weaknesses and
vulnerabilities, that have not simply been published by their vendors or
users have been discovered through reverse engineering and other
analyses. Knowledge and understanding of the vulnerabilities in
commodity technologies, combined with accessibility from the public
network, means that cyber-physical systems are exposed to security
threats that have long targeted more conventional information and
communications technology (ICT) systems, but were unknown to previous
generations of logical/physical systems. Unlike conventional ICT
systems, the components of cyber-physical systems often retain the small
size (both in terms of physical size and size of embedded logic) and low
resource footprints, real time performance imperatives, and operational
scenarios of stand-alone or isolated predecessors. These constraints
often make it impossible for the operators of the systems to employ the
full range of security measures and countermeasures commonly used to
protect more conventional ICT systems against threats. Moreover, the
safety imperative often means that blocking of inputs and shutting down
of processes are simply not an option when responding to perceived
hazards (threats can be characterized intentional hazards). With
emergence of Advanced Persistent Threats (APTs), including those crafted
specifically to target cyber-physical systems (e.g., Stuxnet), as well
as other less complex but invidious methods of intrusion and attack,
even the operators of conventional ICT systems are finding that their
traditional protect-detect-respond-recover security strategies are
increasingly ineffective. Many of these organizations are recognizing
that a "paradigm shift" is needed, that does not rely on trying to
detect, understand, or second-guess the attacker, but instead which
requires a new approach to software and system engineering. This new
approach will enable the systems to survive most, if not all, attacks,
including those that the attackers have yet to think up. Whether the
main imperative for system is security and or safety, or an equal
combination of the two, the logic and mechanical components of a
cyber-physical system must remain dependable under all anomalous
conditions that arise, whether those conditions are accidental or result
from intentional threats. Unlike most conventional ICT systems,
cyber-physical systems must continue operating at the necessary level of
performance under virtually any condition, at least up to the time at
which a graceful shut down can be safely accomplished (e.g., after the
plane has been safely landed, or the nuclear reactor taken offline). By
contrast, the operators of most conventional ICT systems have a much
greater tolerance for port blocking, performance degradation, and even
temporary failure. One can see this when one compares the software in a
safety-critical logical/physical system, in which the proportion of
explicit exception handling logic to actual operational logic is often
3:1 or 4:1, as compared with conventional ICT software, in which
programmers frequently rely on throwing a general exception and hoping
for the best. In this context, a few things distinguish safety-critical
software from security-critical software: (1) what constitutes an
"anomalous condition" and what is likely to cause such a condition, (2)
what is at stake if the software fails as the result of such a
condition, and how many (if any) such failures can be tolerated; (3) the
measures that can be taken to avoid such failures, or to recover from
them, and the acceptable latency between failure and recovery. What both
safety- and security-critical software share is a need to minimize to
the absolute lowest possible degree the possibility of a software
failure. In short, both safety-critical and security-critical software
needs to be able to survive the anomalous conditions it is faced with.
Engineers of safety-critical software are very good at understanding and
writing software that can deal with unintentional anomalies, but are not
usually familiar with the more complex, byzantine (non-contiguous)
nature of intentional anomalies. Developers of security-critical
software are skilled at dealing with intentional anomalies, but not with
doing so under the extreme constraints placed on safety-critical
software engineers. For survivability engineered into cyber-physical
systems, and into the software that makes up the majority of the logic
in such systems, engineers would do well to familiarize themselves with
both software safety and software security strategies, practices, and
tools, and more importantly, to analyze the aspects of each that render
them beneficial or impractical for adoption in cyber-physical system
software engineering. The place for engineers to begin is a study of the
other community's development practices and techniques that have direct
counterparts in their own, e.g., Safety Engineering | Security
Engineering hazard analyses | threat models safety properties | security
objectives safe design principles (e.g., failure avoidance and
redundancy) | secure design principles (e.g., least privilege,
separation of roles) safe coding practices, standards, languages, and
tools (shared by both) stochastic (accidental), simple, contiguous,
directly propagating faults | non-stochastic (intentional), byzantine
(non-contiguous) faults static and dynamic analysis, fault injection |
same, plus fuzz testing, vulnerability scans, and penetration tests
assurance cases | someday...maybe

## The Speakers

<table>

<tr>

<td>

### Karen Mercedes Goertzel

![AppSecDC12-Goertzel.jpg](AppSecDC12-Goertzel.jpg
"AppSecDC12-Goertzel.jpg")Karen Mercedes Goertzel, CISSP, leads Booz
Allen Hamilton's Security Research Service. An expert in software
assurance, ICT supply chain risk management, the insider threat to
information systems, and responsible information sharing, she has
performed in-depth research and analysis for customers in the U.S.
financial and ICT industries, DoD, the Intelligence Community,
Department of State, NIST, IRS, and other civilian government agencies
in the U.S., the UK, NATO, Australia, and Canada. She was lead
author/executive editor of Defense Technical Information Center's books
on Software Security Assurance (2007), The Insider Threat to Information
Systems (2008), and Security Risk Management of the Off-the-Shelf ICT
Supply Chain (2010), among numerous other publications, and is a
frequent contributor to CrossTalk: The Journal of Defense Software
Engineering.

</td>

</tr>

</table>

<noinclude></noinclude>