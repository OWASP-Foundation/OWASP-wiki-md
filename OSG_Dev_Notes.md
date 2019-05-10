Back to [OWASP_SiteGenerator](OWASP_SiteGenerator "wikilink") main page

## To Do

  - Add as many examples of vulnerablilties as possible
  - Add different types of Navigation attacks.
  - Create a better way to do navigation then what there is now. The
    things that need to be accomplished are:
      - Scalability
      - Be able to create different types of navigation (flash, html
        \[different layouts\], etc..)
      - Allow users to customize the look and feel of the generated
        website

## Hacme Bank conversion

The conversion of Hacme Bank to OSG will introduce a number of new
vulnerabilties together the 1st example on a semi-real website
implemtent in OSG.

All (or most) of the latest version of Hacme Bank v2.0 (which I (Dinis)
wrote most of) is implemented in ascx controls and in webservices.

The first step might be to do a direct conversion of Hacmebank aspx and
asmx pages so that there is just about no code rewrite. That said, it
might be better to create a separate VS project just for this
conversion.

Since the installation of the database will also need to be done, I am
starting to think that it might be better to build this an a OSG Module
(or something similar). I.e. not part of the original install, but
something that can be easily added (by clicking in one button)

## Proposed Architecture

For future development the following idea is proposed. Create an
interface that is used for all vulnerabilities. When a user selects a
vulnerability they will have the option how they wish it to be
implemented (web service, normal page, etc...) they can chose one or
more options for the implementation.

Each interface will have to be able to tell the front end what form
fields it needs and also an area to handle the request back.

The reason for doing this is so that we only have to code one
vulnerability and use it in many different places easier.

**Downsides**

  - Potentially to complex for the payoff.
  - There could be a better way to do it while still following the [DRY
    principle](http://en.wikipedia.org/wiki/Don't_repeat_yourself).

\[Dinis Comments on the above\]

The idea of a single interface for all vulnerabilities is a good one.
The key is not to make it mandatory (i.e. has to be used for ALL
vulnerabilties). I still want for 10m vulnerability development where
the creator only needs to create an aspx or jsp page with the example of
the vulnerability.

That said, having reusable blocks (ala Metasploit) sounds like a great
idea.

Looking forward:

  - a major development that we will need to do is to run the
    vulnerabilities in Partial trust (so that we can easily accept third
    party submissions).
  - Auto updates for vulnerability signatures and for new OSG xml
    websites (so that it is easy to update the installed OSG)
  - Auto creation of websites based on live websites (using a web spider
    to craw the website and download the required files). Here is where
    the idea of the 'vulnerability modules' would came in handy since
    one could try to semi-automatically add the vulnerabilities to these
    websites

## Integration with WebGoat and other Web Technologies

The idea here is to be able to use Site Generator's capability to create
dynamic websites (based on XML files) with the vulnerabilities developed
for Web Goat

Basically what I want is to be able to use Web Goat's vulnerabilities in
OSG (OWASP Site Generator), which leverages the work done by WebGoat
developers and exposes OSG users to a wider set of issues.

Since the idea here is to reuse code, the Web Goat OSG pages will need
to be served from an Apache server. So what needs to be done for this to
work is for somebody to write an Java/Apache equivalent to the C\#
Httpmodule/IIS that is used on the current OSG vulnerabilities

This component is quite simple since all that is basically doing (at
this stage) is receiving all requests made to a particular website (lets
say <http://sitegenerator/websiteA/pageb.jsp> ) and going to OSG (via
TCP) and asking "what page does this request maps to?". OSG goes to the
current loaded XML file and if there is a match it says: "that page maps
to 'vulnerabilityDatabase\\SQLInjectionExample\\BlindSQLInjection.jsp").
with that information the apache server (in this example) will load that
jsp page and send it to the client (without rewiring the URL (which is
what creates the illusion of virtual OSG websites)).

Since the current WebGoat pages are designed for lessons, I expect to be
some tweaking on its code , but the idea here is to keep the development
of integrating these two projects to the minimum.