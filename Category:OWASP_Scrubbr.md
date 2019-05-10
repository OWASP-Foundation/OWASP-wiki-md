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

# What is Scrubbr?

Scrubbr is a BSD-licensed database scanning tool that checks numerous
database technologies for the presence of possible stored cross-site
scripting attacks. The tool was partially inspired by "Scrawlr", a
trimmed-down version of HP's WebInspect which was released for free
after the so-called "asprox" mass-SQL injection bot exploited hundreds
of thousands of insecure ASP sites.

In a similar vein, Aspect Security generously donated Scrubbr to OWASP
to help people get some visibility into their databases and check for
malicious data.

## What can Scrubbr do for me?

If you can tell Scrubbr how to access your database, it will search
through every field capable of holding strings in the database for
malicious code. If you want it to, it will search through every table,
every row, and every column. This will be very slow on large enterprise
databases, but its very useful to have assurance that there is no
malicious data anywhere in the system.

Scrubbr can detect input that doesn't match up with an AntiSamy policy
file. There is a subtle difference between "matching an AntiSamy policy"
and being "detected as an attack."

There are numerous tools out that \*detect\* XSS attacks in different
contexts better than AntiSamy. The most prominent and peer-reviewed are
NoScript (http://noscript.net) and PHPIDS
(http://php-ids.org/category/PHPIDS/). However, detection is not
strictly what AntiSamy does. AntiSamy checks if rich input that is
passed in is allowed according to a policy file.

Chances are that there is some input in your database that looks like
rich input how we in the web world think about it, but actually isn't.
For example, if someone writes the following in their profile comment:

"Hey, I sure am gonna miss seeing Sarah Palin on TV all the time <g>".

Obviously the user intended the <g> string to express a grin emotion,
but that unfortunately looks like rich input, and since AntiSamy uses a
whitelist for higher assurance, it will be flagged.

We are always looking to improve our engine, and we are working with the
PHPIDS group to possibly invoke their ruleset in order to provide less
false positives.

With all of that being said, AntiSamy does an excellent job in most
situations and will still detect the vast majority of stored XSS
attacks, depending on the injection context.

## What can't Scrubbr do for me?

Scrubbr can't find XSS vulnerabilities in your web application. It can
only detect data that doesn't follow your site's policy for input that
is in your database. If you don't have a policy for rich input, then
start with the Slashdot policy file and add what you think you need from
the other policy files. More information on policy files can be found on
the OWASP AntiSamy page:

<http://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project>

Once you have a policy in place, then you can enfoce it with Scrubbr.

# How do I get Scrubbr?

You can download the Scrubbr installer from the project's [Google Code
downloads page](http://code.google.com/p/owaspscrubbr/downloads/list).

# Contacting the Scrubbr group

If you would like to request a feature, let us know about a bug, or
provide a patch, please let us know on the Google Code issue tracker for
the project:

<http://code.google.com/p/owaspscrubbr/issues>

General questions can be e-mailed to the [Scrubbr mailing
list](https://lists.owasp.org/mailman/listinfo/owasp-scrubbr). If you
have a question about development, contact the [Scrubbr development
mailing
list](https://lists.owasp.org/mailman/listinfo/owasp-scrubbr-devel).

# Known issues

Scrubbr is a new open source project, and not surprisingly it has a few
issues that we are working to address. If you have an issue that's not
on this list, please add it to the issues list described in the previous
section.

## "The 'Fix' button is not working or causing an error"

Frankly, you'd have to be crazy to change production data with a tool
you didn't write yourself (and maybe even then). Trying to write a
cross-platform database tool that can read and write is also, a little
crazy. The database technologies differ in so many stupid ways, and we
*mostly* rely on JDBC to handle the interaction with the database. The
"Fix" button is provided as-is, but of course we would like to hear
about and fix your particular problem, and you can let us know about it
at the issue tracker.

The "Fix" button has been tested a fair amount on MS SQL Server and
MySQL with data types that commonly hold strings, including varchar(x),
nvarchar(x), text, ntext, and similar fields. The "Fix" button for
Oracle hasn't been tested heavily, and we expect issues when using it in
this environment.

Regardless of your database technology, if your user input strings are
in timestamp fields or something similarly bizarre, we unfortunately
can't help you fix it.

## "I installed Scrubbr to C:\\Program Files on Vista, and now the Uninstaller doesn't work"

Microsoft Vista uses Virtual Paths (like Java servlets) to accommodate
the divergence between UAC and Windows XP security, which makes
uninstalling a manual process when you install to C:\\Program Files.
This is why the installer defaults the value to C:\\Scrubbr on Windows.

When a user executes a setup executable (setup.exe, install.exe, etc.)
Vista will prompt you with a security dialog before it allows the setup
program to install files to a system directory like C:\\Program Files.
However, since Scrubbr uses \[izPack <http://izpack.org>\] as a
cross-platform installer, the setup executable is actually a
cross-platform JAR executable instead of an exe file. This does not trip
the necessary Windows Vista UAC prompt and therefore silently fails to
actually install to C:\\Program Files. However, since Vista knew that
this behavior would happen a lot, they compensated by redirecting the
installation to another path,
C:\\Users\\<your_username>\\AppData\\Local\\VirtualStore\\Program Files.
Therefore, when the Uninstaller runs, it tries to delete C:\\Program
Files\\Scrubbr, which doesn't exist, since it's unaware that Scrubbr has
been installed to a virtual directory.

This can be thought of as a bug in either Vista or in izPack, since
neither accounts for the other. However, izPack allows us to install to
many different platforms cleanly, so we don't think we're going to
switch. That being said, uninstalling on Vista when the Uninstall option
doesn't work is simple: 1. Open up Explorer 2. Navigate to
C:\\Users\\<your_username>\\AppData\\Local\\VirtualStore\\Program Files
3. Delete the Scrubbr directory 4. Confirm that Scrubbr is no longer in
your Start Menu or Program Files directory

Scrubbr has an extremely small footprint. It installs a few files into
Program Files and that is it. There are no user settings in your profile
directory or registry values or anything of the sort. Simply deleting
the directory makes it go away forever.

# Credits

Scrubbr was primarily developed by Arshan Dabirsiaghi
(arshan.dabirsiaghi@aspectsecurity.com) of Aspect Security with help
from Brandon DeVries (brd@jhu.edu). Other folks contributed in their own
ways, including:

  - Dave Wichers, COO, Aspect Security
  - Jeff Williams, CEO, Aspect Security
  - Nick Sanidas, Director of Assurance Services, Aspect Security
  - Mike Fauzy, Senior Application Security Engineer, Aspect Security
  - Marcin Wielgoszewski, Security Consultant, Founder
    TSSCI-Security.com

[Scrubbr Project](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink")