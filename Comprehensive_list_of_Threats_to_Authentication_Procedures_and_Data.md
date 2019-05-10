Background There is a bewildering array of tricks, techniques, and
technologies that exist to steal passwords, attack password systems, and
circumvent authentication security.

The List Here is the list:

1\. Confidence Tricks 1.1. Phishing emails 1.1.1. to lure victims to
spoof sites 1.1.2. to lure victims into installing malicious code 1.1.3.
to lure victims towards O/S vulnerabilities to inject malicious code
1.1.4. to lure victims into revealing information directly via reply or
via embedded FORMS within the email 1.2. telephone phishing 1.2.1. to
directly extract auth info 1.2.2. to direct victim to spoof site 1.3.
person-to-person phishing / situation engineering 1.3.1. to directly
extract auth info (ask) 1.3.2. to direct victim to spoof site 1.3.3.
shoulder surfing (aka 4.5.2) 1.3.4. physical attack of user - see 4.7
1.3.5. physical attack of user resources (eg: computer theft) 1.3.6.
physical attack of server resources (eg: server/hosting-facility
compromise) 1.4. typographic attacks 1.4.1. purpose: spoofing (eg:
paypa1.com - using a number 1 for a little L) 1.4.2. purpose: direct
download of malicious code 1.4.3. purpose: browser exploit injection
1.5. online phishing 1.5.1. pop-up/pop-behind windows to spoof sites
1.5.2. floating

<DIV>

or similar elements (eg: emulating an entire browser UI)

2\. Remote Technical Tricks 2.1. spoof techniques 2.1.1. vanilla fake
look-alike spoof web sites 2.1.2. CGI proxied look-alike web site
(server CGI talks to real site in real time - "man in the middle
attack") 2.1.3. popup windows hiding the address bar (3.4.1/3.4.2)
2.1.4.

<DIV>

simulated browsers (1.5.2) 2.2. iframe exploits (eg: 1.5.1/1.1.3)
(spammers buy iframes to launch 1.5 and 1.4 attacks) 2.3. p2p
filesharing publication of products modified to remove/limit protection
- PGP, IE7, Mozilla, ... 2.4. DNS poisoning (causes correct URL to go to
spoof server) 2.4.1 client "hosts" file modification 2.4.2 ISP's DNS
servers compromised 2.5. traffic sniffing (eg: at ISP, telco, WiFi, LAN,
phone tap...) 2.6. proxy poisoning (correct URL returns incorrect HTML)
2.7. browser exploits (correct URL returns incorrect HTML) 2.8. targeted
proxy attack 2.8.1. directs to vanilla spoof web site (2.1.1) 2.8.2.
uses CGI re-writing to proxy legitimate site (eg: convert HTTPS into
HTTP to activate traffic sniffing) (2.1.2) 2.8.3 activates 5.7 2.9.
Authorized exploitation - see 3.5. 2.10. Exploiting outdated technology
- eg: old browsers allowing frames from site A to read content in site
B. 2.11. undismissable download dialogues (eg: active-X) - see 3.3

3\. Local Technical Tricks 3.2. Software vulnerabilities (aka exploits -
eg - 1.1.3) 3.1.1. Known 3.1.2. Unknown 3.2. Browser "toolbars" (grant
unrestricted DOM access to SSL data) 3.3. Trojans 3.3.1. Standalone
modified/hacked legitimate products (eg: PGP or a MSIE7) with inbuilt
protection removed/modified. 3.3.2. Bogus products (eg: the anti-spyware
tools manufactured by the Russian spam gangs) 3.3.3. Legitimate products
with deliberate secret functionality (eg: warez keygens, sony/CD-Rom
music piracy-block addins) 3.3.4. Backdoors (activate remote control and
3.4.1/3.4.2) 3.4. Viruses 3.4.1. General - keyloggers, mouse/screen
snapshotters 3.4.2. Targeted - specifically designed for certain victim
sites (eg paypal/net banking) or certain victim actions (eg: password
entry, detecting typed credit card numbers) 3.5. Authorized exploitation
3.5.1. An authority (eg: Microsoft WPA/GA, Police, ISP, MSS, FBI, CIA,
MI5, Feds...) Engineers "legitimately" signed & authenticated
Trojan/Viral software to be shipped down the wire (eg: during "Windows
Update") to victim PC 3.5.2. Privileged persons (eg government, company
staff, datacenter staff, hackers) "legitimately" compromise servers or
steal secrets serverside. 3.6. Visual tricks 3.6.1. browser address bar
spoofing 3.6.2. address bar hiding 3.7. Hardware attacks 3.7.1.
keylogger devices 3.7.2. TEMPEST 3.7.3. malicious hardware modification
(token mods, token substitution, auth device substitution/emulation/etc)
3.8. Carnivore, DCS1000, Altivore, NetMap, Echelon, Magic Lantern, RIPA,
SORM... see 3.5

4\. Victim Mistakes 4.1. writing down passwords 4.2. telling people
passwords 4.2.1. deliberately (eg: friends/family) 4.2.2. under duress
(see 4.7) 4.3. picking weak passwords 4.4. using same passwords in more
than one place 4.5. inattentiveness when entering passwords 4.5.1. not
checking "https" and padlock and URL 4.5.2. not preventing shoulder
surfing 4.6. permitting accounts to be "borrowed" 4.7. physical attack
(getting mugged) 4.7.1. to steal auth info 4.7.2. to acquire active
session 4.7.3. to force victim to take action (eg: xfer money) 4.8.
allowing weak lost-password "questions"/procedures 4.9. people using
outdated older technology (see 2.10)

5\. Implementation Oversights 5.1. back button 5.2. lost password
procedures 5.3. confidence tricks against site (as opposed to user) 5.4.
insecure cookies (non-SSL session usage) 5.5. identity theft? site
trusts user's lies about identity - see 7.1 5.6. trusting form data 5.7.
accepting auth info over NON-SSL (eg: forgetting to check $ENV{HTTPS} is
'on' when performing CGI password checks) 5.8. allowing weak
lost-password "questions"/procedures 5.9. replay 5.10. robot exclusion
(eg: block mass password guessing) 5.11. geographical exclusion (eg:
block logins from Korea) 6.12. user re-identification - eg - "We've
never seen you using Mozilla before" 6.13. site-to-user authentication
6.14. allowing users to "remember" auth info in browser (permits local
attacks by unauthorised users) 6.15. blocking users from being allowed
to "remember" auth info in browser (facilitates spoofing / keyloggers)
6.16. using cookies (may permit local attacks by unauthorised users)
6.17. not using cookies (blocks site from identifying malicious activity
or closing co-compromised accounts) 6.18. preventing foreign script in
web site context (eg: cookie theft, bogus injected login screens on live
site, etc) - also called Cros-Site-Scripting or XSS 6.19. input data
sanitization. eg: someone typing this in a "name" input box:

<script>

alert(document.cookie)

</script>

6.20. output data sanitization. eg: allowing this to be printed in a
form value= field without escaping the quotes '
onclick='alert(document.cookie) 6.21. cryptographic oversights - using
time() or rand() or pseudo-random functions to generate cookies or IDs
or session keys (all can be esaily guessed) 6.22. sessions: omitting key
protection (eg: using serial integers when generating session
keys/cookies/etc) 6.23. data: omitting key protection (eg: using
unprotected database key ID's in hidden

<form>

elements) 6.24. ? XmlHttpRequests - might allow XSS or browser-based
spoofing via proxy 6.25. ? Other crypto attacks on implimentations

6\. Denial of Service attacks 6.1. deliberate failed logins to lock
victim out of account 6.2. deliberate failed logins to acquire
out-of-channel subsequent access (eg: password resets)

7\. Enrollment attacks 7.1. Deliberate wrongdoer creates new set of
credentials (eg: via identity theft) 7.2. Identity squatters "register"
your name/nickname/persona prior to you.

8\. Please contribute to this document\! (click the "edit" button above)