# Main

{{\#widget:PayPal Donation |target=_blank
|budget=OWASP_Cyber_Defense_Matrix }}

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="introduction_to_the_cyber_defense_matrix">Introduction to the Cyber Defense Matrix</h2>
<p>Imagine going into a grocery store to shop for Thanksgiving dinner, but instead of seeing nice, orderly aisles, you see a massive pile of food in the middle of the grocery store. Finding the ingredients that you need to make dinner is going to be extremely hard because there’s no organizational system helping you understand where things are. The disorganization makes it very difficult to find what you need and compare competing products.</p>
<p>The cybersecurity vendor marketplace is like this disorganized grocery store. A proof of this assertion can be seen by looking at the vendor hall at any major security conference. The cacophony of sounds from vendors hawking their wares, the confusing language of the vendor’s marketecture, and the lack of any semblance of organization (aside from biggest to smallest) does not help buyers understand what they need or where to find it.</p>
<p>Because the cybersecurity community does not use consistent terminology to describe what we need, there is much confusion about what many vendor products actually do. Instead of a clear articulation of a product's capabilities, we are bombarded with overused, trendy jargon that usually leaves us wondering if the product can really solve any of our woes. Some organizations even organize themselves according to the jargon. We need to stop letting marketing pitches dictate our terminology and not lose sight of the more bland descriptors that actually tell us what something does.</p>
<p>The Cyber Defense Matrix helps us understand what we need organized through a logical construct so that when we go into the security vendor marketplace, we can quickly discern what products solve what problems and be informed on what is the core function of a given product. In addition, the Cyber Defense Matrix provides a mechanism to ensure that we have capabilities across the entire spectrum of options to help secure our environments.</p>
<p>Although the Cyber Defense Matrix was initially created to help organize security technologies, many other use cases have been discovered to help build, manage, and operate a security program. This project intends to capture these use cases and their implementations to help security practitioners mature their security programs.</p>
<h2 id="description_of_the_cyber_defense_matrix">Description of the Cyber Defense Matrix</h2>
<p>The basic construct of the Cyber Defense Matrix starts with two dimensions. The first dimension captures the five operational functions of the NIST Cybersecurity Framework:</p>
<table>
<thead>
<tr class="header">
<th><p>IDENTIFY</p></th>
<th><p>PROTECT</p></th>
<th><p>DETECT</p></th>
<th><p>RESPOND</p></th>
<th><p>RECOVER</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p>The second dimension captures five assets classes that we try to secure:</p>
<table>
<thead>
<tr class="header">
<th><p>DEVICES</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>APPLICATIONS</p></td>
</tr>
<tr class="even">
<td><p>NETWORKS</p></td>
</tr>
<tr class="odd">
<td><p>DATA</p></td>
</tr>
<tr class="even">
<td><p>USERS</p></td>
</tr>
</tbody>
</table>
<p>When these two dimensions are put into a grid, we arrive at with a five-by-five matrix that we call the “Cyber Defense Matrix.”</p>
<div style="width:100%;border:0,margin:0;">
<figure>
<img src="Cyber_Defense_Matrix.png" title="Cyber_Defense_Matrix.png" alt="Cyber_Defense_Matrix.png" /><figcaption>Cyber_Defense_Matrix.png</figcaption>
</figure>
</div>
<p>There is one more important piece of this matrix.  At bottom of the grid, we show a continuum that characterizes the degree of dependency on technology, people, and process as we progress through the five operational functions of the NIST Cybersecurity Framework.  TECHNOLOGY plays a much greater role in IDENTIFY and PROTECT. As we move to DETECT, RESPOND, and RECOVER, our dependency on TECHNOLOGY diminishes and our dependency on PEOPLE grows. Throughout all five operational functions, there's a consistent level of dependency on PROCESS. This continuum helps us understand where we might have imbalances in our reliance on PEOPLE, PROCESS, and TECHNOLOGY when trying to tackle our cybersecurity challenges.</p>
<p>We believe that this matrix is a realistic model describes a broad range of cybersecurity practices. In this website, you will find several insights on the Cyber Defense Matrix and examples of how to leverage it to address the challenges that we face in cybersecurity.</p>
<p>If you discover a new use of the Cyber Defense Matrix, we would love to hear about it. Likewise, if you find a problem with the matrix in that it doesn't seem to properly describe something that we do in cybersecurity, please point that out, and we'll either adjust the matrix or clarify how that perceived discrepancy can be addressed or explained through the matrix.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="presentations_and_other_media">Presentations and Other Media</h2>
<p>[<a href="https://www.rsaconference.com/writable/presentations/file_upload/pdil-w02f_understanding_the_security_vendor_landscape">https://www.rsaconference.com/writable/presentations/file_upload/pdil-w02f_understanding_the_security_vendor_landscape</a>...-final.pdf Cyber Defense Matrix Presentation at RSA Conference 2016]</p>
<p><a href="Cyber_Defense_Matrix_Handouts" title="wikilink">Cyber Defense Matrix Handouts</a></p>
<h2 id="project_leader">Project Leader</h2>
<ul>
<li><a href="Sounil@gmail.com" title="wikilink">Sounil Yu</a></li>
<li><a href="Tomb@owasp.org" title="wikilink">Tom Brennan</a></li>
</ul>
<h2 id="mailing_list">Mailing List:</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp_cyber_defense_matrix">owasp_cyber_defense_matrix@lists.owasp.org</a></p>
<h2 id="faqs">FAQs</h2>
<ul>
<li>TBD</li>
</ul>
<h2 id="roadmap">Roadmap</h2>
<ul>
<li>Document structure of the Cyber Defense Matrix (July 2017)</li>
<li>Map vendors to the Cyber Defense Matrix (September 2017 and ongoing)</li>
<li>Map NIST NICE NCWF skillsets to the Cyber Defense Matrix (September 2017)</li>
<li>Define attributes that can support measurement of efficacy of capability (December 2017 and ongoing)</li>
<li>Define Design Patterns and Business Constraints aligned against the Cyber Defense Matrix (June 2018 and ongoing)</li>
<li>Capture anecdotal and empirical measurements of capability degradation rates (December 2018)</li>
<li>Incorporate and document new use cases as they are discovered (Ongoing)</li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li>TBD</li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>The Cyber Defense Matrix, originally created by Sounil Yu, is licensed under the <a href="http://creativecommons.org/licenses/by-sa/4.0/">http://creativecommons.org/licenses/by-sa/4.0/</a> Creative Commons Attribution-ShareAlike 4.0 license, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="mailing_list_1">MAILING LIST</h2>
<ul>
<li><a href="https://lists.owasp.org/mailman/listinfo/owasp_cyber_defense_matrix">CLICK TO JOIN</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[01 May 2017] Project updated</li>
<li>[26 June 2017] Update</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>rowspan="2" align="center" valign="top" width="50%"</p></td>
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
<img src="Project_Type_Files_DOC.jpg" title="Project_Type_Files_DOC.jpg" alt="Project_Type_Files_DOC.jpg" /><figcaption>Project_Type_Files_DOC.jpg</figcaption>
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

## How can I participate in your project?

Join the mailing list, say hello\!

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator.

# Roadmap

  - Document structure of the Cyber Defense Matrix (July 2017)
  - Map vendors to the Cyber Defense Matrix (September 2017 and ongoing)
  - Map NIST NICE NCWF skillsets to the Cyber Defense Matrix (September
    2017)
  - Define attributes that can support measurement of efficacy of
    capability (December 2017 and ongoing)
  - Define Design Patterns and Business Constraints aligned against the
    Cyber Defense Matrix (June 2018 and ongoing)
  - Capture anecdotal and empirical measurements of capability
    degradation rates (December 2018)
  - Incorporate and document new use cases as they are discovered
    (Ongoing)

# Contributors

Everyone is invited to collaborate on this project.

# Events and Opportunities to Get Involved

April 5th 2017 project announced publicly at the [OWASP NYC Chapter
Meeting](https://www.meetup.com/owaspnyc/events/236400067/) call for
DATA is OPEN

June 2017 - Project Submitted and Approved by OWASP Foundation, page
online

July 2017 - Planning for BlackHat/Defcon Face to Face Meet-Up

Aug 2017 - <Summer Hiatus>

Sept 2017 - AppSecUSA Project Summit

__NOTOC__ <headertabs></headertabs>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")