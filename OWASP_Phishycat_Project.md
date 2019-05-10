# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_phishycat_project">OWASP Phishycat Project</h2>
<p>OWASP Phishycat is a phishing detection framework. It detects a phishing page and show alert to the user. Currently, it only supports chrome browser. This project also includes a plugin called "Phishblocker" to communicate with browser and back-end server. It can be extended in other platforms as well.</p>
<h2 id="description">Description</h2>
<p><img src="P-1.jpg" title="fig:P-1.jpg" alt="P-1.jpg" />OWASP Phishycat is a phishing detection framework. Main idea here is to guess the original domain that attacker is trying to phish. Next, it performs the test by doing real time image comparison and DOM analysis of both web pages (Original domain and phishing domain).</p>
<p>Original domains should be registered in project database before it goes for testing. Once it guess the domain name then it compares the real time images of both web pages (phishing site and original website) . Attacker will try to make the web page design look similar to original website as much as possible. If both images are similar to each other, then next step is to compare DOM of both web pages. If it does not match then there is a high chance that it is a phishing site. Because, we can say two web pages are similar only when every elements of the pages are identical. In this case, we have similar looking two websites but their DOM is different.</p>
<p>We take the phishing domain and try to match it with all the registered domain names. If similar looking domain name exist in project database then we do the real time image compare of both web pages. If image compare is true, we proceed with real time DOM analysis of both web pages.</p>
<p>Here we are assuming that phishing domain name is similar to original domain, which may not be the case always. In future, We can implement services like text analysis in a webpage and find the focused keywords, it will help us to get the idea of original domain.</p>
<p>In our MVP, we are not considering threshold for image comparing and DOM analysis. A little change in image and DOM can give us wrong result. There might be elements in web page which are designed to load dynamically every time we refresh the page. To avoid this problem, threshold values will be added in next release of OWASP Phishycat.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP Phishycat is free to use. It is licensed under the Apache License 2.0 <a href="https://apache.org/licenses/LICENSE-2.0.html">https://apache.org/licenses/LICENSE-2.0.html</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p>Current github: <a href="https://github.com/abhijitio/OWASP-Phishycat"><a href="https://github.com/abhijitio/">https://github.com/abhijitio/</a></a></p>
<p><a href="https://github.com/abhijitio/OWASP-Phishycat">Source Code</a></p>
<p><a href="https://github.com/abhijitio/OWASP-Phishycat/wiki/About-OWASP-PhishyCat">Documentation</a></p>
<p><a href="https://github.com/abhijitio/OWASP-Phishycat/wiki">Wiki Home Page</a></p>
<p><a href="https://github.com/abhijitio/OWASP-Phishycat/issues">Issue Tracker</a></p>
<p><a href="https://www.owasp.org/index.php/Kolkata">OWASP Kolkata</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Abhijitio" title="wikilink">Abhijit Chatterjee</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/Phishing">Phishing</a></li>
<li><a href="https://www.owasp.org/index.php/Content_Spoofing">Content_Spoofing</a></li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>rowspan="2" align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Agplv3-155x51.png" title="Agplv3-155x51.png" alt="Agplv3-155x51.png" /><figcaption>Agplv3-155x51.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[18 May 2017] 1.0 Release Candidate is available for download. Any feedback (good or bad) in the next few weeks would be greatly appreciated.</li>
</ul></td>
</tr>
</tbody>
</table>

# FAQs

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

# Acknowledgements

## Volunteers

The OWASP Security Principles project is developed by a worldwide team
of volunteers. A live update of project [contributors is found
here](https://github.com/abhijitio/OWASP-Phishycat).

The first contributors to the project were:

  - [Abhijit Chatterjee](https://www.owasp.org/index.php/User:Abhijitio)
    who created the MVP.

# Road Map and Getting Involved

**WHAT'S COMING**

## Roadmap

As of **June** <strong>2017, the highest priorities for the next 3
months</strong> are: <strong>

  - Complete the text analysis to find the focused keyword and less
    dependency on domain name analysis.
  - Database integration to properly maintain the registered domains.
  - Get other people to review the Code Project Template and provide
    feedback.
  - Develop plugin for Firefox.
  - Mobile Application support.

</strong>

Subsequent Releases will add <strong>

  - Threshold value for image checking to avoid false positives.
  - Threshold value for DOM analysis to avoid false positives.

</strong>

## Getting Involved

Involvement in the development and promotion of <strong>Code Project
Template</strong> is actively encouraged\! You do not have to be a
security expert or a programmer to contribute. Some of the ways you can
help are as follows:

### Coding

We could implement some of the later items on the roadmap sooner if
someone wanted to help out with unit or automated regression tests

### Localization

Are you fluent in another language? Can you help translate the text
strings in the <strong>Code Project Template</strong> into that
language?

### Testing

Do you have a flair for finding bugs in software? We want to product a
high quality product, so any help with Quality Assurance would be
greatly appreciated. Let us know if you can offer your help.

### Feedback

Please use the [Code Project Template project mailing
list](https://lists.owasp.org/mailman/listinfo/OWASP_Code_Project_Template)
for feedback about:

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

# Minimum Viable Product

Minimum Viable Product of OWASP Phishycat Project can be found here :-
<https://github.com/abhijitio/OWASP-Phishycat>

Wiki Home :- <https://github.com/abhijitio/OWASP-Phishycat/wiki>
__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")