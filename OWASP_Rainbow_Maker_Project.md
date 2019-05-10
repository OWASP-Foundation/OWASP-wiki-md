# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![Low_activity.jpg](Low_activity.jpg "Low_activity.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_rainbow_maker">OWASP Rainbow Maker</h2>
<figure>
<img src="RainbowMaker_icon.jpeg" title="Image:RainbowMaker_icon.jpeg" alt="Image:RainbowMaker_icon.jpeg" /><figcaption>Image:RainbowMaker_icon.jpeg</figcaption>
</figure>
<p>Rainbow Maker is a python based tool for Cracking hash signatures &amp; Creating Rainbow Table.</p>
<h2 id="introduction">Introduction</h2>
<p>OWASP Rainbow Maker is a tool aimed to break hash signatures. It allows testers to insert a hash value and possible keywords and values that might used by the application to create it, then it tried multiple combinations to find the format used to generate the hash value.</p>
<h2 id="description">Description</h2>
<p>give it a hash value, and a possible words that might led to create this value - the tool has a delimiter list (){} ;,'[]"~, etc. and it goes over all the words inserted and tries all possible combinations...</p>
<p>for example: if you entered: password, pass, Pass, Password, secret123</p>
<p>it will try all kind of combinations such as:</p>
<ul>
<li>[password:secret123]</li>
<li>"Pass";"secret12"</li>
<li>{Password,secret123}</li>
<li>etc. etc.</li>
</ul>
<p>Its other use is to produce a Rainbow Table out of the given word-list.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP Rainbow Maker is free to use. It is licensed under the GNU GPL v3 License.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_rainbow_maker">What is Rainbow Maker</h2>
<p>OWASP Rainbow Maker provides:</p>
<p>A windows compatible tool to be downloaded (binary/source code) and used by Pen-Testers.</p>
<h2 id="presentation">Presentation</h2>
<p>Link to presentation</p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Tal_Mel" title="wikilink">Tal Melamed</a> <a href="mailto:tal.melamed@owasp.org">@</a></p>
<h2 id="related_projects">Related Projects</h2>
<h2 id="ohloh">Ohloh</h2></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><a href="https://github.com/nu11p0inter/RainbowMaker/releases">Github</a></p>
<h2 id="email_list">Email List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp_rainbow_maker">Sign Up!</a></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[16 Aug 2014] <a href="http://owasp.blogspot.it/2014/08/owasp-august-19-connector.html">OWASP Connector</a></li>
</ul>
<h2 id="in_print">In Print</h2>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="New_projects.png" title="New_projects.png" alt="New_projects.png" width="100" /><figcaption>New_projects.png</figcaption>
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

# FAQs

  - Q1
    A1

<!-- end list -->

  - Q2
    A2

# Acknowledgements

## Volunteers

Rainbow Maker is developed by a worldwide team of volunteers. The
primary contributors to date have been:

  - xxx
  - xxx

## Others

  - xxx
  - xxx

# Road Map and Getting Involved

As of 2014, the priorities are:

  - Version 1.2 is stable and ready.
  - Version 1.22 \[early 2015\] - case insensitivity, improved progress
    bar and status fixes
  - Version 1.25 \[mid 2015\] - allows to save lists, edit inserted
    values, separate keywords from values
  - Version 1.3 \[mid 2016\] - configuration tab:select delimiters, add
    HMAC signature
  - Version 1.4 \[mid 2017\] - multiple parameters (currently 2), upload
    http request, multiprocessing

Involvement in the development and promotion of Rainbow Maker is
actively encouraged\! You do not have to be a security expert in order
to contribute. Some of the ways you can help:

  - Python experts:
  - threading, GUI (TKInter) and other improvments
  - could be found at the Github project page:
    [issues](https://github.com/nu11p0inter/RainbowMaker/issues)

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")