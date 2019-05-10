# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_secure_tdd_project">OWASP Secure TDD Project</h2>
<p>The OWASP Secure TDD Project allows organizations to integrate security into the Test Driven Development (TDD) lifecycle.<br />
When utilizing TDD, it is important to clarify to the developers that this process will change the way they think, since they need to cover all tests prior development, which is different from the unit testing approach.<br />
The OWASP Secure TDD Project contains an open source tool written for .NET developers in order to allow generation of the most common tests out of the box and enable developers to consciously improve the project by developing additional tests or extensions.</p>
<h2 id="introduction">Introduction</h2>
<p><strong>About TDD</strong></p>
<p>TDD is about writing a test which will fail, then writing the minimum amount of code required to make it run and then refactoring the code to make it clean.<br />
This is done in cycles, fail -&gt; pass -&gt; refactor, adding a new test for each known requirement for the code.<br />
A TDD test expresses the task of the application functionality that needs to be implemented next and the criterion for success.<br />
TDD is not about testing. TDD uses tests to drive the design of the code.<br />
This can be done with unit tests, functional tests and acceptance tests. Usually, all three are used.<br />
The tests tell you what to do, what to do next and when you are done. They tell you what the API is going to be, what the design is.<br />
The tests permit you to refactor safely, ensuring that the desired behavior continues to work while you adjust your design. The tests also guide you to testable code, promoting smaller methods, shorter parameter lists, and overall much simpler design than other methodologies lead you to.<br />
</p>
<p><strong>Difference between TDD and Unit Tests</strong></p>
<p>Unit Testing is about testing individual units of behavior. An individual unit of behavior is the smallest possible unit of behavior that can be individually tested in isolation.<br />
You can write unit tests before you write your code, after you write your code or while you write your code.<br />
So how does a TDD test differ from a unit test?<br />
Unlike a unit test, a TDD test is used to drive the design of an application. A TDD test is used to express what application code should do before the application code is actually written.<br />
TDD is less about testing, and more about designing the code. Unit tests are then used to set the expectations for the end code. When the end code is written, and passes tests (specifications), you have a code that was designed using tests.<br />
Like unit tests, TDD tests can be used for regression testing. You can use TDD tests to immediately determine whether a change in code has broken existing application functionality. However, unlike a unit test, a TDD test does not necessarily test one unit of code in isolation.<br />
You can do unit testing without doing test driven development. However you can't do test driven development without using unit tests.<br />
When you do traditional unit testing, you write test after you wrote your code.<br />
Test driven development approach is to write unit test before writing code.<br />
</p>
<p><strong>How do we solve the problem by implementing STDD?</strong></p>
<p>TDD will help with the following:</p>
<p>- Tests can be written to verify the threat.<br />
- A solution can be implemented to block the threat, and quickly be confirmed to be working.<br />
- Provided all other tests still pass, you can quickly verify that all other security measures and all other functionality still behave correctly.</p>
<p>Basically TDD assists in allowing a quick turnaround time from when a threat is discovered to when a solution becomes available.<br />
TDD is not going to protect you from unknown threats. By its very nature, you have to know what you want to test in order to write the test in the first place.<br />
However, Secure Test Driven Development (STDD) will help us Defend against existing threats and help developers secure their product by reducing and eliminating vulnerabilities in software before deployment while using the TDD life cycle.<br />
TDD favors highly localized (unit testing). As a result you could easily test that:<br />
GetSafeSQLParam() would correctly guard against SQL injection or that SecureZeroMemory() would correctly erase a password from RAM.<br />
However, it becomes more difficult to verify that all developers have used the correct method in every place that it's required.<br />
Our STDD tool solves this problem, discovering security threats and vulnerabilities in software while writing the code.<br />
</p>
<h2 id="description">Description</h2>
<p>STDD is a tool that will ensure secure coding using an Add-On for Microsoft Visual Studio, by creating auto generated STDD tests, assisting us to find vulnerabilities, exploits and security bugs inside the code while using the TDD life cycle. The tests we will be focusing on are prevention against SQL injection and XSS attacks.</p>
<p>The benefits of such a tool will save time, money and keep code safe from security vulnerabilities.</p>
<h2 id="installation_guide">Installation Guide</h2>
<p><u>Requirements:</u><br />
1. Microsoft Visual-Studio 2013 SDK<br />
(http://www.microsoft.com/en-us/download/details.aspx?id=40758)<br />
2. Microsoft Visual-Studio 2013 and above<br />
<u>Setup:</u><br />
1. Download the project from our Github at <a href="https://github.com/SecureTDD/VisualStudio">https://github.com/SecureTDD/VisualStudio</a><br />
2. Select destination folder<br />
3. Select the product you want to install (Microsoft Visual-Studio 2013 and above)<br />
4. Launch Visual-Studio, click on Tools &gt; Secure TDD Wizard<br />
<u>Secure TDD Installer : </u></p>
<p><a href="http://securetdd.byethost10.com/SecureTDDInstaller.zip">http://securetdd.byethost10.com/SecureTDDInstaller.zip</a></p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP Secure TDD Project is free to use. It is licensed under the Apache 2.0 License.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_the_owasp_secure_tdd_project">What is the OWASP Secure TDD Project?</h2>
<p>The OWASP Secure TDD Project provides:</p>
<ul>
<li>Secure testing --&gt; Secure coding</li>
<li>Efficient coding which saves alot of time and money</li>
</ul>
<h2 id="quick_download">Quick Download</h2>
<ul>
<li>Download source code from Github:<br />
</li>
</ul>
<p><a href="https://github.com/SecureTDD/VisualStudio">https://github.com/SecureTDD/VisualStudio</a></p>
<h2 id="presentation">Presentation</h2>
<p>OWASP IL October 2013<a href="https://www.owasp.org/images/5/5c/OWASP_IL_2013_10_Nir_Valtman_STDD.pdf">1</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Nir Valtman</p>
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
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# FAQs

  - What is Secure STDD?
    Secure Test Driven Development (STDD) will help us Defend against
    existing threats and help developers secure their product by
    reducing and eliminating vulnerabilities in software before
    deployment while using the TDD life cycle.

<!-- end list -->

  - How to benefit from STDD?
    The benefits of such a tool will save time, money and keep code safe
    from security vulnerabilities. This tool does not require a thorough
    understanding of the possible Security threats thus making it easier
    for the Programmer to generate such Security tests.
    STDD tests also guide you to testable code, promoting smaller
    methods, shorter parameter lists, and overall much simpler design
    than other methodologies lead you to.

# Acknowledgements

## Volunteers

The OWASP Secure TDD Project is developed by a worldwide team of
volunteers. The primary contributors to date have been:

  - Lauren Tabak
  - Niran Yadai
  - Tal Darsan
  - Ofir Melinger
  - Kobi Barzilay

# Road Map and Getting Involved

As of March 2014, the priorities are:

  - Visual Studio Add-On
  - Configuration test support
  - SQLi and XSS Security tests

Involvement in the development and promotion of the OWASP Secure TDD
Project is actively encouraged\! You do not have to be a security expert
in order to contribute. Some of the ways you can help:

  - Additional Security tests

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")