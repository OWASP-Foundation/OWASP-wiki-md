## Web Honeynet Project Announcement

**Posted January 23rd, 2007**

The newly formed Web Honeynet Project from SecuriTeam and the ISOTF will
in the next few months announce research on real-world web server
attacks which infect web servers with: Tools, connect-back shells, bots,
downloaders, malware, etc. which are all cross-platform (for web
servers) and currently exploited in the wild.

The Web Honeynet Project will, for now, not deal with the regular SQL
injection and XSS attacks every web security expert loves so much, but
just with malware and code execution attacks on web servers and hosting
farms.

These attacks form botnets constructed from web servers (mainly IIS and
Apache on Linux and Windows servers) and transform hosting farms/colos
to attack platforms.

Most of these "tools" are being injected by (mainly) file inclusion
attacks against (mainly) PHP web applications, as is well known and
established.

PHP (or scripting) shells, etc. have been known for a while, as well as
file inclusion (or RFI) attacks, however, mostly as something secondary
and not much (if any - save for some blogs and a few mailing list posts
a year ago) attention was given to the subject other than to the
vulnerabilities themselves.

The bad guys currently exploit, create botnets and deface in a massive
fashion and force ISPs and colos to combat an impossible situation where
any (mainly) PHP application from any user can exploit entire server
farms, and where the web vulnerability serves as a remote exploit to be
followed by a local code execution one, or as a direct one.

What is new here is the scale, and the fact we now start engaging the
bad guys on this front (which so far, they have been unchallenged on) -
meaning aside for research, the Web Honeynet Project will also release
actionable data on offensive IP addresses, URLs and on the tools
themselves to be made available to operational folks, so that they can
mitigate the threat.

It's long overdue that we start the escalation war with web server
attackers, much like we did with spam and botnets, etc. years ago.
Several folks (and quite loudly - me) have been warning about this for a
while, not it's time to take action instead of talk. :)

Note: Below you can find sample statistics on some of the Web Honeynet
Project information for this last Wednesday, on file inclusion attacks
seeding malware. You will likely notice most of these have been taken
care of by now.

The first research on the subject (after looking into several hundred
such tools) will be made public in the February edition of the Virus
Bulletin magazine, from: Kfir Damari, Noam Rathaus and Gadi Evron (yours
truly).

The SecuriTeam and ISOTF Web Honeynet Project would like to thank Beyond
Security ( <http://www.beyondsecurity.com> ) for all the support.

Special thanks (so far) to: Ryan Carter, Randy Vaughn and the rest of
the new members of the project.

For more information on the Web Honeynet Project feel free to contact
me.

Also, thanks for yet others who helped me form this research and
operations hybrid project (you know who you are).

\-- Gadi.