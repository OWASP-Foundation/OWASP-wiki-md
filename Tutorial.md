## Editing the OWASP Wiki

OWASP is built on the MediaWiki platform. Anyone can create an account
and make the OWASP wiki better. To create a new account, click on the
[create an account or log in](Special:Userlogin "wikilink") link at the
top-right of every page. When you make edits, please use the "preview"
feature to make sure your changes are final, and then don't forget to
save. Use the "edit summary" to describe what you did and why.

Writing OWASP wiki articles is a bit different from writing on a
standard word processor. Instead of a strict "what you see is what you
get" approach, wiki uses simple text codes for formatting. The approach
is similar to that used in writing HTML for web pages, but the codes are
simpler. The [MediaWiki
help](http://meta.wikimedia.org/wiki/Help:Contents) is a great place to
start learning about all the features available. Another option for you
to investigate is [OpenOffice](http://www.openoffice.org) as you can
edit pages and export them into MediaWiki format.

## Style guidelines

In general, we follow the [editing
guidelines](http://en.wikipedia.org/wiki/Wikipedia:Tutorial_%28Keep_in_mind%29)
of Wikipedia. You should ensure that your additions to OWASP reflect a
"Neutral Point of View" and a positive collaboration in the interest of
better application security. Also, please remember that OWASP is not the
right place for disclosure of actual vulnerabilities. The bugtraq or
full-disclosure mailing lists are appropriate venues for that sort of
thing.

## Content guidelines

OWASP is not a place to promote commercial products or services. We
strive to provide unbiased information that will enable organizations
and individuals to build and operate more secure applications.
Information about commercial products is allowed, but MUST follow these
guidelines. Violations of these policies should be reported to
<owasp@owasp.org>.

  - Product discussions must mention all comparable tools available
  - "Equal time" must be given to all tools discussed
  - Unsubstantiable claims will not be allowed
  - Discussions of products should include both good and bad
  - Representatives of product companies must disclose their affiliation

## Bold and italics

Bold and italics are created like this:

  - `''italics''` appears as *italics*. (2 apostrophes on both sides)
  - `'''bold'''` appears as **bold**. (3 apostrophes on both sides)

## Headings and subheadings

Headings and subheadings are an easy way to improve the organization of
an article. If you can see two or more distinct topics being discussed,
you can break up the article by inserting a heading for each section.

Headings can be created like this:

  - `==Top level heading==` (2 equals signs)
  - `===Subheading===` (3 equals signs)
  - `====Another level down====` (4 equals signs)

## Discussion pages

There are "discussion" pages (also known as "talk" pages) associated
with every article at OWASP. You can leave questions, comments, or ideas
on these pages for other authors to review. These pages are a good place
to propose ideas or discuss possible approaches to problems. You should
"sign" your comments by adding four tilde characters (\~\~\~\~) after
your comment. Use section headings for different topic areas.

See [Wiki markup
examples](http://meta.wikimedia.org/wiki/Help:Wiki_markup_examples) for
more examples

## Internal links

One thing that makes the OWASP wiki useful (and highly habit-forming) is
extensive cross-listing by internal links. These easily-created links
allow users to access information related to the article they're
reading.

The easiest way to learn when to link is to look at OWASP (or Wikipedia)
articles for examples. If you're trying to decide whether to make a link
or not, ask yourself "If I were reading this article, would the link be
useful to me?"

When you want to make a link to another OWASP page (called a <em>wiki
link</em>) you have to put it in double square brackets, like this:

  -
    `[[Threats|Threats]]`

If you want to use words other than the article title as the text of the
link, you can do so by adding the "|" divider followed by the
alternative name. For example, if you wanted to make a link to the [Main
Page](Main_Page "wikilink"), but wanted it to say "OWASP home" you would
write it as such:

  -
    `To view the article, [[Main_Page|OWASP home]]...`

## Images and files

You can upload certain types of documents using the **Upload File**
option under **Toolbox** in the lower lefthand part of the linkbar at
the left side of any OWASP page. But you need to be logged in to see
this option. We allow common image formats, Word documents, PowerPoint
presentations, and PDF files. Choose your filename carefully, as you'll
use that to reference the document from the rest of the site. Note that
MediaWiki uses the term "image" to mean any file.

Use this syntax to reference files from your page ...

  - Single click to get "image" page:

`     [[Image:filename.ppt|PUT YOUR TITLE HERE]]`

  - Single click to show file:

`     [http://www.owasp.org/index.php/Image:filename.ppt PUT YOUR TITLE HERE]`

This is the [Direct Upload Link](Special:Upload "wikilink") in the event
the **Upload File** option can't be found.

## Categories

OWASP makes extensive use of categories. Categories are used to "tag"
articles in OWASP so that people can find them. An article can be in
lots of categories at the same time. For example, an article discussing
a flaw in the Java sandbox might be in the [:Category:OWASP Java
Project](:Category:OWASP_Java_Project "wikilink"),
[:Category:Vulnerability](:Category:Vulnerability "wikilink"), and
[:Category:Access Control](:Category:Access_Control "wikilink")
categories at the same time.

To add a category to an article, just add
\[\[Category:XXX|Category:XXX\]\] to the end of the article, replacing
the XXX with the name of the appropriate category.

To reference a Category page, simply put a colon (**:**) at the
beginning of the "Category" tag, like this:

  -
    `[[:Category:Principles|:Category:Principles]]`

**It is very important to put in the correct categories so that other
people can easily find your work.** The best way to find which
categories to put in is to look at pages on similar subjects, and check
which categories they use. For example if you write an article about a
type of tree, you may look at an article on another type of tree to see
which categories could be appropriate.

## Linking a User Page

User pages allows community members to provide a bit more information
about themselves. It's easy to link to a user page whenever mentioning
someone on a wiki page.
Here's the format: \[\[User:\<wiki_username\>|FirstName LastName\]\]
Here is an example of the syntax: \[\[User:MichaelCoates|Michael
Coates\]\]