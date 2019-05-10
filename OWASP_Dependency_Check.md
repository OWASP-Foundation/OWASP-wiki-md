# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_flagship_big.jpg](_flagship_big.jpg "_flagship_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_dependency_check">OWASP Dependency-Check</h2>
<p>Dependency-Check is a utility that identifies project dependencies and checks if there are any known, publicly disclosed, vulnerabilities. Currently, Java and .NET are supported; additional experimental support has been added for Ruby, Node.js, Python, and limited support for C/C++ build systems (autoconf and cmake). The tool can be part of a solution to the <a href="Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities" title="wikilink">OWASP Top 10 2017 A9-Using Components with Known Vulnerabilities</a> previously known as <a href="Top_10_2013-A9-Using_Components_with_Known_Vulnerabilities" title="wikilink">OWASP Top 10 2013 A9-Using Components with Known Vulnerabilities</a>.</p>
<h2 id="introduction">Introduction</h2>
<p>The OWASP Top 10 2013 contains a new entry: <a href="Top_10_2013-A9-Using_Components_with_Known_Vulnerabilities" title="wikilink">A9-Using Components with Known Vulnerabilities</a>. Dependency Check can currently be used to scan applications (and their dependent libraries) to identify any known vulnerable components.</p>
<p>The problem with using known vulnerable components was described very well in a paper by Jeff Williams and Arshan Dabirsiaghi titled, "<a href="https://cdn2.hubspot.net/hub/203759/file-1100864196-pdf/docs/Contrast_-_Insecure_Libraries_2014.pdf">Unfortunate Reality of Insecure Libraries</a>". The gist of the paper is that we as a development community include third party libraries in our applications that contain well known published vulnerabilities (such as those at the <a href="https://nvd.nist.gov/vuln/search">National Vulnerability Database</a>).</p>
<p>Dependency-check has a command line interface, a Maven plugin, an Ant task, and a Jenkins plugin. The core engine contains a series of analyzers that inspect the project dependencies, collect pieces of information about the dependencies (referred to as evidence within the tool). The evidence is then used to identify the <a href="https://nvd.nist.gov/products/cpe">Common Platform Enumeration (CPE)</a> for the given dependency. If a CPE is identified, a listing of associated <a href="https://cve.mitre.org/">Common Vulnerability and Exposure (CVE)</a> entries are listed in a report.</p>
<p>Dependency-check automatically updates itself using the <a href="https://nvd.nist.gov/vuln/data-feeds">NVD Data Feeds</a> hosted by NIST. <strong>IMPORTANT NOTE:</strong> The initial download of the data may take ten minutes or more. If you run the tool at least once every seven days, only a small XML file needs to be downloaded to keep the local copy of the data current.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p>Version 4.0.2</p>
<ul>
<li><a href="https://dl.bintray.com/jeremy-long/owasp/dependency-check-4.0.2-release.zip">Command Line</a></li>
<li><a href="https://dl.bintray.com/jeremy-long/owasp/dependency-check-ant-4.0.2-release.zip">Ant Task</a></li>
<li><a href="https://search.maven.org/#artifactdetails%7Corg.owasp%7Cdependency-check-maven%7C4.0.2%7Cmaven-plugin">Maven Plugin</a></li>
<li><a href="https://search.maven.org/#artifactdetails%7Corg.owasp%7Cdependency-check-gradle%7C4.0.2%7Cgradle-plugin">Gradle Plugin</a></li>
<li><a href="https://plugins.jenkins.io/dependency-check-jenkins-plugin">Jenkins Plugin</a></li>
<li><a href="https://brew.sh/">Mac Homebrew</a>:<br />
<code>brew update &amp;&amp; brew install dependency-check</code></li>
</ul>
<p>Other Plugins</p>
<ul>
<li><a href="https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22net.vonbuchholtz%22%20a%3A%22sbt-dependency-check%22">sbt Plugin</a></li>
<li><a href="https://github.com/livingsocial/lein-dependency-check">lein-dependency-check</a></li>
</ul>
<h2 id="integrations">Integrations</h2>
<ul>
<li><a href="https://github.com/SonarSecurityCommunity/dependency-check-sonar-plugin">SonarQube Plugin</a></li>
<li><a href="https://github.com/entur/owasp-orb">Circle CI Orb</a></li>
</ul>
<h2 id="links">Links</h2>
<ul>
<li><a href="https://github.com/jeremylong/DependencyCheck">github</a></li>
<li><a href="https://github.com/jeremylong/dependency-check-gradle">gradle source</a></li>
<li><a href="https://github.com/albuch/sbt-dependency-check">sbt source</a></li>
<li><a href="https://github.com/jenkinsci/dependency-check-plugin">jenkins source</a></li>
<li><a href="https://www.ohloh.net/p/dependencycheck">Ohloh</a></li>
<li><a href="https://bintray.com/jeremy-long/owasp">Bintray</a></li>
</ul>
<h2 id="documentation">Documentation</h2>
<ul>
<li><a href="https://jeremylong.github.io/DependencyCheck/">Documentation (on GitHub)</a></li>
</ul>
<h2 id="mailing_list">Mailing List</h2>
<ul>
<li><a href="mailto:dependency-check+subscribe@googlegroups.com">Subscribe</a></li>
<li><a href="mailto:dependency-check@googlegroups.com">Post</a></li>
<li><a href="https://groups.google.com/forum/#!forum/dependency-check">Archived Posts</a></li>
</ul>
<h2 id="presentation">Presentation</h2>
<ul>
<li><a href="https://jeremylong.github.io/DependencyCheck/general/dependency-check.pdf">dependency-check (PDF)</a></li>
<li><a href="https://jeremylong.github.io/DependencyCheck/general/dependency-check.pptx">dependency-check (PPTX)</a></li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>rowspan="2" align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-flagship-trans-85.png" title="Owasp-flagship-trans-85.png" alt="Owasp-flagship-trans-85.png" /><figcaption>Owasp-flagship-trans-85.png</figcaption>
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
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
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

# Acknowledgements

## Volunteers

Dependency-Check is developed by a team of volunteers. The primary
contributors to date have been:

  - [Jeremy Long](User:Jeremy_Long "wikilink")
  - [Steve Springett](User:Steve_Springett "wikilink")
  - [Will Stranathan](User:Will_Stranathan "wikilink")

# Road Map and Getting Involved

As of March 2015, the top priorities are:

  - Resolving all open [github issues/feature
    requests](https://github.com/jeremylong/DependencyCheck/issues?state=open)
  - Improving analysis for .NET DLLs

Involvement in the development and promotion of dependency-check is
actively encouraged\! You do not have to be a security expert in order
to contribute. How you can help:

  - Use the tool
  - Provide feedback via the [mailing
    list](https://groups.google.com/forum/?fromgroups#!forum/dependency-check)
    or by creating [github
    issues](https://github.com/jeremylong/DependencyCheck/issues?state=open)
    (both bugs and feature requests are encouraged)
  - The project source code is hosted on
    [github](https://github.com/jeremylong/DependencyCheck/) - if you
    are so inclined fork it and provide push requests\!

__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")