**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Bunyamin Demir

**Project coordinator**: Ivan Ristic

**Project Progress**: 40% Complete, [Progress
Page](SpoC_007_-_OWASP_WeBekci_Project_-_Progress_Page "wikilink")

## Bunyamin Demir – OWASP WeBekci Project

### Executive Summary

Web application firewalls (WAF) are gaining importance among the
information security technologies designed to protect web sites from
attack. WAF solutions prevent attacks that network firewalls and
intrusion detection systems can't and they require no modification of
application source code. ModSecurity \[17\] is an open source web
application firewall that runs as an Apache module. It is an embeddable
web application firewall and it provides protection from a range of
attacks against web applications. It is an open source project available
to everyone; it however does not come with an admin panel.

I decided to provide this essential tool with a control panel which I
believe will ease and thus encourage its usage.

ModSecurity allows for HTTP traffic monitoring and real-time analysis
with no changes to existing infrastructure. My main goal is to analyze
attacks and generate rules to change the configuration of the
ModSecurity accordingly.

ModSecurity has a feature called “flexible rule engine” as its heart of
Attack Prevention capability . It uses ModSecurity’s “Rule Language,” (a
programming language designed to work with HTTP transaction data). It is
easy to use and flexible; yet the system administrators need to learn
its own rules to create what is called “Certified ModSecurity Rules” to
be implemented. My control panel will automate the major code-generation
in Rule Language.

### Objectives and Deliverables

  - **Configuration** : Will add all configuration parameter (80%)
  - **RuleLoggin Generator**: Will write all the Rules in Rule
    Language(50%)
  - **Logging** : Errorlog, GuardianLog, Auditlog and Debuglog will be
    added.(30%)
  - **Multiple-DB** : Will add PostgreSql and Sqlite support.(0%)

### Why I should be sponsored for the project

I am involved with OWASP Turkey and interested very much in WAF. Even
though this is my first project for OWASP, I am very much interested in
every aspect of ModSecurity. With SpoC007’s support I will finalize my
work on OWASP WeBekci.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**