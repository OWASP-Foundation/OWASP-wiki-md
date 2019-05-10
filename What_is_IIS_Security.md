By Joe Lima [(Port 80 Software, Inc.)](http://www.port80software.com/)

## Overview

The subject of this new column, **IIS Security**, is bound to occasion
some chuckling in the server room. More than one sys admin will read it
and think: "IIS Security -- isn't that a contradiction in terms?"

It is possible to achieve and maintain an adequate level of security for
[Internet Information Services (IIS)](http://www.microsoft.com/iis),
Microsoft's Web server platform. If I didn't think this, I wouldn't have
agreed to write a regular column on the topic.

This is not to say that IIS security is a trivial task. There are plenty
of challenges involved in making and keeping any Web server secure.
Hence this column, which I hope will be a useful place for anyone
interested in the topic to catch up on Microsoft IIS security
fundamentals, keep abreast of the latest issues, and anticipate future
challenges.

Having said that, there is no denying that IIS has not always been as
secure (or securable) as it needed to be, has become, and is becoming.
That is where the reputation comes from, making the phrase "IIS
Security" a source of potential amusement for harried sys admins. On
balance, IIS' reputation has long since outrun reality here, but that
reputation is fed by a real legacy of sub-par security. To inaugurate
this column, we will take a hard look at the sources of IIS' legacy of
insecurity, the reasons for its persistence, and the way progress
against this perception has been made.

## A Legacy of Trust

The first thing to consider is the platform on which IIS emerged and to
which it has remained bound. The first widespread use of IIS to host Web
sites began with IIS 4.0 on Windows NT Server 4.0. But although NT 4.0
was a substantial improvement over previous versions of the Windows OS,
it never completely overcame their influence. In particular, the OS had
to contend with the fact that Windows had taken off as a server for
fundamentally trusted environments -- LAN environments rather than WAN
environments. In effect, NT was a desktop OS that matured to the point
where it became capable of working the server end of the client/server
equation.

### Raised in a Sheltered LAN

When it came to Web or HTTP servers, NT's LAN heritage gave IIS obvious
advantages as an intranet host in shops with Windows (or a mixture of
Windows and MAC) on the desktop. These same advantages remain IIS
selling points to this day: ease of configuration, multiple
administration options, and abundant out-of-box functionality. But this
also meant that IIS got into the HTTP business primarily in an
environment where the trade-off between functionality and security could
almost always be safely decided in favor of the former. Because of this,
IIS security features had taken a backseat early on, and the urgency for
improving them was relatively low. A good example of this is the long
IIS dependence on the [FAT file
system](http://www.microsoft.com/windowsxp/expertzone/columns/russel/october01.asp)
and its lack of real access control capabilities.

Another aspect of this same LAN bias was IIS's ability to serve as a
general purpose server rather than a Web server per se. This too was in
line with the kind of role flexibility expected of NT boxes. In a small
shop, a single NT box might be file server, database server, mail
server, and intranet server -- all in one. You can see this bias toward
multiple roles in IIS itself with its integrated HTTP, SMTP, FTP, and
NNTP components, all under the IIS administration services umbrella. It
was a sign of the low general degree of security consciousness that one
was invited to install and run so many disparate services, when all one
really needed was a Web server.

### It’s Not My Default

A more general effect of the LAN legacy are the remarkably loose default
settings which have bedeviled, or at least made extra work for, IIS
administrators right on through IIS 5.0 / Windows 2000. Even once NTFS
and user/group file system
[ACLs](http://www.windowswebsolutions.com/Files/11/25934/Table_01.html)
became possible, the default posture remained that of a system expected
to work first and be secured later. Only a server that has its roots in
a trusted environment would have given us something like the Everyone
group and its default permissions. Or think of the sheer number of
superfluous services that often have to be turned off to make an IIS box
secure in a WAN context.

### Getting Schooled

The lack of network administration knowledge required to reliably secure
IIS boxes can also be traced to the legacy of trusted environment
operation. As IIS became more and more common on the Web, and the Web
server began to be given more serious Extranet and Internet duties,
Microsoft did begin to respond both by steadily patching revealed
vulnerabilities and by providing tools and techniques for running a more
secure IIS (see [IIS
LockDown](http://www.microsoft.com/windows2000/downloads/recommended/iislockdown/default.asp)
and
[URLScan](http://www.microsoft.com/technet/treeview/default.asp?url=/technet/security/tools/tools/URLScan.asp)).
But not all the admins in charge of IIS boxes were familiar or
comfortable with the practice of regularly going online to avail
themselves of such supplementary updates, information, and tools. Having
been schooled in an environment of trust, they often lacked the seasoned
UNIX administrator's passion for scouring the Net for the latest code,
tips, and utilities to improve their servers' security profile.

### Knowledge in the Open

Finally, the extraordinary online infrastructure of the open source
community had (and has) no analogue for IIS administrators -- even when
the latter become aware of the critical need to avail themselves of such
resources. Microsoft has done much to catch up and is doing more now,
but it is hard to match the sheer volume and rigor of the collective
conversation on the open source side. Because that conversation is
rooted in the relative transparency of a peer review-driven culture,
this is probably the single hardest security advantage for IIS to
reproduce. To take a small but telling example: the URLScan tool has
long been available as a quite reliable way to beef up application layer
security by filtering HTTP input through the use of a simple set of
allow/deny directives in a text configuration file. And yet, in my own
experience at least, it is still relatively common to come across IIS
5.0 boxes either not running URLScan or not running the latest version.
The very fact that one must still go download this tool and install it,
rather than having it as part of the server's standard distribution the
way many [Apache Web server](http://httpd.apache.org/) modules are,
suggests some of the distance that still needs to be made up here.

## Growing Pains

We all know that IIS didn't stay in the LAN forever. On the contrary,
its Extranet and Internet presence soon exploded. While this was partly
a tribute to the maturing of the OS and the Web server, it also produced
new strains on security.

### Unwanted Attention

First and foremost, the rapid increase in IIS popularity drew unwanted
attention from both serious black hat hackers and their script kiddie
emulators. Since NT was coming onto the Internet in a big way but from a
background known to be less demanding in terms of security, IIS 4.0 on
Windows NT made for an inviting target -- and the rich functionality and
versatility that had been such an advantage in trusted environments
became a gold mine of vulnerabilities to exploit. Default script
mappings became favorite hacker targets, especially when they could be
used to exploit unchecked buffers in various [ISAPI
extensions](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/vccore98/html/_core_internet_server_api_.28.isapi.29_.extensions.asp).
The propensity of some admins to stick with FAT over NTFS made all sorts
of mischief through HTTP more likely to succeed, as did the tendency to
leave default ACLs and directories in place. In short, there was a
natural lag as IIS admins slowly learned to not simply accept the
vulnerabilities of their IIS systems as inevitable and instead began to
adapt their administrative procedures to the reality of those
vulnerabilities.

\===RAD = Bad Security?===

Sys admins weren't the only ones slow to adapt. The extraordinary
success of IIS-based rapid application frameworks such as ASP and
ColdFusion presented a whole raft of additional security challenges. It
is probably the case (though hard to say for sure) that such "parsed
HTML" development environments made for a good deal more spaghetti code
and especially careless handling of user input when compared to their
Perl script and C program counterparts, the workhorses of CGI in the
non-Windows world. This supposition rests on the fact that technologies
like ASP and ColdFusion lowered the barriers to entry for developers
attempting to add interactivity to their applications. Greater numbers
of less seasoned and less network-aware coders went on to produce an
increasing proportion of sloppy code, and this in turn increased the
vulnerability of the hosts running their code. This vulnerability is
underscored by the growing proliferation of [application
firewalls](http://www.nwfusion.com/reviews/2003/0818rev2.html) that
attempt to shore up the holes created by poor code and a lack of
understanding by developers of the URI and form field attack surface.

### Stability as Security

Application vulnerabilities like these have been particularly worrisome
in the IIS context for another reason -- the application architecture of
IIS did not provide the kind of process isolation taken for granted in
Apache. A misbehaving ASP application could crash an entire Web server
when ASP was running in-process, but running out-of-process imposed
significant performance penalties. The ["pooled
process"](http://www.windowswebsolutions.com/Articles/Index.cfm?ArticleID=15887)
compromise introduced in IIS 5.0 was some help, but the fundamental
issue remained that IIS could not recycle processes that had run into
trouble without a restart of the entire Web server (and sometimes of the
whole IIS admin service, including nested services like FTP and SMTP).
All these problems were inherent in the ISAPI extension model used by
ASP. Misbehaving ISAPI filters, often written to order for a specific
purpose like authentication or logging enhancements, were even less
forgiving.

### Patches Away\!

Finally, as a special case of the lag in sys admin procedures, we have
the infamous problem of patch management. Of course, this is something
of special importance to security -- as the [recent spate of RPC
vulnerabilities](http://www.cert.org/advisories/CA-2003-23.html) reminds
us. While Microsoft has done a tremendous amount of work to encourage
the right practices, the sheer volume of patches and the frequent need
to reboot after installing them has made staying up-to-date a
considerably heavier burden for IIS administrators than for their Apache
counterparts.

## The Right Direction with IIS 6

Fortunately on almost all of these fronts, Microsoft IIS has been and
continues to be headed in the right direction. IIS 6.0 on Windows Server
2003 has a [vastly improved security
posture](http://www.microsoft.com/windowsserver2003/evaluation/overview/technologies/iis.mspx#security),
in part a function of a stricter array of default settings. Much of what
would have been simply turned on at install in previous IIS versions
must now be explicitly enabled. The installation asks (after the model
of URLScan) for a role-based profile to be chosen and uses this to
restrict the services available. Default ACLs are tighter, and ISAPIs
have to be given explicit permission to run. But there are more
fundamental changes as well. Notably, process isolation is vastly
improved, allowing the recycling of individual hung applications without
interrupting the server's ability to handle new requests, and much of
the functionality of URLScan has been incorporated into settings exposed
in the registry. There is even a "Web server only" version of Windows
Server 2003.

In short, many lessons have been learned and applied in this latest 6.0
version of IIS. In the meantime though, [the IIS community's primary
platform](http://www.port80software.com/surveys/top1000webservers/) --
for now and for a long time to come -- will be IIS 5.0 on Windows 2000.
Fortunately, that community has also come a long way. Properly
administered, IIS 5.0 can be as secure as anything on the Net. The
amount of good information and tools out there (not only from Microsoft)
makes the job of getting to that level -- and maintaining it -- far less
trying than it was only a few years ago. So don't think of IIS security
as a contradiction in terms. Think of it as mark to be aimed at, and
with diligence and care, it's a mark we can hit.

In future columns, I'll be exploring some of the richest sources of help
the IIS community has to offer. I'll also be going into greater detail
about the new security posture in IIS 6.0 and how to maximize that going
forward. If there is a topic that you would like to see covered in the
column, please [IIS Security Column Suggestion e-mail me with your IIS
Security question or area of
interest.](mailto:iissecurity@port80software.com&subject=OWASP)

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:Deployment](Category:Deployment "wikilink")