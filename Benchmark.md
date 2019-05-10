# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![Lab_big.jpg](Lab_big.jpg "Lab_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_benchmark_project">OWASP Benchmark Project</h2>
<p>The OWASP Benchmark for Security Automation (OWASP Benchmark) is a free and open test suite designed to evaluate the speed, coverage, and accuracy of automated software vulnerability detection tools and services (henceforth simply referred to as 'tools'). Without the ability to measure these tools, it is difficult to understand their strengths and weaknesses, and compare them to each other. Each version of the OWASP Benchmark contains thousands of test cases that are fully runnable and exploitable, each of which maps to the appropriate CWE number for that vulnerability.</p>
<p>You can use the OWASP Benchmark with <a href="Source_Code_Analysis_Tools" title="wikilink">Static Application Security Testing (SAST)</a> tools, <a href=":Category:Vulnerability_Scanning_Tools" title="wikilink">Dynamic Application Security Testing (DAST)</a> tools like OWASP <a href="ZAP" title="wikilink">ZAP</a> and Interactive Application Security Testing (IAST) tools. Benchmark is implemented in Java. Future versions may expand to include other languages.</p>
<h2 id="benchmark_project_scoring_philosophy">Benchmark Project Scoring Philosophy</h2>
<p>Security tools (SAST, DAST, and IAST) are amazing when they find a complex vulnerability in your code. But with widespread misunderstanding of the specific vulnerabilities automated tools cover, end users are often left with a false sense of security.</p>
<p>We are on a quest to measure just how good these tools are at discovering and properly diagnosing security problems in applications. We rely on the <a href="http://en.wikipedia.org/wiki/Receiver_operating_characteristic">long history</a> of military and medical evaluation of detection technology as a foundation for our research. Therefore, the test suite tests both real and fake vulnerabilities.</p>
<p>There are four possible test outcomes in the Benchmark:</p>
<ol>
<li>Tool correctly identifies a real vulnerability (True Positive - TP)</li>
<li>Tool fails to identify a real vulnerability (False Negative - FN)</li>
<li>Tool correctly ignores a false alarm (True Negative - TN)</li>
<li>Tool fails to ignore a false alarm (False Positive - FP)</li>
</ol>
<p>We can learn a lot about a tool from these four metrics. Consider a tool that simply flags every line of code as vulnerable. This tool will perfectly identify all vulnerabilities! But it will also have 100% false positives and thus adds no value. Similarly, consider a tool that reports absolutely nothing. This tool will have zero false positives, but will also identify zero real vulnerabilities and is also worthless. You can even imagine a tool that flips a coin to decide whether to report whether each test case contains a vulnerability. The result would be 50% true positives and 50% false positives. We need a way to distinguish valuable security tools from these trivial ones.</p>
<p>If you imagine the line that connects all these points, from 0,0 to 100,100 establishes a line that roughly translates to "random guessing." The ultimate measure of a security tool is how much better it can do than this line. The diagram below shows how we will evaluate security tools against the Benchmark.</p>
<figure>
<img src="Wbe_guide.png" title="File:Wbe guide.png" alt="File:Wbe guide.png" /><figcaption><a href="File:Wbe">File:Wbe</a> guide.png</figcaption>
</figure>
<p>A point plotted on this chart provides a visual indication of how well a tool did considering both the True Positives the tool reported, as well as the False Positives it reported. We also want to compute an individual score for that point in the range 0 - 100, which we call the Benchmark Accuracy Score.</p>
<p>The Benchmark Accuracy Score is essentially a <a href="https://en.wikipedia.org/wiki/Youden%27s_J_statistic">Youden Index</a>, which is a standard way of summarizing the accuracy of a set of tests. Youden's index is one of the oldest measures for diagnostic accuracy. It is also a global measure of a test performance, used for the evaluation of overall discriminative power of a diagnostic procedure and for comparison of this test with other tests. Youden's index is calculated by deducting 1 from the sum of a test’s sensitivity and specificity expressed not as percentage but as a part of a whole number: (sensitivity + specificity) – 1. For a test with poor diagnostic accuracy, Youden's index equals 0, and in a perfect test Youden's index equals 1.</p>
<p><code> So for example, if a tool has a True Positive Rate (TPR) of .98 (i.e., 98%) </code><br />
<code>   and False Positive Rate (FPR) of .05 (i.e., 5%)</code><br />
<code> Sensitivity = TPR (.98)</code><br />
<code> Specificity = 1-FPR (.95)</code><br />
<code> So the Youden Index is (.98+.95) - 1 = .93</code><br />
<code> </code><br />
<code> And this would equate to a Benchmark score of 93 (since we normalize this to the range 0 - 100)</code></p>
<p>On the graph, the Benchmark Score is the length of the line from the point down to the diagonal “guessing” line. Note that a Benchmark score can actually be negative if the point is below the line. This is caused when the False Positive Rate is actually higher than the True Positive Rate.</p>
<h2 id="benchmark_validity">Benchmark Validity</h2>
<p>The Benchmark tests are not exactly like real applications. The tests are derived from coding patterns observed in real applications, but the majority of them are considerably <strong>simpler</strong> than real applications. That is, most real world applications will be considerably harder to successfully analyze than the OWASP Benchmark Test Suite. Although the tests are based on real code, it is possible that some tests may have coding patterns that don't occur frequently in real code.</p>
<p>Remember, we are trying to test the capabilities of the tools and make them explicit, so that users can make informed decisions about what tools to use, how to use them, and what results to expect. This is exactly aligned with the OWASP mission to make application security visible.</p>
<h2 id="generating_benchmark_scores">Generating Benchmark Scores</h2>
<p>Anyone can use this Benchmark to evaluate vulnerability detection tools. The basic steps are:</p>
<ol>
<li>Download the Benchmark from GitHub</li>
<li>Run your tools against the Benchmark</li>
<li>Run the BenchmarkScore tool on the reports from your tools</li>
</ol>
<p>That's it!</p>
<p>Full details on how to do this are at the bottom of the page on the Quick_Start tab.</p>
<p>We encourage both vendors, open source tools, and end users to verify their application security tools against the Benchmark. In order to ensure that the results are fair and useful, we ask that you follow a few simple rules when publishing results. We won't recognize any results that aren't easily reproducible:</p>
<ol>
<li>A description of the default “out-of-the-box” installation, version numbers, etc…</li>
<li>Any and all configuration, tailoring, onboarding, etc… performed to make the tool run</li>
<li>Any and all changes to default security rules, tests, or checks used to achieve the results</li>
<li>Easily reproducible steps to run the tool</li>
</ol>
<h2 id="reporting_format">Reporting Format</h2>
<p>The Benchmark includes tools to interpret raw tool output, compare it to the expected results, and generate summary charts and graphs. We use the following table format in order to capture all the information generated during the evaluation.</p>
<table>
<thead>
<tr class="header">
<th><p>style="background:#DDDDDD"</p></th>
<th><p>Security Category</p></th>
<th><p>TP</p></th>
<th><p>FN</p></th>
<th><p>TN</p></th>
<th><p>FP</p></th>
<th><p>style="background:#DDDDDD"</p></th>
<th><p>Total</p></th>
<th><p>TPR</p></th>
<th><p>FPR</p></th>
<th><p>style="background:#DDDDDD"</p></th>
<th><p>Score</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>style="background:#DDDDDD" valign="top" width="11%"</p></td>
<td><p>General security category for test cases.</p></td>
<td><p>valign="top" width="11%"</p></td>
<td><p><strong>True Positives</strong>: Tests with real vulnerabilities that were correctly reported as vulnerable by the tool.</p></td>
<td><p>valign="top" width="11%"</p></td>
<td><p><strong>False Negative</strong>: Tests with real vulnerabilities that were not correctly reported as vulnerable by the tool.</p></td>
<td><p>valign="top" width="11%"</p></td>
<td><p><strong>True Negative</strong>: Tests with fake vulnerabilities that were correctly not reported as vulnerable by the tool.</p></td>
<td><p>valign="top" width="11%"</p></td>
<td><p><strong>False Positive</strong>:Tests with fake vulnerabilities that were incorrectly reported as vulnerable by the tool.</p></td>
<td><p>style="background:#DDDDDD" valign="top" width="11%"</p></td>
<td><p>Total test cases for this category.</p></td>
</tr>
<tr class="even">
<td><p>style="background:#DDDDDD"</p></td>
<td><p>Command Injection</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>...</p></td>
</tr>
<tr class="odd">
<td><p>style="background:#DDDDDD"</p></td>
<td><p>Etc...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>...</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>...</p></td>
</tr>
<tr class="even">
<td><p>style="background:#DDDDDD"</p></td>
<td></td>
<td><p>Total TP</p></td>
<td><p>Total FN</p></td>
<td><p>Total TN</p></td>
<td><p>Total FP</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>Total TC</p></td>
<td><p>Average TPR</p></td>
<td><p>Average FPR</p></td>
<td><p>style="background:#DDDDDD"</p></td>
<td><p>Average Score</p></td>
</tr>
</tbody>
</table>
<h2 id="code_repo_and_buildrun_instructions">Code Repo and Build/Run Instructions</h2>
<p>See the <strong>Getting Started</strong> and <strong>Getting, Building, and Running the Benchmark</strong> sections on the Quick Start tab.</p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP Benchmark is free to use under the <a href="http://choosealicense.com/licenses/gpl-2.0/">GNU General Public License v2.0</a>.</p>
<h2 id="mailing_list">Mailing List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp-benchmark-project">OWASP Benchmark Mailing List</a></p>
<h2 id="project_leaders">Project Leaders</h2>
<p><a href="https://www.owasp.org/index.php/User:Wichers">Dave Wichers</a> <a href="mailto:dave.wichers@owasp.org">@</a></p>
<h2 id="project_references">Project References</h2>
<ul>
<li><a href="https://www.mir-swamp.org/#packages/public">Software Assurance Marketplace (SWAMP) - set of curated packages to test tools against</a></li>
<li><a href="http://samate.nist.gov/Other_Test_Collections.html">SAMATE List of Test Collections</a></li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="http://samate.nist.gov/SARD/testsuite.php">NSA's Juliet for Java</a></li>
<li><a href="http://sectoolmarket.com/">The Web Application Vulnerability Scanner Evaluation Project (WAVSEP)</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p>All test code and project files can be downloaded from <a href="https://github.com/OWASP/benchmark">OWASP GitHub</a>.</p>
<h2 id="project_intro_video">Project Intro Video</h2>
<figure>
<img src="BenchmarkPodcastTitlePage.jpg" title="BenchmarkPodcastTitlePage.jpg" alt="BenchmarkPodcastTitlePage.jpg" width="200" /><figcaption>BenchmarkPodcastTitlePage.jpg</figcaption>
</figure>
<h2 id="news_and_events">News and Events</h2>
<p>* LOOKING FOR VOLUNTEERS</p></td>
<td><p>- We are looking for individuals and organizations to join and make this a much more community driven project, including additional coleaders to help take this project to the next level. Contributors could work on things like new test cases, additional tool scorecard generators, adding support for languages beyond Java, and a host of other improvements. Please contact <a href="mailto:dave.wichers@owasp.org">me</a> if you are interested in contributing at any level.</p>
<ul>
<li>June 5, 2016 - Benchmark Version 1.2 Released</li>
<li>Sep 24, 2015 - Benchmark introduced to broader OWASP community at <a href="https://appsecusa2015.sched.org/event/3r9k/using-the-owasp-benchmark-to-assess-automated-vulnerability-analysis-tools">AppSec USA</a></li>
<li>Aug 27, 2015 - U.S. Dept. of Homeland Security (DHS) is financially supporting the Benchmark project.</li>
<li>Aug 15, 2015 - Benchmark Version 1.2beta Released with full DAST Support. Checkmarx and ZAP scorecard generators also released.</li>
<li>July 10, 2015 - Benchmark Scorecard generator and open source scorecards released</li>
<li>May 23, 2015 - Benchmark Version 1.1 Released</li>
<li>April 15, 2015 - Benchmark Version 1.0 Released</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><p><a href="http://choosealicense.com/licenses/gpl-2.0/">GNU General Public License v2.0</a></p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Test Cases

Version 1.0 of the Benchmark was published on April 15, 2015 and had
20,983 test cases. On May 23, 2015, version 1.1 of the Benchmark was
released. The 1.1 release improves on the previous version by making
sure that there are both true positives and false positives in every
vulnerability area. Version 1.2 was released on June 5, 2016 (and the
1.2beta August 15, 2015).

Version 1.2 and forward of the Benchmark is a fully executable web
application, which means it is scannable by any kind of vulnerability
detection tool. The 1.2 has been limited to slightly less than 3,000
test cases, to make it easier for DAST tools to scan it (so it doesn't
take so long and they don't run out of memory, or blow up the size of
their database). The 1.2 release covers the same vulnerability areas
that 1.1 covers. We added a few Spring database SQL Injection tests, but
that's it. The bulk of the work was turning each test case into
something that actually runs correctly AND is fully exploitable, and
then generating a UI on top of it that works in order to turn the test
cases into a real running application.

You can still download Benchmark version 1.1 by cloning the release
marked with the GIT tag '1.1'.

The test case areas and quantities for the Benchmark releases are:

| Vulnerability Area                                              | \# of Tests in v1.1 | \# of Tests in v1.2 | CWE Number                                             |
| --------------------------------------------------------------- | ------------------- | ------------------- | ------------------------------------------------------ |
| [Command Injection](Command_Injection "wikilink")               | 2708                | 251                 | [78](https://cwe.mitre.org/data/definitions/78.html)   |
| Weak Cryptography                                               | 1440                | 246                 | [327](https://cwe.mitre.org/data/definitions/327.html) |
| Weak Hashing                                                    | 1421                | 236                 | [328](https://cwe.mitre.org/data/definitions/328.html) |
| [LDAP Injection](LDAP_injection "wikilink")                     | 736                 | 59                  | [90](https://cwe.mitre.org/data/definitions/90.html)   |
| [Path Traversal](Path_Traversal "wikilink")                     | 2630                | 268                 | [22](https://cwe.mitre.org/data/definitions/22.html)   |
| Secure Cookie Flag                                              | 416                 | 67                  | [614](https://cwe.mitre.org/data/definitions/614.html) |
| [SQL Injection](SQL_Injection "wikilink")                       | 3529                | 504                 | [89](https://cwe.mitre.org/data/definitions/89.html)   |
| [Trust Boundary Violation](Trust_Boundary_Violation "wikilink") | 725                 | 126                 | [501](https://cwe.mitre.org/data/definitions/501.html) |
| Weak Randomness                                                 | 3640                | 493                 | [330](https://cwe.mitre.org/data/definitions/330.html) |
| [XPATH Injection](XPATH_Injection "wikilink")                   | 347                 | 35                  | [643](https://cwe.mitre.org/data/definitions/643.html) |
| [XSS](XSS "wikilink") (Cross-Site Scripting)                    | 3449                | 455                 | [79](https://cwe.mitre.org/data/definitions/79.html)   |
| Total Test Cases                                                | 21,041              | 2,740               |                                                        |

Each Benchmark version comes with a spreadsheet that lists every test
case, the vulnerability category, the CWE number, and the expected
result (true finding/false positive). Look for the file:
expectedresults-VERSION\#.csv in the project root directory.

Every test case is:

  - a servlet or JSP (currently they are all servlets, but we plan to
    add JSPs)
  - either a true vulnerability or a false positive for a single issue

The Benchmark is intended to help determine how well analysis tools
correctly analyze a broad array of application and framework behavior,
including:

  - HTTP request and response problems
  - Simple and complex data flow
  - Simple and complex control flow
  - Popular frameworks
  - Inversion of control
  - Reflection
  - Class loading
  - Annotations
  - Popular UI technologies (particularly JavaScript frameworks)

Not all of these are yet tested by the Benchmark but future enhancements
intend to provide more coverage of these issues.

Additional future enhancements could cover:

  - All vulnerability types in the [OWASP Top 10](Top10 "wikilink")
  - Does the tool find flaws in libraries?
  - Does the tool find flaws spanning custom code and libraries?
  - Does tool handle web services? REST, XML, GWT, etc…
  - Does tool work with different app servers? Java platforms?

## Example Test Case

Each test case is a simple Java EE servlet. BenchmarkTest00001 in
version 1.0 of the Benchmark was an LDAP Injection test with the
following metadata in the accompanying BenchmarkTest00001.xml file:

` `<test-metadata>
`   `<category>`ldapi`</category>
`   `<test-number>`00001`</test-number>
`   `<vulnerability>`true`</vulnerability>
`   `<cwe>`90`</cwe>
` `</test-metadata>

BenchmarkTest00001.java in the OWASP Benchmark 1.0 simply reads in all
the cookie values, looks for a cookie named "foo", and uses the value of
this cookie when performing an LDAP query. Here's the code for
BenchmarkTest00001.java:

` package org.owasp.benchmark.testcode;`
` `
` import java.io.IOException;`
` `
` import javax.servlet.ServletException;`
` import javax.servlet.annotation.WebServlet;`
` import javax.servlet.http.HttpServlet;`
` import javax.servlet.http.HttpServletRequest;`
` import javax.servlet.http.HttpServletResponse;`
` `
` @WebServlet("/BenchmarkTest00001")`
` public class BenchmarkTest00001 extends HttpServlet {`
`   `
`   private static final long serialVersionUID = 1L;`
`   `
`   @Override`
`   public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {`
`       doPost(request, response);`
`   }`
` `
`   @Override`
`   public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {`
`       // some code`
` `
`       javax.servlet.http.Cookie[] cookies = request.getCookies();`
`       `
`       String param = null;`
`       boolean foundit = false;`
`       if (cookies != null) {`
`           for (javax.servlet.http.Cookie cookie : cookies) {`
`               if (cookie.getName().equals("foo")) {`
`                   param = cookie.getValue();`
`                   foundit = true;`
`               }`
`           }`
`           if (!foundit) {`
`               // no cookie found in collection`
`               param = "";`
`           }`
`       } else {`
`           // no cookies`
`           param = "";`
`       }`
`       `
`       try {`
`           javax.naming.directory.DirContext dc = org.owasp.benchmark.helpers.Utils.getDirContext();`
`           Object[] filterArgs = {"a","b"};`
`           dc.search("name", param, filterArgs, new javax.naming.directory.SearchControls());`
`       } catch (javax.naming.NamingException e) {`
`           throw new ServletException(e);`
`       }`
`   }`
` }`

# Test Case Details

The following describes situations in the Benchmark that have come up
for debate as to the validity/accuracy of the test cases in these
scenarios.

## Cookies as a Source of Attack for XSS

Benchmark v1.1 and early versions of the 1.2beta included test cases
that used cookies as a source of data that flowed into XSS
vulnerabilities. The Benchmark treated these tests as False Positives
because the Benchmark team figured that you'd have to use an XSS
vulnerability in the first place to set the cookie value, and so it
wasn't fair/reasonable to consider an XSS vulnerability whose data
source was a cookie value as actually exploitable. However, we got
feedback from some tool vendors, like Fortify, Burp, and Arachni, that
they disagreed with this analysis and felt that, in fact, cookies were a
valid source of attack against XSS vulnerabilities. Given that there are
good arguments on both sides of this safe vs. unsafe question, we
decided on Aug 25, 2015 to simply remove those test cases from the
Benchmark. If, in the future, we decide who is right, we may add such
test cases back in.

## Headers as a Source of Attack for XSS

Similarly, the Benchmark team believes that the names of headers aren't
a valid source of XSS attack for the same reason we thought cookie
values aren't a valid source. Because it would require an XSS
vulnerability to be exploited in the first place to set them. In fact,
we feel that this argument is much stronger for header names, than
cookie values. Right now, the Benchmark doesn't include any header names
as sources for XSS test cases, but we plan to add them, and mark them as
false positive in the Benchmark.

We do have header values as sources for some XSS test cases in the
Benchmark and only 'referer' is treated as a valid XSS source (i.e.,
true positives) because other headers are not viable XSS sources. Other
headers are, of course, valid sources for other attack vectors, like SQL
injection or Command Injection.

## False Positive Scenario: Static Values Passed to Unsafe (Weak) Sinks

The Benchmark has MANY test cases where unsafe data flows in from the
browser, but that data is replaced with static content as it goes
through the propagators in the that specific test case. This static
(safe) data then flows to the sink, which may be a weak/unsafe sink,
like, for example, an unsafely constructed SQL statement. The Benchmark
treats those test cases as false positives because there is absolutely
no way for that weakness to be exploited. The NSA Juliet SAST benchmark
treats such test cases exactly the same way, as false positives. We do
recognize that there are weaknesses in those test cases, even though
they aren't exploitable.

Some SAST tool vendors feel it is appropriate to point out those
weaknesses, and that's fine. However, if the tool points those
weaknesses out, and does not distinguish them from truly exploitable
vulnerabilities, then the Benchmark treats those findings as false
positives. If the tool allows a user to differentiate these
non-exploitable weaknesses from exploitable vulnerabilities, then the
Benchmark scorecard generator can use that information to filter out
these extra findings (along with any other similarly marked findings) so
they don't count against that tool when calculating that tool's
Benchmark score. In the real world, its important for analysts to be
able to filter out such findings if they only have time to deal with the
most critical, actually exploitable, vulnerabilities. If a tool doesn't
make it easy for an analyst to distinguish the two situations, then they
are providing a disservice to the analyst.

This issue doesn't affect DAST tools. They only report what appears to
be exploitable to them. So this has no affect on them.

If you are a SAST tool vendor or user, and you believe the Benchmark
scorecard generator is counting such findings against that tool, and
there is a way to tell them apart, please let the project team know so
the scorecard generator can be adjusted to not count those findings
against the tool. The Benchmark project's goal is the generate the most
fair and accurate results it can generate. If such an adjustment is made
to how a scorecard is generated for that tool, we plan to document this
was done for that tool, and explain how others could perform the same
filtering within that tool in order to get the same focused set of
results.

## Dead Code

Some SAST tools point out weaknesses in dead code because they might
eventually end up being used, and serve as bad coding examples (think
cut/paste of code). We think this is fine/appropriate. However, there is
no dead code in the OWASP Benchmark (at least not intentionally). So
dead code should not be causing any tool to report unnecessary false
positives.

# Tool Support/Results

The results for 5 free tools, PMD, FindBugs, FindBugs with the
FindSecBugs plugin, SonarQube and OWASP ZAP are available here against
version 1.2 of the Benchmark:
<https://rawgit.com/OWASP/Benchmark/master/scorecard/OWASP_Benchmark_Home.html>.
We've included multiple versions of FindSecBugs' and ZAP's results so
you can see the improvements they are making finding vulnerabilities in
Benchmark.

We have Benchmark results for all the following tools, but haven't
publicly released the results for any commercial tools. However, we
included a 'Commercial Average' page, which includes a summary of
results for 6 commercial SAST tools along with anonymous versions of
each SAST tool's scorecard.

The Benchmark can generate results for the following tools:

**Free Static Application Security Testing (SAST) Tools:**

  - [PMD](https://pmd.github.io/) (which really has no security rules) -
    .xml results file
  - [Findbugs](http://findbugs.sourceforge.net/) - .xml results file
    (Note: The 'new' Findbugs is now at: <https://spotbugs.github.io/>)
  - FindBugs with the [FindSecurityBugs
    plugin](http://find-sec-bugs.github.io/) - .xml results file
  - [SonarQube](https://www.sonarqube.org/downloads/) - .xml results
    file

Note: We looked into supporting
[Checkstyle](http://checkstyle.sourceforge.net/) but it has no security
rules, just like PMD. The
[fb-contrib](http://fb-contrib.sourceforge.net/) FindBugs plugin doesn't
have any security rules either. We did test [Error
Prone](http://errorprone.info/), and found that it does report some use
of \[<http://errorprone.info/bugpattern/InsecureCipherMode>) insecure
ciphers (CWE-327)\], but that's it.

**Commercial SAST Tools:**

  - [CAST Application Intelligence Platform
    (AIP)](http://www.castsoftware.com/products/application-intelligence-platform)
    - .xml results file
  - [Checkmarx
    CxSAST](https://www.checkmarx.com/products/static-application-security-testing/)
    - .xml results file
  - [Synopsys Static Analysis (Formerly Coverity Code Advisor)
    (On-Demand and stand-alone
    versions)](https://www.synopsys.com/content/dam/synopsys/sig-assets/datasheets/SAST-Coverity-datasheet.pdf)
    - .json results file (You can scan Benchmark w/Coverity for free.
    See: <https://scan.coverity.com/>)
  - [Micro Focus (Formally HPE) Fortify (On-Demand and stand-alone
    versions)](https://software.microfocus.com/en-us/products/static-code-analysis-sast/overview)
    - .fpr results file
  - [IBM AppScan Source (Standalone and
    Cloud)](https://www.ibm.com/us-en/marketplace/ibm-appscan-source) -
    .ozasmt or .xml results file
  - [Julia
    Analyzer](https://juliasoft.com/solutions/julia-for-security/) -
    .xml results file
  - [Parasoft Jtest](https://www.parasoft.com/products/jtest/) - .xml
    results file
  - [ShiftLeft SAST](https://www.shiftleft.io/product/) - .sl results
    file (Benchmark specific format. Ask vendor how to generate this)
  - [SourceMeter](https://www.sourcemeter.com/features/) - .txt results
    file of ALL results from VulnerabilityHunter
  - [Thunderscan SAST](https://www.defensecode.com/thunderscan.php) -
    .xml results file
  - [Veracode
    SAST](http://www.veracode.com/products/binary-static-analysis-sast)
    - .xml results file
  - [XANITIZER](https://www.rigs-it.com/xanitizer/) - xml results file
    ([Their white paper on how to setup Xanitizer to scan
    Benchmark.](https://www.rigs-it.com/wp-content/uploads/2018/03/howtosetupxanitizerforowaspbenchmarkproject.pdf))
    (Free trial available)

We are looking for results for other commercial static analysis tools
like: [Grammatech CodeSonar](http://www.grammatech.com/codesonar),
[Klocwork](http://www.klocwork.com/products-services/klocwork), etc. If
you have a license for any static analysis tool not already listed above
and can run it on the Benchmark and send us the results file that would
be very helpful.

The free SAST tools come bundled with the Benchmark so you can run them
yourselves. If you have a license for any commercial SAST tool, you can
also run them against the Benchmark. Just put your results files in the
/results folder of the project, and then run the BenchmarkScore script
for your platform (.sh / .bat) and it will generate a scorecard in the
/scorecard directory for all the tools you have results for that are
currently supported.

**Free Dynamic Application Security Testing (DAST) Tools:**

Note: While we support scorecard generators for these Free and
Commercial DAST tools, we haven't been able to get a full/clean run
against the Benchmark from most of these tools. As such, some of these
scorecard generators might still need some work to properly reflect
their results. If you notice any problems, let us know.

  - [Arachni](http://www.arachni-scanner.com/) - .xml results file
      - To generate .xml, run: ./bin/arachni_reporter
        "Your_AFR_Results_Filename.afr"
        --reporter=xml:outfile=Benchmark1.2-Arachni.xml
  - [OWASP ZAP](https://www.owasp.org/index.php/ZAP) - .xml results
    file. To generate a complete ZAP XML results file so you can
    generate a valid scorecard, make sure you:
      - Tools \> Options \> Alerts - And set the Max alert instances to
        like 500.
      - Then: Report \> Generate XML Report...

**Commercial DAST Tools:**

  - [Acunetix Web Vulnerability Scanner
    (WVS)](https://www.acunetix.com/vulnerability-scanner/) - .xml
    results file (Generated using [command line interface (see
    Chapter 10.)](https://www.acunetix.com/resources/wvs7manual.pdf)
    /ExportXML switch)
  - [Burp Pro](https://portswigger.net/burp/) - .xml results file
      - You must use Burp Pro v1.6.30+ to scan the Benchmark due to a
        limitation fixed in v1.6.30.
  - [Micro Focus (Formally HPE)
    WebInspect](https://software.microfocus.com/en-us/products/webinspect-dynamic-analysis-dast/overview)
    - .xml results file
  - [This was IBM AppScan (but I believe IBM sold this product off. To
    whom?](http://www-03.ibm.com/software/products/en/appscan) - .xml
    results file
  - [Netsparker](https://www.netsparker.com/web-vulnerability-scanner/)
    - .xml results file
  - [Rapid7 AppSpider](https://www.rapid7.com/products/appspider/) -
    .xml results file

<!-- end list -->

  - Qualys - We ran Qualys against v1.2 of the Benchmark and it found
    none of the vulnerabilities we test for as far as we could tell. So
    we haven't implemented a scorecard generator for it. If you get
    results where you think it does find some real issues, send us the
    results file and, if confirmed, we'll produce a scorecard generator
    for it.

If you have access to other DAST Tools, PLEASE RUN THEM FOR US against
the Benchmark, and send us the results file so we can build a scorecard
generator for that tool.

**Commercial Interactive Application Security Testing (IAST) Tools:**

  - [Contrast
    Assess](https://www.contrastsecurity.com/interactive-application-security-testing-iast)
    - .zip results file (You can scan Benchmark w/Contrast for free.
    See: <https://www.contrastsecurity.com/contrast-community-edition>)
  - [Hdiv Detection
    (IAST)](https://hdivsecurity.com/interactive-application-security-testing-iast)
    - .hlg results file
  - [Seeker
    IAST](https://www.synopsys.com/software-integrity/security-testing/interactive-application-security-testing.html)
    - .csv results file

**Commercial Hybrid Analysis Application Security Testing Tools:**

  - [Fusion Lite Insight](http://www.iappsecure.com/products.html) -
    .xml results file

**WARNING: If you generate results for a commercial tool, be careful who
you distribute it to. Each tool has its own license defining when any
results it produces can be released/made public. It may be against the
terms of a commercial tool's license to publicly release that tool's
score against the OWASP Benchmark. The OWASP Benchmark project takes no
responsibility if someone else releases such results.**

The project has automated test harnesses for these vulnerability
detection tools, so we can repeatably run the tools against each version
of the Benchmark and automatically produce scorecards in our desired
format.

We want to test as many tools as possible against the Benchmark. If you
are:

  - A tool vendor and want to participate in the project
  - Someone who wants to help score a free tool against the project
  - Someone who has a license to a commercial tool and the terms of the
    license allow you to publish tool results, and you want to
    participate

please let [me](mailto:dave.wichers@owasp.org) know\!

# Quick Start

## What is in the Benchmark?

The Benchmark is a Java Maven project. Its primary component is
thousands of test cases (e.g., BenchmarkTest00001.java) , each of which
is a single Java servlet that contains a single vulnerability (either a
true positive or false positive). The vulnerabilities span about a dozen
different types currently and are expected to expand significantly in
the future.

An expectedresults.csv is published with each version of the Benchmark
(e.g., expectedresults-1.1.csv) and it specifically lists the expected
results for each test case. Here’s what the first two rows in this file
looks like for version 1.1 of the Benchmark:

`# test name        category    real vulnerability  CWE Benchmark version: 1.1  2015-05-22`
`BenchmarkTest00001 crypto      TRUE            327`

This simply means that the first test case is a crypto test case (use of
weak cryptographic algorithms), this is a real vulnerability (as opposed
to a false positive), and this issue maps to CWE 327. It also indicates
this expected results file is for Benchmark version 1.1 (produced May
22, 2015). There is a row in this file for each of the tens of thousands
of test cases in the Benchmark. Each time a new version of the Benchmark
is published, a new corresponding results file is generated and each
test case can be completely different from one version to the next.

The Benchmark also comes with a bunch of different utilities, commands,
and prepackaged open source security analysis tools, all of which can be
executed through Maven goals, including:

  - Open source vulnerability detection tools to be run against the
    Benchmark
  - A scorecard generator, which computes a scorecard for each of the
    tools you have results files for.

## What Can You Do With the Benchmark?

  - Compile all the software in the Benchmark project (e.g., mvn
    compile)
  - Run a static vulnerability analysis tool (SAST) against the
    Benchmark test case code

<!-- end list -->

  - Scan a running version of the Benchmark with a dynamic application
    security testing tool (DAST)
      - Instructions on how to run it are provided below

<!-- end list -->

  - Generate scorecards for each of the tools you have results files for
      - See the Tool Support/Results page for the list of tools the
        Benchmark supports generating scorecards for

## Getting Started

Before downloading or using the Benchmark make sure you have the
following installed and configured properly:

`GIT: `<http://git-scm.com/>` or `<https://github.com/>
`Maven: `<https://maven.apache.org/>`  (Version: 3.2.3 or newer works.)`
`Java: `<http://www.oracle.com/technetwork/java/javase/downloads/index.html>` (Java 7 or 8) (64-bit)`

## Getting, Building, and Running the Benchmark

To download and build everything:

`$ git clone `<https://github.com/OWASP/benchmark>` `
`$ cd benchmark`
`$ mvn compile   (This compiles it)`
`$ runBenchmark.sh/.bat - This compiles and runs it.`

Then navigate to: <https://localhost:8443/benchmark/> to go to its home
page. It uses a self signed SSL certificate, so you'll get a security
warning when you hit the home page.

Note: We have set the Benchmark app to use up to 6 Gig of RAM, which it
may need when it is fully scanned by a DAST scanner. The DAST tool
probably also requires 3+ Gig of RAM. As such, we recommend having a 16
Gig machine if you are going to try to run a full DAST scan. And at
least 4 or ideally 8 Gig if you are going to play around with the
running Benchmark app.

## Using a VM instead

We have several preconstructed VMs or instructions on how to build one
that you can use instead:

  - Docker: A Dockerfile is checked into the project
    [here](https://github.com/OWASP/Benchmark/blob/master/VMs/Dockerfile).
    This Docker file should automatically produce a Docker VM with the
    latest Benchmark project files. After you have Docker installed, cd
    to /VMs then run:

`./buildDockerImage.sh --> This builds the Docker Benchmark VM (This will take a WHILE)`
`docker images  --> You should see the new benchmark:latest image in the list provided`
`# The Benchmark Docker Image only has to be created once. `

`To run the Benchmark in your Docker VM, just run:`
`  ./runDockerImage.sh  --> This pulls in any updates to Benchmark since the Image was built, builds everything, and starts a remotely accessible Benchmark web app.`
`If successful, you should see this at the end:`
`  [INFO] [talledLocalContainer] Tomcat 8.x started on port [8443]`
`  [INFO] Press Ctrl-C to stop the container...`
`Then simply navigate to: `<https://localhost:8443/benchmark>` from the machine you are running Docker`

`Or if you want to access from a different machine:`
` docker-machine ls (in a different terminal) --> To get IP Docker VM is exporting (e.g., tcp://192.168.99.100:2376)`
` Navigate to: `<https://192.168.99.100:8443/benchmark>` in your browser (using the above IP as an example)`

  - Amazon Web Services (AWS) - Here's how you set up the Benchmark on
    an AWS VM:

`sudo yum install git`
`sudo yum install maven`
`sudo yum install mvn`
`sudo wget `<http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo>` -O /etc/yum.repos.d/epel-apache-maven.repo`
`sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo`
`sudo yum install -y apache-maven`
`git clone `<https://github.com/OWASP/benchmark>
`cd benchmark`
`chmod 755 *.sh`
`./runBenchmark.sh -- to run it locally on the VM.`
`./runRemoteAccessibleBenchmark.sh -- to run it so it can be accessed outside the VM (on port 8443).`

## Running Free Static Analysis Tools Against the Benchmark

There are scripts for running each of the free SAST vulnerability
detection tools included with the Benchmark against the Benchmark test
cases. On Linux, you might have to make them executable (e.g., chmod 755
\*.sh) before you can run them.

Generating Test Results for PMD:

`$ ./scripts/runPMD.sh (Linux) or .\scripts\runPMD.bat (Windows)`

Generating Test Results for FindBugs:

`$ ./scripts/runFindBugs.sh (Linux) or .\scripts\runFindBugs.bat (Windows)`

Generating Test Results for FindBugs with the FindSecBugs plugin:

`$ ./scripts/runFindSecBugs.sh (Linux) or .\scripts\runFindSecBugs.bat (Windows)`

In each case, the script will generate a results file and put it in the
/results directory. For example:

`Benchmark_1.2-findbugs-v3.0.1-1026.xml`

This results file name is carefully constructed to mean the following:
It's a results file against the OWASP Benchmark version 1.2, FindBugs
was the analysis tool, it was version 3.0.1 of FindBugs, and it took
1026 seconds to run the analysis.

NOTE: If you create a results file yourself, by running a commercial
tool for example, you can add the version \# and the compute time to the
filename just like this and the Benchmark Scorecard generator will pick
this information up and include it in the generated scorecard. If you
don't, depending on what metadata is included in the tool results, the
Scorecard generator might do this automatically anyway.

## Generating Scorecards

The scorecard generation application BenchmarkScore is included with the
Benchmark. It parses the output files generated by any of the supported
security tools run against the Benchmark and compares them against the
expected results, and produces a set of web pages that detail the
accuracy and speed of the tools involved. For the list of currently
supported tools, check out the: Tools Support/Results tab. If you are
using a tool that is not yet supported, simply send us a results file
from that tool and we'll write a parser for that tool and add it to the
supported tools list.

The following command will compute a Benchmark scorecard for all the
results files in the **/results** directory. The generated scorecard is
put into the **/scorecard** directory.

`createScorecard.sh (Linux) or createScorecard.bat (Windows)`

An example of a real scorecard for some open source tools is provided at
the top of the Tool Support/Results tab so you can see what one looks
like.

We recommend including the Benchmark version number in any results file
name, in order to help prevent mismatches between the expected results
and the actual results files. A tool will not score well against the
wrong expected results.

### Customizing Your Scorecard Generation

The createScorecard scripts are very simple. They only have one line.
Here's what the 1.2 version looks like:

`mvn validate -Pbenchmarkscore -Dexec.args="expectedresults-1.2.csv results"`

This Maven command simply says to run the BenchmarkScore application,
passing in two parameters. The 1st is the Benchmark expected results
file to compare the tool results against. And the 2nd is the name of the
directory that contains all the results from tools run against that
version of the Benchmark. If you have tool results older than the
current version of the Benchmark, like 1.1 results for example, then you
would do something like this instead:

`mvn validate -Pbenchmarkscore -Dexec.args="expectedresults-1.1.csv 1.1_results"`

To keep things organized, we actually put the expected results file
inside the same results folder for that version of the Benchmark, so our
command looks like this:

`mvn validate -Pbenchmarkscore -Dexec.args="1.1_results/expectedresults-1.1.csv 1.1_results"`

In all cases, the generated scorecard is put in the /scorecard folder.

**WARNING: If you generate results for a commercial tool, be careful who
you distribute it to. Each tool has its own license defining when any
results it produces can be released/made public. It is likely to be
against the terms of a commercial tool's license to publicly release
that tool's score against the OWASP Benchmark. The OWASP Benchmark
project takes no responsibility if someone else releases such results.**
It is for just this reason that the Benchmark project isn't releasing
such results itself.

# Tool Scanning Tips

People frequently have difficulty scanning the Benchmark with various
tools due to many reasons, including size of the Benchmark app and its
codebase, and complexity of the tools used. Here is some guidance for
some of the tools we have used to scan the Benchmark. If you've learned
any tricks on how to get better or easier results for a particular tool
against the Benchmark, let us know or update this page directly.

## Generic Tips

Because of the size of the Benchmark, you may need to give your tool
more memory before it starts the scan. If its a Java based tool, you may
want to pass more memory to it like this:

`-Xmx4G (This gives the Java application 4 Gig of memory)`

## SAST Tools

### Checkmarx

The Checkmarx SAST Tool (CxSAST) is ready to scan the OWASP Benchmark
out-of-the-box. Please notice that the OWASP Benchmark “hides” some
vulnerabilities in dead code areas, for example:

``` java
if (0>1)
{
  //vulnerable code
}
```

By default, CxSAST will find these vulnerabilities since Checkmarx
believes that including dead code in the scan results is a SAST best
practice.

Checkmarx's experience shows that security experts expect to find these
types of code vulnerabilities, and demand that their developers fix
them. However, OWASP Benchmark considers the flagging of these
vulnerabilities as False Positives, as a result lowering Checkmarx's
overall score.

Therefore, in order to receive an OWASP score untainted by dead code,
re-configure CxSAST as follows:

1.  Open the CxAudit client for editing Java queries.
2.  Override the "Find_Dead_Code" query.
3.  Add the commented text of the original query to the new override
    query.
4.  Save the queries.

### FindBugs

We include this free tool in the Benchmark and its all dialed in. Simply
run the script: ./script/runFindBugs.(sh or bat). If you want to run a
different version of FindBugs, just change its version number in the
Benchmark pom.xml file.

### FindBugs with FindSecBugs

[FindSecurityBugs](http://h3xstream.github.io/find-sec-bugs/) is a great
plugin for FindBugs that significantly increases the ability for
FindBugs to find security issues. We include this free tool in the
Benchmark and its all dialed in. Simply run the script:
./script/runFindSecBugs.(sh or bat). If you want to run a different
version of FindSecBugs, just change the version number of the
findsecbugs-plugin artifact in the Benchmark pom.xml file.

### Micro Focus (Formally HP) Fortify

If you are using the Audit Workbench, you can give it more memory and
make sure you invoke it in 64-bit mode by doing this:

` set AWB_VM_OPTS="-Xmx2G -XX:MaxPermSize=256m"`
` export AWB_VM_OPTS="-Xmx2G -XX:MaxPermSize=256m"`
` auditworkbench -64`

We found it was easier to use the Maven support in Fortify to scan the
Benchmark and to do it in 2 phases, translate, and then scan. We did
something like this:

` Translate Phase:`
` export JAVA_HOME=$(/usr/libexec/java_home)`
` export PATH=$PATH:/Applications/HP_Fortify/HP_Fortify_SCA_and_Apps_17.10/bin`
` export SCA_VM_OPTS="-Xmx2G -version 1.7"`
` mvn sca:clean`
` mvn sca:translate`

` Scan Phase:`
` export JAVA_HOME=$(/usr/libexec/java_home)`
` export PATH=$PATH:/Applications/HP_Fortify/HP_Fortify_SCA_and_Apps_4.10/bin`
` export SCA_VM_OPTS="-Xmx10G -version 1.7"`
` mvn sca:scan`

### PMD

We include this free tool in the Benchmark and its all dialed in. Simply
run the script: ./script/runPMD.(sh or bat). If you want to run a
different version of PMD, just change its version number in the
Benchmark pom.xml file. (NOTE: PMD doesn't find any security issues. We
include it because its interesting to know that it doesn't.)

### SonarQube

We include this free tool in the Benchmark and its mostly dialed in. But
its a bit tricky because SonarQube requires two parts. There is a stand
alone scanner for Java. And then there is a web application that accepts
the results, and in turn can then produce the results file required by
the Benchmark scorecard generator for SonarQube. Running the script
runSonarQube.(sh or bat) will generate the results, but if the SonarQube
Web Application isn't running where the runSonarQube script expects it
to be, then the script will fail.

If you want to run a different version of SonarQube, just change its
version number in the Benchmark pom.xml file.

### Xanitizer

The vendor has written their own guide to [How to Set Up Xanitizer for
OWASP
Benchmark](http://www.rigs-it.net/opendownloads/whitepapers/HowToSetUpXanitizerForOWASPBenchmarkProject.pdf).

## DAST Tools

### Burp Pro

You must use Burp Pro v1.6.29 or greater to scan the Benchmark due to a
previous limitation in Burp Pro related to ensuring the path attribute
for cookies was honored. This issue was fixed in the v1.6.29 release.

To scan, first spider the entire Benchmark, and then select the
/Benchmark URL and actively scan that branch. You can skip all the .html
pages and any other pages that Burp says have no parameters.

NOTE: We have been unable to simply run Burp Pro against the entire
Benchmark in one shot. In our experience, it eventually freezes/stops
scanning. We've had to run it against each test area one at a time. If
you figure out how to get Burp Pro to scan all of Benchmark in one shot,
let us know how you did it\!

### OWASP ZAP

ZAP may require additional memory to be able to scan the Benchmark. To
configure the amount of memory:

  - Tools --\> Options --\> JVM: Recommend setting to: -Xmx2048m (or
    larger). (Then restart ZAP).

To run ZAP against Benchmark:

1.  Because Benchmark uses Cookies and Headers as sources of attack for
    many test cases: Tools --\> Options --\> Active Scan Input Vectors:
    Then check the HTTP Headers, All Requests, and Cookie Data
    checkboxes and hit OK
2.  Click on Show All Tabs button (if spider tab isn't visible)
3.  Go to Spider tab (the black spider) and click on New Scan button
4.  Enter: <https://localhost:8443/benchmark/> into the 'Starting Point'
    box and hit 'Start Scan'
      - Do this again. For some reason it takes 2 passes with the Spider
        before it stops finding more Benchmark endpoints.
5.  When Spider completes, click on 'benchmark' folder in Site Map,
    right click and select: 'Attack --\> Active Scan'
      - It will take several hours, like 3+ to complete (it's actually
        likely to simply freeze before completing the scan - see NOTE:
        below)

For faster active scan you can

  - Disable the ZAP DB log (in ZAP 2.5.0+):
      - Disable it via Options / Database / Recover Log
      - Set it on the command line using "-config
        database.recoverylog=false"
  - Disable unnecessary plugins / Technologies: When you launch the
    Active Scan
      - On the Policy tab, disable all plugins except: XSS (Reflected),
        Path Traversal, SQLi, OS Command Injection
      - Go the Technology Tab, disable everything and only enable:
        MySQL, YOUR_OS, Tomcat
      - Note: This 2nd performance improvement step is a bit like
        cheating as you wouldn't do this for a normal site scan. You'd
        want to leave all this on in case these other
        plugins/technologies are helpful in finding more issues. So a
        fair performance comparison of ZAP to other tools would leave
        all this on.

To generate the ZAP XML results file so you can generate its scorecard:

  - Tools \> Options \> Alerts - And set the Max alert instances to like
    500.
  - Then: Report \> Generate XML Report...

NOTE: Similar to Burp, we can't simply run ZAP against the entire
Benchmark in one shot. In our experience, it eventually freezes/stops
scanning. We've had to run it against each test area one at a time. If
you figure out how to get ZAP to scan all of Benchmark in one shot, let
us know how you did it\!

Things we tried that didn't improve the score:

  - AJAX Spider - the traditional spider appears to find all (or 99%) of
    the test cases so the AJAX Spider does not appear to be needed
    against Benchmark v1.2
  - XSS (Persistent) - There are 3 of these plugins that run by default.
    There aren't any stored XSS in Benchmark, so you can disable these
    plugins for a faster scan.
  - DOM XSS Plugin - This is an optional plugin that didn't seem to find
    any additional XSS issues. There aren't an DOM specific XSS issues
    in Benchmark v1.2, so not surprising.

## IAST Tools

Interactive Application Security Testing (IAST) tools work differently
than scanners. IAST tools monitor an application as it runs to identify
application vulnerabilities using context from inside the running
application. Typically these tools run continuously, immediately
notifying users of vulnerabilities, but you can also get a full report
of an entire application. To do this, we simply run the Benchmark
application with an IAST agent and use a crawler to hit all the pages.

### Contrast Assess

To use Contrast Assess, we simply add the Java agent to the Benchmark
environment and run the BenchmarkCrawler. The entire process should only
take a few minutes. We provided a few scripts, which simply add the
-javaagent:contrast.jar flag to the Benchmark launch configuration. We
have tested on MacOS, Ubuntu, and Windows. Be sure your VM has at least
4M of memory.

  - Ensure your environment has Java, Maven, and git installed, then
    build the Benchmark project

`  `**`$``   ``git``   ``clone``
 `<https://github.com/OWASP/Benchmark.git>**
`  `**`$``   ``cd``   ``Benchmark`**
`  `**`$``   ``mvn``   ``compile`**

  - Download a licensed copy of the Contrast Assess Java Agent
    (contrast.jar) from your Contrast TeamServer account and put it in
    the /Benchmark/tools/Contrast directory.

`  `**`$``   ``cp``   ``~/Downloads/contrast.jar``   ``tools/Contrast`**

  - In Terminal 1, launch the Benchmark application and wait until it
    starts

`  '''$ cd tools/Contrast  `
`  `**`$``   ``./runBenchmark_wContrast.sh`**` (.bat on Windows)`
`  '''[INFO] Scanning for projects...`
`  '''[INFO]                                                                         `
`  '''[INFO] ------------------------------------------------------------------------`
`  '''[INFO] Building OWASP Benchmark Project 1.2`
`  '''[INFO] ------------------------------------------------------------------------`
`  '''[INFO] `
`  '''...`
`  `**`[INFO]``   ``[talledLocalContainer]``   ``Tomcat``   ``8.x``
 ``started``   ``on``   ``port``   ``[8443]`**
`  `**`[INFO]``   ``Press``   ``Ctrl-C``   ``to``   ``stop``   ``the``
 ``container...`**

  - In Terminal 2, launch the crawler and wait a minute or two for the
    crawl to complete.

`  `**`$``   ``./runCrawler.sh`**` (.bat on Windows)`

  - A Contrast report has been generated in
    /Benchmark/tools/Contrast/working/contrast.log. This report will be
    automatically copied (and renamed with version number) to
    /Benchmark/results directory.

`  `**`$``   ``more``   ``tools/Contrast/working/contrast.log`**
`  '''2016-04-22 12:29:29,716 [main b] INFO - Contrast Runtime Engine`
`  '''2016-04-22 12:29:29,717 [main b] INFO - Copyright (C) 2012`
`  '''2016-04-22 12:29:29,717 [main b] INFO - Pat. 8,458,789 B2`
`  '''2016-04-22 12:29:29,717 [main b] INFO - Contrast Security, Inc.`
`  '''2016-04-22 12:29:29,717 [main b] INFO - All Rights Reserved`
`  '''2016-04-22 12:29:29,717 [main b] INFO - `<https://www.contrastsecurity.com/>
`  `**`...`**

  - Press Ctrl-C to stop the Benchmark in Terminal 1. Note: on Windows,
    select "N" when asked Terminate batch job (Y/N))

`  `**`[INFO]``   ``[talledLocalContainer]``   ``Tomcat``   ``8.x``
 ``is``   ``stopped`**
`  `**`Copying``   ``Contrast``   ``report``   ``to``   ``results``
 ``directory`**

  - In Terminal 2, generate scorecards in /Benchmark/scorecard

`  `**`$``   ``./createScorecards.sh`**` (.bat on Windows)`
`  '''Analyzing results from Benchmark_1.2-Contrast.log`
`  '''Actual results file generated: /Users/owasp/Projects/Benchmark/scorecard/Benchmark_v1.2_Scorecard_for_Contrast.csv`
`  '''Report written to: /Users/owasp/Projects/Benchmark/scorecard/Benchmark_v1.2_Scorecard_for_Contrast.html`

  - Open the Benchmark Scorecard in your browser

`  `**`/Users/owasp/Projects/Benchmark/scorecard/Benchmark_v1.2_Scorecard_for_Contrast.html`**

### Hdiv Detection

Hdiv has written their own instructions on how to run the detection
component of their product on the Benchmark here:
<https://hdivsecurity.com/docs/features/benchmark/#how-to-run-hdiv-in-owasp-benchmark-project>.
You'll see that these instructions involve using the same crawler used
to exercise all the test cases in the Benchmark, just like Contrast
above.

# RoadMap

Benchmark v1.0 - Released April 15, 2015 - This initial release included
over 20,000 test cases in 11 different vulnerability categories. As this
initial version was not a runnable application, it was only suitable for
assessing static analysis tools (SAST).

Benchmark v1.1 - Released May 23, 2015 - This update fixed some
inaccurate test cases, and made sure that every vulnerability area
included both True Positives and False Positives.

Benchmark Scorecard Generator - Released July 10, 2015 - The ability to
automatically and repeatably produce a scorecard of how well tools do
against the Benchmark was released for most of the SAST tools supported
by the Benchmark. Scorecards present graphical as well as statistical
data on how well a tool does against the Benchmark down to the level of
detail of how exactly it did against each individual test in the
Benchmark. [Here are the latest public
scorecards](https://rawgit.com/OWASP/Benchmark/master/scorecard/OWASP_Benchmark_Home.html).
Support for producing scorecards for additional tools is being added all
the time and the current full set is documented on the **Tool
Support/Results** and **Quick Start** tabs of this wiki.

Benchmark v1.2beta - Released Aug 15, 2015 - The 1st release of a fully
runnable version of the Benchmark to support assessing all types of
vulnerability detection and prevention technologies, including DAST,
IAST, RASP, WAFs, etc. This involved creating a user interface for every
test case, and enhancing each test case to make sure its actually
exploitable, not just uses something that is theoretically weak. This
release is under 3,000 test cases to make it practical to scan the
entire Benchmark with a DAST tool in a reasonable amount of time, with
commodity hardware specs.

Benchmark 1.2 - Released June 5, 2016 - Based on feedback from a number
of DAST tool developers, and other vendors as well, we made the
Benchmark more realistic in a number of ways to facilitate external DAST
scanning, and also made the Benchmark more resilient against attack so
it could properly survive various DAST vulnerability detection and
exploit verification techniques.

Plans for Benchmark 1.3:

While we don't have hard and fast rules of exactly what we are going to
do next, enhancements in the following areas are planned for the next
release:

  - Add new vulnerability categories (e.g., XXE, Hibernate Injection)
  - Add support for popular server side Java frameworks (e.g., Spring)
  - Add web services test cases

We are also starting to work on the ability to score WAFs/RASPs and
other defensive technology against Benchmark.

# FAQ

## 1\. How are the scores computed for the Benchmark?

Each test case has a single vulnerability of a specific type. Its either
a real vulnerability (True Positive) or not (a False Positive). We
document all the test cases for each version of the Benchmark in the
expectedresults-VERSION\#.csv file (e.g., expectedresults-1.1.csv). This
file lists the test case name, the CWE type of the vulnerability, and
whether it is a True Positive or not. The Benchmark supports scorecard
generators for computing exactly how a tool did when analyzing a version
of the Benchmark. The full list of supported tools is on the Tools
Support/Results tab. For each tool there is a parser that can parse the
native results format for that tool (usually XML). This parser simply,
for each test case, looks to see if that tool reported a vulnerability
of the type expected in the test case source code file (for SAST) or the
test case URL (for DAST/IAST). If it did, and the test case was a True
Positive, the tool gets credit for finding it. If it is a False Positive
test, and the tool reports that type of finding, then its recorded as a
False Positive. If the tool didn't report that type of vulnerability for
a test case, then they get either a False Negative, or a True Negative
as appropriate. After calculating all of the individual test case
results, a scorecard is generated providing a chart and statistics for
that tool across all the vulnerability categories, and pages are also
created comparing different tools to each other in each vulnerability
category (if multiple tools are being scored together).

A detailed file explaining exactly how that tool did against each
individual test case in that version of the Benchmark is produced as
part of scorecard generation, and is available via the Actual Results
link on each tool's scorecard page. (e.g.,
Benchmark_v1.1_Scorecard_for_FindBugs.csv).

## 2\. What if the tool I'm using doesn't have a scorecard generator for it?

Send us the results file\! We'll be happy to create a parser for that
tool so its now supported.

## 3\. What if a tool finds other unexpected vulnerabilities?

We are sure there are vulnerabilities we didn't intend to be there and
we are eliminating them as we find them. If you find some, let us know
and we'll fix them too. We are primarily focused on unintentional
vulnerabilities in the categories of vulnerabilities the Benchmark
currently supports, since that is what is actually measured.

Right now, two types of vulnerabilities that get reported are ignored by
the scorecard generator:

1.  Vulnerabilities in categories not yet supported
2.  Vulnerabilities of a type that is supported, but reported in test
    cases not of that type

In the case of \#2, false positives reported in unexpected areas are
also ignored, which is primarily a DAST problem. Right now those false
positives are completely ignored, but we are thinking about including
them in the false positive score in some fashion. We just haven't
decided how yet.

## 4\. How should I configure my tool to scan the Benchmark?

All tools support various levels of configuration in order to improve
their results. The Benchmark project, in general, is trying to **compare
out of the box capabilities of tools**. However, if a few simple tweaks
to a tool can be done to improve that tool's score, that's fine. We'd
like to understand what those simple tweaks are, and document them here,
so others can repeat those tests in exactly the same way. For example,
just turn on the 'test cookies and headers' flag, which is off by
default. Or turn on the 'advanced' scan, so it will work harder, find
more vulnerabilities. Its simple things like this we are talking about,
not an extensive effort to teach the tool about the app, or perform
'expert' configuration of the tool.

So, if you know of some simple tweaks to improve a tool's results, let
us know what they are and we'll document them here so everyone can
benefit and make it easier to do apples to apples comparisons. And we'll
link to that guidance once we start documenting it, but we don't have
any such guidance right now.

## 5\. I'm having difficulty scanning the Benchmark with a DAST tool. How can I get it to work?

We've run into 2 primary issues giving DAST tools problems.

a) The Benchmark Generates Lots of Cookies

The Burp team pointed out a cookies bug in the 1.2beta Benchmark. Each
Weak Randomness test case generates its own cookie, 1 per test case.
This caused the creation of so many cookies that servers would
eventually start returning 400 errors because there were simply too many
cookies being submitted in a request. This was fixed in the Aug 27, 2015
update to the Benchmark by setting the path attribute for each of these
cookies to be the path to that individual test case. Now, only at most
one of these cookies should be submitted with each request, eliminating
this 'too many cookies' problem. However, if a DAST tool doesn't honor
this path attribute, it may continue to send too many cookies, making
the Benchmark unscannable for that tool. Burp Pro prior to 1.6.29 had
this issue, but it was fixed in the 1.6.29 release.

b) The Benchmark is a BIG Application

Yes. It is, so you might have to give your scanner more memory than it
normally uses by default in order to successfully scan the entire
Benchmark. Please consult your tool vendor's documentation on how to
give it more memory.

Your machine itself might not have enough memory in the first place. For
example, we were not able to successfully scan the 1.2beta with OWASP
ZAP with only 8 Gig of RAM. So, you might need a more powerful machine
or use a cloud provided machine to successfully scan the Benchmark with
certain DAST tools. You may have similar problems with SAST tools
against large versions of the Benchmark, like the 1.1 release.

# Acknowledgements

The following people, organizations, and many others, have contributed
to this project and their contributions are much appreciated\!

  - Lots of Vendors - Many vendors have provided us with either trial
    licenses we can use, or they have run their tools themselves and
    either sent us results files, or written and contributed scorecard
    generators for their tool. Many have also provided valuable feedback
    so we can make the Benchmark more accurate and more realistic.
  - Juan Gama - Development of initial release and continued support
  - Ken Prole - Assistance with automated scorecard development using
    CodeDx
  - Nick Sanidas - Development of initial release
  - Denim Group - Contribution of scan results to facilitate scorecard
    development
  - Tasos Laskos - Significant feedback on the DAST version of the
    Benchmark
  - Ann Campbell - From SonarSource - for fixing our SonarQube results
    parser
  - Dhiraj Mishra - OWASP Member - contributed SQLi/XSS fuzz vectors as
    initial contribution towards adding support for WAF/RASP scoring

![CWE_Logo.jpeg](CWE_Logo.jpeg "CWE_Logo.jpeg") - The CWE project for
providing a mapping mechanism to easily map test cases to issues found
by vulnerability detection tools.

We are looking for volunteers. Please contact [Dave
Wichers](mailto:dave.wichers@owasp.org) if you are interested in
contributing new test cases, tool results run against the benchmark, or
anything else.

__NOTOC__ <headertabs />

[Category:OWASP_Project](Category:OWASP_Project "wikilink")