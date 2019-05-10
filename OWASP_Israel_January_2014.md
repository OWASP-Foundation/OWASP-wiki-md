The first meeting of 2014 for the Israel chapter of OWASP took place on
January 14th, at 17:00.

The meeting was held at the Amdocs Auditorium, Hapnina 8, Raanana, with
over 120 participants.

The building is called the Kenyon (it's the one on the right, where MS
and other companies are sitting). In the Kenyon, the conference room is
called the Auditorium. Parking is available in the visitor's parking
lot.

## Agenda:

''' 17:00 – 17:30
''' **Gathering, pizza, and drinks (KOSHER)**

''' 17:30 – 17:45
''' '''Opening note '''

''' 17:45 – 18:30
''' **PHP SuperGlobals: Supersized Trouble - Shelly Hershkovitz,
Imperva** ([download
presentation](Media:OWASP-IL-2014-01_PhpSuperGlobals.pptx "wikilink"))‎

Used in over 80% of all websites, PHP is the most popular Web
application development platform in the world. The widespread use of
PHP, however, makes it an attractive target for malicious hackers. By
focusing attacks on vulnerabilities found in popular third party
components, such as PHP, hackers are able to expand their reach to many
unsuspecting websites.

In this talk we look at in-the-wild modification and exploitation of PHP
SuperGlobal variables. This is a special case of a more general weakness
called “External Variable Modification”. This weakness was assigned a
specific Common Weakness Enumeration (CWE) code, CWE-473 by MITRE, with
the following description: “A PHP application does not properly protect
against the modification of variables from external sources, such as
query parameters or cookies”.

We detail the in the wild exploitation of SuperGlobal variables issues
for the purpose of remote code execution, remote file inclusion, and
security filter evasions attacks. A special focus is given to the
analysis of a specific exploit that combines together different
vulnerabilities in order to achieve remote code execution. The analysis
includes a deep dive into the technical details of each of the
vulnerabilities, analysis of the exploit itself and its use in the wild.

Finally, we suggest several practical steps that allow security officers
to defend their websites against such attacks.

''' 18:30 – 19:15
''' **NTLM Based Authentication in Web Applications: The Good, The Bad,
and the NHASTIE - Oren Ofer, EY** ([download
presentation](Media:OWASP-IL-2014-01_nhastie-presentation.pdf "wikilink"))‎

The crusade against NTLM started (without me) over 16 years ago.

Nevertheless, NTLM proved as a cunning opponent; It mutated, improved,
got stronger, survived, and still refuses to go away. “If there is no
struggle there is no progress” (F. Douglas).

The lecture will begin with a live demonstration which will reveal a new
design flaw in NTLM along with a dedicated tool that enables attackers
to fully impersonate any web application user.

The lecture will cover the mechanics of the new attack vector and will
inspect its relevancy to OWASP’s Top 10 categories and its deadliest
attacks.

Prezi:
<http://prezi.com/f1dvuojlwco_/ntlm-based-authentication-in-web-applications/>

Demo: <http://youtu.be/3FGYSXKq-b0>

Project: <https://github.com/hacktics/nhastie>

'''19:15 – 19:30
''' **Coffee break**

'''19:30 – 20:15
''' **Hacking an Electric Car Charging Station - Ofer Shezaf, HP**

[Category:Israel](Category:Israel "wikilink")