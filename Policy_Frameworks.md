[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink") __TOC__

Secure applications do not just happen – they are the result of an
organization deciding that they will produce secure applications. OWASP
does not wish to mandate a particular approach or require an
organization to pick up compliance with laws that do not affect them -
every organization is different.

However, for a secure application, the following at a minimum are
required:

  - Organizational management which champions security

<!-- end list -->

  - A written information security policy properly derived from national
    standards

<!-- end list -->

  - A development methodology with adequate security checkpoints and
    activities

<!-- end list -->

  - Secure release and configuration management processes

Many of the controls within OWASP Development Guide 2.0 are influenced
by requirements of national standards or control frameworks such as
COBIT; typically controls selected out of OWASP will satisfy relevant
ISO 27002(17799) and COBIT controls.

## Organizational commitment to security

Organizations that have security buy-in from the highest levels will
generally produce and procure applications that meet basic information
security principles. This is the first of many steps along the range
between ad hoc “possibly secure (but probably not)” to “best practices”.

Organizations that do not have management buy-in, or simply do not care
about security, are extraordinarily unlikely to produce secure
applications. Each secure organization documents its “taste” for risk in
their information security policy, thus making it easy to determine
which risks will be accepted, mitigated, or assigned.

Insecure organizations simply don’t know where this “taste” is set, and
so when projects run by the insecure organization select controls, they
will either end up implementing the wrong controls or not enough
controls. Rare examples have been found where every control, including a
kitchen sink tealeaf strainer has been implemented, usually at huge
cost.

Most organizations produce information security policies derived from
ISO 27002(17799), or if in the US, from COBIT, or occasionally both or
other standards. There is no hard and fast rule for how to produce
information security policies, but in general:

  - If you’re publicly traded in most countries, you must have an
    information security policy

<!-- end list -->

  - If you’re publicly traded in the US, you must have an information
    security policy which is compliant with SOX requirements, which
    generally means COBIT controls

<!-- end list -->

  - If you’re privately held, but have more than a few employees or
    coders, you probably need one

<!-- end list -->

  - Popular FOSS projects, which are not typical organizations, should
    also have an information security policy

It is perfectly fine to mix and match controls from COBIT and ISO
27002(17799) and most any other respected information security standard;
rarely do they disagree on the details. The method of production is
sometimes tricky – if you “need” certified policy, you will need to
engage qualified firms to help you.

## OWASP’s Place at the Framework table

The following diagram demonstrates where OWASP fits in (substitute your
own country and its laws, regulations and standards if it does not
appear):

![Image:Policy_frameworks.JPG](Policy_frameworks.JPG
"Image:Policy_frameworks.JPG")

Organizations need to establish information security policy informed by
relevant national legislation, industry regulation, merchant agreements,
and subsidiary best practice guides, such as OWASP. It is impossible to
draw a small diagram containing all relevant laws and regulations, so
you should assume all of the relevant laws, standards, regulations, and
guidelines are missing – you need to find out which affect your
organization, customers (as applicable), and where the application is
deployed.

IANAL: OWASP is not a qualified source of legal advice; you should seek
your own legal advice.

### *COBIT*

COBIT is a popular risk management framework structured around four
domains:

  - Planning and organization

<!-- end list -->

  - Acquisition and implementation

<!-- end list -->

  - Delivery and support

<!-- end list -->

  - Monitoring

Each of the four domains has 13 high level objectives, such as DS5
''Ensure Systems Security. ''Each high level objective has a number of
detailed objectives, such as 5.2 *Identification, Authentication, and
Access*. Objectives can be fulfilled in a variety of methods that are
likely to be different for each organization.

COBIT is typically used as a SOX control framework, or as a complement
to ISO 27002(17799) controls.

OWASP does not dwell on the management and business risk aspects of
COBIT. If you are implementing COBIT, OWASP is an excellent start for
systems development risks and to ensure that custom and off-the-shelf
applications comply with COBIT controls, but OWASP is not a COBIT
compliance magic wand.

Where a COBIT objective is achieved with an OWASP control in this book,
you will see “COBIT XXy z.z” to help direct you to the relevant portion
of COBIT control documentation. Such controls should be a part of all
COBIT compliant applications.

For more information about COBIT, please visit
<u><http://www.isaca.org/></u>

### *ISO 27002(17799)*

ISO 27002(17799) is a risk-based Information Security Management
framework directly derived from the AS/NZS 4444 and BS 7799 standards.
It is an international standard and used heavily in most organizations,
although not in the US. However, a few US organizations use ISO
27002(17799) as well, particularly if they have subsidiaries outside the
US.

ISO 27002(17799) dates back to the mid-1990s, and some of the control
objectives reflect this age – for example referring to administrative
interfaces as “diagnostic ports”.

Organizations using ISO 27002(17799) can use OWASP for detailed guidance
when selecting and implementing a wide range of ISO 17799 controls,
particularly those in the Systems Development chapter, among others.
Where a 27002(17799) objective is achieved with an OWASP control in this
book, you will see “ISO 27002(17799) X.y.z” to help direct you to the
relevant portion of ISO 27002(17799). Such controls should be a part of
all ISO 27002(17799) compliant applications.

For more information about ISO 27002(17799), please visit
<u><http://www.computersecuritynow.com/></u> and the relevant standards
bodies, such as Standards Australia
(<u><http://www.standards.com.au/></u>), Standards New Zealand
(<u><http://www.standards.co.nz/></u>), or British Standards
International (<u><http://www.bsi-global.com/></u>).

Note that ISO 17799 was renamed to ISO 27002 in July 2007, to achieve
numerical alignment with ISO's overall security standards set (ref:
<u><http://www.27000.org></u>)

### *Sarbanes-Oxley*

A primary motivator for many US organizations in adopting OWASP controls
is to assist with ongoing Sarbanes-Oxley compliance. If an organization
followed every control in this book, it would not automatically grant
the organization SOX compliance. Therefore, The Development Guide is
useful as a suitable control for application procurement and in-house
development, as part of a wider compliance program.

However, SOX compliance is often used as a case for resource-starved IT
managers to implement long neglected security controls, so it is
important to understand what SOX actually requires. A summary of SOX,
section 404 obtained from AICPA’s web site at
<u><http://www.aicpa.org/info/sarbanes_oxley_summary.htm></u> states:
[the above link is not working](category:FIXME "wikilink")

Section 404: Management Assessment of Internal Controls

Requires each annual report of an issuer to contain an "internal control
report", which shall:

  - state the responsibility of management for establishing and
    maintaining an adequate internal control structure and procedures
    for financial reporting; and

<!-- end list -->

  - contain an assessment, as of the end of the issuer's fiscal year, of
    the effectiveness of the internal control structure and procedures
    of the issuer for financial reporting.

This essentially states that management must establish and maintain
internal ''financial control ''structures and procedures, and conduct an
annual evaluation that verifies the controls are effective. As finance
is no longer conducted using double entry ledger books, “SOX compliance”
is often extended to mean IT.

The Development Guide can facilitate SOX compliance by providing
effective controls for all applications, and not just for the purposes
of financial reporting. It allows organizations to buy products which
claim they use OWASP controls, or allows organizations to mandate to
software suppliers that they must use OWASP controls to provide more
secure software.

However, avoid using SOX as an excuse. SOX controls are intended to
prevent another Enron, not to buy widgets that may or may not help. All
controls, whether off the shelf widgets, training, code controls, or
process changes, should be selected based on measurable results and
ability to manage risk, and not just to “tick the boxes”.

## Development Methodology

High performing development shops employ a development methodology and
some set of coding standards or conventions. As it turns out, the choice
of development methodology is not as important as simply having one.

Ad hoc development is too unstructured to produce secure applications.
Therefore, organizations who wish to produce secure code consistently
need to utilize a methodology that supports that goal. Choose carefully
– small teams should never consider heavy weight methodologies that
identify many different roles, while large teams must choose
methodologies that will scale to their needs.

Here are some key attributes to look for in selecting a development
methodology:

  - Strong acceptance of design, testing, and documentation processes

<!-- end list -->

  - Clear instances where security controls (such as threat risk
    analysis, peer reviews, code reviews, etc) can be slotted in

<!-- end list -->

  - Works well for the organization’s size and maturity

<!-- end list -->

  - Has the potential to reduce the current error rate and improve
    developer productivity

<!-- end list -->

  - Will scale as the organization or product line grows

## Coding Standards

Methodologies alone are not coding standards; each team will either need
to determine what to use based upon common practice, or simply lay down
the law based upon known best practices.

Inputs to consider:

  - Architectural guidance (i.e., “The web tier cannot call the database
    directly”)

<!-- end list -->

  - Minimum documentation levels required

<!-- end list -->

  - Mandatory testing and coverage requirements

<!-- end list -->

  - Minimum levels of code commenting and the preferred comment style

<!-- end list -->

  - Proper use of exception handling

<!-- end list -->

  - Correct use of flow of control blocks (e.g., “All uses of
    conditional flow shall use explicit statement blocks”)

<!-- end list -->

  - Preferred variable, function, class, and table naming styles

<!-- end list -->

  - A preference for maintainable and readable code over clever or
    complex code

Indentation style and tabbing are a holy war, and from a security
perspective, they simply do not matter that much. However, it should be
noted that we no longer use 80x24 terminals, so vertical space usage is
not as important as it once was. Indent and tabbing can be “fixed” using
automated tools or simply a style within a code editor, so do not get
overly fussy on this issue.

## Source Code Control

High performance software engineering requires the use of regular
improvements to code, along with associated testing regimes. All code
and test changes must be able to be versioned and capable of being
reverted.

This could be done by copying folders on a file server, but it is better
performed by source code revision tools, such as Subversion, CVS,
SourceSafe, or ClearCase.

Why include tests with a software revision? Most simply put, because
tests for later builds will not necessarily match the tests required for
earlier builds. So, it is vital that a test is applied to the build for
which it was intended.

## Summary

The use of policy frameworks does not automatically guarantee secure
applications or standards compliance. However, it is very difficult to
produce secure applications consistently without some structure in place
to do so.

Select your policy framework carefully -- it should meet the needs of
your organization today, while providing room for growth, too.

Finally, get started today\! Incorporating a security-conscious
development process is a crucial first step to delivering secure
applications. Your policy framework and development process should
leverage your local conventions, risk management goals, and applicable
standards to ensure a secure and quality result.

## Other

[NSA](http://www.nsa.gov/snac/downloads_all.cfm?doc=%22Web%20Application%20Security%20Overview.pdf%2)
[link not working](category:FIXME "wikilink")

[FFIEC](http://www.occ.treas.gov/ftp/bulletin/2008-16.html)

[FTC](http://www.ftc.gov/bcp/conline/pubs/buspubs/security.shtm) [link
not working](category:FIXME "wikilink")

[NIST](http://csrc.nist.gov/publications/PubsSPs.html)

[DHS](https://buildsecurityin.us-cert.gov/swa/downloads/SwA_in_Acquisition.pdf)
[link not working](category:FIXME "wikilink")



[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[need to change the JPG so it refers to the Development Guide, not just
the Guide. Also, it's very large, perhaps reduce its
size.](Category:FIXME "wikilink")
[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Requirements](Category:Requirements "wikilink")