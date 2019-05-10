# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="introduction">Introduction</h2>
<p>The OWASP PenText XML documentation project is a collection of XML templates, XML schemas and XSLT code, which combined provide an easy way to generate IT security documents including test reports (for penetration tests, load tests, code audits, etc), offers (to companies requesting these tests) and invoices.</p>
<h2 id="description">Description</h2>
<p>The OWASP PenText XML documentation project can help your software security company produce offers, reports, invoices and generic documents by offering a well-structured and easy to maintain documenting system you can modify to your liking. The XML content is multilingual (current languages: English and Dutch) and can be easily adapted - by editing the constants provided in each document - or expanded - by creating new files. Both reports and offers are comprised of smaller snippets, i.e. template texts containing, respectively, offerte text or common vulnerabilities, which can be included where relevant. The XSLT can be customized by anyone versed in XSLT. To get started it is neccessary to install a few Open Source tools. Please visit our <a href="https://github.com/radicallyopensecurity/pentext/blob/master/xml/doc/Tools%20manual.md">documentation page</a> on how to set up the environment.</p>
<h2 id="technical_information">Technical information</h2>
<p>The OWASP PenText project is based on XML. A PenText Report, Offer, Invoice or Generic Document is in fact a (modular) XML document, conforming to an XML Schema. The XML Schema ensures that the documents are structured correctly, so that they can then be transformed into other formats using XSLT and the <a href="http://saxon.sourceforge.net/#F9.7HE">SAXON XSLT processor</a>. Currently there is only one target format: PDF. To produce the PDF document, the report, offer, invoice or generic document XML is first transformed into XSL-FO (XSL Formatting Objects), which is then converted to PDF using <a href="https://xmlgraphics.apache.org/fop/">Apache FOP</a>.</p>
<h2 id="licensing">Licensing</h2>
<p>All files distributed with this project are free software: all documents are released under the GNU General Public License v3 (http://www.gnu.org/licenses/gpl.html) which allows you to modify and redistribute the files freely.</p>
<h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/radicallyopensecurity/pentext">sources</a></p>
<p><a href="https://github.com/radicallyopensecurity/pentext/tree/master/xml/doc">1</a></p>
<p><a href="https://github.com/radicallyopensecurity/pentext/issues">Issue Tracker</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>This project is managed by Radically Open Security members Patricia Piolon and Peter Mosmans. They can be reached at <a href="mailto:info@pentext.org">info@pentext.org</a>.</p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>rowspan="2"</p></td>
<td><figure>
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
</figure></td>
<td><p>rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[17 July 2016] Updated the wiki with basic info.</li>
<li>[21 July 2016] Expanded the wiki</li>
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
looking for writers and translators. See the Road Map and Getting
Involved tab for more details.

# Acknowledgements

## Contributors

The Pentext XML Documentation Project is developed by a worldwide team
working at [Radically Open
Security](https://www.radicallyopensecurity.com). A live update of
project [contributors can be found
here](https://github.com/radicallyopensecurity/pentext/graphs/contributors).

The first contributors to the project were:

  - XSLT coding and documentation by Patricia Piolon
  - ChatOps scripts by Peter Mosmans and John
  - XML content by Peter Mosmans, Christine, Deborah, Marcus Bointon and
    others.

# Road Map and Getting Involved

## Roadmap

As of **October 2017, the highest priorities for the next 6 months
are**:

  - Create additional content for Forensics, code audits and such
  - Get other people to review the PenText XML documentation project and
    provide feedback
  - Get others to provide translations for the snippet library

Subsequent Releases would preferably contain

  - Templates in a wider variety of languages

## Getting Involved

Involvement in the development and promotion of the <strong>PenText XML
documentation project</strong> is actively encouraged\! You do not have
to be a security expert or a programmer to contribute. Some of the ways
you can help are as follows:

### Coding

Suggestions on the the XSLT side are welcome\!

### Localization

Are you fluent in another language? Can you help translate the snippets
and strings in the <strong>PenText XML documentation project</strong>
into that language?

### Testing

Do you have a flair for finding bugs in software? We want to product a
high quality product, so any help with Quality Assurance would be
greatly appreciated. Let us know if you can offer your help.

### Feedback

Please [mail us](mailto:info@pentext.org) for feedback:

  - What do you like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")