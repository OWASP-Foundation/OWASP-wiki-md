**'[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Bernardo Damele

**Project coordinator**: Dinis Cruz

**Project Progress**: **100%** Complete, [Progress
Page](SpoC_007_-_SQLMap_-_Progress_Page "wikilink")

## Bernardo Damele - SQLMap

### Executive Summary

[sqlmap](http://sqlmap.sourceforge.net) is an automatic SQL injection
tool entirely developed in [Python](http://www.python.org). It is
capable to perform an extensive database management system back-end
fingerprint, retrieve remote DBMS databases, usernames, tables, columns,
enumerate entire DBMS, read system files and much more taking advantage
of web application programming security flaws that lead to SQL injection
vulnerabilities.

### Objectives for OWASP Spring of Code 2007

  - Add support for Oracle database management system
  - Add support to extract database users password hash
  - Extend inband SQL injection functionality to all other possible
    queries
  - Add Microsoft SQL Server database fingerprint
  - Add a fuzzer class with the aim to parse html page looking for
    standard database error messages consequently improving database
    fingerprinting
  - Add support for SQL injection on HTTP *Cookie* and *User-Agent*
    headers
  - Add support for query ETA (Estimated Time of Arrival) real time
    calculation
  - Improve Google dorking support to take advantage of remote hosts
    affected by SQL injection to perform other command line argument
    actions
  - Improve logging functionality

**NOTE**: All objectives have been acoomplished within the deadline
([5th of
November 2007](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007#Schedule)),
check the [Progress
Page](http://www.owasp.org/index.php/SpoC_007_-_SQLMap_-_Progress_Page)
for details.

### Long-term vision for the project

Make sqlmap available as an easy-to-use enumeration and penetration
testing tool to the OWASP community extending its functionality to
exploit SQL injection vulnerabilities to provide a remote shell on the
affected web application database server when possible. In the long run
I would also like to develop a graphical user interface.

### Why I should be sponsored for the project

I have good python programming skills and some years of experience in
computer networks security. I spent most of the last year researching on
web application insecurity taking over the [sqlmap
development](http://sqlmap.svn.sourceforge.net/viewvc/sqlmap/) since
December 2006. Actually I work as software developer at an information
security company in Italy where I mostly deal with vulnerability
assessment.

### Links

  - [sqlmap homepage](http://sqlmap.sourceforge.net)
  - [sqlmap SVN repository web
    interface](http://sqlmap.svn.sourceforge.net/viewvc/sqlmap/)
  - [sqlmap SourceForge File List
    page](https://sourceforge.net/project/showfiles.php?group_id=171598&package_id=196107)
  - [sqlmap development
    documentation](http://sqlmap.sourceforge.net/dev/index.html)

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**