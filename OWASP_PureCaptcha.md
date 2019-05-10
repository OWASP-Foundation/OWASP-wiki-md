# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p>Welcome to OWASP Pure Captcha project page!</p>
<h2 id="owasp_purecaptcha">OWASP PureCaptcha</h2>
<p>Use CAPTCHAs in your application without any dependencies, no required libraries and nothing to install. Just include a single small source-code file to have fully functional lightweight CAPTCHAs in your project.</p>
<h2 id="description">Description</h2>
<p>CAPTCHA is a feature detecting humans from computers, needed in many aspects of all web applications to prevent bots from flooding and spamming. Unfortunately all existing libraries and APIs require too much effort for a small application to be feasible and maintainable, so a lot of developers just give up on using CAPTCHAs where they are needed. This is due to the fact that generating CAPTCHAs requires a large body of code libraries to be available. It depends on image manipulation (like GD and Imagick), font rendering (Freetype and etc.) SOAP or Curl and etc. each of which are high level libraries and have a lot more dependencies. PureCapthca provides a single source code file which does the entire CAPTCHA generation and handling, because it only includes code for rendering a few alphanumeric letters from scratch, creating simple BMP files from nothing and modifying simple bitmap images.</p>
<p>This allows developers to easily add a single source code file to their projects and reap full CAPTCHA benefits with minimal memory and processing footprint and ZERO dependencies.</p>
<h2 id="licensing">Licensing</h2>
<p>Creative Commons Attribution ShareAlike 3.0 License</p>
<p>Apache 2 License</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><a href="https://github.com/OWASP/PureCaptcha">Download</a></p>
<p><a href="https://github.com/OWASP/PureCaptcha">Source Code</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="mailto:abiasx@owasp.org">Abbas Naderi</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><a href="OWASP_PHP_Security_Project" title="wikilink">OWASP PHP Security Project</a></p>
<p><a href="CSRFProtector_Project" title="wikilink">CSRFProtector Project</a></p>
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
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Agplv3-155x51.png" title="Agplv3-155x51.png" alt="Agplv3-155x51.png" /><figcaption>Agplv3-155x51.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<p>First version released!</p></td>
</tr>
</tbody>
</table>

# Documentation

There are basically three operations needed to properly utilize
CAPTCHAs:

  - Generating A Captcha

This can be done by the **show** method of PureCaptcha. It will
terminate the current request and return an image to the client.

  - Persisting The Captcha Value

The **show** method also returns a string equal to the Captcha contents.
You need to persist it on the session for the user (preferably for a
limited amount of time). The example code shows how this can be done
simply in your programming language, but any other persistence layer
would be fine. Keep in mind that for every Captcha used inside your
application (e.g one for login page, one for password reset page, one
for remove user page) you should persist the Captcha separately, so that
a user can simultaneously use all your applications functionalities
without one Captcha overriding the expected value for the other.

  - Validating The Captcha

**It is very important to remove the Captcha from persistence after its
validated, whether its wrong or right.** If you leave a Captcha
persisting after validation, attackers can bypass your Captcha by
inspecting it once and then using the same Captcha over and over to send
requests to your application. See the example usages for more details.

# FAQs

## How Can I Use PureCaptcha?

Just include the source code file in your project, and visit the sample
usage files to learn how to properly use a captcha.

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

The first contributors to the project were:

  - [Abbas Naderi](User:Abbas_Naderi "wikilink")

# Road Map and Getting Involved

## Roadmap

Currently PHP library is available and tested. Porting to all major
programming languages is the next step. Since the library is pretty
small, this shouldn't be a hard task and can be done in one summer by 1
candidate.

## Getting Involved

Involvement in the development and promotion is actively encouraged\!
You do not have to be a security expert or a programmer to contribute.
Some of the ways you can help are as follows:

### Coding

Any programming language you like, you can either port PureCaptcha to or
improve the existing code\!

### Localization

Are you fluent in another language? Can you help translate the text
strings and documents into that language?

### Testing

Do you have a flair for finding bugs in software? We want to product a
high quality product, so any help with Quality Assurance would be
greatly appreciated. Let us know if you can offer your help.

### Feedback

mailing list: TBA

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")