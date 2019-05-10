# Goal

**The goal of this page is to provide the baseline of knowledge to begin
a thoughtful conversation of enhancements and changes to continue
growing the OWASP top 10.**

# About

This page is intended to provide greater clarity on the development
methodology of the OWASP Top 10. This page provides information on the
data sources used as input to the top 10, the current development
processes, suggestions to improve involvement and participation, and
also an FAQ to cover common questions & concerns.

This is a wiki and editable by anyone with an OWASP account. Please
constructively contribute to the conversation. Additional discussions
should also take place within the [OWASP top 10 mailing
list](https://lists.owasp.org/mailman/listinfo/Owasp-topten).

# Current Methodology

The 2010 and later versions of OWASP Top 10 are organized based on the
[OWASP_Risk_Rating_Methodology](OWASP_Risk_Rating_Methodology "wikilink"),
adjusted for the fact that the Top 10 is independent of any particular
system. This adjusted methodology is documented in the OWASP Top 10 for
2010 here:
[Top_10_2010-Notes_About_Risk](Top_10_2010-Notes_About_Risk "wikilink").

This resulted in 4 risk factors used to calculate the order of the Top
10, 3 Likelihood Factors and 1 Impact Factor. These factors are:

  - Likelihood of an Application Having that Vulnerability (Prevalence)
  - Likelihood of an Attacker Discovering that Vulnerability
    (Detectability)
  - Likelihood of An Attacker Successfully Exploiting that Vulnerability
    (Exploitability)
  - Typical Technical Impact if that Vulnerability is Successfully
    Exploited (Impact)

Each of these factors is scored on a scale from 1 through 3, except for
XSS, which has a prevalence of 4

The Top 10 uses data sources provided by a variety of companies (see
[Top_10_2013/ProjectMethodology\#Current_Data_Sources
sources](Top_10_2013/ProjectMethodology#Current_Data_Sources_sources "wikilink"))
to calculate Vulnerability Prevalence. We would love to use similar data
to help calculate the scores for the other risk factors if that data is
available (which is one of the improvement suggestions recommended
below).

The process for producing an update to the OWASP Top 10 is generally as
follows:

1.  Collect prevalence data from data suppliers.
2.  Rank prevalence data for each supplier and then aggregate the
    results to create an overall prevalence ranking for this update to
    the Top 10.
3.  Determine the values of the other risk factors based on professional
    opinion. (This step not done prior to 2010)
      - Adjustments are sometimes done based on professional opinion
        (like adding CSRF in 2007, and Vulnerable Libraries in 2013)
4.  Calculate the Top 10 order
5.  Write a Draft/Release Candidate
6.  For 2010, a Draft was reviewed by the Data Contributors and other
    members of the OWASP Community, and the core commenters/contributors
    to the Release Candidate and Final Release were acknowledged here:
    [Top_10_2010-Introduction](Top_10_2010-Introduction "wikilink")
    (About 15 individuals/groups)
      - Note, for 2013 this internal project review step was eliminated
        in order to get the release candidate out for public comment
        faster
7.  Publish Release Candidate for public comment (Prior to 2010 there
    was no release candidate, just a final release)
8.  Accept comments during a comment period
9.  Interact with comment providers to update the Top 10
10. Publish all provided comments
11. Publish a Final Release

This certainly doesn't cover every nuance of what it takes to produce
the Top 10. For example, one of the most common comments is "Why don't
you combine these two items into one to make room for my favorite
Risk?". Like combining XSS into Injection, since XSS is really just a
client side injection issue. The goal of the OWASP Top 10 is to raise
awareness of the most important Risks, not to include every possible
Risk we can stuff into the Top 10. So, in some cases, we've kept related
issues separate to try to increase awareness of each issue. But there is
always debate as to what's best, which is clearly subjective. In the
2013 release candidate, we combined cryptographic storage and
communications into a single category, and then pulled use of known
vulnerable libraries out of the Security Misconfiguration category in
order to bring more attention to the use of Known Vulnerable Libraries
since we believe this is an extremely important issue that deserves more
attention as the use of libraries becomes more and more prevalent. In
past updates, to make room for new issues, we dropped the least
important issues, like error handling and denial of service, which some
people agreed with, but others did not.

In 2010, the Release Candidate process worked like this:

1.  It was open for public comment for several months
2.  Dave Wichers, primarily, interacted via email with each comment
    provider to address their comments or provide rationale as to why no
    change was thought to be most appropriate.
3.  All provided comments were published at:
      - [OWASP Top 10 - 2010 Public
        Comments](http://www.owasp.org/images/e/e1/OWASP_Top_10_RC-Public_Comments.docx),
        and
      - [Kai Jendrian's Top 10 - 2010
        Comments](http://www.owasp.org/images/2/2e/OWASP_T10_-_2010_rc1_cmts_Kai_Jendrian.pdf)
4.  The final version was published.

In 2013, the process is currently like so:

1.  Public comment period of Release Candidate is currently from
    February through end of March 2013. (This can be extended if
    necessary)
2.  We were planning on following the same process as for 2010 to
    complete the Top 10, but clearly the OWASP Community wants to get
    more heavily involved in producing the Final Release, which is
    great.
3.  So, at this point, the process for completing the 2013 Top 10 is
    TBD, subject to your input/suggestions.

# Current Prevalence Data Sources

  - Aspect Security
  - HP (Results for both Fortify and WebInspect)
  - Minded Security -
    [Statistics](http://blog.mindedsecurity.com/2013/02/real-life-vulnerabilities-statistics.html)
  - Softtek
  - Trustwave Spiderlabs -
    [Statistics](http://www2.trustwave.com/rs/trustwave/images/2013-Global-Security-Report.pdf)
  - Veracode –
    [Statistics](http://info.veracode.com/rs/veracode/images/VERACODE-SOSS-V4.PDF)
  - WhiteHat Security –
    [Statistics](https://www.whitehatsec.com/home/resource/stats.html)

If you would like to contribute your vulnerability statistics to the
OWASP Top 10 project, please send your data to: dave.wichers@owasp.org.
Please indicate if its OK for OWASP to publish this raw data. If you
have already published this data, please provide us a link to the public
posting.

Note: In the first version of the Top 10 in 2003, we started with the
MITRE CVE data, and each update expanded the number of prevalence data
contributors. Unfortunately, the CVE data for 2011/2012 wasn't available
for the 2013 release, which is why its not included this year.

# Suggested Enhancements

Note: This is a wiki - please add new suggestions into this page.

1.  Use a public wiki or [google
    issues](http://code.google.com/p/owasptop10/issues/list) to capture
    feedback - mailing lists are tough and things get lost
2.  Use a public wiki to allow for public edits, not just feedback.
    These edits will all be tracked with rollback capabilities for
    editing and will allow the history of Top 10 edit history to be
    "public" for maximum "open" and "visibility".
3.  Establish a Top 10 panel to evaluate and make final decisions on
    inclusion & ranking
      - Not feasible for everyone to vote on every item
      - A diverse panel representing various verticals (vendor,
        enterprise, offense/defense, etc)
4.  Additional data sources could be considered (please add links)
      - WASC [Web Hacking Incident
        Database](http://projects.webappsec.org/w/page/13246995/Web-Hacking-Incident-Database)
          - [WHID Top Attack Methods
            for 2012](https://www.google.com/fusiontables/DataSource?snapid=S91371616ef)
          - [WHID Top App Weaknesses
            for 2012](https://www.google.com/fusiontables/DataSource?snapid=S91371786H4)
      - Firehosts Web Application Attack Reports
          - [Web Application Attack Report for
            Q4 2012](http://www.firehost.com/company/newsroom/web-application-attack-report-fourth-quarter-2012)
      - Imperva's Web Application Attack Reports
          - [Web Application Attack Report for
            Q3 2012](http://www.imperva.com/docs/HII_Web_Application_Attack_Report_Ed3.pdf)
      - Prolexic Attack Report
          - [DDoS Attack Report for
            Q2 2012](http://www.prolexic.com/pdf/Prolexic_Q212_Attack_Report_071212.pdf)
5.  Additional reports could be considered:
      - Annual Symantec Internet Threat Reports
      - Datalossdb
      - IBM XForce threat reports
      - Akamai State of the Internet Reports
6.  Public forum to brainstorm and discuss key topics
7.  Remove corporate logos from the Top Ten PDF and provide a "Who we
    are" link similar to Apache for maximum vendor neutrality:
    <http://hadoop.apache.org/who.html>

# FAQ

1\. The Three Cycle Reasons. Why OWASP Top 10 is release every three
year cycle?

  -
    Here are the reasons:
    a) The field does evolve pretty quick but Top 10 risks not
    substantially change every single year. Release every year is too
    much.
    b) It takes a lot of work to produce OWASP Top 10 update and spacing
    it out balances between the effort to produce and the amount of
    change when its updated.
    c) Lots of organizations, tools, etc, organize to the OWASP Top 10.
    So if it was published every single year, then everyone that chooses
    to align themselves to each update would have to do that work every
    year.

2\. ...