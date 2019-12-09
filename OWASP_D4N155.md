<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p><span style="color:#ff0000"></p>
<h2 id="owasp_tool_project_d4n155">OWASP Tool Project D4N155</h2>
<p>OWASP Tool Project D4N155The project uses <a href="https://en.wikipedia.org/wiki/Open-source_intelligence">OSINT</a> for dynamic and smart attack of brute force, using a complex operation and get the word list using expressions find</p>
<h2 id="description">Description</h2>
<figure>
<img src="Owasp-d4n155-logo.png" title="Owasp-d4n155-logo.png" alt="Owasp-d4n155-logo.png" /><figcaption>Owasp-d4n155-logo.png</figcaption>
</figure>
<p><span></p>
<p><code>   On the abstract we can presume that this isn’t just another pentest tool this is a truly powerful tool, that integrate various key features of another projects and ideas of the developers and aggregate then in a same place.</code></p>
<p></span></p>
<h4 id="key_features">KEY FEATURES</h4>
<ul>
<li>Search vulnerable url’s</li>
<li>Anonymous feature</li>
<li>Make a smart wordlist based on page content</li>
<li>Totally CLI (BASH + PYTHON)</li>
<li>FREE SOFTWARE IN LICENSE(GPL V3) AND IN ESSENCE</li>
<li>Automatic Report Feature with two options:
<ul>
<li>PDF</li>
<li>HTML Where it generate a dynamic graphic for quick visualization</li>
</ul></li>
</ul>
<p>People with bad intentions dedicate a long part of their time to read profiles,posts analyzing then, observing reactions with in order to obtain the maximum information about their targets in order to make their list(of passwords) and the door for attack. Even if you do not have specific knowledge, so you may be using this tool will help you get a sense of how vulnerable you are and consequently take action and prevent a possible attack.</p>
<p>Besides this it’s a friendly tool for a pentester with the features of automatics reports the professional can save time, writing extensive reports with pages of print screens, technician reports and transcription of procedures this tool can make a half of a job for him.</p>
<h2 id="operations">Operations</h2>
<p>The process of password speculation is performed using various functions, all using recursive ones, as the equation shows.</p>
<p><code> λ→(η) = Op.</code></p>
<h3 id="combinatorial_analysis">Combinatorial Analysis</h3>
<p>The code follows combinatorial analysis in order to speculate passwords and we’ll explain next.</p>
<h3 id="combinatorial_enumerative">Combinatorial Enumerative</h3>
<p>Enumerative combinatorial is more classical area of combinatorics and concentrates on counting the number of combinatorial objects</p>
<figure>
<img src="Tree.png" title="Tree.png" alt="Tree.png" /><figcaption>Tree.png</figcaption>
</figure>
<h3 id="analytic_combinatorics">Analytic combinatorics</h3>
<p>Analytic combinatorics concerns the enumeration of combinatorial structures using tools from complex analysis and probability theory. In contrast with enumerative combinatorics, which uses explicit combinatorial formulae and generating functions to describe the results, analytic combinatorics aims at obtaining asymptotic formulae.</p>
<p>This is the most important thing for code. <img src="Permutation.gif" title="fig:Permutation.gif" alt="Permutation.gif" /> With all the possibilities of combinations, example: <span></p>
<p><code>Root text: i walk</code><br />
<code>---- Tests ----</code><br />
<code>1,1: walk i</code><br />
<code>1,2: walki</code><br />
<code>2,1: i walk</code><br />
<code>2,2: iwalk</code><br />
<code>Removed repeated words</code><br />
<code>------------------------</code><br />
<code>walk i</code><br />
<code>walki</code><br />
<code>iwalk</code></p>
<p></span></p>
<p>Using this script are possible see in practical with 4 values <code>"John","have","easy","pass"</code>, run:</p>
<p><code> wget -qO- "</code><a href="https://gist.githubusercontent.com/Jul10l1r4/a5edfae6b0f206b4e491152c9f6b4347/raw/6c246b3a32db2f19fe5c68394663a1c995d8f625/mess.py"><code>https://gist.githubusercontent.com/Jul10l1r4/a5edfae6b0f206b4e491152c9f6b4347/raw/6c246b3a32db2f19fe5c68394663a1c995d8f625/mess.py</code></a><code>" | python3</code></p>
<figure>
<img src="Calc.png" title="Calc.png" alt="Calc.png" /><figcaption>Calc.png</figcaption>
</figure>
<h2 id="licensing">Licensing</h2>
<p>GNU GPL v3 License (allows commercial use, but requires that modifications to your code stay open source, thus prohibiting proprietary forks of your project)</p>
<h2 id="changelog">CHANGELOG</h2>
<p>All notable changes to this project will be documented in this file.</p>
<p>The format is based on <a href="https://keepachangelog.com/en/1.0.0/">Keep a Changelog</a>, and this project adheres to <a href="https://semver.org/spec/v2.0.0.html">Semantic Versioning</a>.</p>
<ol>
<li><ol>
<li><a href="https://github.com/adasecurity/D4N155/tree/0.50">0.50</a> - 2019-03-14</li>
<li>Added</li>
</ol></li>
</ol>
<ul>
<li>Rate time, between requests</li>
</ul>
<ol>
<li><ol>
<li><a href="https://github.com/adasecurity/D4N155/tree/0.10">0.10</a> - 2019-02-24
<ol>
<li>Added</li>
</ol></li>
</ol></li>
</ol>
<ul>
<li>Make report: HTML, PDF</li>
<li>Analysis for all dorks [Exhausting]</li>
<li>Crawler based results using Google-Hacking</li>
<li>Some <a href="https://adasecurity.github.io/D4N155/theories/#operation-of-d4n155">calculations</a></li>
</ul>
<h2 id="getting_involved">Getting Involved</h2>
<ol>
<li>Hello, World!</li>
</ol>
<p>Thanks for your interest in making D4N155 There are mutliple ways to help beyond just writing code:</p>
<p><code>- [Submit bugs and feature requests] with detailed information about your issue or idea.</code><br />
<code>- [Help fellow users with open issues] or [help fellow committers test recent pull requests].</code></p>
<ol>
<li>Contributing to D4N155</li>
</ol>
<p>If you want help for undestand the code contact us:</p>
<p><code>* jul10l1r4@disroot.org (Julio Lira)</code><br />
<code>* matheusoliveiratux4me@gmail.com (Matheus Oliveira)</code><br />
<code>* x4fUz_K39z@tutanota.com (@sophiesch0ll)</code></p>
<ol>
<li><ol>
<li>Understand the code</li>
</ol></li>
</ol>
<p><a href="https://framindmap.org/c/maps/655325/public">UML at D4N155</a></p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/OWASP/D4N155">Installation Package</a></p>
<p><a href="https://github.com/OWASP/D4N155">Source Code</a></p>
<p><a href="https://github.com/adasecurity/D4N155/blob/master/CHANGELOG.md">What's New (Revision History)</a></p>
<p><a href="https://d4n155.rtfd.io">Documentation</a></p>
<p><a href="https://github.com/OWASP/D4N155/issues">Issue Tracker</a></p>
<p><a href="https://asciinema.org/a/222527">Video</a></p>
<p><a href="https://adasecurity.github.io/D4N155/theories/#operation-of-d4n155">Operation of D4N155</a></p>
<h2 id="colaborators">Colaborators</h2>
<p>Clara Nobre (@claranobre)</p>
<p>Fernando Eloi(@EloiAlbuquerque)</p>
<p>Guilmour Rossi (<a href="https://guilmour.org">@guilmour</a>)</p>
<p>Julio Lira (<a href="https://jul10l1r4.github.io/">@jul10l1r4</a>)</p>
<p>Kádson Breno (<a href="https://github.com/att4ck3rs3cur1ty">@kr4m3r</a>)</p>
<p>Matheus Oliveira (<a href="https://www.linkedin.com/in/matheus-0liveira/">@Matheus_0liveira</a>)</p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="https://youtu.be/z6-B-eqhyI4">Posso quebrar sua senha? D4N155 - CPBSB</a></li>
</ul></td>
</tr>
</tbody>
</table>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")