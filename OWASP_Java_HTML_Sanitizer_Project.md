# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_html_sanitizer_project">OWASP HTML Sanitizer Project</h2>
<p>The OWASP HTML Sanitizer is a fast and easy to configure HTML Sanitizer written in Java which lets you include HTML authored by third-parties in your web application while protecting against XSS. The existing dependencies are on guava and JSR 305. The other jars are only needed by the test suite. The JSR 305 dependency is a compile-only dependency, only needed for annotations. This code was written with security best practices in mind, has an extensive test suite, and has undergone adversarial security review. A great place to get started using the OWASP Java HTML Sanitizer is here: <a href="https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md">https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md</a>.</p>
<h2 id="benefits">Benefits</h2>
<ul>
<li>Very easy to use. It allows for simple programmatic POSITIVE policy configuration (see below). No XML config.</li>
<li>Actively maintained by Mike Samuel from Google's AppSec team!</li>
<li>Passing 95+% of AntiSamy's unit tests plus many more.</li>
<li>This is code from the Caja project that was donated by Google. It is rather high performance and low memory utilization.</li>
<li>Java 1.5+</li>
<li>Provides 4X the speed of <a href="https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project">AntiSamy</a> sanitization in DOM mode and 2X the speed of AntiSamy in SAX mode.</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>The OWASP HTML Sanitizer is free to use and is dual licensed under the <a href="http://www.apache.org/licenses/LICENSE-2.0">Apache 2 License</a> and the <a href="http://opensource.org/licenses/BSD-3-Clause">New BSD License</a>.</p></td>
<td><h2 id="what_is_this">What is this?</h2>
<p>The OWASP HTML Sanitizer Projects provides Java based HTML sanitization of untrusted HTML!</p>
<h2 id="code_repo">Code Repo</h2>
<p><a href="https://github.com/owasp/java-html-sanitizer">OWASP HTML Sanitizer at GitHub</a></p>
<h2 id="email_list">Email List</h2>
<p>Questions? Please sign up for our <a href="https://groups.google.com/forum/#!forum/owasp-java-html-sanitizer-support">Project Support List</a></p>
<h2 id="project_leaders">Project Leaders</h2>
<p>Author/Project Leader<br />
<a href="https://www.owasp.org/index.php/User:Mike_Samuel">Mike Samuel</a> <a href="mailto:mikesamuel@gmail.com">@</a><br />
<br />
Project Manager<br />
<a href="https://www.owasp.org/index.php/User:Jmanico">Jim Manico</a> <a href="mailto:jim.manico@owasp.org">@</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet" title="wikilink">XSS (Cross Site Scripting) Prevention Cheat Sheet</a></li>
<li><a href="OWASP_JSON_Sanitizer" title="wikilink">OWASP JSON Sanitizer</a></li>
<li><a href="OWASP_Java_Encoder_Project" title="wikilink">OWASP Java Encoder Project</a></li>
<li><a href="OWASP_Dependency_Check" title="wikilink">OWASP Dependency Check</a></li>
<li><a href="https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project">OWASP AntiSamy</a></li>
<li><a href="https://github.com/sourceclear/headlines">Sourceclear Headlines</a></li>
<li><a href="https://github.com/google/keyczar">Google KeyCzar</a></li>
<li><a href="http://shiro.apache.org/">Apache SHIRO</a></li>
</ul>
<h2 id="ohloh">Ohloh</h2>
<ul>
<li><a href="https://www.ohloh.net/p/owasp-java-html-sanitizer">https://www.ohloh.net/p/owasp-java-html-sanitizer</a></li>
</ul></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><a href="https://search.maven.org/#search%7Cga%7C1%7Cowasp%20html%20sanitizer">OWASP HTML Sanitizer at Maven Central</a><br />
</p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[20 Feb 2018] Update 20180219.1 addresses iOS/MacOS "text bomb"</li>
<li>[3 April 2017] <a href="https://groups.google.com/forum/#!topic/owasp-java-html-sanitizer-announce/ijqUZaJjJ4U">HTML5 Support Update</a></li>
<li>[28 June 2016] v20160628.1 Released</li>
<li>[14 Apr 2016] v20160413.1 Released</li>
<li>[1 May 2015] Move to GitHub</li>
<li>[2 July 2014] v239 Released</li>
<li>[3 Mar 2014] v226 Released</li>
<li>[5 Feb 2014] New Wiki</li>
<li>[4 Sept 2013] v209 Released</li>
</ul>
<h2 id="change_log">Change Log</h2>
<p>For recent release notes, please visit the <a href="https://github.com/OWASP/java-html-sanitizer/blob/master/change_log.md">changelog on GitHub</a>.</p></td>
</tr>
</tbody>
</table>

# Creating a HTML Policy

You can view a few basic prepackaged policies for links, tables,
integers, images and more here:
<https://github.com/OWASP/java-html-sanitizer/blob/master/src/main/java/org/owasp/html/Sanitizers.java>.

`PolicyFactory policy = Sanitizers.FORMATTING.and(Sanitizers.LINKS);`
`String safeHTML = policy.sanitize(untrustedHTML);`

There tests illustrate how to configure your own policy here:
<https://github.com/OWASP/java-html-sanitizer/blob/master/src/test/java/org/owasp/html/HtmlPolicyBuilderTest.java>

`PolicyFactory policy = new HtmlPolicyBuilder()`
`   .allowElements("a")`
`   .allowUrlProtocols("https")`
`   .allowAttributes("href").onElements("a")`
`   .requireRelNofollowOnLinks()`
`   .build();`
`String safeHTML = policy.sanitize(untrustedHTML);`

... or you can write custom policies ...

`PolicyFactory policy = new HtmlPolicyBuilder()`
`   .allowElements("p")`
`   .allowElements(`
`       new ElementPolicy() {`
`         public String apply(String elementName, List`<String>` attrs) {`
`           attrs.add("class");`
`           attrs.add("header-" + elementName);`
`           return "div";`
`         }`
`       }, "h1", "h2", "h3", "h4", "h5", "h6"))`
`   .build();`
`String safeHTML = policy.sanitize(untrustedHTML);`

Please note that the elements "a", "font", "img", "input" and "span"
need to be explicitly whitelisted using the \`allowWithoutAttributes()\`
method if you want them to be allowed through the filter when these
elements do not include any attributes.

You can also use the default "ebay" and "slashdot" policies. The
Slashdot policy (defined here
<https://github.com/OWASP/java-html-sanitizer/blob/master/src/main/java/org/owasp/html/examples/SlashdotPolicyExample.java>)
allows the following tags ("a", "p", "div", "i", "b", "em",
"blockquote", "tt", "strong"n "br", "ul", "ol", "li") and only certain
attributes. This policy also allows for the custom slashdot tags,
"quote" and "ecode".

# CSS Sanitization

CSS sanitization is challenging.

We disallow position:sticky and position:fixed so that client code can
use a position:relative;overflow:hidden to contain self-styling
sanitized snippets. Embedders of sanitized content do have to
consistently do that and make sure that contributed content is clearly
demarcated.

Most CSS attacks require a payload to specify selectors which the
sanitizer should not allow. Unproxied images do allow tracking and, by
positioning below the fold, can track whether a user scrolls down.
Embedders do need to use URL rewriting if they allow background styling
and use sensible Referrer-Policy and related headers.

That said, even if care is taken, CSS has a large attack surface, so not
using it puts you in a safer place.

# Inline/Embedded Images

Inline images use the data URI scheme to embed images directly within
web pages. The following describes how to allow inline images in an HTML
Sanitizer policy.

1\) Add the "data" protocol do your whitelist. See:
<https://static.javadoc.io/com.googlecode.owasp-java-html-sanitizer/owasp-java-html-sanitizer/20160628.1/org/owasp/html/HtmlPolicyBuilder.html#allowUrlProtocols>

`.allowUrlProtocols("data")`

2\) You can then allow an attribute with an extra check thus

`.allowAttributes("src")`
`.matching(...)`
`.onElements("img")`

3\) There are a number of things you can do in the matching part such as
allow the following instead of just allowing data.

<data:image/>`...`

4\) Since allowUrlProtocols("data") allows data URLs anywhere data URLs
are allowed, you might want to also add a matcher to any other URL
attributes that reject anything with a colon that does not start with
http: or https: or mailto:

`.allowAttributes("href")`
`.matching(...)`
`.onElements("a")`

# Questions

<b>How was this project tested?</b>
This code was written with security best practices in mind, has an
extensive test suite, and has undergone [adversarial security
review](https://github.com/OWASP/java-html-sanitizer/blob/master/docs/attack_review_ground_rules.md).

<b>How is this project deployed?</b>
This project is best deployed through Maven
<https://github.com/OWASP/java-html-sanitizer/blob/master/docs/getting_started.md>

# Roadmap

  - Maintaining a fully featured HTML sanitizer is a lot of work. We
    intend to continue to handle community questions and bug reports in
    a very timely manner.
  - There are no plans for major new features other than supporting
    incoming requests for advanced sanitization such as additional HTML5
    support.

__NOTOC__ <headertabs/>

[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[Java HTML Sanitizer](Category:OWASP_Project "wikilink")