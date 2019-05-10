## 360 Reviews

The term **360 Review** refers to an approach in which the results of a
source code review are used to plan and execute a penetration test, and
the results of the penetration test are, in turn, used to inform
additional source code review:

![<File:360> Review.jpg](360_Review.jpg "File:360 Review.jpg") A
penetration test that uses a code review as input to planning is
referred to as [white box
testing](http://encyclopedia2.thefreedictionary.com/white+box+testing)
(also called *clear box* and *glass box* testing). This approach can
lead to a more productive penetration test, since testing can be
focussed on suspected or even known vulnerabilities. Using knowledge of
the specific frameworks, libraries and languages used in the web
application, the penetration test can concentrate on weaknesses known to
exist in those frameworks, libraries and languages.

A white box penetration test can also be used to establish the actual
risk posed by a vulnerability discovered through code review. A
vulnerability found during code review may turn out not to be
exploitable during penetration test. This could be due to an incomplete
code review, in which a missing protective measure (input validation,
for instance) was determined to be missing, but was actually present.
But it is also possible that mitigating controls (such as [Defense in
Depth](http://www.nsa.gov/ia/_files/support/defenseindepth.pdf) mask the
vulnerability in the actual operating environment. While the
vulnerability in this latter case is real, the actual risk may be lower.

While vulnerabilities exploited during a white box penetration test
(based on source code review) are certainly real, the actual risk of
these vulnerabilities should be carefully analyzed. It is unrealistic
that an attacker would be given access to the target web application's
source code and advice from its developers. Thus, the risk that an
outside attacker could exploit the vulnerabilities found by the white
box penetration tester is probably lower. However, if the web
application organization is concerned with the risk of attackers with
inside knowledge (former employees or collusion with current employees
or contractors), the real-world risk may be just as high.

The results of the penetration test can then be used to target
additional code review. Besides addressing the particular vulnerability
exploited in the test, it is a good practice to look for additional
places where that same class of vulnerability is present, even if not
explicitly exploited in test. For instance, if output encoding is not
used in one area of the application and the penetration test exploited
that, it is quite possible that output encoding is also not used
elsewhere in the application.