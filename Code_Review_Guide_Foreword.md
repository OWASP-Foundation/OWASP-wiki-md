## Foreword by [Jeff Williams](User:Jeff_Williams "wikilink"), OWASP Chair

Many organizations have realized that their code is not as secure as
they may have thought. Now they're starting the difficult work of
verifying the security of their applications.

There are four basic techniques for analyzing the security of a software
application - automated scanning, manual penetration testing, static
analysis, and manual code review. This OWASP Guide is focused on the
last of these techniques. Of course, all of these techniques have their
strengths, weaknesses, sweet spots, and blind spots. Arguments about
which technique is the best are like arguing whether a hammer or saw is
more valuable when building a house. If you try to build a house with
just a hammer, you'll do a terrible job. More important than the tool is
probably the person holding the hammer anyway.

The OWASP guides are intended to teach you how to use these techniques.
But the fact that they are separate shouldn't be an indicator that they
should be used alone. The Development Guide shows your project how to
architect and build a secure application, this Code Review Guide tells
you how to verify the security of your application's source code, and
the Testing Guide shows you how to verify the security of your running
application.

Security moves too fast for traditional books to be of much use. But
OWASP's collaborative environment allows us to keep up to date. There
are hundreds of contributors to the OWASP Guides, and we make over a
thousand updates to our materials every month. We're committed to making
high quality application security materials available to everyone. It's
the only way we'll ever make any real progress on application security
as a software community.

## Why Code Review?

I've been performing security code reviews (along with the other
techniques) since 1998, and I've found thousands of serious
vulnerabilities. In my experience, design documentation, code comments,
and even developers themselves are often misleading. The code doesn't
lie. Actually, the code is your only advantage over the hackers. Don't
give up this advantage and rely only on external penetration testing.
Use the code.

Despite the many claims that code review is too expensive or time
consuming, there is no question that it is the **fastest** and **most
accurate** way to find and diagnose many security problems. There are
also dozens of serious security problems that simply can't be found any
other way. I can't emphasize the cost-effectiveness of security code
review enough. Consider which of the approaches will identify the
largest amount of the **most significant** security issues in your
application, and security code review quickly becomes the obvious
choice. This applies no matter what amount of money you can apply to the
challenge.

Every application is different; that's why I believe it's important to
to empower the individuals verifying security to use the most
cost-effective techniques available. One common pattern is to use
security code review to find a problem and penetration testing to prove
that it is exploitable. Another pattern is finding a potential issue
with penetration testing, and then verifying the issue by finding and
examining the code. I strongly believe that the "combined" approach is
the best choice for most applications.

## Getting Started

It's important to recognize that code is a rich expressive language that
can be used to build anything. Analyzing arbitrary code is a difficult
job that requires a lot of context. It's a lot like searching a legal
contract for loopholes. So while it may seem tempting to rely on an
automated tool that simply finds security holes, it's important to
realize that these tools are more like spell-checkers or
grammar-checkers. While important, they don't understand the context,
and miss many important security issues. Still, running tools is a great
way to gather data that you can use in your code review.

All you need to get started is a copy of the software baseline, a modern
IDE, and the ability to think about the ways security holes get created.
I strongly recommend that before you look at any code, you think hard
about what is most important to your application. Then you verify that
the security mechanisms are present, free from flaws, and properly used.
You'll trace through the control and data flows in the application,
thinking about what might go wrong.

## Call to Action

If you're building software, I strongly encourage you to get familiar
with the security guidance in this document. If you find errors, please
add a note to the discussion page or make the change yourself. You'll be
helping thousands of others who use this guide.

Please consider [joining us](Membership "wikilink") as an individual or
corporate member so that we can continue to produce materials like this
code review guide and all the other great projects at OWASP.

Thank you to all the past and future contributors to this guide, your
work will help to make applications worldwide more secure.

\-- [Jeff Williams](User:Jeff_Williams "wikilink"), OWASP Chair, October
17, 2007

__NOTOC__

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")