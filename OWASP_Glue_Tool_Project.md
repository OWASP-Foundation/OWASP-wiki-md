# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_glue_tool_project">OWASP Glue Tool Project</h2>
<p>The OWASP Glue Tool Project is a tools based project intended to make security automation easier. It is essentially a ruby gem that co-ordinates the running of different analysis tools and reporting from those tools.</p>
<h2 id="description">Description</h2>
<p>The purpose of the project is to make it easy to integrate security tools (like static or dynamic analysis) into the CI/CD pipeline.</p>
<h2 id="licensing">Licensing</h2>
<p>Apache 2.0 License</p>
<p>This program is free software: you can redistribute it and/or modify it under the terms of the <a href="http://www.apache.org/licenses/LICENSE-2.0">link Apache 2.0 License</a> as published by the Apache Software Foundation. Any contributions are Copyright © by OWASP 2015.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/OWASP/glue">Source Code</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Matt Konda</p>
<p>Omer Levi Hevroni</p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_AppSec_Pipeline" title="wikilink">OWASP_AppSec_Pipeline</a></li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
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
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[6 Sep 2018] <a href="https://github.com/OWASP/glue/releases/tag/0.10.0">0.10.0</a></li>
<li>[2 Jan 2016] 0.8.0</li>
<li>[27 Aug 2015] Initial Release.</li>
<li>[14 Sep 2016] Renamed to Glue from Pipeline.</li>
</ul></td>
</tr>
</tbody>
</table>

# FAQs

## What does Glue do?

The OWASP Glue tool attempts to make it very easy to run different types
of security tools at various stages of the software development process
and produce unified issues that can be used in other contexts to track
or remediate issues.

## Why would I use Glue?

To help get security feedback into your developers hands faster.

## How can I participate in your project?

Reach out to matt.konda@owasp.org with any questions or ideas or ideas
about how to participate. We are welcoming input. We are following
standard github workflow so you can fork the code and submit a pull
request if you prefer. Alternatively, you can get more deeply involved
and talk with us about roadmap and other items. And finally, you are
always invited to our Slack channel.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers, writers, graphic designers, and a project
administrator. See the Road Map and Getting Involved tab for more
details.

# Acknowledgements

## Contributors

To this point, project contributors include:

  - [Matt Konda](https://www.owasp.org/index.php/User:Matt_Konda)
  - Rafael Zambrano
  - Alex Lock
  - Omer Levi Hevroni

# Road Map and Getting Involved

Deliverable: Glue is delivered as a ruby gem (executable binary) and in
a docker image with required tools already bundled.

## Roadmap

Allows extending the tool more without changing code. Currently, it’s
possible to integrate new tools without changing code, in the future we
would like to add a similar support for reports and filters. Check out
the open issues on GitHub. This is what we hope to achieve in future
releases.

## Getting Involved

Involvement in the development and promotion of <strong>Glue</strong> is
actively encouraged\! You do not have to be a security expert or a
programmer to contribute. Some of the ways you can help are as follows:

### Coding

We could implement some of the later items on the roadmap sooner if
someone wanted to help out with a unit or automated regression tests

### Localization

Are you fluent in another language? Can you help translate the text
strings in the <strong>Tool Project Template</strong> into that
language?

### Testing

Do you have a flair for finding bugs in software? We want to produce a
high-quality product, so any help with Quality Assurance would be
greatly appreciated. Let us know if you can offer your help.

### Feedback

Please use the [Tool Project Template project mailing
list](https://lists.owasp.org/mailman/listinfo/OWASP_Tool_Project_Template)
for feedback about:

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

Alternativly, you can also use our Slack channel on OWASP slack.

# Minimum Viable Product

## Pipeline needs

1\. Pull from github or a specified location on the file system 2. Run
tools like brakeman, bundler-audit and owasp-dependency-check on the
code. 3. Standardizes the format of results then reports them in text,
csv, json or via JIRA's REST API. 4. Detect duplicates and won't report
the same thing more than once.

It also needs to be easy to set up the security tools and digest
results. Hence a focus on docker.

# Project About

Detail around this project can be found at:
<https://github.com/owasp/github>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")