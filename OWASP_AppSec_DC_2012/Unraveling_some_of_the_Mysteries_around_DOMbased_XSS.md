<noinclude></noinclude> __NOTOC__

## The Presentation

DOM-based XSS was first revealed to the world back in 2005 by Amit
Klien, when it was an interesting theoretical vulnerability. In 2012,
with the push towards Web 2.0 well into the mainstream, DOM-based XSS
has become a very commonly uncovered and exploited vulnerability, but
it's poorly understood.

This talk will focus on the full range of issues around DOM-based XSS.
It will start with a discussion of the technical details of the
vulnerability, the true nature of the risk it introduces (both
likelihood and impact), and some new terminology and updated definitions
about what truly is a DOM-based XSS vulnerability as compared to the
standard Stored and Reflected XSS that the community is well aware of.
It will then discuss the difficulties that security analysts face when
trying to find DOM-based XSS flaws, and provide recommended analysis
techniques that help move DOM-based XSS discovery from an art towards
more of a science. And finally, it will discuss simple techniques for
avoiding DOM-based XSS issues in the first place as well as how to
mitigate issues that are uncovered during a security review.

This talk will include discussion of numerous open source resources that
are available on this topic. OWASP has numerous articles on DOM-based
XSS, including a definition article
[DOM_Based_XSS](DOM_Based_XSS "wikilink"), an OWASP testing guide
article
[Testing_for_DOM-based_Cross_site_scripting_(OWASP-DV-003)](Testing_for_DOM-based_Cross_site_scripting_\(OWASP-DV-003\) "wikilink"),
and the
[DOM_based_XSS_Prevention_Cheat_Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink"),
and there are also other open source articles from leading researchers
like Stefano Di Paola's [Introduction to DOM-Based
XSS](http://code.google.com/p/domxsswiki/wiki/Introduction) as well. The
speaker has already contributed to all of these OWASP articles and in
preparation for this talk, plans to review and contribute additional
enhancements to each of these articles in order to make the author's
recommendations publically available to the web security community in a
very broad manner far beyond just delivering this talk at AppSec DC. The
talk will also survey how open source proxy tools like OWASP
[ZAP](ZAP "wikilink") and [WebScarab](WebScarab "wikilink"), along with
Firebug and Chrome's developer tools can be used to track down DOM-based
XSS issues within an application. Open source DOM-based XSS detection
tools, such as [DOMinator](http://code.google.com/p/dominator/), will
also be showcased in this talk.

This talk was delivered at the conference. The presentation is [now
available online
here](https://www.owasp.org/images/f/f4/ASDC12-Unraveling_some_of_the_Mysteries_around_DOMbased_XSS.pdf).

## The Speakers

<table>

<tr>

<td>

### Dave Wichers

![Owasp_logo_normal.jpg](Owasp_logo_normal.jpg
"Owasp_logo_normal.jpg")Dave Wichers is a cofounder and the Chief
Operating Officer (COO) of [Aspect
Security](http://www.aspectsecurity.com), a consulting firm focused
exclusively on application security that supports a worldwide clientele
with critical applications in the government, defense, financial,
healthcare, services and retail sectors. Dave and his team at Aspect
Security are founding members of the Open Web Application Security
Project (OWASP), and have made major industry contributions including:
the OWASP Top Ten, Enterprise Security API (ESAPI), and Application
Security Verification Standard (ASVS). He is also a long time
contributor to OWASP itself including being a member of the OWASP Board
since it was formed in 2003 and established the OWASP conferences
program through his role as OWASP Conferences Chair from 2005 through
2009.

Dave has over 20 years of experience in the information security field,
and has focused exclusively on application security since 1998. At
Aspect, in addition to his COO duties, he is Aspect's application
security courseware lead, one of their chief instructors, and provides a
wide variety of application security consulting services to Aspect's
clients. This includes frequent application security verification
efforts involving both code review and application penetration testing
for both commercial and Government clients.

Prior to starting Aspect, he ran the Application Security Services Group
at Exodus Communications. Dave has a Bachelors and Masters degree in
Computer Science, is a CISSP, and a CISM.

For more details, see my full bio at:
[User:Wichers](User:Wichers "wikilink")

</td>

</tr>

</table>

<noinclude></noinclude>