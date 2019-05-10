<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>


**Welcome to the OWASP CAL9000 project...**

## PREVIOUS NOTE

This project, while still useful, is pretty much dormant and orphaned by
the project lead.

![HttpRequests.jpg](HttpRequests.jpg "HttpRequests.jpg")

## Overview

CAL9000 is a collection of web application security testing tools that
complement the feature set of current web proxies and automated
scanners. CAL9000 gives you the flexibility and functionality you need
for more effective manual testing efforts. Works best when used with
Firefox or Internet Explorer.

CAL9000 is written in JavaScript, so you have full access to the source
code. Feel free to modify it to best suit your particular needs. CAL9000
has some powerful features (like executing cross-domain xmlHttpRequests
and writing to disk). It is purposefully designed to do some horribly
insecure things. Therefore, I would strongly encourage that you only run
it locally and NOT off of a server.

Take a few moments to check out the CAL9000 built-in Help file for
information about all of the new features and some potential gotchas
(browser quirks, xmlHttpRequest limitations, etc.)

Please only use this tool for testing your own applications or those
that you have been authorized to test.

## Features

  - XSS Attacks - This is a listing of the XSS Attack Info from
    [RSnake](http://ha.ckers.org/xss.html). You can filter the listing
    based on which browsers the attacks work in, test them, apply RegEx
    filters and create/edit/save/delete your own attacks.
  - Character Encoder/Decoder - Encodes and decodes the following types:
    URL, Standard Hex, Unicode, Html(Named), Html(Decimal), Html(Hex),
    Html(Hex Long), Javascript Escaped, XML Escaped, Straight Decimal,
    Straight Hex, IE Hex, IE Unicode, Base64 and MD5. Encode only with
    MD4 and SHA1. Specify Upper/Lowercase, Delimiters and Trailing
    Characters. You can add/remove wrappers around your results and
    encode/decode selected text instead of the entire contents of the
    window.
  - Http Requests - Manually craft and send HTTP requests to servers.
    GET, POST, HEAD, TRACE, TRACK, OPTIONS, CONNECT, PUT, DELETE, COPY,
    LOCK, MKCOL, MOVE, PROPFIND, PROPPATCH, SEARCH and UNLOCK methods
    supported. Send single requests or launch automated attacks with
    more than one request at a time. All results are saved in a history
    file.
  - Http Responses - View the status codes, response headers and body.
    Isolate the script, form and cookie information in the response.
  - Scratchpad - A place to save code snippets, notes, results, etc.
  - Cheatsheets - Collection of references for various web-related
    platforms and languages.
  - IP Encode/Decode - Go to/from IP, Dword, Hex and Octal addresses.
  - String Generator - Create character strings of almost any length.
  - Scroogle Search - A privacy-friendly scrape of Google results
    w/Advanced Operators.
  - Testing Tips - Collection of testing ideas for assessments.
  - Testing Checklist - Track the progress of your testing efforts and
    record your findings. The checklist categories roughly correlate
    with the Manual Testing Techniques from the OWASP Testing Guide.
    Create/edit/save/delete your own checklist items.
  - AutoAttack Editor - Create/edit/save/delete the AutoAttack Lists
    that are used to drive the automated multiple-request capabilities
    on the HTTP Requests page.
  - Store/Restore - Temporarily hold and retrieve textarea and text
    field contents.
  - Save/Load State - Allows you to save CAL9000 textarea and text field
    contents and reload them when you are ready to resume testing.
  - Selected Text Processing - Allows you to process selected text
    inside of a textarea instead of the entire contents.

## Downloads

LATEST RELEASE - Version 2.0 released November 16, 2006. See the [OWASP
CAL9000 Project Roadmap](OWASP_CAL9000_Project_Roadmap "wikilink") for
release notes.

  - The latest release has been incorporated into the [OWASP LiveCD
    project](:Category:OWASP_Live_CD_Project "wikilink")
  - Click
    [here](http://owasp-code-central.googlecode.com/svn/trunk/labs/cal9000/)
    to view the CAL9000 source code.

## Project Contributors

Chris Loomis wrote the CAL9000 tool and currently leads the project. Any
and all questions, comments or suggestions are welcome and may be
directed [here](mailto:cal9000tool@mac.com) or submitted via the
[mailing list](http://lists.owasp.org/mailman/listinfo/owasp-cal9000).

Thanks to everyone who has emailed me their comments and great
suggestions for enhancing CAL9000. Keep the ideas coming\! Special
thanks to Achim Hoffmann for his significant contributions of code and
time to the project.

**Geeze, Really helpful stuff.**

## Feedback and Participation:

We hope that you find the OWASP CAL9000 Project useful. Please
contribute to the Project by volunteering for one of the Tasks and/or
sending your comments, questions and suggestions to owasp@owasp.org. To
join the OWASP CAL9000 Project mailing list or to view the archives,
please visit the [subscription
page](http://lists.owasp.org/mailman/listinfo/owasp-cal9000).

## Roadmap

Please refer to the [OWASP CAL9000 Project
Roadmap](OWASP_CAL9000_Project_Roadmap "wikilink") for current tasks.

[CAL9000 Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Download](Category:OWASP_Download "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")