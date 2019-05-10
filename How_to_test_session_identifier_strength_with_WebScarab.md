## Objective

To collect and examine a reasonably large sample of session identifiers,
to determine if they could be vulnerable to prediction, or brute force
attacks.

## Approach

Identify a request that generates a suitable session identifier. For
example, if the identifier is supplied in a cookie, look for responses
that include Set-Cookie headers, then use the request repeatedly to
obtain more session identifiers. We will then perform some analysis on
the resulting series of identifiers. The WebScarab SessionID analysis
plugin currently converts the session identifier into a large integer,
using a per-position base-conversion algorithm. I'll explain more about
the algorithm later, once we have collected some results.

## Collecting session identifiers

It is possible to collect session identifiers from both Set-Cookie
headers, as well as from within the body of the response. WebScarab will
collect all identifiers from all cookies if the radio button is set to
"Cookies". It is not necessary to provide a name for the session
identifier, as WebScarab will use the site name, path and cookie name to
construct a unique identifier. If you choose to extract session
identifiers from the body of the response, you have to give it a unique
name, and provide a regular expression that defines which part of the
response body is considered to be the identifier. This is typically done
by using ".\*" to indicate all characters leading up to some unique
surrounding text, followed by that unique text, then a pattern
surrounded by a regex group (e.g. "(....)" would take 4 characters),
finally followed by ".\*" again to indicate all characters to the end of
the body text.

For a more concrete example, let's suppose that the identifier is in a
URL query parameter in the body text, and the url parameter is called
"id". An example might look like:
<http://www.example.com/loggedin.aspx?id=>\<10 alphanumeric characters\>

A suitable regex might be: .\*loggedin.aspx\\?id=(.{10}).\*

In order to check that your regular expression is actually correctly
matching the text in the response, use the "Test" button to show what
would be extracted. The results of the test are not stored for later
use.

Once you are satisfied with your configuration, simply enter the number
of samples desired, and press "Go". If you decide to interrupt the
collection process, you can do so by requesting 0 samples, and pressing
"Fetch" again.

## Analysing the results

As mentioned earlier, WebScarab uses a per-position base-conversion
algorithm to convert a string into a number. What this really means is
that the string is converted to a number using the same approach that
one uses to convert a number of one base (e.g. hex - base 16) to another
(e.g. decimal - base 10). The major difference is that the base can
change for each position/index, according to what characters have
actually been observed in that position throughout the sampled series.
This means that if you have a constant character in the middle of your
series, the base ends up being "1", the only possible value in a base-1
number system is 0, and so the constant character plays no part in
actually calculating the numerical value of the total.

Here is a worked example, on a small scale.

Assuming we have the following session ids:

`AAAA`
`AAAC`
`ABAB`
`ABAD`

Starting from the left-most column (MSB), we have the following observed
character sets:

`1: "A"`
`2: "A", "B"`
`3: "A"`
`4: "A", "B", "C", "D"`

So, our bases are, in order (1,2,1,4).

Let's calculate the value of each id. In order to translate each
character to a number, we use its zero-based position in the sorted
character set:

`AAAA = 0 * (2*1*4) + 0 * (1*4) + 0 * (4) + 0 = 0`
`AAAC = 0 * (2*1*4) + 0 * (1*4) + 0 * (4) + 2 = 2`
`ABAB = 0 * (2*1*4) + 1 * (1*4) + 0 * (4) + 1 = 5`
`ABAD = 0 * (2*1*4) + 1 * (1*4) + 0 * (4) + 3 = 7`

## Looking at the graph

The calculated values are then plotted on a graph against time. The idea
is that the human eye is very good at visually identifying patterns,
which may not be obvious from a list of numbers. The most likely
patterns that you will see are lines or bands (possibly
interrupted/broken), or else points scattered all over the graph. The
first indicates predictability, while the second suggests randomness.

![WebScarabAnalysis-large.png](WebScarabAnalysis-large.png
"WebScarabAnalysis-large.png")

### Plotting the results in an external program

WebScarab can export the results in a comma delimited format suitable
for plotting with your favorite graphing program (e.g. Excel or
gnuplot). In some cases (e.g. for writing a formal report) you may find
plotting the results in a more full featured program looks better.

From the Analysis page, click the "Export" button. Save the output to a
file. Under Windows, you should probably go ahead and name the file .CSV
or .TXT. A couple example lines are shown below:

` 1162494041997,11826346672417325953,6c30d8130bc05b6ec381`
` 1162494042104,4008986413070164165,6c3053d2a0cb7e2a20c5`
` 1162494042224,11293771226654801443,6c30cf10801d38497e23`

Although it is useful to have the precision, the numbers are not in a
format most graphing programs can use. The problem is that the first
column, the timestamp, is not parseable by Excel. Worse than that, It's
not even a Unix timestamp. Traditional Unix timestamps are measured in
seconds since 00:00 January 1, 1970. This number, 1162494041997 for
example, is actually <i>milliseconds</i> since January 1, 1970.

Have no fear. In one line of perl, you can convert all the timestamps to
a format that Excel can grok. Something like: 11/02/2006 14:00:41.997,
which is what 1162494041997 really is.

Here's the one line of perl. It assumes the exported data from WebScarab
was saved to a file named JSESSIONID.txt:

` perl -pi -e 'use POSIX qw(strftime); s/^(\d+)/strftime("%m\/%d\/%Y %H:%M:%S", localtime($1\/1000)) . "." . ($1 % 1000)/e;' JSESSIONID.txt`

I didn't say it was a *short* line.

Here's an explanation of the key components to that line. You don't need
to know this in order to use this perl code. If you're wondering what it
does, however, this will help you understand.

<dl>

<dt>

<b>/^(\\d+)/</b>

<dd>

Match some digits beginning at the beginning of the line.

<dt>

<b>strftime("%m\\/%d\\/%Y %H:%M:%S",</b>

<dd>

This is the format for the time to come out. Notice a couple things: It
doesn't have the fraction of a second (that is done separately) and it
has backslashes to escape the forward slashes in the date. Otherwise
those forward slashes would confuse the regular expression parser.

<dt>

<b>localtime($1\\/1000)</b>

<dd>

This is where we take the number we found on the beginning of the line
and divide it by 1000. That way, we get Unix seconds, which `localtime`
likes.

<dt>

<b>. "." . ($1 % 1000)</b>

<dd>

Take the output of the `strftime()` call and append some stuff on the
end. Namely, a literal "." and then the milliseconds value from the
time.

That's it\! It's not easy stuff, but it is wonderfully effective.

The three lines above get turned into:

` 11/02/2006 14:00:41.997,11826346672417325953,6c30d8130bc05b6ec381`
` 11/02/2006 14:00:42.104,4008986413070164165,6c3053d2a0cb7e2a20c5`
` 11/02/2006 14:00:42.224,11293771226654801443,6c30cf10801d38497e23`

![WebScarabExcel.png](WebScarabExcel.png "WebScarabExcel.png")

If you're familiar with Excel, you'll realize that Excel can handle
those date formats just fine. Now you can plot the data in Excel, which
gives me a bit more control than WebScarab does directly.

### Caveats on Predictability and Randomness

Predictability and randomness are relative terms. If the algorithm
appears to be "predictable", but the key space that you'd have to check
is greater than about 100000 items, it is likely to be infeasible to
actually find a session belonging to someone else during that session's
lifetime. Obviously, this depends on your own CPU power, network
bandwidth, the target's CPU power and network bandwidth, the typical
lifetime of a session, and a bunch of other factors. Please look at the
scale of the numbers before deciding that a predictable identifier is a
realistic risk. It is possible for something to be "predictable" in the
strictest mathematical sense, but not exploitable in a practical sense.

One very important thing to note about the conversion algorithm is that
it works from right (Least Significant Bit) to left (Most Significant
Bit), much as one would expect from a numerical conversion. What this
means in practice is that if you have a session identifier that has some
sequential data at the left, and significant random data to the right,
the sequential data will appear to dominate the values, and will result
in a straight line graph. Again, check the scale of the numbers before
deciding that an identifier is predictable.

[Category:How To](Category:How_To "wikilink") [Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink") [Category:Session
Management](Category:Session_Management "wikilink") [Category:OWASP
Testing Project](Category:OWASP_Testing_Project "wikilink")