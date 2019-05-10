  - [OWASP Netherland Wiki](Netherlands "wikilink")
    [All OWASP NL Events
    2017](Netherlands_Previous_Events_2017 "wikilink")

# October 12th, 2017

[click here to
register](https://www.eventbrite.nl/e/tickets-owasp-netherlands-chapter-meeting-12-oktober-2017-37724873111)

## Venue

Radboud University Nijmegen

`   Faculty of Science, Huygensgebouw - room HG00.307`
`   Heyendaalseweg 135, 6525 AJ Nijmegen `
`   Parkeergarage P11 `

## Programme

  -
    18:00 - 19:00 Registration & Pizzas
    19:00 - 19:15 Welcome & OWASP update
    19:15 - 20:00 [Playing in the Sandbox: Bypassing Adobe Flash Input
    Validation](Netherlands_October_12th,_2016#Playing_in_the_Sandbox:_Bypassing_Adobe_Flash_Input_Validation "wikilink")
    by [Björn
    Ruytenberg](Netherlands_October_12th,_2016#Björn_Ruytenberg "wikilink")
    20:00 - 20:15 Break
    20:15 - 21:00 [How to rob a
    bank](Netherlands_October_12th,_2016#How_to_rob_a_bank "wikilink")
    by [Pieter
    Ceelen](Netherlands_October_12th,_2016#Pieter_Ceelen "wikilink")
    21:00 - 21:30 Networking

## Presentations

### Playing in the Sandbox: Bypassing Adobe Flash Input Validation

Sandboxing is a popular technique used by vendors to minimize damages
that applications might potentially inflict on a system. Dictated by
so-called sandbox policies, legitimate and malicious code alike are
restricted in their trust boundaries, preventing unauthorized actions.

Input validation plays an important role in enforcing sandbox policies.
With input validation, context often matters: given some policy set,
some input may be allowed, while the same input may be invalid given
another. File paths are a notable example. In Adobe Flash Player, the
"remote" sandbox prohibits local file system access but enables remote
connections, while the "local-with-filesystem" sandbox enables the
opposite use case.

While being a seemingly simple input format, validating file paths
becomes increasingly complicated when considering the entire picture.
With Flash constituting the intermediate glue between operating systems
and a range of host environments - web browsers, Microsoft Office, PDF
readers - one has a diverse landscape of path schemes to consider. This
leads to challenges in proper input validation, and as it turns out,
subtle but unforgiving mistakes.

**This talk examines two sandbox escape vulnerabilities I have recently
found in Adobe Flash.**

Tracked as CVE-2016-4271, the first vulnerability details a local
sandbox escape through bypassing input validation, enabling to
exfiltrate local data and obtain Windows user credentials. The second
vulnerability, dubbed CVE-2017-3085, extends the vulnerability to
include a remote sandbox escape, showing by extension that Adobe's patch
for the first vulnerability incompletely solved the issue. In analyzing
these vulnerabilities, we review the underlying causes that rendered
them possible: arbitrary definitions of what constitutes "remote" and
"local", insufficient input validation schemes, and unmitigated
platform-specific vulnerabilities. Finally, in light of recent efforts
to deprecate Adobe Flash, we also discuss how Flash will remain
important in the short and long term - as an attack vector, and as an
object of study.

[presentation as
PDF](https://nautilus.bjornweb.nl/owasp/playing-in-the-sandbox-owaspnl.pdf)

### How to rob a bank

We are going to digitally rob a bank. Not for profit, but as a friendly
match against the security team of this bank. We believe that only
perfect practice makes perfect: by simulating an attack as realistically
as possible, an organisation is optimally prepared for real incidents.
Expect a very practical presentation about modern hacker techniques
combined with lessons learned from security teams in defending against
targeted attacks.

## Speakers

### Björn Ruytenberg

Björn Ruytenberg is an Information Security student at Eindhoven
University of Technology and Radboud University. Being a technology
enthusiast, he has graduated in the field of Electrical Engineering, and
cum laude in the field of Computer Science. His special interests
include hardware and software security, in particular when the case at
hand stretches across the former disciplines. Aside from his work as a
software developer, he is an active participant in bug bounty programs.

### Pieter Ceelen

Pieter’s first ‘hack’ was adjusting the sprites in Space Invaders on his
MSX and claiming that the aliens now looked like his little sister. 15
Years later he turned his hobby into profession at KPMG, hacking and
advising multinational companies (instead of Space Invaders). In 2016,
together with three other experts, Pieter founded Outflank: a company
specialised in red teaming and attack simulations. Besides being a very
experienced hacker and pentester, Pieter brings years of incident
response, forensics and threat intelligence knowledge to the table. This
allows him to tune his attacks and use the tools and techniques employed
by real attackers in red teaming and attack simulations.