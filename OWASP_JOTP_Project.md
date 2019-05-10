# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_jotp">OWASP jOTP</h2>
<p>OWASP jOTP is a microservice implemented in Java that can be used to generate, validate, and automatically expire one-time use password tokens.</p>
<h2 id="description">Description</h2>
<p>A common use case for jOTP is as follows: 1. Client applications displays a login page requesting the user enter his/her username and password. 2. If the credentials check passes, the user's email is looked up and a message containing the token is sent. 3. The application then requests that the OTP token that was sent be entered in a text box. Once entered, it is sent to jOTP. 4. jOTP validates the token. If the token was valid, the application finishes authenticating the user. If the token was not valid, the user is redirected to the login page.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP jOTP is available under the <a href="http://opensource.org/licenses/BSD-2-Clause">BSD 2-Clause License</a>.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_jotp">What is jOTP?</h2>
<p>OWASP jOTP provides:</p>
<ul>
<li>OTP token generation, validation, and expiration.</li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<p>Rob Upcraft</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://bintray.com/upcrob/generic/jOTP/_latestVersion">Bintray Download</a></li>
<li><a href="https://github.com/upcrob/jOTP">GitHub Repository</a></li>
</ul>
<h2 id="email_list">Email List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp_jotp_project">OWASP jOTP Mailing List</a> NOTE: Include "jOTP" in the subject heading of all emails to this list.</p>
<h2 id="news_and_events">News and Events</h2>
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

  - Where can OWASP jOTP be downloaded?
    The source code, along with basic documentation, is located here:
    [GitHub Repository](https://github.com/upcrob/jOTP)

<!-- end list -->

  - I can see the /sys/monitor endpoint, but when I try to test the
    other endpoints (eg. /otp/validate), I don't get anything in the
    response.
    The endpoints under /otp only respond to POST requests, and will
    return an empty response if they are requested via GET.

# Acknowledgements

## Volunteers

OWASP jOTP is developed by a worldwide team of volunteers. The primary
contributors to date have been:

  - Rob Upcraft

# Road Map and Getting Involved

As of
[April 2014](https://www.owasp.org/index.php/Projects/OWASP_JOTP_Project/Roadmap),
the priorities are:

Development work for jOTP is largely complete as of now. Because it is
intended to be lightweight and focused on this use case, the feature set
is not planned to grow significantly, if at all. Most future work will
include bug fixes, and additional customization options developed on an
as-needed basis.

Involvement in the development and promotion of OWASP jOTP is actively
encouraged\! You do not have to be a security expert in order to
contribute.

Some of the ways you can help:

  - Submit issues to the GitHub repository.
  - Submit pull requests for fixes to the GitHub repository.

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")