**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Arshan Dabirsiaghi

**Project coordinator**: Jeff Williams

**Project Progress**: 100% Complete, [Progress
Page](SpoC_007_-_OWASP_The_Anti-Samy_Project_-_Progress_Page "wikilink")

## Arshan Dabirsiaghi - OWASP The Anti-Samy Project

(To view the official OWASP AntiSamy project, please go to the project's
new home page at [AntiSamy](AntiSamy "wikilink").

### Executive Summary

My name is Arshan Dabirsiaghi and I am a 25 year old security
consultant. I want to open the door for web sites to allow users to
supply their own HTML without exposing them to cross-site scripting
attacks.

### Background

B.S., M.S. in Computer Science (focus on Information Security)

2.5 years security engineer/consultant experience

4 years of web and systems development

8 years of security hobbying

### Challenge

Many sites today would enjoy the ability to allow users to provide their
own HTML in order to customize their page layout and general user
experience. Because of the concerns regarding XSS, it is generally
thought of as 'too dangerous' to allow them to input any HTML at all.
Sites like MySpace who have been brave enough to provide this
functionality have no standardized, proven solution to validate user
HTML. In many cases, it's easier to disallow everything that looks HTML
or to output encode all user input. Not coincidentally, those sites have
been the targets of complex attacks. Many sites today don't offer this
type of functionality because of concerns for XSS and dangerous HTML.

### Objectives

The first goal is to conduct a survey of existing browsers and compare
their respective behavior regarding JavaScript (both well-formed and
not) inside HTML with regards to W3C specifications

The second goal is to create a software library (versions in both .Net
and J2EE) that can accomplish the following goals:

  - provide an input validation utility that can detect non-obvious
    JavaScript inside user-provided HTML
  - provide a filtering utility that can take blocks of HTML and strip
    any JavaScript inside of it while retaining all formatting-related
    code
  - provide these capabilities even when dealing with realistically
    dirty HTML
  - build on the mountain of research available for parsing broken HTML
  - provide feedback information to the user to help them tune their
    source to fall within acceptable values
  - provide these capabilities in an API that's simple and portable
  - utilize an XML engine file that can be used in various language
    implementations (.Net/J2EE/PHP)

I envision the project requiring 3 man-months, with a few milestones to
be established at reasonable intervals, such as:

  - 3 months out: Begin browser/W3C survey.
  - 2 months out: Finish survey and begin development of API.
  - 1 month out: Complete initial API in both Java and .Net
  - Near release: Perform intense QA on API, fix any remaining bugs.

### Long Term Vision

My goal is to create a peer-reviewed and eventually time-tested solution
for detecting and filtering JavaScript from user input. By doing so, we
can enable web applications to provide users with richer, more
interactive experiences without sacrificing security. This tool will not
only provide an input validation component to sites who are currently
facing this challenge, but it will also act as an enabler to sites who
wished to embrace the new age of user-generated content but were unable
to do so.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**