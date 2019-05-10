![Image:T._browser_security.jpg](T._browser_security.jpg
"Image:T._browser_security.jpg")

![Google-groups-logo-1.jpg](Google-groups-logo-1.jpg
"Google-groups-logo-1.jpg")[Join the Google Group for this
track](https://groups.google.com/group/owasp-summit-browsersec)
\==== About ==== The Browser Security track of the OWASP Summit 2011 was
an initial community effort to bring together browser vendors, major web
app providers, well-known white hat hackers, and OWASP leaders to
discuss what can be done to enhance web security through the browser.
The track comprised of two half-day day workshops on chosen subtopics
(see tabs). We invited some of the world's top experts to maximize the
chances of moving forward this important area or application security.

### Session Notes

Here are the notes from all the four browser security sessions. Later on
we will publish a Browser Security Report building on these sessions.

[Site Security Policy notes
(pdf)](http://www.owasp.org/images/6/6d/OWASPSummit2011SiteSecurityPolicyBrowserSecurityTrack.pdf)
[DOM Sandboxing notes
(pdf)](http://www.owasp.org/images/0/06/OWASPSummit2011DOMSandboxingBrowserSecurityTrack.pdf)
[HTML5 Security notes
(pdf)](http://www.owasp.org/images/c/cd/OWASPSummit2011HTML5SecurityBrowserSecurityTrack.pdf)
[EcmaScript 5 Security notes
(pdf)](http://www.owasp.org/images/f/f7/OWASPSummit2011EcmaScript5SecurityBrowserSecurityTrack.pdf)
[Enduser Warnings notes
(pdf)](http://www.owasp.org/images/f/f7/OWASPSummit2011EnduserWarningsBrowserSecurityTrack.pdf)

### Who Participated?

The following browser, major web app, and plugin vendors participated in
the browser security sessions:
[<http://www.owasp.org/images/f/f6/Chrome_small.jpg>](http://www.google.com/chrome)
[<http://www.owasp.org/images/4/47/Firefox_small.jpg>](http://www.mozilla.com/en-US/firefox/)
[<http://www.owasp.org/images/6/62/Internet_explorer_small.jpg>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
[<https://www.owasp.org/images/c/c9/Paypal_logo.gif>](http://www.paypal.com)
[<http://www.owasp.org/images/8/87/Adobe_logo_standard_for_Tasha.jpg>](http://www.adobe.com)

/John Wilander, Session Chair

#### DOM Sandboxing

### Virtualization and Sandboxing for Secure Multi-Domain Web Apps

![Image:JS_DOM_Box_Jasvir_Gaz.jpg](JS_DOM_Box_Jasvir_Gaz.jpg
"Image:JS_DOM_Box_Jasvir_Gaz.jpg")

### Co-chair Dr Jasvir Nagra

Jasvir Nagra is a researcher and software engineer at Google. He is the
designer of [Caja](http://code.google.com/p/google-caja/) - a secure
subset of HTML, CSS and JavaScript; co-author of [Surreptitious
Software](http://www.amazon.com/Surreptitious-Software-Obfuscation-Watermarking-Tamperproofing/dp/0321549252)
- a book on obfuscation, software watermarking and tamper-proofing,
contributer to [Shindig](http://shindig.apache.org/) - the reference
implementation of OpenSocial.

### Co-chair Gareth Heyes

Gareth "Gaz" Heyes calls himself Chief Conspiracy theorist and is
affiliated with Microsoft. He is the designer and developer behind
[JSReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=JSReg)
– a Javascript sandbox which converts code using regular expressions;
[HTMLReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=HTMLReg)
&
[CSSReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=CSSReg)
– converters of malicious HTML/CSS into a safe form of HTML. He is also
one of the co-authors of [Web Application Obfuscation:
'-/WAFs..Evasion..Filters//alert(/Obfuscation/)-'](http://www.amazon.com/Web-Application-Obfuscation-WAFs-Evasion-Filters-alert/dp/1597496049)
– a book on how an attacker would bypass different types of security
controls including IDS/IPS.

### Subjects and Goals (draft)

Goals and issues that need browser vendor cooperation:

  - **Attenuated versions of existing apis to sandboxed code**. How
    should browsers introduce new apis into the sandbox or allow the
    sandbox to provide attenuated versions of existing apis to sandboxed
    code? For example, lets say the sandbox wants to provide an
    attenuated "alert" function to sandboxed code which does something
    slightly different than the real "alert". What kind of apis could
    the browser provide to safely allow such extensions/apis? Do these
    need to be standardized such that different sandbox vendors can
    interoperate.
  - **Client side sandboxed apps maintaining state and authentication**.
    For example if a user is created in a sandboxed app how is it
    determined what that user can do?
  - **Create a standard for modifying a sandboxed environment**
  - **Deprecate and discourage standards** which ambiently or undeniably
    pass credentials.
  - **Adopt a simpler rights amplification api** like [Web
    Introducer](http://web-send.org/introducer)
  - **Create a standard for authentication within a sandboxed
    environment** (maybe interfacing with existing auth without passing
    creds like 0Auth works)

### Working Form

The working form will most probably be short presentations to frame the
topic and then round table discussions. Depending on number of attendees
we'll break into groups.

#### HTML5

### HTML5 Security

![Image:Html5_mario_hackvertor.jpg‎‎](Html5_mario_hackvertor.jpg‎‎
"Image:Html5_mario_hackvertor.jpg‎‎")

### Co-chair Mario Heiderich

Mario Heiderich works as a researcher for the Ruhr-University in Bochum,
Germany and currently focuses on HTML5, SVG security and security
implications of the ES5 specification draft. Mario invoked the [HTML5
security cheat-sheet](http://html5sec.org/) and maintains the [PHPIDS
filter rules](http://php-ids.org/). In his spare time he delivers
trainings and security consultancy for larger German and international
companies. He is also one of the co-authors of [Web Application
Obfuscation:
'-/WAFs..Evasion..Filters//alert(/Obfuscation/)-'](http://www.amazon.com/Web-Application-Obfuscation-WAFs-Evasion-Filters-alert/dp/1597496049)
– a book on how an attacker would bypass different types of security
controls including IDS/IPS.

### Co-chair Gareth Heyes

Gareth "Gaz" Heyes calls himself Chief Conspiracy theorist and is
affiliated with Microsoft. He is the designer and developer behind
[JSReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=JSReg)
– a Javascript sandbox which converts code using regular expressions;
[HTMLReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=HTMLReg)
&
[CSSReg](http://www.owasp.org/index.php/OWASP_JavaScript_Sandboxes#tab=CSSReg)
– converters of malicious HTML/CSS into a safe form of HTML. He is also
one of the co-authors of [Web Application Obfuscation:
'-/WAFs..Evasion..Filters//alert(/Obfuscation/)-'](http://www.amazon.com/Web-Application-Obfuscation-WAFs-Evasion-Filters-alert/dp/1597496049)
– a book on how an attacker would bypass different types of security
controls including IDS/IPS.

### Subjects and Goals (draft)

  - **Handle autofocus in a unified and secure way**. Make sure SOP
    applies for autofocus usage in frame/iframe'd websites. Re-discuss
    necessity for (future) attributes like this.
  - **Discuss necessity and capability for the HTML5 form controls**. Do
    we need a non-SOP formaction attribute and why?
  - **Goal I**: Initiate and create documentation and references for
    developers that address security issues. Html5sec.org is a start but
    impossible to continue or extend large scale without vendor help
  - **Goal II**: Discuss and heavily restrict SVG capabilities -
    especially when deployed in CSS backgrounds and <img> tags. Mainly
    Opera and Mozilla are addressed here.
  - **Long Term Goal(s)**: Provide a working and easy to use as well as
    vendor supported HTML5 compliant filter software such as
    HTMLPurifier. Browser vendors should participate in creating
    security software and filters - not undermine them as we could
    experience in the last decade

#### EcmaScript 5

### EcmaScript 5 Security

### Co-chair Mario Heiderich

Mario Heiderich works as a researcher for the Ruhr-University in Bochum,
Germany and currently focuses on HTML5, SVG security and security
implications of the ES5 specification draft. Mario invoked the [HTML5
security cheat-sheet](http://html5sec.org/) and maintains the [PHPIDS
filter rules](http://php-ids.org/). In his spare time he delivers
trainings and security consultancy for larger German and international
companies. He is also one of the co-authors of [Web Application
Obfuscation:
'-/WAFs..Evasion..Filters//alert(/Obfuscation/)-'](http://www.amazon.com/Web-Application-Obfuscation-WAFs-Evasion-Filters-alert/dp/1597496049)
– a book on how an attacker would bypass different types of security
controls including IDS/IPS.

### Co-chair 2

To be confirmed.

### Subjects and Goals (draft)

  - **Fix the problems with Object.defineProperty() and property
    unsealing /
    [double-freezing](https://bugzilla.mozilla.org/show_bug.cgi?id=588138)**.
    Implement it if not yet done.
  - **Goal I**: Raise awareness for the power or object freezing in a
    security context. ES5 can really make a change here.
  - **Goal II**: Raise awareness in seeing the DOM as the place where
    XSS attacks actually take place - and where they should be
    prevented. CSP is a great yet still immature start - but worth
    discussing and extending. Discuss specification drafts for a secure
    DOM and easy to configure capability profiles with reasonable and
    quantitative proofs of concept.
  - **Long Term Goal**: Discuss the possibility of vendor supported
    client side security mechanisms. Client side IDS/IPS based on ES5
    can be possible - yet have to be designed and specified.

#### Site Security Policy

There are several initiatives for expressing and enforcing website
security policies. [HTTP Strict Transport
Security](http://tools.ietf.org/html/draft-hodges-strict-transport-sec-02)
for enforced TLS. [Content Security
Policy](https://developer.mozilla.org/en/Introducing_Content_Security_Policy)
for whitelisting resource domains and enforcing file-only JavaScript.
[X-Frame-Options](http://blogs.msdn.com/b/ie/archive/2009/01/27/ie8-security-part-vii-clickjacking-defenses.aspx)
for enforce framing restrictions. Harmonizing these features among
browsers is a huge task. Getting developers to adopt and implement is
even more challenging. This session will try to address all of these
questions as well as the technical alternatives – headers, meta tags,
nonces, signatures, html zones, css-like policies, violation events etc.

  - Should we have independent, coherent and simple policy mechanisms or
    a generalized, extensible policy mechanism?
  - Should developers have multiple choices for expressing policies such
    as headers *and* meta tags?
  - Should policies restrict domains, URLs, or elements? What are the
    consequences?
  - Should one or two browser vendors deploy a policy mechanism in the
    field, collect experience, and then we set a standard?
  - How do we help developers understand the need for policies and how
    do we help them write/generate/maintain policies?
  - How important is performance and web 1.0/web 2.0 compliance? How
    much of the web can we afford to break? 0 %?

### Co-chair Jeff Hodges

Jeff Hodges is Distinguished Security Engineer at PayPal, Inc and one of
the three original authors of the [HTTP Strict Transport
Security](http://tools.ietf.org/html/draft-hodges-strict-transport-sec-02)
spec. Check out [IdentityMeme.org Jeff's
blog](http://identitymeme.org/).

### Co-chair David Ross

David Ross is a Principal Security Software Engineer on the MSRC
Engineering team at Microsoft. Prior to joining MSRC Engineering in
2002, David spent his formative years on the Internet Explorer Security
Team and wears the battle scars with pride. Check out [David’s
blog](http://blogs.msdn.com/dross).

### Co-chair Lucas Adamski

Lucas Adamski is the Director of Security Engineering at Mozilla
Corporation. He specializes in penetration testing, incident response,
spec and code reviews, fuzzing, training, security processes and
software PLC. Check out [Lucas'
blog](http://blog.mozilla.com/ladamski/).

#### Enduser Warnings

### Enduser Warnings

![Image:Three_browsers_user_info.jpg](Three_browsers_user_info.jpg
"Image:Three_browsers_user_info.jpg")

### Subjects and Goals (draft)

Clearly there is a need for warnings that users understand and that
conveys the right information. Perhaps we can agree on some guidelines
or at least exchange lessons learned.

  - How should browsers signal invalid SSL certs to the enduser? Are we
    helping security right now? What to do about 50 % of users clicking
    through warnings? Mozilla replaces the padlock with a [site identity
    button](https://support.mozilla.com/en-US/kb/Site%20Identity%20Button)
    i Firefox 4. "Larry" will inform the user of the site's status.
    Google recently tried out a skull & bones icon for bad certs but
    moved back to
    [padlocks](http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=95617)
    again.
  - How should browsers communicate other kinds of information such as
    privacy, malware warnings, "not visited before" etc? Forbes had an
    interesting example of [how to visualize
    privacy](http://blogs.forbes.com/kashmirhill/2011/01/05/visualizing-better-privacy-policies/?boxes=Homepagechannels).

Some additional information, thoughts and discussions on these subjects
elsewhere:

  - [Web Browser Security User Interfaces: Hard to Get Right and
    Increasingly
    Inconsistent](http://www.freedom-to-tinker.com/blog/sjs/web-browser-security-user-interfaces-hard-get-right-and-increasingly-inconsistent),
    Freedom to Tinker, 18 Jan 2011
  - [Security Dialogs and
    Graphics](http://intrepidusgroup.com/insight/2010/04/security-dialogs-and-graphics/),
    Insight, 27 Apr 2010
  - [Web Security Context: User Interface
    Guidelines](http://www.w3.org/TR/wsc-ui/), W3C, 12 Aug 2010
  - [Colour Overload with IE8 Tab
    Grouping](http://www.clerkendweller.com/2009/7/28/Colour-Overload-with-IE8-Tab-Grouping),
    Clerkendweller, 28 Jul 2009
  - [The Emperor's New Security Indicators: An evaluation of website
    authentication and the effect of role playing on usability
    studies](http://www.usablesecurity.org/emperor/), IEEE Symposium on
    Security and Privacy, May 2007

#### Securing Plugins

### Securing Plugins

Should browsers ship with default plugins? Should plugins be
auto-updated? Can plugins or versions of plugins be blacklisted
centrally?

#### Blacklisting

### Blacklisting

Can we cooperate better on blacklisting? Does it work between cultures,
i e can we have the same process for reporting throughout the world?

#### OS Integration

### OS Integration

More and more features in browsers get integrated with the underlying
operating system. Processes, fonts, filesystem, 3D graphics. How do we
secure this?

#### Sandboxed Browser

### Sandboxed Tabs/Domains/Browser

Microsoft Research has been doing some groundbreaking work on the
[Gazelle
browser](http://research.microsoft.com/apps/pubs/default.aspx?id=79655),
Chrome uses a sandboxing model, and the
[IronSuite](http://www.romab.com/ironsuite/) provides sandboxed versions
of Firefox ([IronFox](http://www.romab.com/ironfox/)) and Safari on Mac
OS X.

__NOTOC__ <headertabs />

Questions? Contact [John Wilander, Session
Chair](mailto:john.wilander@owasp.org)

[**Return Global Summit 2011 Home Page**](Summit_2011 "wikilink")
[**Return to Global Summit 2011 Working
Sessions**](:Category:Summit_2011_Tracks "wikilink")

[Category:Summit_2011](Category:Summit_2011 "wikilink") [Category:
Summit 2011 Tracks](Category:_Summit_2011_Tracks "wikilink")