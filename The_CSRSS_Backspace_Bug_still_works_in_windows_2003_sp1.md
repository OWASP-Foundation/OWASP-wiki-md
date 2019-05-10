The bug described here [The CSRSS Backspace Bug in Windows
NT 4/NT 2000/NT
XP](http://homepages.tesco.net/%7EJ.deBoynePollard/FGA/csrss-backspace-bug.html)
and documented in this KB article: [A Program that Passes Invalid Screen
Size Parameters Causes an Access
Violation](http://support.microsoft.com/kb/311486) was reportetly fixed
in NT/2000/Xp but a variation of it still exists in Windows 2003 Sp1

Basicaly just compile this and you will get a 100% processor usage by
the compiled exploit and Csrss.exe

`#include <stdio.h>`
`int main(void)`
`{`
`while(1)`
`printf("\t\t\b\b\b\b\b\b");`
`return 0;`
`}`

Sadly, this seems to be another good example of Microsoft's disrespect
for people who tried to help them, here are some snippets from the
'Service fix' section of [The CSRSS Backspace Bug in Windows
NT 4/NT 2000/NT
XP](http://homepages.tesco.net/%7EJ.deBoynePollard/FGA/csrss-backspace-bug.html)

<i> "... **Service fix**

There [will not be further service packs for Windows
NT 4.](http://www.microsoft.com./ntserver/sp7.asp) This is a permanent
bug in Windows NT 4.

On 2002-03-23, almost five months since this bug became public knowledge
and this web page was published, I received an unconfirmed report from a
third party that a fixpack that includes a fix for this bug will be
released, and that a knowledgebase article covering it "will" be
written.

On 2002-08-01, nine and a half months since this bug became public
knowledge and this web page was published, Microsoft released the third
service pack for Windows NT 2000. With this service pack applied, it
appears to be impossible to reproduce this bug. However, neither the
change that causes this nor even the bug itself are listed anywhere in
either the Windows NT 2000 service pack documentation or in Microsoft's
KnowledgeBase. The problem does not officially exist, and is certainly
not officially solved. The worry here is that the fact that it is no
longer reproducable is coincidental, and (since Microsoft has not
recognised it to actually be a problem, and therefore will not include
it in any regression testing) liable to be reintroduced by subsequent
service packs.

On 2002-09-09, ten and a half months since this bug became public
knowledge and this web page was published, Microsoft released the first
service pack for Windows NT XP. As with the Windows NT 2000 service
pack, there is no official acknowledgement in the service pack
documentation either that the bug exists or that it has intentionally
been fixed by the service pack. I was unable myself to confirm that the
bug is indeed fixed by the service pack, and no-one else had yet
reported to me that it is.

On 2002-09-12, the same third party that reported the fixpack
information to me reported Microsoft as saying to him that it has "a KB
article that should be live soon" and that this will, when it appears,
be Microsoft KnowledgeBase article ID Q311486. I confirmed that no
article by that ID was currently available.

On 2002-09-24, Microsoft KnowledgeBase article ID Q311486, promised six
months ago, finally appeared. Its publication date is falsified to claim
that it appeared on 2001-10-26. It talks about programs that "pass
invalid screen size parameters" when the sample program code that it
gives for replicating the bug clearly contains nothing at all relating
to screen size parameters. And the explanation that it gives for the
actual cause of the problem is woefully incorrect. Were it not that it
has taken over eleven months for Microsoft to produce it, one might
think that this article was a very badly done rush job...."

Published 09 December 2005 10:06 by Dinis Cruz

## Email to MSRC

From: "Dinis Cruz" \<dinis@ddplus.net\> Sent: Tuesday, December 13, 2005
11:32 PM To: secure@microsoft.com Subject: The CSRSS Backspace Bug still
works in windows 2003 sp1

Dear MSRC

Please see this post The CSRSS Backspace Bug still works in windows 2003
sp1 for an issue that you should follow up and do more research.

Given the nature of this issue I think that there is a strong
possibility that this can be further exploited (note that csrss runs
under SYSTEM)

Best regards

Dinis Cruz

## Response from MSRC

From: "Microsoft Security Response Center" \<secure@microsoft.com\>
Sent: Wednesday, December 14, 2005 2:44 PM To: dinis@ddplus.co.uk
Subject: RE: The CSRSS Backspace Bug still works in windows 2003 sp1

Hello Dinis,

Thanks for your note. I have reopened the case to investigate this and
the case manager, Adrian, will be in touch when he has more information.

Thanks, Christopher, CISSP, Security+

## Follow-up from MSRC

None until today (23 jul 2006)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")