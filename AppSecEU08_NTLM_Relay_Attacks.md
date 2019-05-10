**NTLM Relay Attacks**

NTLM relay attacks have been around for years. Since 2001, in fact.
Until now, every implementation of this attack has been SMB-based, using
it to access the victim’s hidden c$ file share. But NTLM relay attacks
can be launched against any protocol that uses NTLM authentication.
Besides SMB, that includes more or less every Microsoft enterprise
software product, and more or less every third-party app ever to
leverage Windows Integrated Authentication.

Simply put, whenever an Active Directory domain user authenticates to a
web server in a Windows enterprise environment, that web server's
operator can then access *arbitrary network resources* as the victim.

Although this vulnerability has been exploitable for over seven years,
nobody has paid much attention to the fact that it can also be used to
access HTTP-based resources -- until now. In this talk, Eric Rachner
will demonstrate Scurvy, a new tool for launching NTLM relay attacks.
The underlying mechanics of NTLM relay attacks will also be discussed,
along with mitigation options.

**About the Speaker:** Eric Rachner is an independent security
consultant, researcher, and enthusiast specializing in security analysis
and penetration testing of network applications and systems. He began
his career at Microsoft in 1994, where in 2002 he helped Microsoft start
the Application Consulting Engineering (ACE) team, leading efforts such
as application penetration testing, code reviews, design reviews of
applications throughout Microsoft's global IT organization. In 2005,
Eric left Microsoft to pursue an independent career, providing services
to large global enterprises in North America and Europe. Outside of the
office, his hobbies include motorsports and yet still more IT security
activity; he was also a core member of the hacking team that won the
prestigious "Capture the Flag" contest at Def Con in 1999, 2000, and
2001.