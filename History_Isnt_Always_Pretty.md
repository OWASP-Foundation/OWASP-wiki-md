## Introduction

Fall is about to hit here in New England. Labor Day has been and gone;
the communities pools have all closed up and I have the hard roof back
on my Jeep. There is a definite chill in the air when you leave the
house in the morning. It sure wasn't like that when I lived in
California let me tell you. But despite where you live in the world,
it's often that time of year when you sit back and think about all of
those things you wanted to get done this year and how little time you
have left to make good the promises you made to yourself.

I think I have an interesting perspective on many things information
security that comes from the fact that for the last seven years I have
systematically gone from being a vendor to a purchaser: selling software
or services to being a corporate security consumer in large
international banks. I drift from writing code (badly) and reading Dr
Dobbs to wearing smart casuals and even suits from Gieves and Hawke when
I am London. It keeps me on my toes and allows me to see both sides of
the coin or at least empathize with both parties. It has also made me
more than a little grumpy at times with both sides of the fence but more
of that later in the year.

When we think about security management many of us immediately start
thinking about policy and procedures and dusty documents usually written
for the authors themselves. When I think about web security management I
think about the art and science of solving real world security problems
strategically.

## The OWASP Bank has an SSL issue

So let's take a brief look at a problem the fictitious "OWASP Bank" has
with SSL. Why pick SSL as the example? Well it's the lowest common
security denominator of most web sites and when you scratch beneath the
surface you will find that the majority of sites still have a
significant way to go with their SSL implementations. I believe it's a
management issue; a combination of a lack of awareness, education,
technology, policy and process. Besides, it will prove my point that
with a little thought, solving security problems strategically is very
achievable and it will magically make my creative title make sense.

As CSO of the OWASP Bank I often get internal memos from compliance.
They don't like email and besides now Sarbanes Oxley is here.....no,
stop. Don't go there yet. Any how, a tech savvy customer recently
pointed out in a letter to the CEO that we make a claim in our online
security policy that we protect customers data by supporting 128 bit SSL
and that in actual fact he used a 40 bit browser to connect to our site
and transfer money. How could this be they asked and attached an
official looking document from the Office of the Controller of the
Currency stating that all data should be protected by "...equivalent to
128 bit SSL..." As I file the memo in the "to do" tray, the phone rings
and it's a legal admin inviting me to a meeting about the issue next
Monday. The wild fire has started and before long I know people will be
talking behind my back about "another information security failure" and
how "the security department is out of touch with real world problems".

I download the latest copy of Mozilla, set the cryptography to only
allow 40 bit SSL and login. For giggles I turn off SSL 3.0 and 2.0 and
login with SSL 1.0 and 40 bits. Really where is the problem I ask
myself. I think I know the answer but call in two of my esteemed
colleagues who will at some point be tasked with dealing with the issue.
Jack is my technical specialist, a keen developer with an unhealthy
interest in cryptography, Dilbert cartoons and Anna Kornikova. She's one
step away from Julio Englesias now I have told him on many occasions but
it seems to fly over his head. Maybe I am too old. I explain the issue,
show him my demonstration and ask him what he thinks.

"Holly smoke, that"s not good" said Jack. "40 bits crypto can be broken
in two and a half hours, this is bad. I think you need to call the CIO .
Man how did that happen, John uses WebInvesitgator every week and it
never said anything. I check the reports. We need to run the Security
Wizard on IIS to only allow 128 bit sessions straight away." Not
surprisingly Jack immediately saw the issue as a technical one and
looked for reasons why it happened and how to fix it.

Jack left with instructions not to do anything and in came Hana. As a
former internal auditor she is responsible for the banks security
policy. Having explained the issue and after showing her my demo she
sighed. "Our online policy says we support 128 bit SSL to protect all
data to and from the bank; I wrote it" she explained.

So what do I the CSO think? Is it a policy violation or is it a
technical issue? Or is it a web security management issue? Of course it
is. Before we move on to discuss a real world solution to this trivial
problem lets look some other facts that neither Jack or Hana asked.

:\* Do we have any customers from International locations that need 40
bits?

:\* What other regulatory bodies have standards for SSL?

:\* What are the system requirements?

:\* How many users stay online for more than 2 and an a half hours
anyway?

Monday came around fast. In a room full of people shuffling papers and
sending Blackberry messages, the legal meeting kicked off abruptly. Cara
the head of Compliance explains the context of the meeting and asks me
the CSO to address the meeting with the facts.

"The facts are this meeting will be very short", I start. A few jaws
drop and a few people look disappointed. "SSL is a way for our users to
encrypt their transactions with us over the web. It happens seamlessly
in the customer browser. That's that the padlock is at the bottom of the
screen". A few lawyers nod their approval that I have a good grasp on
the technical subject matter. "The OCC regulation provides a guideline
that we should use 128 bit SSL with our users. We do. 128 bit SSL is the
default way any user would connect to us. The technicality here is that
if a user specifically wanted to connect to us with a 40 bit weaker
browser we would have also supported it. Let me re-iterate that if the
customer intentionally chose it were would have supported it but no
modern browser would do that. It is a technicality that will be changed
in the next web site release in two weeks".

The facts:

:\* We say online that we "support" 128 bit SSL and we do.

:\* The OCC says we should use 128 bit SSL and we do.

:\* If you intentionally wanted to connect to us with a 40 bit weaker
browser you could. 40 bit security is generally accepted to be strong
enough for two and half hours. In the last 6 months only 5 of our
250,000 users have stayed online for more than two and a half hours.
Therefore this issue could have potentially affected 0.00002 % of our
user population."

However to ensure that we are cleaner than clean, we have

:\* Contracted with legal counsel to update us of any regulatory
obligations about SSL.

:\* Created an SSL configuration policy for operations to follow.

:\* Bought a tool to check the SSL we are using on a daily basis and
report any deviance from policy.

And with that I suggest we all enjoy the gift of time unless anyone has
any questions?" I hand Cara a copy of a draft letter to the kind
gentlemen who wrote to us (who incidentally offered his resume along
with the hint). I sit back, sip my Grande decaff latte and grab for my
phone. With a sigh I think; another day in management paradise. Another
storm in a tea cup subverted. Another scenario we have solved.

## Conclusion

All very interesting you say but what does that have to do with being
inspired living in New England? Well at this time of the year I remind
myself that the same things will happen that happen this year that
happened for the last one hundred years and will happen for the next one
hundred years. The leaves will turn into amazing colors and eventually
drop off. We will be covered in snow for three months and then it will
melt and we will get some small floods. Managing a web site is much like
life. If you are prepared, nothing will be a surprise. After all, why
turn life into a drama?

## Tips for Managing SSL

:\* Understand the site requirements and how SSL works - international
sites may require lower strength SSL and compatibility with older
browsers. Remember the level of SSL used is the users choice. You need
to define the minimum level you will accept.

:\* Understand your regulatory obligations (engage with legal counsel).
The OCC are just one party that defines standards.

:\* Develop an SSL and digital certificate policy and configuration
guidelines. This should include SSL versions, cipher suites, key lengths
(tied to cipher suites), and digital certificate properties and should
form part of your web security policy.

:\* Build or buy technology to check your web servers on a regular basis
and implement a process to ensure it happens - There are commercial SSL
analysis tools on the market. Shameless plug, I built one.

:\* Develop a process to ensure the results are acted upon.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink") [Category:
Control](Category:_Control "wikilink")