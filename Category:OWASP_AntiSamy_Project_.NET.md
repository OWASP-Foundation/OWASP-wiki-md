## What is AntiSamy .NET?

The OWASP AntiSamy .NET project is a few things. Technically, it is an
API for ensuring user-supplied HTML/CSS is in compliance within an
application's rules. Another way of saying that could be: It's an API
that helps you make sure that clients don't supply malicious cargo code
in the HTML they supply for their profile, comments, etc. that gets
persisted on the server. The term malicious code in terms of web
applications is usually regarded only as JavaScript. Cascading
Stylesheets are only considered malicious when they invoke the
JavaScript engine. However, there are many situations where "normal"
HTML and CSS can be used in a malicious manner.

Philosophically, AntiSamy .NET is a departure from all contemporary
security mechanisms. Generally, the security mechanism and user have a
communication that is virtually one way, for good reason. Letting the
potential attacker know details about the validation is considered
unwise as it allows the attacker to "learn" and "recon" the mechanism
for weaknesses. These types of information leaks can also hurt in ways
you don't expect. A login mechanism that tells the user, "Username
invalid" leaks the fact that a user by that name does not exist. A user
could use a dictionary or phone book or both to remotely come up with a
list of valid usernames. Using this information, an attacker could
launch a brute force attack or massive account lock denial-of-service.
So, we get that.

Unfortunately, that's just not very usable in this situation. Typical
Internet users are largely ineffective when it comes to writing
HTML/CSS, so where do they get their HTML from? Usually they copy it
from somewhere out on the web. Simply rejecting their input without any
clue as to why is jolting and annoying. Annoyed users go somewhere else
to do their social networking.

Socioeconomically, AntiSamy .NET is a have-not enabler. Private
companies like Google, MySpace, eBay, etc. have come up with proprietary
solutions for solving this problem. This introduces two problems. One is
that proprietary solutions are not usually all that good, and even if
they are, well - naturally they're reluctant to share this hard-earned
IP for free. Fortunately, we just don't care. We don't see any reason
why only these private companies should have this functionality, so we
are releasing this for free.

The [OWASP licensing
policy](http://www.owasp.org/index.php/OWASP_Licenses) (further
explained in the [membership
FAQ](http://www.owasp.org/index.php/Membership)) allows OWASP projects
to be released under any [approved open source
license](http://www.opensource.org/licenses/alphabetical). Under these
guidelines, AntiSamy .NET is distributed under a [BSD
license](http://www.opensource.org/licenses/bsd-license.php).

## Getting Started

There's 4 steps in the process of integrating AntiSamy. Each step is
detailed in the next section, but the high level overview follows:

1.  Download AntiSamy from its home on Google Code
2.  Choose one of the standard policy files that matches as close to the
    functionality you need:
      - antisamy-slashdot.xml
      - (more to come in the near future)
3.  Tailor the policy file according to your site's rules
4.  Call the API from the code

### Downloading

Currently, you can download the code using SVN from [AntiSamy .NET
Google Code
SVN](http://code.google.com/p/owaspantisamy/source/browse/#svn/trunk/dotNet)

In the future the source code and the compiled .dll can be found at
[Google Code](http://code.google.com/p/owaspantisamy/downloads/list)

### Installing

There is no installation needed to get AntiSamy .NET to run. Simply
reference the .dll in your code, make sure the dependencies are present,
and you are good to go.

Currently, there is only one dependency, HtmlAgilityPack.dll. To run the
unit tests, you will also need:

1.  nunit.core.dll
2.  nunit.core.interfaces.dll
3.  nunit.framework.dll

### Tailoring the policy file

Smaller organizations may want to deploy AntiSamy in a default
configuration, but it's equally likely that a site may want to have
strict, business-driven rules for what users can allow. The discussion
that decides the tailoring should also consider attack surface - which
grows in relative proportion to the policy file.

### Running

Using AntiSamy is abnormally easy. Here is an example of invoking
AntiSamy with a policy file:

`       AntiSamy _as = new AntiSamy();`
`       string filename = Server.MapPath("./properties/antisamy-slashdot.xml");`
`       Policy policy = Policy.getInstance(filename);`
`       CleanResults results = _as.scan(txtInput.Text, policy);`

And here is an example of using both the clean HTML and the error
messages:

`       lblOutput.Text = results.getCleanHTML();`
`       string s = "";`
`       for (int i = 0; i < results.getErrorMessages().Count; i++)`
`       {`
`           s += results.getErrorMessages()[i].ToString() + "`

";

`       }`
`       lblErrors.Text = s;`

## Limitations

No CSS support has been included yet in AntiSamy .NET. It will be added
hopefully within the next few months. With the default stylesheet, style
tags are not allowed and are stripped out, as is the style attribute.

**Update 03/15/2009**: CSS support has been implemented in the latest
revision (r95) of AntiSamy.NET, and can be checked out from the SVN.

## Contacting us

There are two ways of getting information on AntiSamy. The mailing list,
and contacting the project lead directly.

### OWASP AntiSamy mailing list

The first is the mailing list which is located at
<https://lists.owasp.org/mailman/listinfo/owasp-antisamy>. The list was
previously private and the archives have been cleared with the release
of version 1.0. We encourage all prospective and current users and bored
attackers to join in the conversation. We're happy to brainstorm attack
scenarios, discuss regular expressions and help with integration.

### Emailing the project lead

For content which is not appropriate for the public mailing list, you
can alternatively contact Jerry Hoff, at jerry@owasp.org

### Issue tracking

Visit the [Google Code issue
tracker](http://code.google.com/p/owaspantisamy/issues/list)

Visit the Google Code issue tracker

[Category:OWASP_AntiSamy_Project](Category:OWASP_AntiSamy_Project "wikilink")
[AntiSamy Project .NET](Category:OWASP_Project "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Beta
Quality Tool](Category:OWASP_Beta_Quality_Tool "wikilink")