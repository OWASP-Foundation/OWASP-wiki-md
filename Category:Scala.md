# Main

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="about">About</h2>
<p>The OWASP Scala and JVM Technology Knowledge Base is the clearing house for all information related to building secure web/distributed applications and services based on Java and JVM technologies. The focus of these pages is on guidance for developers and architects using Scala frameworks and JVM based technologies for Backend development</p>
<h2 id="purpose">Purpose</h2>
<ul>
<li>Provide deep, rich guidance for Scala developers in using the security features of Scala frameworks.</li>
<li>Address security in relation to the Java Virtual Machine and derived technologies.</li>
<li>Guide system administrators in managing Scala and JVM related components and applications.</li>
<li>Create guidance for use of OWASP components that are designed for use with Scala or other JVM languages.</li>
<li>Focus on information about working with and on OWASP tools built using Scala or other JVM technologies.</li>
<li>Provide a stream of security related information, like vulnerabilities and security patches, related to the Scala and JVM universe.</li>
<li>Build an ecosystem allowing to all actors interested to discuss, share and learn.</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>OWASP Java™ and JVM Technology Knowledge Base is free to use. It is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p>
<p>Oracle® and Java™ are <a href="http://www.oracle.com/us/legal/trademarks/index.html%7Cregistered">trademarks of Oracle</a> and/or its affiliates. Other names may be trademarks of their respective owners.</p>
<h2 id="whats_hot">What's Hot!</h2>
<p>See the "Tasks and Roadmap" tab for more information.</p>
<p><a href="OWASP_Java_Project_WIPRO_1_2015" title="wikilink">Wiki Pages Review Operation - 2015/2016</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><figure>
<img src="Scala_logo.png" title="Scala_logo.png" alt="Scala_logo.png" /><figcaption>Scala_logo.png</figcaption>
</figure>
<h2 id="meta">Meta</h2>
<p>Last Update: <strong>//</strong></p>
<p><br />
</p>
<h2 id="other_resources">Other Resources</h2>
<p><a href="http://lists.owasp.org/mailman/listinfo/java-project">Mailing List</a></p>
<p><a href="https://github.com/owasp">GitHub (OWASP)</a></p>
<p><br />
</p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_Project" title="wikilink">OWASP Project Repository</a></li>
<li><a href="Language" title="wikilink">Languages Repository</a></li>
<li><a href="OWASP_.NET_Project" title="wikilink">.NET Project</a></li>
<li><a href="Ruby" title="wikilink">Ruby</a></li>
<li><a href="PHP" title="wikilink">PHP</a></li>
<li><a href="Perl" title="wikilink">Perl</a></li>
<li><a href="Python" title="wikilink">Python</a></li>
<li><a href="JavaScript" title="wikilink">JavaScript</a></li>
<li><a href="C/C++" title="wikilink">C/C++</a></li>
<li><a href="SQL" title="wikilink">SQL, PL/SQL, DB Scripting</a></li>
<li><a href="OWASP_Internet_of_Things_Project" title="wikilink">OWASP IoT Security</a></li>
<li><a href="OWASP_Mobile_Security_Project" title="wikilink">OWASP Mobile Security</a></li>
</ul></td>
</tr>
</tbody>
</table>

# Related OWASP Projects

## Security Tools

|             |                                                               |
| ----------- | ------------------------------------------------------------- |
| colspan="2" | [OWASP Dependency Check](OWASP_Dependency_Check "wikilink")   |
| width="20"  |                                                               |
| colspan="2" | [OWASP SonarQube Project](OWASP_SonarQube_Project "wikilink") |
| width="20"  |                                                               |

## General Documents

|                                                                                                                           |                                                             |                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [OWASP Secure Coding Practices - Quick Reference Guide](OWASP_Secure_Coding_Practices_-_Quick_Reference_Guide "wikilink") | [OWASP Codes of Conduct](OWASP_Codes_of_Conduct "wikilink") | [OWASP Cheat Sheets Series](Cheat_Sheets "wikilink")                                                          |
| [OWASP Testing Project](OWASP_Testing_Project "wikilink")                                                                 | [OWASP Web Top 10](OWASP_Top_Ten_Project "wikilink")        | [OWASP Vulnerable Web Applications Directory](OWASP_Vulnerable_Web_Applications_Directory_Project "wikilink") |

# Security Frameworks

| Framework                                                                                           | Authentication | Authorization | CSRF | XSS | SQLInjection | OWASP page | Notes |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- | ---- | --- | ------------ | ---------- | ----- |
| [Play](https://www.playframework.com/documentation/2.0.4/ScalaSecurity)                             |                | ✓             |      | ✓   |              | \-         |       |
| [Deadbolt 2](http://deadbolt.ws/#service)                                                           |                |               |      | ✓   |              | \-         |       |
| [Play-pac4j](https://github.com/pac4j/play-pac4j)                                                   |                | ✓             |      | ✓   |              | ✓          |       |
| [Scala-oauth2-provider](https://auth0.com/authenticate/scala/oauth2/)                               |                | ✓             |      | \-  |              | \-         |       |
| [SecureSocial](http://www.securesocial.ws/)                                                         |                | ✓             |      | \-  |              | \-         |       |
| [Silhouette - Play Framework Library](https://www.silhouette.rocks/)                                |                | ✓             |      | \-  |              | \-         |       |
| [Lift](https://liftweb.net/)                                                                        |                | ✓             |      | ✓   |              | ✓          |       |
| [Akka (Akka-http)](https://index.scala-lang.org/akka/akka-http/akka-http-core/10.0.10?target=_2.12) |                | ✓             |      | ✓   |              | \-         |       |
| [Spray](http://spray.io/)                                                                           |                | ✓             |      | ✓   |              | \-         |       |

Reference <https://www.47deg.com/blog/security-frameworks-for-scala/>

# Resources

## Mailing List

[OWASP Java and JVM Technologies Mailing
List](http://lists.owasp.org/mailman/listinfo/java-project)

## Code Repository

[GitHub OWASP Global Repository](https://github.com/owasp)

## Related Project Resources

[OWASP Project Repository](OWASP_Project "wikilink")

[Languages Repository](Language "wikilink")

[.NET Project](OWASP_.NET_Project "wikilink")

[Ruby Technology Knowledge Base](Ruby "wikilink")

[PHP Technology Knowledge Base](PHP "wikilink")

[Perl Technology Knowledge Base](Perl "wikilink")

[Python Technology Knowledge Base](Python "wikilink")

[JavaScript Technology Knowledge Base](JavaScript "wikilink")

[C/C++ Technology Knowledge Base](C/C++ "wikilink")

[SQL, PL/SQL and DB Scripting Technology Knowledge Base](SQL "wikilink")

[OWASP IoT Security
Project](OWASP_Internet_of_Things_Project "wikilink")

[OWASP Mobile Security
Project](OWASP_Mobile_Security_Project "wikilink")

# Tasks and Roadmap

## Roadmap

  - General review of all Scala and JVM related pages in the wiki.
  - Build Scala and JVM security related resources guide
  - Concrete guideline for Scala and JVM developers
  - Clear checklists, around various topics, language, servers and
    frameworks.



# Get involved

The first step would be to establish contact with the project leaders
and/or the entire team. This can be done using a direct and private
message, or by joining the public mailing list to say hello.

When it comes to participating in project activities, everything depends
on the time you are willing and able to invest. It is however very
important to not jump into too many things at the beginning, later
having to back out or to let unfinished things behind you. It is much
better to start with small tasks, increasing intensity and investment
over time.

Please also be patient with expecting the "merge" of your work into the
existing project pages and code. As everywhere in live, trust has to be
built-up.

The Java and JVM knowledge base has currently multiple tasks open, which
can be found on the adequate section of this page. Not all tasks require
a wiki account. Please take something you are interested in and start
participating. Work load is not the only outcome when participating in
open projects. You are getting a lot of things back: recognition,
satisfaction, knowledge and contacts, sometime friends.

Sounds cool? Then jump in...

To get involved join the mailing list, follow this link: [OWASP Java and
JVM Mailing List](http://lists.owasp.org/mailman/listinfo/java-project)

# Archives

The previous version of this JAVA Project home page is archived here:
[OWASP Java Project Archive
(8.2010)](OWASP_Java_Project_Archive_\(8.2010\) "wikilink")



<hr/>

__NOTOC__ <headertabs />



(The pages in the "old" category "OWASP Java Project" have to be moved
into the category "Java". Work is in progress).

<categorytree mode=pages>OWASP Java Project</categorytree>

[Category:Technology](Category:Technology "wikilink")
[Category:Language](Category:Language "wikilink")