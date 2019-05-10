## Brief Summary

This section describes how to retrieve information about the application
being tested using spidering and googling techniques.

## Description of the Issue

Web spiders are the most powerful and useful tools developed for both
good and bad intentions on the internet. A spider serves one major
function, Data Mining. The way a typical spider (like Google) works is
by crawling a web site one page at a time, gathering and storing the
relevant information such as email addresses, meta-tags, hidden form
data, URL information, links, etc. The spider then crawls all the links
in that page, collecting relevant information in each following page,
and so on. Before you know it, the spider has crawled thousands of links
and pages gathering bits of information and storing it into a database.
This web of paths is where the term 'spider' is derived from.

The Google search engine found at <http://www.google.com> offers many
features, including language and document translation; web, image,
newsgroups, catalog, and news searches; and more. These features offer
obvious benefits to even the most uninitiated web surfer, but these same
features offer far more nefarious possibilities to the most malicious
Internet users, including hackers, computer criminals, identity thieves,
and even terrorists. This article outlines the more harmful applications
of the Google search engine, techniques that have collectively been
termed "Google Hacking." In 1992, there were about 15,000 web sites, in
2006 the number has exceeded 100 million. What if a simple query to a
search engine like Google such as "Hackable Websites w/ Credit Card
Information" produced a list of websites that contained customer credit
card data of thousands of customers per company? If the attacker is
aware of a web application that stores a clear text password file in a
directory and wants to gather these targets, then he could search on
"intitle:"Index of" .mysql_history" and the search engine will provide
him with a list of target systems that may divulge these database
usernames and passwords (out of a possible 100 million web sites
available). Or perhaps the attacker has a new method to attack a Lotus
Notes web server and simply wants to see how many targets are on the
internet, he could search on "inurl:domcfg.nsf". Apply the same logic to
a worm looking for its new victim.

## Black Box testing and example

### Spidering

**Description and goal**

Our goal is to create a map of the application with all the points of
access (gates) to the application. This will be useful for the second
active phase of penetration testing. You can use a tool such as wget
(powerful and very easy to use) to retrieve all the information
published by the application.

**Test:**

The -S option is used to collect the HTTP header of the web requests.
The --spider options is used to not download anything since we only want
the HTTP header.

    wget -S --spider <target>

**Result:**

    http://www.<target>/
               => `index.html'
    Resolving www.<target>... 64.xxx.xxx.23, 64.xxx.xxx.24, 64.xxx.xxx.20, ...
    Connecting to www.<target>
    |64.xxx.xxx.23
    |:80... connected.
    HTTP request sent, awaiting response...
      HTTP/1.1 200 OK
      Date: Mon, 10 Sep 2007 00:43:04 GMT
      Server: Apache
      Accept-Ranges: bytes
      Cache-Control: max-age=60, private
      Expires: Mon, 10 Sep 2007 00:44:01 GMT
      Vary: Accept-Encoding,User-Agent
      Content-Type: text/html
      X-Pad: avoid browser bug
      Content-Length: 135750
      Keep-Alive: timeout=5, max=64
      Connection: Keep-Alive
    Length: 135,750 (133K) [text/html]
    200 OK

**Test:**

The -r option is used to collect recursively the web-site's content and
the -D option restricts the request only for the specified domain.

    wget -r -D <domain> <target>

**Result:**

    22:13:55 (15.73 KB/s) - `www.******.org/indice/13' saved [8379]

    --22:13:55--  http://www.******.org/*****/********
               => `www.******.org/*****/********'
    Connecting to www.******.org[xx.xxx.xxx.xx]:80... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: unspecified [text/html]

        [   <=>                                                                                                                                                                ] 11,308        17.72K/s

    ...

### Googling

**Description and goal**

The scope of this activity is to find information about a single web
site published on the internet or to find a specific kind of application
such as Webmin or VNC. There are tools available that can assist with
this technique, for example googlegath, but it is also possibile to
perform this operation manually using Google's web site search
facilities. This operation does not require specialist technical skills
and is a good way to collect information about a web target.

'''Useful Google Advanced Search techniques '''

  - Use the plus sign (+) to force a search for an overly common word.
    Use the minus sign (-) to exclude a term from a search. No spaces
    follow these signs.
  - To search for a phrase, supply the phrase surrounded by double
    quotes (" ").
  - A period (.) serves as a single-character wildcard.
  - An asterisk (\*) represents any word —- not the completion of a
    word, as is traditionally used.

Google advanced operators help refine searches. Advanced operators use
the following syntax: operator:search_term . Notice that there is no
space between the operator, the colon, and the search term. A list of
operators and search terms follows:

  - The *site* operator instructs Google to restrict a search to a
    specific web site or domain. The web site to search must be supplied
    after the colon.
  - The *filetype* operator instructs Google to search only within the
    text of a particular type of file. The file type to search must be
    supplied after the colon. Don't include a period before the file
    extension.
  - The *link* operator instructs Google to search within hyperlinks for
    a search term.
  - The *cache* operator displays the version of a web page as it
    appeared when Google crawled the site. The URL of the site must be
    supplied after the colon.
  - The *intitle*, *allintitle* operator instructs Google to search for
    a term within the title of a document.
  - The *inurl*, *allinurl* operator instructs Google to search only
    within the URL (web address) of a document. The search term must
    follow the colon.
  - The *info* operator instructs Google to search only within the
    summary information of a site
  - The *phonebook* operator instructs Google to search business or
    residential phone listing.
  - The *stocks* operator instructs Google to search for stock market
    information about a company.
  - The *bphonebook* operator instructs Google to search business phone
    listing only.

The following are a set googling examples (for a complete list look at
\[1\]):

**Test:**

    site:www.xxxxx.ca AND intitle:"index.of" "backup"

**Result:**

The operator site: restricts a search in a specific domain, while the
intitle: operator makes it possibile to find the pages that contain
"index of backup" as a link title of the Google output.
The AND boolean operator is used to combine more conditions in the same
query.

```
Index of /backup/

 Name                    Last modified       Size  Description

 Parent Directory        21-Jul-2004 17:48      -
```

**Test:**

    "Login to Webmin" inurl:10000

**Result:**

The query produces an output with every Webmin authentication interface
collected by Google during the spidering process.

**Test:**

    site:www.xxxx.org AND filetype:wsdl wsdl

**Result:**

The filetype operator is used to find specific kind of files on the
web-site.

**How can you prevent Google hacking?**

Make sure you are comfortable with sharing everything in your public Web
folder with the whole world, because Google will share it, whether you
like it or not. Also, in order to prevent attackers from easily figuring
out what server software you are running, change the default error
messages and other identifiers. Often, when a "404 Not Found" error is
detected, servers will return a page like that says something like:

    Not Found
    The requested URL /cgi-bin/xxxxxx was not found on this server.
    Apache/1.3.27 Server at your web site Port 80

The only information that the legimitate user really needs is a message
that says "Page Not found." Restricting the other information will
prevent your page from turning up in an attacker's search for a specific
flavor of server. Google periodically purges it's cache, but until then
your sensitive files are still being offered to the public. If you
realize that the search engine has cached files that you want to be
unavailable to be viewed you can go to
<http://www.google.com/remove.html> and follow the instructions on how
to remove your page, or parts of your page, from their database.

**Using a search engine to discover virtual hosts**

Live.com, another well-known search engine (see link at the bottom of
the page), provides the "ip" operator, which returns all the pages that
are known to belong to a certain IP address. This is a very useful
technique to find out which virtual hosts are configured on the tested
server. For instance, the following query will return all indexed pages
belonging to the domain owasp.org:

    ip:216.48.3.18

## References

**Whitepapers**
\* \[1\] Johnny Long: "Google Hacking" - <http://johnny.ihackstuff.com>

**Tools**
\* Google – <http://www.google.com>
\* Live Search - <http://www.live.com>

  - wget - <http://www.gnu.org/software/wget/>
  - Foundstone SiteDigger -
    <http://www.foundstone.com/index.htm?subnav=resources/navigation.htm&subcontent=/resources/proddesc/sitedigger.htm>
  - NTOInsight - <http://www.ntobjectives.com/freeware/index.php>
  - Burp Spider - <http://portswigger.net/spider/>
  - Wikto - <http://www.sensepost.com/research/wikto/>
  - Googlegath - <http://www.nothink.org/perl/googlegath/>
  - Advanced Dork (Firefox Add-on) -
    <https://addons.mozilla.org/firefox/2144/>