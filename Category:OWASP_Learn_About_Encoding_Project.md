{{ ProjectTabs | Proj_About=


**Preamble**

Starting with projects such as overtime

  - **[XSS (Cross Site Scripting) Prevention Cheat
    Sheet](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")**
  - [**ESAPI Codecs and
    Encoder**](http://code.google.com/p/owasp-esapi-java/source/browse/trunk/src/org/owasp/esapi/codecs/?r=364)

The "OWASP Learn About Encoding Project" has not discovered anything
new, but rather wants to emphasize the importance of input sanitize and
output escaping. In the network there are often errors in the
visualization of pages: you see question marks (?) where it should be
accented letters, there are strange characters (i.e. A+tilde, A+umlauts)
where this should be the "euro" character, and so way. Not only that:
but there are communication channels that allow the exchange of
characters not properly controlled: i.e. sms messages, chat messages,
voip client, ecc.. often contain values are not consistent.

The use of proper Charset is essential for

  - integrity of the data: if we take in input some characters, we want
    to "see" the same characters in output
  - the prevention of the problem of Canonicalization: the knowledge of
    Charsets is the first thing to do


**Goal**

This is a project that aims to educate developers, systems analysts or
anyone who writes code regarding the knowledge of proper use of Charset
and Canonicalization. The project will seek to give a comprehensive
response by crossing one another most scenarios highlighting the roles
of key players (browser, operating system, database, etc. ..).

To achieve this goal we decided to create a tool in three different
formats:

  - web application
  - swing application
  - shell tool


|

Proj_Documentation=


**Why do I have to understand about encoding?**
**Why do I have to understand about charset?**


You can find
[**here**](http://code.google.com/p/learn-about-encoding/w/list) some
wiki documents.



#### Download


The project is hosted by Google Code
[**here**](http://code.google.com/p/learn-about-encoding)
You can download the source code from
[**here**](http://code.google.com/p/learn-about-encoding/source/checkout).


\--

#### Project Information

\--\>

#### Project Details

| Proj_Mail =
**A Java security improvement**

<http://blogs.sun.com/CoreJavaTechTips/entry/the_overhaul_of_java_utf>


| Proj_Contributors =
The project hasn't yet a contributor.
If you want to become a contributor start from mailing list:
[**Subscribe
here**](https://lists.owasp.org/mailman/listinfo/owasp-learn-about-encoding)
[**Use here**](mailto:owasp-learn-about-encoding@lists.owasp.org)

}} *Content license:Creative Commons 3.0 BY-SA - Code license:GNU Lesser
General Public License*

[Learn About Encoding Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")