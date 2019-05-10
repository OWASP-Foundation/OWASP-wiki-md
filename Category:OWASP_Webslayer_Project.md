[Click here to return to OWASP Projects
page.](:Category:OWASP_Project "wikilink")
[Click here to see (& edit, if wanted) the
template.](:Project_Information:template_Webslayer_Project "wikilink")

## Overview

WebSlayer is a tool designed for brute forcing Web Applications, it can
be used to discover not linked resources (directories, servlets,
scripts, etc), brute force GET and POST parameters, brute force Forms
parameters (User/Password), Fuzzing, etc. The tools has a payload
generator and a easy and powerful results analyzer to aid the tester in
all the brute force tests.

It's possible to perform attacks like:

  - Predictable resource locator (File and directories discovery)
  - Login forms brute force
  - Session brute force
  - Parameters brute force
  - Parameter fuzzing and Injection (XSS, SQL, etc)
  - Basic and Ntml brute forcing

## Features

Some features are:

  - Encodings: 15 encodings supported
  - All parameters attack: the tool will inject the payload in every
    parameter (Headers, Get, Post)
  - Authentication: Webslayer supports Ntml and Basic authentication,
    also you can brute force the authentication
  - Multiple payloads: you can use 2 paylods in different parts
  - Proxy support (authentication supported)
  - Live filters: You can change the filters as the attack is taking
    place
  - Multiple threads: You can set how many threads to use in the attack
  - Session import/export: Allows you to save the session and to
    continue working with the results
  - Integrated web browser: a full fledge webkit browser is included to
    analyze the results
  - Predefined dictionaries for predictable resource location, based on
    known servers (Thanks to Dark Raver, www.open-labs.org)
  - Payload Generator (custom payload generator)
  - Time delay between requests
  - Attack balancing across multiple proxies

### For Resource Location prediction

  - Recursion: When discovering directories, you can set how deep to go
  - Non standard code error checking: Webslayer will detect NoN Standard
    Code, to avoid presenting useless results
  - Extensions: You can add a list of file extensions to a dictionary

## Results analysis

The power of Webslayer resides in the way you can work with the results,
for every attack you will have all the responses, and for each ; request
you will have:

  - Html results
  - Source code
  - Headers
  - Web browser view (it will replay the request via the browser)

Multiple filters for improving the performance and for producing better
results for the analyst

  - Return Code
  - Characters length
  - Words length
  - Lines length
  - MD5
  - Regular expression

Webslayer will maintain all the attacks in the session so you can work
with them, compare, check later, etc.

![Image:Webslayer-analysis.jpg](Webslayer-analysis.jpg
"Image:Webslayer-analysis.jpg")

## Payload Generator

Another interesting feature of WebSlayer is the Payload Generator, with
this tool you can create your custom payloads, for all your needs. It
has some basic functions like:

  - Files: You can load dictionaries and encode the content.
  - Numeric Ranges: Allow the creation of a numeric payload given a
    chosen range. Also allow to use a fixed width. Eg: "01","02",..,"09"
  - Block: You can create characters block, given a string or set of
    characters. Eg: "A" "AA" AAA" "AAAA"
  - Permutation: Given a charset and a width it will create all
    possibles permutations. Eg: "ABC", "ACB", "BAC" ..., "CBA"
  - Credit Cards: You can create well formed credit card numbers for
    testing shopping carts, and payment modules
  - Usernames: Given some names, it will create all the possibles
    combinations used in account naming patterns. Eg: John Doe:
    "j.doe","john.doe","johndoe", etc.

After you have some Generators, you can concatenate and create your
final Payload, in the screenshot we created a Permutation of "abcaeiou"
with a width of 5 characters, and for the final payload we concatenated
the word "-owasp08" to the generator. The pattern to create the Payload
is: \[@PPerm00@\]-owasp08 Yo can drag'n'drop the temporal generator, to
the Payload creator pattern:

![Image:Webslayer-payload.jpg](Webslayer-payload.jpg
"Image:Webslayer-payload.jpg")

## Getting Started

### Downloading

At the moment WebSlayer is available in google code subversion:

svn checkout <http://webslayer.googlecode.com/svn/trunk/>
webslayer-read-only

Grab the latest version from here:
<http://code.google.com/p/webslayer/downloads/list>

### Installing

It works fine with the OWASP LIVE CD, and Backtrack R2, just make sure
you install:

python-qt4 python-pycurl

### Launching a basic attack

First of all, you must understand that the tool is based in replacing
the Keyword "FUZZ" or "FUZ2Z" by the payload that you have chosen.

So lets start using the application for discovering directories in a
website:

  - 1- In the Attack tab, insert the website URL that you want to brute
    force, with the keyword FUZZ in the end so WebSlayer will insert the
    content of the payload in that position. Eg:

<!-- end list -->

    http://www.mysite.com/FUZZ

  - 2- Next we are going to choose the payload type, we will leave
    "Dictionary", and we are going to choose a dictionary file, in this
    case i recommend to use the file "common.txt", which is located in
    the wordlists folder.

<!-- end list -->

  - 3- Now click the "Start attack" button

## Future Developments

We are working on the new release of WebSlayer, which will have a
complete engine redesign, and some changes in the GUI.

Also we are working in:

  - Adding more generators in the Payload Generator
  - The possibility to have more than 2 payloads
  - Changing the payload keyword convention (instead of ussing FUZZ, we
    will allow the use of @mypayload@)
  - Improving the logs
  - Multiple target URLS, ip range support for massive attacks
  - Responses diffing
  - Check for backups of detected files (.bak,.old,.txt,etc)

Also we are working in the release of packages for Linux and OS X

## Contacting us

There are two ways of getting information on WebSlayer. The mailing
list, and contacting the project leader directly.

Mailing list:
<https://lists.owasp.org/mailman/listinfo/owasp-webslayer-project>

For content which is not appropriate for the public mailing list, you
can alternatively contact Christian Martorella, at \[cmartorella\] at
the \[edge-security.com\]

## FAQ's

  - a) Once a panel is detached how can i attach it again?

`      You can attach the panel again by double clicking on the title bar`

## Project Contributors

The WebSlayer project is run by Christian Martorella and Carlos del Ojo
from Edge-Security

[Webslayer Project](Category:OWASP_Project "wikilink")