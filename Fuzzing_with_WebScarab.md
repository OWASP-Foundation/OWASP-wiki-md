This document is intended to explain how to use the WebScarab Fuzzer
plugin.

I assume that you are familiar with the basic functionality of
WebScarab, and have managed to use it as a proxy to view and intercept
some conversations already. If not, I suggest reading the ["Getting
Started"](WebScarab_Getting_Started "wikilink") document first.

## Overview

The Fuzzer plugin is intended to simplify or automate repetitive testing
of a web site. In essence, what the fuzzer does is sequentially try each
one of a list of values replacing some user-specified parameters in a
request that is then sent to the server. The response is then saved into
the Summary, where it can be manually reviewed.

The first thing to understand is how the Fuzzer defines a parameter. A
parameter is a portion of the request that is considered when creating
the response:

  - A parameter may be found as part of the path, as is commonly seen in
    a Wiki. For example it is common to see something like
    "<http://example.com/index.php/Some_Topic>". In this case, the
    string "Some_Topic" is a "Path parameter"

<!-- end list -->

  - A parameter may also be found as a "fragment", appended to the path
    with a semi-colon, before the query portion of the URL. For example,
    it is common to find session ids in a URL, like
    "<http://example.com/index.php;PHPSESSIONID=some_hex_string>"

<!-- end list -->

  - A parameter can commonly be found as an URL Query parameter,
    collected as Name/Value pairs following a "?" in the URL, separated
    by ampersands, as in
    "<http://example.com/index.php?title=Some_Topic&action=edit>", which
    illustrates 2 query parameters: "title" and "action"

<!-- end list -->

  - A parameter may also be found in a Cookie. Of course, cookies are
    most commonly used to track session state, and fuzzing a cookie is
    often pointless. However, if data is stored in the cookie, fuzzing
    it may give promising results, as it is a less commonly tested
    aspect of a site.

<!-- end list -->

  - A parameter may also be found in the body/content portion of a
    request, typically when the request is sent as a POST. Parameters
    are most commonly formatted using the same scheme as for encoding
    URL Query parameters. Of course, POST parameters may be formatted
    using any scheme supported by the server. WebScarab can currently
    only support POST's with a Content-Type of
    "application/x-www-form-urlencoded".

## Using the fuzzer

The fuzzer interface allows a knowledgeable user to construct a new
request, specifying the method, basic URL (excluding any path
parameters, fragments or query parameters), the request version, any
request headers, and the required parameters. Unfortunately, this is
rather a tedious and error-prone way of constructing a request to fuzz.

Fortunately, there is a much easier way\! Once you have used the proxy
for a bit, go to the Summary View, and find a conversation that has
parameters that you would like to fuzz. Then right-click on that
conversation, and select "Use as fuzz template". This will identify all
of the parameters in the request (other than path parameters, which are
not possible to identify automatically), and copy all of the relevant
information to the Fuzzer plugin interface. If you wish to, you can make
any modifications you want at this point, for example, adding or
deleting some headers, adding or removing parameters, etc.

Once you have defined the basic structure of the request, you need to
define the fuzz sources. A "fuzz source" is a list of alternative inputs
to be used a values for one or more parameters. In most cases, you will
create a file containing one value per line. If you installed WebScarab
using the "installer" version, you should also find two files "xss.txt"
and "sql.txt" in the directory in which you installed it. These two
files contain a collection of Cross Site Scripting and Sql Injection
strings respectively, which may trigger errors in the application you
are testing.

Define available fuzz sources by selecting the "Sources" button in the
Fuzzer interface. In the dialog, type in a description of the Fuzz
source. e.g. for the xss.txt file, type XSS (case is not important).
Then use the "browse" button to locate the file containing the strings
you wish to use, or type the filename in the "File" field. Once the file
has been chosen, click "Add". WebScarab will read the file, and add each
item to the list identified by the description you supplied. You can
check to see if they were properly read in by clicking on the item in
the list on the left hand side. You should see the fuzz strings
displayed 1 per line, and the "Items" label should show how many strings
were read in.

You can also define a list of strings to use, using a reduced regular
expression syntax. By reduced, I mean that the syntax elements that
allow for an infinitely large set to be defined is not permitted. For
example, the "." character defines 65536 possible characters, and is
disallowed. Similarly, the \* and + operators allow an indefinite number
of characters, and are also disallowed. Finally, the character count
syntax that allows a variable number of characters "{3,5}" is also
disallowed. This is useful if you wish to attempt to brute force
something like a document identifier, that obeys a regular pattern.

Once you have defined your fuzz sources, close the dialog, and return to
the main Fuzzer interface.

It would probably be a good idea to explain what each of the columns in
the "Parameters" table represent at this point:

  - The Location column represents where the parameter is found. The
    location can be one of "Path", "Fragment", "Query", "Cookie" or
    "Body", as explained above.

<!-- end list -->

  - The Name column represents the name of the parameter.

<!-- end list -->

  - The Value column is for the default value of that parameter, if that
    parameter is not being fuzzed.

<!-- end list -->

  - The Priority column allows the user to control how the various fuzz
    sources increment. Fuzz sources at the same priority increment in
    lock step. Fuzz sources at different priorities increment
    sequentially. For example, if you had a list of known usernames and
    matching passwords, you would use a username source and a password
    source with the same priority. However, if you wanted to try each of
    the usernames with each of the passwords, you would use sources with
    different priorities.

<!-- end list -->

  - The Fuzz Source column allows the user to control which parameters
    will be fuzzed, and which list of fuzz strings will be used.

Now you can instruct the Fuzzer on which fuzz sources to use for each
parameter. The "Fuzz Source" column is editable using a combo box, and
you can selected from the defined fuzz sources, or an empty item if you
do not want to fuzz that parameter.

As you change the various parameters to be fuzzed, and possibly modify
the priorities of the parameters, you should notice the "Total Requests"
field updating. If your fuzzed parameters are all at the same priority,
the "Total Requests" field will reflect the size of the smallest Fuzz
Source. If the fuzzed parameters are at different priorities, the "Total
Requests" field will show the product of the sizes of the various Fuzz
Sources.

## Running the fuzzer

When you hit the Start button, you'll see the "Current Request" field
incrementing, and conversations appearing in the table in the bottom
half of the screen, until the "Current Request" field shows one less
than the "Total Requests" field. (Yes, this is a bug that should be
fixed.) If there are any errors detected while executing the fuzzer, the
fuzzer plugin will pause. As long as you do not make any changes to the
fuzzer setup, you can resume fuzzing where you left off. (This may or
may not be a good idea, depending on the nature of the error)

Once the fuzzer is finished, you can review the resulting conversations
by double-clicking on the rows in the Conversation Table in the lower
half of the screen, and stepping through the list. Alternatively, you
can review them from the Summary pane, at any time. Note that rerunning
the fuzzer will clear the table in the Fuzzer, but will not change the
conversations already in the Summary.

## Limitations

The Fuzzer is not able to fuzz "compound requests". For example, when
submitting values to a function results in a frameset description, and
the real interesting result shows up in one of the child frames,
WebScarab will not try to retrieve the child frame. For more complex
fuzzing, I'd suggest investigating the Scripting plugin.

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink")