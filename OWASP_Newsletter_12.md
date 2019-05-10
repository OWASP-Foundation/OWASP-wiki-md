## OWASP Newsletter \#12 (01-Feb-2008)

Welcome to the 12th edition of the OWASP Newsletter, featuring the OWASP
AppSec Europe 2008 Call for Papers and the release of ESAPI v1.1.

Don’t forget, there are only a few weeks left until the OWASP Australia
AppSec 2008 Conference. The conference is being held at the Gold Coast
Convention Center in Queensland, Australia, and will include a Training
day on February 27th, and presentations on the 28th and 29th. [Register
Now\!](http://www.owasp.org/index.php/OWASP_Australia_AppSec_2008_Conference)

I would like to welcome OWASP's newest chapters in Jordan, Indianapolis
and Eugene.

As always, if you have any content to add to the next edition, please
feel free to add it directly to its WIKI page [OWASP Newsletter
13](OWASP_Newsletter_13 "wikilink").

Alison McNamee - OWASP Operations Director - alison.mcnamee@owasp.org

## Featured Item: OWASP AppSec Europe 2008 call for papers and refereed papers track

The Call for Papers for the OWASP AppSec Europe 2008 Conference is now
open\! The OWASP AppSec conferences bring together application security
experts and software engineers from all over the world. Industry and
academia meet to discuss open problems and new solutions in application
security. The conferences offer researchers and practitioners a set of
tutorials, keynotes, and invited presentations.

The conference will have the usual two tracks on application security.
The first track will focus on business aspects and also provide some
entry level OWASP topics. The second track wil focus on more technical
and advanced OWASP topics. This year the referereed papers track will be
extended to 2 days.

#### Call for topics-papers

OWASP is seeking for presentations on Application Security and related
OWASP projects from the community. Over the conference program there are
9 technical and 9 business presentation sessions running approximately 1
hour in length each.The call for topics is
[online](OWASP_AppSec_Europe_2008_-_Belgium/CFTP "wikilink") now.

#### Refereed papers track

As in the previous editions, the OWASP AppSec Europe 2008 conference
will feature a refereed papers track. The call for papers is
[online](OWASP_AppSec_Europe_2008_-_Belgium/CFP "wikilink") now.

Submissions are due March 1\!

## Featured Project: ESAPI v1.1

ESAPI v1.1 is now available\! Version 1.1 Major changes include:

1\) ESAPIFilter – Added a new class that can be put in front of most
applications that handles ESAPI busywork including login, logging
requests, URL access check, HTTP request validation (global rules), set
no cache headers, set content type, and threadlocal cleanup.

2\) AccessReferenceMap – Added addDirectReference and
removeDirectReference

3\) Authenticator – Added Request and Response ThreadLocals to allow
logout from the IntrusionDetector

4\) Added “context” parameter to all validation calls so that log
messages can indicate where bad data came from

5\) Encoder – Move canonicalize method from Validator to Encoder as it
seems to fit with all the encoding methods better.

6\) Encryptor – Digital signature keypair is now derived from the master
secret.

7\) HTTPUtilities – Add safe versions of encodeURL and encodeRedirectURL
to prevent session rewriting.

8\) HTTPUtilities – Add methods to encrypt/decrypt the querystring. Also
methods to encrypt/decrypt state into a cookie.

9\) HTTPUtilities – Rename safe versions of dangerous methods in Java to
all start with “safe”, like safeSendRedirect, safeSendForward,
safeAddHeader, safeAddCookie, safeEncodeURL, safeSetContent.

10\) Validator – Add getValidSafeHTML method that invokes OWASP AntiSamy
to clean up rich content that might contain an attack.

11\) HTTPUtilities – Added pragma nocache to the list of HTTP headers
sent for setNoCacheHeaders

12\) Many minor fixes, documentation enhancements, and tweaks.

Learn more on the [Project Home
Page](https://www.owasp.org/index.php/ESAPI)\!

## Latest additions to the WIKI

#### New Pages

  - [ESAPI-Building](http://www.owasp.org/index.php/ESAPI-Building)
  - [Shared Objects](http://www.owasp.org/index.php/Shared_Objects)
  - [SandBox Security
    Model](http://www.owasp.org/index.php/SandBox_Security_Model)
  - [CFPFAQ](http://www.owasp.org/index.php/CFPFAQ)
  - [OWASP AppSec Europe 2008
    Agenda](http://www.owasp.org/index.php/OWASP_AppSec_Europe_2008_-_Belgium/Agenda)
  - [OWASP AppSec Europe 2008
    Training](http://www.owasp.org/index.php/OWASP_AppSec_Europe_2008_-_Belgium/Training)
  - [Struts Validation in validator.xml using an
    ActionForm](http://www.owasp.org/index.php/Struts_Validation_in_validator.xml_using_an_ActionForm)

#### New Chapter Pages

  - [Jordan](http://www.owasp.org/index.php/Jordan)
  - [Indianapolis](http://www.owasp.org/index.php/Indianapolis)
  - [Eugene](http://www.owasp.org/index.php/Eugene)

#### Updated pages

  - [Backend Security
    Project](http://www.owasp.org/index.php/Category:OWASP_Backend_Security_Project)
  - [OWASP Project
    Assessment](http://www.owasp.org/index.php/Category:OWASP_Project_Assessment)
  - [SpoC 2007 Attacks Reference
    Guide](http://www.owasp.org/index.php/SpoC_007_-_Attacks_Reference_Guide)
  - [Spring of Code 2007
    Projects](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_-_Projects)
  - [WebScarab Differences Classic vs.
    NG](http://www.owasp.org/index.php/OWASP_WebScarab_Differences_%28Classic_vs_NG%29)

#### Update Chapter pages

  - [Cincinnati](http://www.owasp.org/index.php/Cincinnati)
  - [Sacramento](http://www.owasp.org/index.php/Sacramento)
  - [New Zealand](http://www.owasp.org/index.php/New_Zealand)
  - [Brazil](http://www.owasp.org/index.php/Brazil_-_San_Paulo)
  - [Helsinki](http://www.owasp.org/index.php/Helsinki)
  - [Austin](http://www.owasp.org/index.php/Austin)
  - [NYNJMetro](http://www.owasp.org/index.php/NYNJMetro)
  - [Rochester](http://www.owasp.org/index.php/Rochester)
  - [Boulder](http://www.owasp.org/index.php/Boulder)
  - [Italy](http://www.owasp.org/index.php/Italy)
  - [Seattle](http://www.owasp.org/index.php/Seattle)

## OWASP references in the Media

  - [Bruce Schneier's Speech at
    OWASP](http://www.technologyevangelist.com/2008/01/bruce_schneiers_spea.html)
  - [Does your enterprise suck at finding top
    talent?](http://duckdown.blogspot.com/2008/01/does-your-enterprise-suck-at-finding.html)
  - [Snake
    Bytes](http://www.darkreading.com/blog.asp?blog_sectionid=403&doc_id=143521&WT.svl=tease2_2)
  - [Another myspace XSS through an
    API](http://ha.ckers.org/blog/20080121/another-myspace-xss-through-an-api/)
  - [OWASP Top 10 - Pune
    Chapter](http://abhijitapatil.blogspot.com/2008/01/owasp-top-10-owasp-pune-chapter.html)
  - [OWASP Java
    Gotchas](http://aboulton.blogspot.com/2008/01/owasp-java-gotchas.html)
  - [Free books to help secure your web
    applications](http://blogs.ittoolbox.com/security/adventures/archives/free-books-to-help-secure-your-web-applications-22154?rss=1)
  - [OWASP San Antonio Presentation about Static
    Analysis](http://denimgroup.typepad.com/denim_group/2008/01/owasp-san-anton.html)