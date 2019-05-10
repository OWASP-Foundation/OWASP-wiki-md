## Summary

Web servers usually give developers the ability to add small pieces of
dynamic code inside static HTML pages, without having to deal with
full-fledged server-side or client-side languages. This feature is
incarnated by the **[Server-Side
Includes](Server-Side_Includes_%28SSI%29_Injection "wikilink")**
(**SSI**). In SSI injection testing, we test if it is possible to inject
into the application data that will be interpreted by SSI mechanisms. A
successful exploitation of this vulnerability allows an attacker to
inject code into HTML pages or even perform remote code execution.

Server-Side Includes are directives that the web server parses before
serving the page to the user. They represent an alternative to writing
CGI programs or embedding code using server-side scripting languages,
when there's only need to perform very simple tasks. Common SSI
implementations provide commands to include external files, to set and
print web server CGI environment variables, and to execute external CGI
scripts or system commands.

Putting an SSI directive into a static HTML document is as easy as
writing a piece of code like the following:

```
```

to print out the current time.

```
```

to include the output of a CGI script.

```
```

to include the content of a file or list files in a directory.

```
```

to include the output of a system command.

Then, if the web server's SSI support is enabled, the server will parse
these directives. In the default configuration, usually, most web
servers don't allow the use of the ***exec*** directive to execute
system commands.

As in every bad input validation situation, problems arise when the user
of a web application is allowed to provide data that makes the
application or the web server behave in an unforeseen manner. With
regard to SSI injection, the attacker could provide input that, if
inserted by the application (or maybe directly by the server) into a
dynamically generated page, would be parsed as one or more SSI
directives.

This is a vulnerability very similar to a classical scripting language
injection vulnerability. One mitigation is that the web server needs to
be configured to allow SSI. On the other hand, SSI injection
vulnerabilities are often simpler to exploit, since SSI directives are
easy to understand and, at the same time, quite powerful, e.g., they can
output the content of files and execute system commands.

## How to Test

### Black Box testing

The first thing to do when testing in a Black Box fashion is finding if
the web server actually supports SSI directives. Often, the answer is
yes, as SSI support is quite common. To find out we just need to
discover which kind of web server is running on our target, using
classic information gathering techniques.

Whether we succeed or not in discovering this piece of information, we
could guess if SSI are supported just by looking at the content of the
target web site. If it contains ***.shtml*** files, then SSI are
probably supported, as this extension is used to identify pages
containing these directives. Unfortunately, the use of the ***shtml***
extension is not mandatory, so not having found any ***shtml*** files
doesn't necessarily mean that the target is not prone to SSI injection
attacks.

The next step consists of determining if an SSI injection attack is
actually possible and, if so, what are the input points that we can use
to inject our malicious code.

The testing activity required to do this is exactly the same used to
test for other code injection vulnerabilities. In particular, we need to
find every page where the user is allowed to submit some kind of input,
and verify whether the application is correctly validating the submitted
input. If sanitization is insufficient, we need to test if we can
provide data that is going to be displayed unmodified (for example, in
an error message or forum post). Besides common user-supplied data,
input vectors that should always be considered are HTTP request headers
and cookies content, since they can be easily forged.

Once we have a list of potential injection points, we can check if the
input is correctly validated and then find out where the provided input
is stored. We need to make sure that we can inject characters used in
SSI directives:

    < ! # = / . " - > and [a-zA-Z0-9]

To test if validation is insufficient, we can input, for example, a
string like the following in an input form:

```
```

This is similar to testing for XSS vulnerabilities using

    <script>alert("XSS")</script>

If the application is vulnerable, the directive is injected and it would
be interpreted by the server the next time the page is served, thus
including the content of the Unix standard password file.

The injection can be performed also in HTTP headers, if the web
application is going to use that data to build a dynamically generated
page:

    GET / HTTP/1.0
    Referer: <!--#exec cmd="/bin/ps ax"-->
    User-Agent: <!--#include virtual="/proc/version"-->

### Gray Box testing

If we have access to the application source code, we can quite easily
find out:
\# If SSI directives are used. If they are, then the web server is going
to have SSI support enabled, making SSI injection at least a potential
issue to investigate.
\# Where user input, cookie content and HTTP headers are handled. The
complete list of input vectors is then quickly determined.
\# How the input is handled, what kind of filtering is performed, what
characters the application is not letting through, and how many types of
encoding are taken into account.

Performing these steps is mostly a matter of using grep to find the
right keywords inside the source code (SSI directives, CGI environment
variables, variables assignment involving user input, filtering
functions and so on).

## Tools

  - Web Proxy Burp Suite - <http://portswigger.net>
  - Paros - <http://www.parosproxy.org/index.shtml>
  - [WebScarab](OWASP_WebScarab_Project "wikilink")
  - String searcher: grep - <http://www.gnu.org/software/grep>

## References

**Whitepapers**
\* Apache Tutorial: "Introduction to Server Side Includes" -
<http://httpd.apache.org/docs/1.3/howto/ssi.html>
\* Apache: "Module mod_include" -
<http://httpd.apache.org/docs/1.3/mod/mod_include.html>
\* Apache: "Security Tips for Server Configuration" -
<http://httpd.apache.org/docs/1.3/misc/security_tips.html#ssi>
\* Header Based Exploitation -
<http://www.cgisecurity.net/papers/header-based-exploitation.txt>
\* SSI Injection instead of JavaScript Malware -
<http://jeremiahgrossman.blogspot.com/2006/08/ssi-injection-instead-of-javascript.html>

  - IIS: "Notes on Server-Side Includes (SSI) syntax" -
    <http://blogs.iis.net/robert_mcmurray/archive/2010/12/28/iis-notes-on-server-side-includes-ssi-syntax-kb-203064-revisited.aspx>