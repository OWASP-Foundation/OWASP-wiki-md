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

# Main

The goal of this project is to build a secure applications framework
based off of JAVA and .NET architectures but written in javascript
utilizing DOM and json as its foundation. This will allow JAVA and .NET
programmers the ability to use their current programming methodologies
via javascript .js files. See the Roadmap OWASP Focus Roadmap for more
information on our plans.

I am sorry I have not been diligent on the project. As I am just one
person and still five kids and a wife at home they have taken a bit of
my time. I am hoping to have a little more time this year to finish this
up and add some stuff to it.

## Web Security Overview

While Java and .NET contain many security technologies for back-end
development, it has not been so easy for back-end programmers to produce
flexible front-end application without security vulnerabilities. Most
application security vulnerabilities apply to developers not being able
to code the front-end the same as the back-end with consistent coding
methodologies. Notable this is because they are using different API
frameworks for coding back-end (JAVA) verses front-end (JavaScript
json/dom).

There are a lot of articles with tons of information regarding
JavaScript and web UI programming
[vulnerabilities](:Category:Vulnerability "wikilink") here at OWASP,
however, this project is intended to provide a set of client side API's
familiar to JAVA and .NET programmers along with built in OWASP best
practices. This will enable them to write more secure code with little
or no vulnerabilities.

# Resources

<tbd>

# Roadmap

The OWASP Focus overall goal is to...

1.  Create a core structure of how interface components will be built.
    (done)
2.  Create an accessibility API for allowing other technologies
    interactive capabilities. (done)
3.  Create a way to organize these APIs for various categories such as
    look-and-feel, events and so on. (done)
4.  Create documentation on how to use the APIs
5.  Create the basic frame to simulate a .java or .cs where you can use
    a sudo class structure for coding
6.  Create a basic layered pane structure for the content pane, menu
    bar, and glass pane.

# Current Tasks

  - Call for volunteers - Join the [mailing
    list](http://lists.owasp.org/mailman/listinfo/owasp_focus) and get
    started\!

# Ideas

Please submit your high level ideas or what you would like to see added
to this project for future releases.

# Installation and configuration notes

This should work in any web server so it should be easy to get up and
running.

  - After you have downloaded the latest code you should be able to
    explode the jar file and place it in your web container.
  - You can either use the index.html or copy and paste the contents
    from the provided index.html. (Note if you are not going to use DWR
    you can remove the following:

<script language="javascript1.2" type="text/javascript" src="/dwr/engine.js">

</script>

<script language="javascript1.2" type="text/javascript" src="/dwr/util.js">

</script>

  - It is important to note that you the index.html is only used as a
    place holder for the web site. It only has limited use for things
    such as DWR.
  - All other third party applications we will put in the Includes.js
    file under generic.3rdParty.

[Category:OWASP Project](Category:OWASP_Project "wikilink")