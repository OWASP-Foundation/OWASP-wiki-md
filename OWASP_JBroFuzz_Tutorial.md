

## Introduction

*“If you can’t fuzz with JBroFuzz, you probably do not want to fuzz\!”*

<div align="right">

Old JBroFuzz Motto

</div>


The art of teaching, Mark Van Doren said, is the art of assisting
discovery. Fuzzing is a representative discipline towards assisting the
discovery of security vulnerabilities, that is just beginning to come of
age. Over the last two years, through continuous development, JBroFuzz
has attempted to expose the intrinsic beauty of the subject: Constantly
submit a vast amount of payloads to a service, device or prompt, waiting
for the one response that makes all the difference. This is the
mentality that JBroFuzz embraces and attempts to offer back to security
professionals.

Fuzzing as a concept goes beyond a conventional work flow or a standard
methodology. I would argue that to know how to fuzz well, is to master a
new language. Thus, similar to the process of learning a programming (or
foreign) language, there are three things you must master:

• Grammar: How fuzzing as a process is structured
• Vocabulary: How to name fuzzing concepts you want to use
• Usage: Ways of achieving everyday effective results with fuzzing
![001-JBroFuzz-Tutorial.jpg](001-JBroFuzz-Tutorial.jpg
"001-JBroFuzz-Tutorial.jpg")From the pre-existing information available
for JBroFuzz, this tutorial focuses on usage: How to best put a fuzzing
tool to good use, either via the UI, or using APIs that *JBroFuzz.jar*
is constituted of. As a result, this document has a small requirement as
a caveat; you need to have a beginner level understanding of the Java
programming language in order to understand some sections.

There are a number of working examples described here within, which
**grep** for statements such as “*public static void main(String\[\]
args)*”. The majority of the content relates to reviewing these examples
and putting the Java syntax into a fuzzing perspective.

To summarise, this tutorial focuses on customary and effective usage of
fuzzing through the JBroFuzz Java APIs and the respective UI. It is
targeting (without attacking them) web applications. Without further
redo, let’s get fuzzing\!

## JBroFuzz Basic Functionality

This section carries a number of basic fuzzing examples to get you
started with JBroFuzz. Overall, even though the actions performed to not
produce any amazing fuzzing results, it serves as a starting point in
understanding how to perform particular fuzzing operations on web
applications.

### 'Hello Google\!' (forget 'Hello World')

As the traditional first program that you learn when indulging in a new
programming language, 'Hello World\!' represents the norm for
understanding the basic output operations and syntax (let alone compiler
and execution behaviour) of the language in question.

As with most web application security related tools, when I am given the
responsibility to run them, often in order to understand how they work,
I would first craft a legitimate, single request to a trusted (to be up
and behaving) popular Internet location. Needless, to say this request
more than on occasion finds itself on Google servers.

So 'Hello World\!' for programming languages seems to transform to
'Hello Google\!' for understanding how web application security related
tools work. Let us see, how JBroFuzz does it.

• Double-click on JBroFuzz and browse to the 'Fuzzing' tab

JBroFuzz is constituted of tabs, typically located in the bottom or top
(if you bother to change the settings) of the main window.

The 'Fuzzing' tab is where you craft your request message to a
particular host. Once that is in place, you can select any part of the
request and proceed into adding any number of payloads. We shall see how
in later sections.

• In the 'URL' field type: <http://www.google.com/>
<http://www.google.com>

Unlike conventional URLs, the URL field in JBroFuzz is only used for the
underlying protocol (HTTP or HTTPS), host name (e.g. www.yahoo.com) and
(optionally) port number.

All remaining information pasted or typed into the 'URL' field will be
ignored; you are expected to enter it in the 'Request' field below.

Still, if you want to just copy-paste a URL from a browser, hit
\[Ctrl+L\] while you are not fuzzing, paste the URL value that you have
copied from a browser and JBroFuzz will automatically do the work for
you.

Examples of valid URL values to be put in the

Treat the 'URL' and 'Request' fields as the two stages of a 'telnet'
session on port 80; you are effectively using the 'URL' field to specify
the equivalent of:

`>telnet www.google.com 8088`

As equivalent to:

<http://www.google.com:8088>

or in the case of HTTPS:

<https://www.google.com:8088>

Naturally, default ports for HTTP is 80 and HTTPS is 443.

• In the 'Request' field type:

`GET / HTTP/1.0`


And press 'Enter' twice

This is where the body of the message you are sending is to be placed.
So anything obeying HTTP/S protocol, such as GET and POST requests,
header fields and/or HTML content should be included here.

As part of the process of fuzzing web applications with JBroFuzz you
need to have done your homework, in terms of providing a base request
message. This message is what will be used later on to add payloads to
particular sections of the request.

• Hit 'Start' \[Ctrl+Enter\]

This will instigate the process of sending a single request to the
specified host on a given (or default) port, over HTTP or HTTPS.

Once a connection has been established JBroFuzz will proceed to submit
the message you have typed into the 'Request' field.

Finally, JBroFuzz will log all data sent and received into a file;
accessing this file is typically a process of double clicking on the
output line on the table at the bottom section of the 'Fuzzing' tab.

You should see a response received in the bottom part of the 'Fuzzing'
panel. Double click (or right click for more options) to see the
information exchanged; typically this would be a 302 redirect pointing
you to another location. Congratulations, you have just said "Hello" to
Google\!

![002-JBroFuzz-Tutorial.png](002-JBroFuzz-Tutorial.png
"002-JBroFuzz-Tutorial.png")

Now this would typically be enough under RFC rules, to get a response
back; but damn all the bots out here, most websites require further
information to respond back. So, in the 'Request' field let's pretend to
be a (kind of) legitimate browser by typing:

`GET / HTTP/1.0`
`Host: www.google.com`
`User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.0; en-GB;
rv:1.9.0.10) Gecko/2009042316 Firefox/3.0.10 (.NET CLR 3.5.30729)
JBroFuzz/1.5`
`Accept:
text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8Accept-Language:
en-gb,en;q=0.5Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7`


Not forgetting to end the request typed with two returns: Press 'Enter'
twice. Again, you should be able to see a line added with the response
received back.

Practice sending single requests to a website of your choice by changing
the URL and also the 'Host:' field from the 'Request' above. Also try
accessing an HTTPS website.

Alternatively, you can use the shortcut \[Ctrl+L\] to type in your URL,
with the 'Request' field filled automatically, based on the URL you have
typed.

### HTTP Version Numbers & www.cia.gov Headerless Responses

For web applications, very often ill-defined requests submitted over the
Internet, will trigger semi-legitimate responses that actually do not
obey HTTP RFC protocol specification. Often, even though this is not the
case in this example, these responses can lead to the identification of
one or more security vulnerabilities.

In this example we test for the responses received for invalid HTTP
version numbers on a particular website, namely www.cia.gov, over https.
Now a word of caution here; please do not attempt to fuzz web
applications that you do not have the authority to do so, especially
over the Internet.

Still, for the purposes of this tutorial exercise, we will subject a web
server to no more than a dozen or so requests. These requests would be
otherwise identical, if it was not for the HTTP version number
incrementing by a value of 1 on each request.

In terms of having the authority to do so, well this is identical to
hitting 'Refresh' in your web browser a dozen or so times, while you are
browsing to www.cia.gov. I do not consider this remotely close to any
form of hacking, cracking, or proper fuzzing; web servers across the
globe receive a lot more abuse than this on a daily basis.

Finally, by the time you are reading this, the particular issue
described might have been fixed. So here goes:

• Within JBroFuzz, select:

`File -> Open Location [Ctrl+L]`

Type: <https://www.cia.gov> and hit enter. This is depicted in the
following screenshot:

![JBroFuzz Open Location](003-JBroFuzz-Tutorial.png
"JBroFuzz Open Location")

Hitting 'Enter' should automatically populate the 'URL' field and the
'Request' field within the 'Fuzzing' tab. What you see is the base
request that we intend to add fuzzing payloads to. Before we do so, let
us make one small alteration first:

• Modify the first line of the 'Request' field to:

`GET / HTTP/0.0`

Our objective is to enumerate the supported by the web server (in this
case www.cia.gov) HTTP version numbers, following the two digit format
that it has. We could be a lot more agressive here and test for buffer
overflows and all types of injection; that would be out of line without
the authority to do so. Instead we are going to see how JBroFuzz will
iterate through the values of 0.0 to 1.4 by means of adding a Fuzzer to
our base request.

• Highlight the second zero from the line 'GET / HTTP/0.0' and
right-click, selecting 'Add'. This is depicted in the screeshot below:

![004-JBroFuzz-Tutorial.png](004-JBroFuzz-Tutorial.png
"004-JBroFuzz-Tutorial.png")

• From the appearing 'Add a Fuzzer' window, select as 'Category Name',
in the most left column 'Base' and as 'Fuzzer Name' in the middle column
'Base 10 (Decimal) Alphabet.

• Click on 'Add Fuzzer' on the bottom right of the window

![005-JBroFuzz-Tutorial.png](005-JBroFuzz-Tutorial.png
"005-JBroFuzz-Tutorial.png")

This should add a Fuzzer of length 1 that iterates over the decimal
(i.e. base 10) numbers 0 to 9. If we have added a hexadecimal Fuzzer
instead of a decimal one (i.e. base 16) the iteration would from 0 to F.
If we had selected two digits instead of one and proceeded to add a
decimal Fuzzer, the iteration would be from:

`00`
`01`
`..`
`98`
`99`

From a User Interface (UI) perspective you should see a line added to
the 'Added Payloads Table'.

• Click 'Start' \[Ctrl+Enter\]

This process will send 10 requests to the specified web server changing
only first line of the request to:

`GET / HTTP/0.0...`
`GET / HTTP/0.1...`
`...`
`GET / HTTP/0.8...`
`GET / HTTP/0.9...`

While this is ongoing, you can sort the results by 'No' in the 'Output'
table in the bottom of the 'Fuzzing' tab. This should enable you to see
what request is currently being transmitted and received in real time.

Once complete, change the first line of the 'Request' field to read:

`GET / HTTP/1.0`

• Click 'Start' \[Ctrl+Enter\]

The resulting output should resemble the following screenshot:

![006-JBroFuzz-Tutorial.png](006-JBroFuzz-Tutorial.png
"006-JBroFuzz-Tutorial.png")

Straight away we can notice a difference in the response size: For HTTP
version numbers 0.0 to 0.9 we are getting back what seems fairly big in
size responses; 32222 bytes in size worth of responses, given that HTTP
protocol version 0.0 to 0.8 do not officially exist\!

By double-clicking on one of these requests, we can see that the web
server in question is responding back with no headers, yet returning a
full HTML body; this represents the 32222 bytes of response of data we
are receiving back. The following screenshot illustrates this:

![007-JBroFuzz-Tutorial.png](007-JBroFuzz-Tutorial.png
"007-JBroFuzz-Tutorial.png")

Using the 'Graphing' tab we can proceed to graph the particular requests
and responses for this given session.

• Within the 'Graphing' tab, click 'Start' \[Ctrl+Enter\].

• Select the directory corresponding to the Output folder we have used
for this fuzzing session. This will typically be the last one.

• Right-click and select 'Graph'

Once complete, browse to the 'Response Size' tab within the 'Graphing'
tab, as illustrated in the screenshot below:

![008-JBroFuzz-Tutorial.png](008-JBroFuzz-Tutorial.png
"008-JBroFuzz-Tutorial.png")

To re-iterate this does not present a security vulnerability in any
shape or form; merely the fact that by manipulating HTTP version numbers
as part of the request we transmit, we can impact the response that we
get back. In this case, what changes is the non-existent header fields,
with some HTML content being received back.

If I was to guess what is causing this, I would say that some sort of
load balancing or content delivery is not happening as it should when
non-existent version numbers are being transmitted.

## Using JBroFuzz with a Generic Proxy

JBrofuzz 2.0 and subsequent releases include generic proxy support. As
of this writing, basic authentication is supported with plans to
eventually support NTLM and Kerberos authentication as well. We've tried
to make the use of a proxy as straight forward as possible. All
arguments for the proxy can be passed in the URL field and will take one
of the following forms.

    Without Authentication: <proxy server>:<proxy port>
    With Authentication: <proxy username>:<proxy password>@<proxy server>:<proxy port>

The structure of the request field and whether the GET parameter
contains an absolute URL depends on the proxy you are using. For this
reason, you may have to do a bit of trial and error to determine what
format(s) your proxy accepts. To make all of this a bit clearer lets
look at a couple of examples.

### Squid Proxy

In the first example, we are fuzzing through a squid proxy that requires
ncsa user authentication as shown in the figure below. When producing
similar results, its important that you use your own proxy and not the
one shown in the figure. This proxy was setup for demonstration
purposes, will not accept connections from your IP address, and the
credentials will no longer be active.

![016-JBroFuzz-Tutorial.jpg](016-JBroFuzz-Tutorial.jpg
"016-JBroFuzz-Tutorial.jpg")

### Paros Proxy

In the second example, we are fuzzing through a local Paros proxy
running on port 8080 that does not require user authentication. Notice
the difference in the syntax of the URL field when user authentication
is not required.

![017-JBroFuzz-Tutorial.jpg](017-JBroFuzz-Tutorial.jpg
"017-JBroFuzz-Tutorial.jpg")

In the third example, we are still fuzzing through Paros, but notice the
slight difference in the Request Field. Specifically, pay special
attention to the GET line. We are no longer including the fully
qualified path. Unlike Squid, Paros will accept both formats. Keep this
in mind when you are performing initial testing with JBroFuzz and the
proxy of your choice.

![018-JBroFuzz-Tutorial.jpg](018-JBroFuzz-Tutorial.jpg
"018-JBroFuzz-Tutorial.jpg")

### Burp Proxy

In the final example, we are fuzzing through Burp. Similar to Squid,
Burp requires absolute URLs in the request. A successful Burp request is
shown below.

![019-JBroFuzz-Tutorial.jpg](019-JBroFuzz-Tutorial.jpg
"019-JBroFuzz-Tutorial.jpg")

## Using JBroFuzz with Paros Proxy

JBroFuzz is a standalone fuzzer; it can release and create sockets over
HTTP and HTTPS, but in order to use JBroFuzz correctly you will have to
know what it is that you are fuzzing.

In comes the need for a proxy tool; the opening versions of JBroFuzz
actually had a proxy tab that you could use to intercept traffic
generated by your web browser. That functionality got removed in an
attempt to focus and deliver solely on the fuzzing capabilities of the
tool.

This section details how to use JBroFuzz in combination with a client
side proxy. The one selected is Paros Proxy, which, despite the fact
that it hasn't been updated since 2006 is still a popular tool that you
see in web security testing live CDs. You could use any of the other
proxy tools available.

### Winning on a Remix of the Year Award

At 17:53, on a frosty winter evening, a message window popped up:

    17:53 http://www.localhost.com/remixcontest/club/annual2010.html
    17:53 Hey bro, could you cast in a vote here for the Such & Such Remix?
    17:53 Appreciated!

A friend in need is a friend indeed, so here goes I thought. Opening up
a web browser configured to work with Paros as an intermediate proxy,
allowed for the casting of my vote. while keeping a record of each
request and reply.

No registration, or any other form of submitting an identifier was
needed. The request that Paros stored for the casting of the actual vote
was:

    GET http://www.localhost.com/remixcontest/club/vote.php?onLoad=%5Btype%20Method%5D&id=55 HTTP/1.1
    Host: www.localhost.com
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-GB; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 (.NET CLR 3.5.30729) Paros/3.2.13
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-gb,en;q=0.5
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Proxy-Connection: keep-alive
    Cookie: PHPSESSID=ab6afb883dbgf8084f6dcf1eafdb225e

Paros Proxy actually places the domain (in this case www.localhost.com)
with the protocol (i.e. http) in front of the GET request. As a result,
you can't open a telnet/netcat session and just copy-paste the above.
Similarly when we bring the request into JBroFuzz, a bit of tweaking is
required.

  - In the URL field, type:

<!-- end list -->

    http://www.localhost.com

In the Request field, let's keep what is of interest:

    GET /remixcontest/club/vote.php?onLoad=%5Btype%20Method%5D&id=55 HTTP/1.0
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-GB; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-gb,en;q=0.5
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Cookie: PHPSESSID=ab6afb883dbgf8084f6dcf1eafdb225e

No needs for Keep-Alive and Proxy-Connection. Let's simplify the HTTP
request by making it a version 1.0 request and getting rid of the Host
header as well. Also on the user agent, let us keep that mainstream
vanilla: Firefox on Windows (popular browser combination), getting rid
of the .NET and Paros additives.

Checking on the website, our Such & Such remix already has about 100
votes or so and the top remix has approximately 310 votes. Let's fuzz
this:

  - Select 2 of the digits of the cookie value:

<!-- end list -->

    PHPSESSID=ab6afb883dbgf8084f6dcf1eafdb225e

  - Select: Panel -\> Add

<!-- end list -->

  - In the "Add a Fuzzer" panel, select:

<!-- end list -->

    Base -> Base16 (HEX)

and select "Add Fuzzer".

This will add a line within the Payloads tab on the right hand side.

Our cookie value above (PHPSESSID=ab6afb883dbgf8084f6dcf1eafdb225e) is
in lowercase, hexadecimal format. Let's make sure the encoding we select
is also that.

Within the Payloads tab, click on the encoding drop down menu and select
lowercase. Just before clicking "Start", JBroFuzz should look something
like the screenshot below.

![Adding Votes by iterating through PHPSESSID cookie
values](014-JBroFuzz-Tutorial.png
"Adding Votes by iterating through PHPSESSID cookie values")

## Performing User Enumeration with a Valid Set of Credentials

Often you encounter an application that allows for the enumeration of
one or more pages after a user has been successfully granted a set of
session credentials. One of the key areas to test from an application
specific perspective, relates to the page(s) that provide user account
information.

In the following example, we investigate an ASP.NET 2.0 application with
a C\# back-end. In this, an authenticated user has the option to select
to "View My Profile". This page provides them with account information
(including the typical username, email address, further notes) that they
can proceed to update and save to the back-end system.

After a user has authenticated, the following URL, gives them access to
their profile information stored on the database:

    http://www.myattackingdomain.com/portal-location/UserInfo.aspx?UserID=23

Simple investigation confirms that the digits allowed as part of the
UserID value are decimal numbers only. Lets feed that information into
JBroFuzz.

### Fuzzing a User ID

• Within JBroFuzz, select:

`File -> Open Location [Ctrl+L]`

Type:
<http://www.myattackingdomain.com/portal-location/UserInfo.aspx?UserID=23>
and hit enter. This is depicted in the following screenshot:

![009-JBroFuzz-Tutorial.png](009-JBroFuzz-Tutorial.png
"009-JBroFuzz-Tutorial.png")

From the URL the important parameter is the value of the UserID query
string (the value 23, above). We want to fuzz that.

• Within the Fuzzing Tab, in the "Request" text area, highlight the
above number 23 • Right-click and select "Add"

In the "Add a Fuzzer" window that appears, select:

• Category Name: `Base` • Fuzzer Name: `Base10 (DEC)` • Select "Add
Fuzzer" in the bottom right

This would have added a decimal (base 10 fuzzer) of length 2 onto the
location.

• You will see a row added within the "Added Fuzzers Table" of the
Fuzzing panel. • Click "Start" `Ctrl+Enter`

This will transmit 100 requests to the domain in question, which in this
case is assumed: www.myattackingdomain.com. The value being changed
within each request will be:

    • GET /portal-location/UserInfo.aspx?UserID=00 HTTP/1.0
    • GET /portal-location/UserInfo.aspx?UserID=01 HTTP/1.0
    ...
    • GET /portal-location/UserInfo.aspx?UserID=98 HTTP/1.0
    • GET /portal-location/UserInfo.aspx?UserID=99 HTTP/1.0

Done. Let's proceed to graph the responses that we have obtained. Our
objective is to understand which two-digit numbers from 00 to 99
correspond to valid user accounts.

### Graphing Results

• Within the "Graphing" tab, click "Start" `Ctrl+Enter`

A list of directories will appear on the left-hand side. If you scroll
to the bottom of the list you should see the directory corresponding to
your fuzzing session, in our case it was (175 2009-06-24 16-18-24)

    • Right-click on (175 2009-06-24 16-18-24)
    • Click "Graph"

This will generate the graphs in their respective tabs. The question now
becomes which graph is of interest for our user enumeration exercise.

By definition enumerating users against an ID value, or any other
identifier involves being able to obtain a different response for an
existing user to that of a user that is not have a corresponding ID
value.

Thus, from the metrics available, the one useful for enumerating users
will be that of measuring the "Hamming Distance" between responses
received. Based on the JBroFuzz documentation:

'''Fuzzing Hamming Distance '''

    A bar chart with the hamming distance of the characters in the response,
    relative to the first response received. Check each character of the first
    response received, against the character at the same position of the
    current response received. If they are not identical, increment the
    hamming distance.

As we can see the Fuzzing Hamming Distance (FHD) varies quite a bit from
the definition of the normal hamming distance term, used in
telecommunications. Still, they share a lot of similarities.

As we can from the above, the first request is critical to calibrating
our user enumeration exercise. It represents the value that all other
Fuzzing Hamming Distances (FHD) will be measured and normalised towards.
For the java-skilled audience, the algorithm is quite trivial, but
offers spectacular results in distinguishing responses:

    in = new BufferedReader(new FileReader(f));
       58
       59           int counter = 0;
       60           int check = 0;
       61           int c;
       62           while (((c = in.read()) > 0) && (counter < MAX_CHARS)) {
       63
       64               // If we are passed "--jbrofuzz-->\n" in the file
       65               if (check == END_SIGNATURE.length()) {
       66
       67                   firstSet.append((char) c);
       68
       69               }
       70               // Else find "--jbrofuzz-->\n" using a counter
       71               else {
       72                   // Increment the counter for each success
       73                   if (c == END_SIGNATURE.charAt(check)) {
       74                       check++;
       75                   } else {
       76                       check = 0;
       77                   }
       78               }
       79
       80               counter++;
       81
       82           }
       83           in.close();

Ergo, the corresponding graph is depicted in the screenshot below. The
peak graphs correspond to number that if you hover the mouse over will
give you the enumeration ID of a valid user.

![015-JBroFuzz-Tutorial.png](015-JBroFuzz-Tutorial.png
"015-JBroFuzz-Tutorial.png")

## Eliminating False Positives: LDAP Injection

Every now and then a tool (that does not produce false positives) will
hit an application reporting back a huge variety of (hopefully not
confirmed, but pending further investigation) injection findings.

Due to the limited number of characters required in performing LDAP
Injection, such issues will be high on that list. But let's refresh our
memory a bit of how LDAP injection works:

<http://www.owasp.org/index.php/LDAP_injection>

So typically, during an automated scan, negating LDAP cn-type queries
would be submitted and their responses noted. Example:

    GET /myfilelocation.jsp?lang=en&city=user)(sn=*&rid=97 HTTP/1.1
    ...

vs.

    GET /myfilelocation.jsp?lang=en&city=user)!(sn=*&rid=97 HTTP/1.1
    ...

or

    GET /myfilelocation.jsp?lang=en&city=admin*)((
    |userpassword=*)&rid=97 HTTP/1.1
    ...

As great as this check might be from an LDAP perspective, it has a high
likelihood of generating false positives, due to the character sets
being used. Ergo, a protection mechanism (silly worst-case blacklist
present for example) would typically hunt down cross-site scripting and
sql injection type of characters:

    < > ' etc.

Not considering =, \*, or brackets as completely bad (he says).

### What characters are allowed through?

Enough of all that; we want to know what responses are allowed back and
what's different about them for all characters being filtered through a
black-list.

Let's transform the above GET into the following and proceed to add a
single fuzzer that tells us that:

    GET /myfilelocation.jsp?lang=en&city=X&rid=97 HTTP/1.1

Now in the position of the X character, proceed to add an ASCII 94
Alphabet Fuzzer (available in version 2.1 and above). This will check
the responses for all characters which are printable ASCII, with the
exception of space.

In total there are 95 printable ASCII characters; minus the one present
for space (yes, the one you hit all the time, every day) leaves 94. This
fuzzer produces each of those values, in incrementing ASCII order.

![020-JBroFuzz-Tutorial.png](020-JBroFuzz-Tutorial.png
"020-JBroFuzz-Tutorial.png")

Based on the above graph, the following responses trigger a different
response size. Thus the characters blocked by a black-list are:

    ! " , < > @ [ \ ] ^ ` {
    | } ~

Interesting. Know any payloads that can evade those?

  -
    )

## JBroFuzz Development Corner

This section presents how to setup and use JBroFuzz as a fuzzing
library. Also, it offers an insight in how to setup and compile your own
version of JBroFuzz. As different people have different levels of
expertise of the java programming language, eclipse, ant and subversion,
some of the steps presented herein might be considered basic by advanced
developers.

### Setting up a JBroFuzz Development Environment

This section guides you towards setting up a development environment for
JBroFuzz. Despite the Operating System (O/S) being windows XP, a similar
process can be followed in a number of other O/S.

You will need to have installed:

  - Tortoise SVN (using TortoiseSVN-1.6.6.17493-win32-svn-1.6.6.msi)
  - Eclipse Java (using eclipse-java-galileo-SR1-win32.zip)

Optionally, if you don't like building your application through eclipse
you could also require to install Apache Ant.

#### Step 1: Obtain the source code

JBroFuzz uses SubVersion with the repository being publicly available
for download through anonymous access on sourceforge. There is a plan to
move it the source to the OWASP Git repository, but until then, use the
guidelines below.

![Tortoise SVN Check out JBroFuzz Source Code](010-JBroFuzz-Tutorial.png
"Tortoise SVN Check out JBroFuzz Source Code")

Right click on the folder location where you want to download the source
code and select:

  - SVN Checkout

In the "URL of repository", enter:

    https://jbrofuzz.svn.sourceforge.net/svnroot/jbrofuzz

In the "Checkout directory", enter the folder location of your choice,
in this case:

    C:\root\code\jbrofuzz

In the "Checkout Depth" select:

  - Fully recursive

Untick "Omit Externals" (should be unticked by default)

In the "Revision" select:

  - "Head revision"

Select OK.

This process, once complete will checkout the entirety of the JBroFuzz
source code from the SVN repository on sourceforge.

#### Step 2: Configuring a JBroFuzz Project within Eclipse

Having obtained the latest copy of the source code, the next step
entails importing that source code within the Eclipse IDE.

Within Eclipse, select:

    File -> New -> Other

From the "New" panel that appears, select:

    Java -> Java Project from Existig Ant Buildfile

![Import JBroFuzz Code into Eclipse from Ant
File](011-JBroFuzz-Tutorial.png
"Import JBroFuzz Code into Eclipse from Ant File")

Select "Next".

In the next menu, under "Ant buildfile", select "Browse".

Browse to the location where you have just (step 1) downloaded the
source code and select the following file:

  - build.xml

The build.xml file is an Ant build file that JBroFuzz uses.

![Select the Ant File](012-JBroFuzz-Tutorial.png "Select the Ant File")

Selecting that file should have populated the "Project name" as jbrofuzz
and also given you:



    "javac" task found in target "compile"

MAKE SURE TO TICK:

  - "Link to the buildfile in the filesystem"

Otherwise eclipse will try to replicate the source code within your
workspace and that makes the process a tiny bit more complicated when it
comes to actually building JBroFuzz.

Click "Finish"

You will see the item "Building workspace (76%) on the bottom right hand
side of Eclipse. Once that is complete, you should see the jbrofuzz
project on the top left corner of the Package Explorer within Eclipse.

#### Step 3: Building JBroFuzz

Within the Package Explorer, expand the jbrofuzz project and
double-click on the build.xml file.

Right click on the "build \[default\]" task within the "Outline" window
(typically seen on the right hand side) and select:

    Run As -> 1. Ant Build [Alt+Shift+X, Q]

If the build has been successful, a JBroFuzz.jar file within the the
/jar folder would have been created. Following the path conventions
above that should be in:

    C:\root\code\jbrofuzz\jar\JBroFuzz.jar

![Building JBroFuzz within Eclipse](013-JBroFuzz-Tutorial.png
"Building JBroFuzz within Eclipse")

### How to Use JBroFuzz as a Fuzzing Library

Quite often what you need to do in terms of fuzzing, far exceeds the
User Interface (UI) of JBroFuzz. For this reason, a set of core fuzzing
APIs have been made available that can be used for more advanced fuzzing
scenarios.

The JBroFuzz.jar standalone archive (made available with every release)
carries a core fuzzing library that holds a number of key classes. These
are located under:

    org.owasp.jbrofuzz.core.*;
    -Database.java
    -Fuzzer.java
    -FuzzerBigInteger.java
    -NoSuchFuzzerException.java
    -Prototype.java

The class of importance is Fuzzer.java. If you are going to use
recursive iterators of great length, there is also
FuzzerBigInteger.java. The difference between the two is that
Fuzzer.java uses the primitive java data type long (up to 16^16 values)
while FuzzerBigInteger.java uses java BigInteger to perform the
counting. Naturally, the class FuzzerBigInteger is slower and takes more
memory than the Fuzzer class.

Within JBroFuzz a Fuzzer is an instance of a java Iterator. This implies
that values can be accessed by simply calling the `next()` method once
an object has been made available. Typically, a call to `hasNext()`
should also be performed prior to avoid an exception being thrown.

A Fuzzer can be obtained from the factory method `createFuzzer(String,
int);` available for every instance of the fuzzing Database. Ergo:

#### A HelloFuzzer Example

    Database myDatabase = new Database();

    Fuzzer myFuzzer = myDatabase.createFuzzer("031-B16-HEX", 5);

So how do I use the API? Here is a simple HelloFuzzer (file called
HelloFuzzer.java) example:

    import org.owasp.jbrofuzz.core.*;

    public class HelloFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     try {
         for(Fuzzer f = fuzzDB.createFuzzer("031-B16-HEX", 4); f.hasNext();) {
           // Get the next payload value...
           System.out.println(" The fuzzer payload is: " + f.next());
         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloFuzzer.java OWASP JBroFuzz Example 1

To compile the above use:

    javac -classpath ".\jbrofuzz\jar\JBroFuzz.jar" HelloFuzzer.java

This assumes that you are currently inside the directory where
HelloFuzzer.java resides and that the JBroFuzz.jar is located two
directories within your current location i.e. in jbrofuzz/jar. In order
to run the above compiled HelloFuzzer class issue:

    java -cp ".\jbrofuzz\jar\JBroFuzz.jar;." HelloFuzzer

Note: The above 2 commands have been crafted in a win32 environment. The
process for compiling and running HelloFuzzer.java above is the same in
\*nix machines. Simply replace the backslash "\\" with "/".

#### Fuzzing Payload Definitions

Within the JBroFuzz.jar file, there is a file called fuzzers.jbrf that
carries all the fuzzer definitions that you see in the UI payloads tab
of JBroFuzz. To view a latest copy of this file you can browse the SVN
repository of JBroFuzz:

    http://jbrofuzz.svn.sourceforge.net/viewvc/jbrofuzz/tar/fuzzers.jbrf?view=log

A note here worth mentioning: Files ending in .jbrofuzz are session
files saved by users while performing fuzzing operations. Files ending
in .jbrf are JBroFuzz system files. Typical examples of .jbrf files are
headers.jbrf, as well as fuzzers.jbrf. Both these use an internal
proprietary format not to be confused with the .jbrofuzz file format.

Fuzzers belong in categories (1 to many) and each fuzzer carries a set
of payloads that define the alphabet of the fuzzer.

Also, you have replacive and recursive fuzzers, zero fuzzers, etc. There
are a number of different fuzzer categories. As an example of a fuzzer
within the fuzzers.jbrf file, consider the hexadecimal fuzzer:

    Fuzzer Name: Base16 (HEX)
    Fuzzer Type: Recursive
    Fuzzer Id:   031-B16-HEX

    Total Number of Payloads: 16

Within the fuzzers.jbrf file this fuzzer is defined in plain-text format
as follows:

    R:031-B16-HEX:Base16 (HEX):16
    > Number Systems
    | Base
    | Recursive Fuzzers
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    a
    b
    c
    d
    e
    f


There is very little preventing you from defining your own fuzzers
within this file, by following the file format specified above. You can
use the UI to see if they have been loaded successfully.

Further to recursive and replacive fuzzers you also have zero fuzzers
(i.e. a zero fuzzer of 1000 will just transmit 1000 requests as they
are, without adding any payloads) double fuzzers, cross product fuzzers,
etc.

Notice the factory method Database.createFuzzer("031-B16-HEX", 4)
yielding: "I want a 4 digit recursive fuzzer (why because NUM-HEX is
recursive in its definition, starts with R: instead of P:) of HEX
digits."

Thus the above scenario would iterate through all the digits from 0000
to ffff. I wouldn't recommend using the above scenario for such trivial
fuzzing capabilities; simply presented as an example of the inner
workings of JBroFuzz.jar

#### HelloFuzzer Refined

A more detailed code breakdown of the above HelloFuzzer example can be
found below:

    /**
     * JBroFuzz API Examples 01
     *
     * JBroFuzz - A stateless network protocol fuzzer for web applications.
     *
     * Copyright (C) 2007, 2008, 2009 subere@uncon.org
     *
     * This file is part of the JBroFuzz API examples on how to use the
     * fuzzer libraries included in JBroFuzz.jar.
     *
     * JBroFuzz is free software: you can redistribute it and/or modify
     * it under the terms of the GNU General Public License as published by
     * the Free Software Foundation, either version 3 of the License, or
     * (at your option) any later version.
     *
     * JBroFuzz is distributed in the hope that it will be useful,
     * but WITHOUT ANY WARRANTY; without even the implied warranty of
     * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
     * GNU General Public License for more details.
     *
     * You should have received a copy of the GNU General Public License
     * along with JBroFuzz.  If not, see <http://www.gnu.org/licenses/>.
     * Alternatively, write to the Free Software Foundation, Inc., 51
     * Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
     *
     * Verbatim copying and distribution of this entire program file is
     * permitted in any medium without royalty provided this notice
     * is preserved.
     *
     */

    import org.owasp.jbrofuzz.core.NoSuchFuzzerException;
    import org.owasp.jbrofuzz.core.Database;
    import org.owasp.jbrofuzz.core.Fuzzer;

    /**
     * <p>In JBroFuzz a Fuzzer is a java Iterator.</p>
     *
     * <p>In order to create a Fuzzer, use the factory method
     * Database.createFuzzer(String, int), passing as arguments
     * the Fuzzer ID and the specified length as a positive int.</p>
     *
     * <p>Be careful to check that the fuzzer ID (labelled as f_ID)
     * is actually an existing ID from the Database of Fuzzers.</p>
     *
     * <p>Expected Output:</p>
     * <code>
     *  The fuzzer payload is: 00000<br>
     *  The fuzzer payload is: 00001<br>
     *  ...<br>
     *  (a total of 16^5 = 1048576 lines)<br>
     *  ...<br>
     *  The fuzzer payload is: ffffd<br>
     *  The fuzzer payload is: ffffe<br>
     *  The fuzzer payload is: fffff<br>
     * </code>
     *
     * <p>For more information on the Database of Fuzzers, see the
     * HelloDatabase Class.</p>
     *
     * @author subere@uncon.org
     * @version n/a
     */
    public class HelloFuzzer {

        /**
         * @param args
         */
        public static void main(String[] args) {

            // You have to construct an instance of the fuzzers database
            Database fuzzDB = new Database();
            // You have to supply a valid fuzzer ID
            String f_ID = "031-B16-HEX";
            // You have to supply a (+)tive int
            int f_len = 5;

            try {

                for(Fuzzer f = fuzzDB.createFuzzer(f_ID, f_len); f.hasNext();) {

                    // Get the next payload value...
                    System.out.println(" The fuzzer payload is: " + f.next());

                }

            } catch (NoSuchFuzzerException e) {

                System.out.println("Could not find fuzzer " + e.getMessage());

            }

        }

    }

#### Hello Database of Fuzzers

Having seen how to access a single Fuzzer through the createFuzzer()
method available in the Database object. The next question that comes
naturally is what are the Fuzzers that are available by default in
JBroFuzz?

To answer that, this example focuses more on the database component that
we previously initialised, investigating the list of available methods
that it offers.

In JBroFuzz, all Fuzzers are stored in a Database object that you will
be required to construct in order to access them.

    /**
     * JBroFuzz API Examples 02
     *
     * JBroFuzz - A stateless network protocol fuzzer for web applications.
     *
     * Copyright (C) 2007, 2008, 2009 subere@uncon.org
     *
     * This file is part of the JBroFuzz API examples on how to use the
     * fuzzer libraries included in JBroFuzz.jar.
     *
     * JBroFuzz is free software: you can redistribute it and/or modify
     * it under the terms of the GNU General Public License as published by
     * the Free Software Foundation, either version 3 of the License, or
     * (at your option) any later version.
     *
     * JBroFuzz is distributed in the hope that it will be useful,
     * but WITHOUT ANY WARRANTY; without even the implied warranty of
     * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
     * GNU General Public License for more details.
     *
     * You should have received a copy of the GNU General Public License
     * along with JBroFuzz.  If not, see <http://www.gnu.org/licenses/>.
     * Alternatively, write to the Free Software Foundation, Inc., 51
     * Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
     *
     * Verbatim copying and distribution of this entire program file is
     * permitted in any medium without royalty provided this notice
     * is preserved.
     *
     */

    import org.owasp.jbrofuzz.core.NoSuchFuzzerException;
    import org.owasp.jbrofuzz.core.Database;
    import org.owasp.jbrofuzz.core.Fuzzer;

    /**
     * <p>In JBroFuzz all Fuzzers are stored in a Database
     * object that you will be required to construct in order
     * to access them.</p>
     *
     * <p>Within the Database, each Fuzzer is a collection of
     * payloads, which carries a unique ID string value.</p>
     *
     * <p>Example ID values are the output of this program:</p>
     * <code>
     *  The fuzzer ID is: 013-LDP-INJ<br>
     *  The name of the fuzzer is:          LDAP Injection<br>
     *  The id of the fuzzer is:            013-LDP-INJ<br>
     *  The of payloads it carries (it's alphabet) is:  20<br>
     *  It has as 1st payload:<br>
     *
    |<br>
     *  The fuzzer ID is: 018-XSS-4IE<br>
     *  The name of the fuzzer is:          XSS IE<br>
     *  The id of the fuzzer is:            018-XSS-4IE<br>
     *  The of payloads it carries (it's alphabet) is:  38<br>
     *  It has as 1st payload:<br>
     *      < img src=`x` onrerror= ` ;; alert(1) ` /><br>
     *
     * </code>
     *
     * <p>Do not be confused between Prototypes and Fuzzers;
     * JBroFuzz uses Prototype objects to construct the Fuzzers
     * that get added into the Database upon initialisation.</p>
     *
     * <p>As a result, the getter methods available within a Database
     * object can carry the name of getAllPrototypeIDs and
     * getAllFuzzerIDs interchangebly.</p>
     *
     * @author subere@uncon.org
     * @version n/a
     */
    public class HelloDatabase {

        /**
         * @param args
         */
        public static void main(String[] args) {

            // You have to construct an instance of the fuzzers database
            Database fuzzDB = new Database();

            // Get a list of all the fuzzer IDs from the database
            String[] fuzzer_IDs = fuzzDB.getAllPrototypeIDs();

            System.out.println("The fuzzer IDs found are:");

            for(String fuzzerID : fuzzer_IDs) {

                System.out.println("The fuzzer ID is: " + fuzzerID);

                // We pass of length of 1, irrelevant if we are
                // just going to access the first payload
                // of the fuzzer
                Fuzzer fuzzer;
                try {

                    fuzzer = fuzzDB.createFuzzer(fuzzerID, 1);
                    // Normally you should check for fuzzer.hasNext()
                    String payload = fuzzer.next();

                    System.out.println("\tThe name of the fuzzer is:\t\t\t" + fuzzer.getName() );
                    System.out.println("\tThe id of the fuzzer is:\t\t\t" + fuzzer.getId() );
                    System.out.println("\tThe of payloads it carries (it's alphabet) is:\t" + fuzzDB.getSize(fuzzerID));
                    System.out.println("\tIt has as 1st payload:\n\t\t" + payload );

                } catch (NoSuchFuzzerException e) {
                    System.out.println("Could not find the specified fuzzer!");
                    System.out.println("Going to print all the fuzzer IDs I know:");
                    // old vs new for loop :)
                    // in case of an error, print just the
                    // fuzzer IDs, accessed from the DB
                    for(int j = 0; j < fuzzer_IDs.length; j++) {
                        System.out.println("The fuzzer ID is: " + fuzzer_IDs[j]);
                    }

                }

            }

        }

    }

#### Methods available within the Fuzzer Class

A final example of this section, involves seeing the usage of all the
method calls available in the Fuzzer.java class

    /**
     * JBroFuzz API Examples 03
     *
     * JBroFuzz - A stateless network protocol fuzzer for web applications.
     *
     * Copyright (C) 2007, 2008, 2009 subere@uncon.org
     *
     * This file is part of the JBroFuzz API examples on how to use the
     * fuzzer libraries included in JBroFuzz.jar.
     *
     * JBroFuzz is free software: you can redistribute it and/or modify
     * it under the terms of the GNU General Public License as published by
     * the Free Software Foundation, either version 3 of the License, or
     * (at your option) any later version.
     *
     * JBroFuzz is distributed in the hope that it will be useful,
     * but WITHOUT ANY WARRANTY; without even the implied warranty of
     * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
     * GNU General Public License for more details.
     *
     * You should have received a copy of the GNU General Public License
     * along with JBroFuzz.  If not, see <http://www.gnu.org/licenses/>.
     * Alternatively, write to the Free Software Foundation, Inc., 51
     * Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
     *
     * Verbatim copying and distribution of this entire program file is
     * permitted in any medium without royalty provided this notice
     * is preserved.
     *
     */

    import org.owasp.jbrofuzz.core.NoSuchFuzzerException;
    import org.owasp.jbrofuzz.core.Database;
    import org.owasp.jbrofuzz.core.Fuzzer;

    /**
     * <p>Example iterating through all the methods available
     * in the Fuzzer Object and their respective outputs.</p>
     *
     * @author subere@uncon.org
     * @version n/a
     */
    public class IndigoFuzzerTests {

        /**
         * @param args
         */
        public static void main(String[] args) {

            // You have to construct an instance of the fuzzers database
            Database fuzzDB = new Database();
            // You have to supply a valid fuzzer ID
            String f_ID = "033-B08-OCT";
            // You have to supply a (+)tive int
            int f_len = 5;

            try {

                Fuzzer f = fuzzDB.createFuzzer(f_ID, f_len);

                while(f.hasNext()) {

                    // Could do this via reflection, but..
                    f.next();
                    // System.out.println(" The fuzzer payload is: " + f.next());
                    System.out.println(" The maximum value is: " + f.getMaximumValue());

                    System.out.println(" The current value is: " + f.getCurrectValue());



                }


            } catch (NoSuchFuzzerException e) {

                System.out.println("Could not find fuzzer " + e.getMessage());

            }

        }

    }

### Advanced Fuzzing with the JBroFuzz Library

This section covers more advanced APIs that are available under the
**org.owasp.jbrofuzz.core package**. It should be noted that some of
these classes and their corresponding functionality are not used by the
JBroFuzz program application. Instead, they are made available for
incorporation into other java code that you have perhaps written that
requires more specialized type of fuzzing.

#### Fuzzing Really Long Values with Big Integer

As stated previously, within JBroFuzz a Fuzzer is a java Iterator. This
implies that while fuzzing, we typically keep track of a counter
representing the value that we are currently on. Consider the example of
HelloFuzzer.java, above:

    import org.owasp.jbrofuzz.core.*;

    public class HelloFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     try {
         for(Fuzzer f = fuzzDB.createFuzzer("031-B16-HEX", 4); f.hasNext();) {
           // Get the next payload value...
           System.out.println(" The fuzzer payload is: " + f.next());
         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloFuzzer.java OWASP JBroFuzz Example 1

If we compile this program:

    javac -classpath ".\jbrofuzz\jar\JBroFuzz.jar" HelloFuzzer.java

and run it:

    java -cp ".\jbrofuzz\jar\JBroFuzz.jar;." HelloFuzzer

We are going to see output similar to:

```
 The fuzzer payload is: 0000
 ... (output omitted)
 The fuzzer payload is: fffd
 The fuzzer payload is: fffe
 The fuzzer payload is: ffff
```

Now what if we want a hexadecimal fuzzer of length not 4, but, say, 24.
Let's try compile and run the above program with a length of 24.
Changing the line to:

```
     for(Fuzzer f = fuzzDB.createFuzzer("031-B16-HEX", 24); f.hasNext();) {
```

Running this modified version of HelloFuzzer.java, yields:

    >javac -classpath ".\jbrofuzz\jar\JBroFuzz.jar;." HelloFuzzer.java

    >java -classpath ".\jbrofuzz\jar\JBroFuzz.jar;." HelloFuzzer

    >

Nothing\! What is actually happening is JBroFuzz is figuring out that
the specified length of the Fuzzer we are about to create is far greater
than that of the long java data type. As a result, the Fuzzer is not
even entering the iteration mode that is typically expected with methods
next() and hasNext().

That's all great, but we still want a hexadecimal fuzzer, 24 digits long
going from:

    000000000000000000000000
    ...to...
    ffffffffffffffffffffffff

For this JBroFuzz offers another type of Fuzzer class, that of
FuzzerBigInteger. Let's modify the critical line within the original
HelloFuzzer.java program that we had:

```
     for(FuzzerBigInteger f = fuzzDB.createFuzzerBigInteger("031-B16-HEX", 24); f.hasNext();) {
```

With the entire program becoming:

    import org.owasp.jbrofuzz.core.*;

    public class HelloFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     try {
         for(FuzzerBigInteger f = fuzzDB.createFuzzerBigInteger("031-B16-HEX", 24); f.hasNext();) {
           // Get the next payload value...
           System.out.println(" The fuzzer payload is: " + f.next());
         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloFuzzer.java OWASP JBroFuzz Example 1

Compiling and running this program yields:

```
 The fuzzer payload is: 000000000000000000000000
 The fuzzer payload is: 000000000000000000000001
 ... (output omitted)
 The fuzzer payload is: 00000000000000000001a982
 ... (output omitted)
 The fuzzer payload is: 00000000000000000001a982
 The fuzzer payload is: ffffffffffffffffffffffff
```

There are limitations to this class, as governed by the BigInteger class
itself. Further information can be found at:

    http://java.sun.com/j2se/1.5.0/docs/api/java/math/BigInteger.html

Still, on a virtual windows xp machine with 256Mb of RAM the above code
had no problem running to completion. It took some time though..
Characteristics of the windows machine while this iteration was ongoing:
The CPU was being utilised at 100% and memory usage was constant at 212
Mb. Overall, a clean sheet for FuzzerBigInteger.java.

#### Using the Power Fuzzer API

With web applications, it is often that you find yourself re-using part
of, or the entirety of a fuzzing payload in more than one location, as
part of the GET, POST, or any other type of request you submit.

For this reason, JBroFuzz offers the PowerFuzzer class: A type of
iterator for which you can specify how many copies of the payload you
require in each request.

Let's consider the following trivial scenario. You are in need of all
hexadecimal values, which are 4-digits long (i.e. 0000 to FFFF) and you
are in need of these 5 times for each request.

This scenario is trivial, because typically you can assign the fuzzing
payload (i.e. the value you get back from Fuzzer.next() ) to a String
variable and re-use it as many times as you see fit.

```
 Database fuzzDB = new Database();

 String fuzzerID = "031-B16-HEX";
 int length = 4;
 ....
     for(Fuzzer f = fuzzDB.createFuzzer(fuzzerID, length); f.hasNext();) {
          String payload = f.next();
          ....
     }
```

Using the PowerFuzzer.class, the following HelloPowerFuzzer.java program
can be created:

    import org.owasp.jbrofuzz.core.*;

    public class HelloPowerFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     String fuzzerID = "031-B16-HEX";
     int length = 4;
     int power = 5;

     try {
         for(PowerFuzzer f = fuzzDB.createPowerFuzzer(fuzzerID, length, power); f.hasNext();) {
           // Get the next payload in an array of length[power]
           String [] identicalElements = f.nextPower();

            // f.getPower() == identicalElements.length, always
            System.out.print(" I have " + f.getPower() + " elements: ");

           for(String elem : identicalElements) {

             System.out.print(elem + " ");
           }
           System.out.println("");

         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloPowerFuzzer.java OWASP JBroFuzz Power Fuzzer Example

This program would output the following; no rocket science here:

    ....
     I have 5 elements: 4817 4817 4817 4817 4817
     I have 5 elements: 4818 4818 4818 4818 4818
     I have 5 elements: 4819 4819 4819 4819 4819
     I have 5 elements: 481a 481a 481a 481a 481a
     I have 5 elements: 481b 481b 481b 481b 481b
     I have 5 elements: 481c 481c 481c 481c 481c
     I have 5 elements: 481d 481d 481d 481d 481d
     I have 5 elements: 481e 481e 481e 481e 481e
     I have 5 elements: 481f 481f 481f 481f 481f
     I have 5 elements: 4820 4820 4820 4820 4820
     I have 5 elements: 4821 4821 4821 4821 4821
     I have 5 elements: 4822 4822 4822 4822 4822
     I have 5 elements: 4823 4823 4823 4823 4823
     I have 5 elements: 4824 4824 4824 4824 4824
     I have 5 elements: 4825 4825 4825 4825 4825
     I have 5 elements: 4826 4826 4826 4826 4826
    ....

Now imagine you need to change the number of elements you obtain back
every time. For every second request, you need to obtain back two
identical payloads, for every third request, you need to obtain back
three payloads and for every fourth request, you need to obtain back
four payloads.

The PowerFuzzer class, with the corresponding method **setPower(int)**
allows you to set how many identical elements you obtain back, without
having to worry about the length argument. Below is a class that solves
the above scenario:

    import org.owasp.jbrofuzz.core.*;

    public class HelloPowerFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     String fuzzerID = "031-B16-HEX";
     int length = 4;
     int power = 5;

     try {
         for(PowerFuzzer f = fuzzDB.createPowerFuzzer(fuzzerID, length, power); f.hasNext();) {

           int currentValue = (int) f.getCurrentValue();
           currentValue %= 4;
           switch (currentValue) {
                case 0: f.setPower(1); break;
                case 1: f.setPower(2); break;
                case 2: f.setPower(3); break;
                default: f.setPower(4); break;
           }

           // Get the next payload in an array of length[power]
           String [] identicalElements = f.nextPower();

            // f.getPower() == identicalElements.length, always
            System.out.print(" I have " + f.getPower() + " elements: ");
            // System.out.println(currentValue);

           for(String elem : identicalElements) {

             System.out.print(elem + " ");
           }
           System.out.println("");

         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloPowerFuzzer.java

This class has as output:

```
 ....
 I have 1 elements: 22a8
 I have 2 elements: 22a9 22a9
 I have 3 elements: 22aa 22aa 22aa
 I have 4 elements: 22ab 22ab 22ab 22ab
 I have 1 elements: 22ac
 I have 2 elements: 22ad 22ad
 I have 3 elements: 22ae 22ae 22ae
 I have 4 elements: 22af 22af 22af 22af
 I have 1 elements: 22b0
 I have 2 elements: 22b1 22b1
 I have 3 elements: 22b2 22b2 22b2
 I have 4 elements: 22b3 22b3 22b3 22b3
 I have 1 elements: 22b4
 I have 2 elements: 22b5 22b5
 I have 3 elements: 22b6 22b6 22b6
 I have 4 elements: 22b7 22b7 22b7 22b7
 I have 1 elements: 22b8
 I have 2 elements: 22b9 22b9
 ....
```

Naturally, the algorithm of the number of elements required can vary
based on any number of parameters. The PowerFuzzer class gives you a
quick way to control the number of identical payloads you obtain back,
without having to worry about creating a data type to store them in.

#### Using the Double Fuzzer API

In some cases of fuzzing web applications, a requirement to fuzz two (or
more) locations part of the request being submitted to the web server
becomes apparent.

The DoubleFuzzer class allows you to create a fuzzer based on two
prototype definitions. Similarly to instantiating a Fuzzer through a
prototype and a given length, with a DoubleFuzzer, we pass two prototype
definitions and two lengths. The corresponding method call available
within the **Database** class of org.owasp.jbrofuzz.core is:

    public DoubleFuzzer createDoubleFuzzer(String id1, int length1,
                                    String id2, int length2) throws NoSuchFuzzerException {

Let's cross-breed some fuzzers, see what results we get back during an
iteration.

The first example below, uses two hexadecimal fuzzers of different
lengths, as specified by the variables:

    String fuzzID1 = "031-B16-HEX";
    String fuzzID2 = "031-B16-HEX";

    int length1 = 4;
    int length2 = 2;

As the double fuzzer iteration is taking place, the second fuzzer,
defined by the fuzzID2 & length2 loops, starting from 00 and going all
the way up to FF. An example output is:

```
 I have 2 elements: fefb fb
 I have 2 elements: fefc fc
 I have 2 elements: fefd fd
 I have 2 elements: fefe fe
 I have 2 elements: feff ff
 I have 2 elements: ff00 00
 I have 2 elements: ff01 01
 I have 2 elements: ff02 02
 I have 2 elements: ff03 03
```

The complete code listing of HelloDoubleFuzzer.java is:

    import org.owasp.jbrofuzz.core.*;

    public class HelloDoubleFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     String fuzzID1 = "031-B16-HEX";
     String fuzzID2 = "031-B16-HEX";

     int length1 = 4;
     int length2 = 2;

     try {
         DoubleFuzzer f = fuzzDB.createDoubleFuzzer(fuzzID1, length1, fuzzID2, length2);

         while( f.hasNext() ) {
           // Get the next payload in an array of length[power]
           String [] payloads = f.next();

            // f.getPower() == identicalElements.length, always
            System.out.print(" I have " + f.getPower() + " elements: ");
            // System.out.println(currentValue);

           for(String elem : payloads) {

             System.out.print(elem + " ");
           }
           System.out.println("");

         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloDoubleFuzzer.java

That's simple enough; now let's cross-breed something a bit more exotic:
Imagine a 3-digit octal ID value \[000 - 777\] being submitted inline
with, say, a parameter that we want to test for Cross-Site Scripting
(XSS). Let's adjust the program above with the corresponding fuzzer IDs
of these fuzzers. Remember all the IDs of all the fuzzers can be found
in the fuzzers.jbrf file within JBroFuzz.jar:

    import org.owasp.jbrofuzz.core.*;

    public class HelloDoubleFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     String fuzzID1 = "033-B08-OCT";
     String fuzzID2 = "019-XSS-GEK";

     int length1 = 3;
     int length2 = 1;

     try {
         DoubleFuzzer f = fuzzDB.createDoubleFuzzer(fuzzID1, length1, fuzzID2, length2);

         while( f.hasNext() ) {
           // Get the next payload in an array of length[power]
           String [] payloads = f.next();

            // f.getPower() == identicalElements.length, always
            System.out.print(" I have " + f.getPower() + " elements: ");
            // System.out.println(currentValue);

           for(String elem : payloads) {

             System.out.print(elem + " ");
           }
           System.out.println("");

         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloDoubleFuzzer.java

The output from this program is:

```
 I have 2 elements: 000 (1?(1?{a:1?""[1?"ev\a\l":0](1?"\a\lert":0):0}:0).a:0)[1?"\c\a\l\l":0](content,1?"x\s\s":0)
 I have 2 elements: 001 <STYLE TYPE="text/javascript">alert('XSS');</STYLE>
 I have 2 elements: 002 <SCRIPT SRC=http://ha.ckers.org/xss.js
 I have 2 elements: 003 <A HREF="http://google:ha.ckers.org">XSS</A>
 I have 2 elements: 004 <A HREF="http://ha.ckers.org@google">XSS</A>
 I have 2 elements: 005 <A HREF="//google">XSS</A>
 ....
 ...
 ..
 .
 ..
 ...
 ....
 I have 2 elements: 774 <SCRIPT SRC=http://ha.ckers.org/xss.js
 I have 2 elements: 775 <A HREF="http://google:ha.ckers.org">XSS</A>
 I have 2 elements: 776 <A HREF="http://ha.ckers.org@google">XSS</A>
 I have 2 elements: 777 <A HREF="//google">XSS</A>
```

With the list stopping iterating at the last element of the greatest of
the two fuzzers.

#### Using the Cross Product Fuzzer API

A final case of a special Double Fuzzer is the the Cross Product Fuzzer
of the payloads of two fuzzers. This type of fuzzing is virtually
encountered in username/password login form on the Internet. Let's work
on this by example.

Consider your home network router. You recall changing the default
password to one of the typical password values that you use. Also, you
are not 100% certain about the username for the router either, it is one
of the typical admin, user, administrator, root, yoda type values, but
you cannot recall which one. Needless to say, you don't know what the
username, or password actually is.

So in a mini brute-forcing attack scenario, you have the following list
of usernames, out of which one is valid:

    admin
    administrator
    Administrator
    root
    adminUser

Also you know that the password is one of the following (Top 10
Threadwatch 2007 passwords):

    password
    123456
    qwerty
    abc123
    letmein
    monkey
    myspace1
    password1
    blink182

The set that contains every possible combination of the two sets is the
Cross Product of the list of usernames, times the list of passwords. So
manually, (as most people do while locking themselves out) you would
try, popular combinations of the above, starting with:

    admin password
    admin 123456
    admin qwerty
    ....
    admin blink182
    administrator password
    administrator 123456
    administrator qwerty
    ....
    adminUser password1
    adminUser blink182

Thus the total number of attempts would be (number of usernames) x
(number of passwords). No rocket science here.

JBroFuzz introduces the CrossProductFuzzer class capable of iterating
through the cross product of two fuzzers. Let's put it into code; the
following program provides a list of all 2-digit octal numbers with
every 2-digit binary number. A total of (8 x 8) x (2 x 2) = 256 values.

    import org.owasp.jbrofuzz.core.*;

    public class HelloCrossFuzzer {

     public static void main(String[] args) {

     Database fuzzDB = new Database();

     String fuzzID1 = "033-B08-OCT";
     String fuzzID2 = "034-B02-BIN";

     int length1 = 2;
     int length2 = 2;

     try {
         CrossProductFuzzer f = fuzzDB.createCrossFuzzer(fuzzID1, length1, fuzzID2, length2);

         while( f.hasNext() ) {
           // Get the next payload in an array of length[power]
           String [] payloads = f.next();

            // f.getPower() == identicalElements.length, always
            System.out.print(" I have " + f.getPower() + " elements: ");
            // System.out.println(currentValue);

           for(String elem : payloads) {

             System.out.print(elem + " ");
           }
           System.out.println("");

         }
       } catch (NoSuchFuzzerException e) {
           System.out.println("Could not find fuzzer " + e.getMessage());
     }

     }

    } // HelloCrossFuzzer.java

This program has as output:

```
 I have 2 elements: 00 00
 ...
 ..
 .
 ..
 ...
 I have 2 elements: 74 00
 I have 2 elements: 74 01
 I have 2 elements: 74 10
 I have 2 elements: 74 11
 I have 2 elements: 75 00
 I have 2 elements: 75 01
 I have 2 elements: 75 10
 I have 2 elements: 75 11
 I have 2 elements: 76 00
 I have 2 elements: 76 01
 I have 2 elements: 76 10
 I have 2 elements: 76 11
 I have 2 elements: 77 00
 I have 2 elements: 77 01
 I have 2 elements: 77 10
 I have 2 elements: 77 11
```

You can substitute any list of fuzzer ID to the IDs you use in this
program.

**Remember\!** The total number of payloads must not exceed that of the
the maximum value of the long primitive java data type *Long.MAX_VALUE*
which is 2^63 - 1. If you are in need of more than that payloads, you
would have to use the big integer implementation of the Fuzzer class,
namely: FuzzerBigInteger.java.

## Graphing with JBroFuzz

Once a fuzzing session has completed, JBroFuzz offers the ability to
generate a number of graphs, using various metrics. This section
investigates how to further the graphing functionality available with
the application.

### Customizing the logo on each Graph

As of version 2.0, all image icons within JBroFuzz are located within
the /icons directory of the application. The particular transparent
image file displayed on top right part of the graphs is named:

    /icons/owasp-med.png

This file is a 64 x 64 PNG image file. You can replace it with your own
file, as follows:

    >ls -l JBroFuzz.jar
    -rw-rw-rw-   1 user     group     4033612 Feb 15 12:33 JBroFuzz.jar

    >unzip -oq JBroFuzz.jar
    >cd icons
    >mv owasp-med.png file64x64-file.png
    >cd ..
    >zip -r JBroFuzz.zip *
    >mv JBroFuzz.zip JBroFuzz.jar

This enables you to have your own (company logo) on JBroFuzz graphs.
Further to this, a number of other customization options are available,
by right clicking on each of the graph generated.

## Added Fuzzer Transformations

A fuzzing transform is a simple term used to define the linear
transposition of every set of payloads contained within a fuzzer. Say
you have the following 4 basic XSS payloads:

<code> "\>

<script>

alert('I can do some damage here\!');

</script>


\<IMG SRC=\`javascript:alert("XSS says, 'XSS'")\`\>
<IFRAME SRC="javascript:alert('XSS');"></IFRAME>
</XSS STYLE=xss:expression(alert('XSS'))>
</code>

Note that even though this example only looks at replacive fuzzers,
recursive fuzzers, fuzzing transforms do apply to recursive fuzzers as
well.

Without getting too algebraic, if X is the payload value, a transform is
a linear equation such that for every original payload contained within
a fuzzer, the resulting payload Y is of the form.

From version 2.4, JBroFuzz supports linear fuzzing tranforms for all its
respective fuzzers. These are of the form:

Y = A\*X + B

Where B represents a constant being padded to the original payload X,
with A being the act of multiplication i.e. that of applying a
particular encoding on X. Let's look at an example:

X = "\>

<script>

alert('I can do some damage here\!');

</script>

B = %00%00 A = URL Cp1252

Ergo, ignoring the brackets:

<code> Y = (URL Cp1252)\*("\>

<script>

alert('I can do some damage here\!');

</script>

) + %00%00
Y =
%22%3E%3Cscript%3Ealert%28%27I+can+do+some+damage+here%21%27%29%3B%3C%2Fscript%3E%00%00
</code> Unfortunately, in fuzzing algebraic equivalence relations do not
really hold much ground i.e. generating a payload, by padding a constant
value at the end is not at all the same as padding a constant value at
the beginning and the end for that payload. Thus in:

Y = A\*X + B

We have to break down the constant B in two parts:

Y = B + A\*X + C

This is the fuzzing transform that JBroFuzz uses. Whatsmore, we can
chain this with friends, with benefits:

`Y{1} = B{1} + A{1}*X{1} + C{1}`
`Y{2} = B{2} + A{2}*Y{1} + C{1}`
Ergo,

Y{2} = B{2} + A{2}\*{ B{1} + A{1}\*X{1} + C{1} } + C{1}

But we all hated math at school, think it was the teachers, not the
subject, so let's look at an example:

<code> Y{1} = %00 + {URL Cp1252}{"\>

<script>

alert('I can do some damage here\!');

</script>

} + %00%00
Y{2} = {Base64}Y{1}
</code> Note that B{2} = C{2} = null

And of course we get:

`Y{2} =
JTAwJTIyJTNFJTNDc2NyaXB0JTNFYWxlcnQlMjglMjdJK2Nhbitkbytzb21lK2RhbWFnZStoZXJlJTIxJTI3JTI5JTNCJTNDJTJGc2NyaXB0JTNFJTAwJTAw`

JBroFuzz 2.4 can do this in two rows for every payload grouped in a
fuzzer, within the Added Fuzzer Tranformations Table of the Fuzzing tab.

After fuzzing that triple URL encode, base64 padded, timestamp MD5 into
SHA512 hash? That would be 4 rows within the Added Fuzzer Tranformations
Table.

One fine day, we will write a process to reverse back transforms by
simple cryptanalysis.

[Category:OWASP_JBroFuzz](Category:OWASP_JBroFuzz "wikilink")