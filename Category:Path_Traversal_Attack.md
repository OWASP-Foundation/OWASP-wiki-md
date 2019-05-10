## Description

This category of attacks exploit various [path
vulnerabilities](:Category:Path_Vulnerability "wikilink") to access
files or directories that are not intended to be accessed. This attack
works on applications that take user input and use it in a "path" that
is used to access a filesystem. If the attacker includes special
characters that modify the meaning of the path, the application will
misbehave and may allow the attacker to access unauthorized resources.
This type of attack has been successful on web servers, application
servers, and custom code.

## Examples

The most basic Path Traversal attack uses the '../' special character
sequence to alter the location of the request. In an Operating System,
this special character combination notes to move down one directory. An
example of such an attack could look like the following:
<http://foo.com/>../../barfile

While the web server may stand up well to such an attack, another
approach is to target the application itself. Most commonly the use of
parameters being passed by the application can be exploited. Such data
can come from user input or application data being passed between pages.
Let's take for the following example into account:
<http://foo.com/bar.cgi?store=mystore.html>

We can observe from the above that bar.cgi takes a parameter to navigate
through the application; in this case, the store location is
mystore.html. We can use this knowledge to attempt the retrieval of
bar.cgi's source code by submitting:
<http://foo.com/bar.cgi?store=bar.cgi>

This can be taken a step further. By combining the two methods above one
may be able to retrieve server resident content using the application as
a means of accessing it. Keep in mind, the web server daemon (process)
runs as a user on the machine and as such the application has read
access to certain areas. Using the foobar store example URL above, let's
look at how we can grab a file from another location of the server:
<http://foo.com/bar.cgi?store=>../../secretfile.txt

## Categories

[Category:Attack](Category:Attack "wikilink")