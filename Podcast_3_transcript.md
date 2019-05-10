## OWASP Podcast \#3 Transcript

[Back to the show notes](Podcast_3 "wikilink")

**Jim Manico:**

You are listening to the Open Web Application Security Project, OWASP,
Podcast number 3 recorded on December 30, 2008.

We have with us today, Matt Tesauro. Matt is an application security
professional working for Texas Education Agency. Matthew, are you there?

**Matt Tesauro:**

I am here.

**Jim Manico:** Well Matt, lets get started. How did you start your IT
career and, specifically, what took you into the field of application
security?

**Matt Tesauro:**

Uh, it was a sort of circuitous path actually. I, actually have an
undergrad in Economics because I was almost through that degree before I
realized that someone would actually pay me to do the farting around
with computers that I had been doing since my Dad bought the 8088.
Anyway, so I ended up after my undergrad getting a MIS degree from Texas
A\&M University and actually my first job was at an international
telecom whose primary business was in Europe although the data center
was in College Station, Texas which is a very small town Texas that
probably wouldn't make the map except for Texas A\&M is there. I was
actually converting some legacy Perl and some classic ASP to PHP 3.03
back when that was new and fresh. Regrettably, that place dot bombed and
I moved over to the business school at Texas A\&M and I was sort of the
web guy. And I inherited this very ugly, not maintained environment and
thought, “If I'm gong to have to code in this, I'm going to set up the
environment I want.” Ended up with 3 graduate assistants and one
full-time guy working for me and about 17 Linux boxes and setup just a
beautiful environment to work in. We had CVS to manage code. It was
wonderful and really my desire to even get into security came about
because I had great pride in the system I set up and I didn't want to
get pwned. Eh, you know, no one was going to hit my baby – those web
servers were my babies. So I really worked at tightening those down and
getting them hardened. And then, also, writing code that wasn't
exploitable, although back in, that was probably 2001. I'm sure some of
my early code was highly exploitable.

My first sort of intro to OWASP was finding WebGoat, using that to kind
of, you know, get a clue and then, going back and doing some of the
WebGoat things against stuff I wrote and find out, “Oh my” (laughs) I
was a little bit lucky at Viatel because we had a sort of unofficial QA
process before it went to the real QA where our group would get together
and say “I'm done with, you know, App X that I just wrote. The rest of
the guys in the group - have a go at it”. And it was, it was a great
source of pride if you could bend over your co-worker's app and then you
know, you got to give the guy grief for the next several weeks. So my
first app, I got done, and I'm like “Hey, I'm done guys. Its working”
and it got destroyed (laughs) utterly destroyed. And that was great for
me because I thought “OK. I don't want to go down this road again.” But
then I worked at A\&M for a number of years. I actually lectured for a
bit at A\&M, actually doing an XML and a Web App Development lecture
both at the grad and undergraduate level. Left College Station, moved to
Austin. Did some pen testing for a while, just general pen testing, and
then moved to TEA to actually do strictly application security. So I'm
the voice of security amongst 120 some developers and 70-ish web apps.

**Jim Manico:**

So Matt, what encouraged you to begin working on the OWASP Live CD
project?

**Matt Tesauro:**

Ah, it was a kind of interesting accident. I was on a mail list for
OWASP and I got mail across my, uh, mail reader, whatever, that said
“Hey we're doing this Summer of Code thing. Come and look at our
projects and apply if you want.” And I thought “Oh hey, OWASP is cool.”
I had used them allot in the past and that's how I kind of learned
security, you know, years ago and I thought, “Lets see what they've
got.” They had a list of, I can't remember what they called it, but
kind of like preferred projects – we'd like to see these done but you
can do something else if you want to. And there was a project listed to
update the Live CD from 2007 and I thought “This is perfect. I'm a Linux
guy – I've been doing Linux for years. I do app sec stuff. Its a perfect
match. I applied and got approved.

**Jim Manico:**

Matt, is this the first Live CD project at OWASP?

**Matt Tesauro:**

Well actually the Summer of Code project was to update the existing Live
CD which was done as a Spring of Code 2007 and also Autumn of Code 2006
projects for OWASP. They were named LabRat – version 2.1 was the latest
one. It was based on Morphix which is a Debian derivative and
interestingly enough, to me, when I started the Live CD project, the
2008 Live CD project, it looked like the prior one was dormant. There
hadn't been any traffic on the mail list in a long time and there wasn't
any new releases and so one of my reasons for going to SLAX was –
there's no reason to continue this, its sort of dead or at least
dormant. And unfortunately, midway through the Summer of Code I heard
from the project lead that said “Hey, I hear you're doing a Live CD. I
was going to update it.” And he's – Joshua Perrymon is the person who
did the prior releases, he was extremely gracious about it. He actually
talked at OWASP NYC and said “I'm going to step back and let Matt take
over the Live CD. He's doing a really good job” And I appreciate how
gracious he was because I really had no idea he had intended to keep it
going and I was kind of blind sided when all that came down.

**Jim Manico:**

What are the goals of the Live CD project?

**Matt Tesauro:**

As far as the Summer of Code goes, I wanted to move... The previous Live
CD was done in an Autumn of Code and a Spring of Code 2006 and 2007. It
was actually based on Morphix which is a Debian variant. And I wanted to
move that from Morphix to SLAX. I also wanted to get, obviously, tool
parity between 07 and the now SLAX version for 08. The previous version
had very little OWASP branding so I put OWASP all over this thing. Its,
I mean, from the boot screen down to the wallpaper when it finally gets
running, it all says OWASP all over the place. And then I wanted to add
a bunch of different tools and do some good documentation. One of my
reviewers \[[1](Podcast_3_transcript#Footnotes "wikilink")\], and I am
glad he did this, requested that not only do I include general security
documentation in the CD but actually document how I created it which is
very thoroughly documented on the CD – not perfectly, but certainly on
the website.

**Jim Manico:**

So you mentioned that you're using SLAX for this project. So, first of
all, what is SLAX, why are you using SLAX, what kind of benefits does
the OWASP community get from your choice of using SLAX.

**Matt Tesauro:**

Ah, great. SLAX is a Linux distribution that was made to be on a Live
CD. It is very small and it uses lzm compression so you can actually
squeeze down your binaries rather, well small - decently small anyway.
The other reason for me wanting to use SLAX is quite honestly I was
already familiar with it from using Backtrack which is another Live CD
that generally used by Pen Testers and my hope was that if I use SLAX, I
get a nice small install – in terms of total size of the CD and any of
the tools that I make available to SLAX potentially can bleed over into
Backtrack. So if Backtrack doesn't have OWASP's WebScarab, let say, and
somebody using Backtrack wants to use it, they can just grab my module
and add it to a running Backtrack system. So one of the nice things
about SLAX is you can actually take these modules, which are just little
compressed programs, and install them in a running Live CD. So, that to
me was pretty dang cool because now, not only can I share beyond the
OWASP Live CD, OWASP tools and other app sec tools, but I can actually
have a – the goal was to have a method to have the CD actually able to
be updated on the fly.

**Jim Manico:**

So where are you at now, what's the current status with the OWASP Live
CD project?

**Matt Tesauro:**

Well, right now, I've actually finished the Summer of Code. I finished
that actually back in September. I've done another release of the Live
CD – what I'm calling the Portugal release, sort of in honor of the
OWASP Summit which happen recently in Portugal which I went to and was
amazingly fantastic. And I've just done... released a beta of a VMware
hard drive install. One of my
reviewers\[[2](Podcast_3_transcript#Footnotes "wikilink")\] actually
took the Live CD and installed it onto a, you know, quote unquote
virtual hard drive in VMware so that you can have persistent image
instead just something which goes away when you reboot. And the other
nice thing is that you can, you know, bump up the size. I actually am
using one now at work that I took and increased the hard drive up to 12
Gig and so I can run it and save reports and its nice because it
persists between reboots.

**Jim Manico:**

I'm really curious about how you decided what tools go on the CD and I
would love to hear what these tools actually are – maybe you could list
some of the more critical tools that you included on the CD.

**Matt Tesauro:**

Let me back up and one step and tell you how I picked the tools because
I got the project, right, and I had the list of tools which were on the
2007 Live CD. I was definitely going to do those but I wanted to do
more. And I started poking around on the Internet and there's tons of
tools out there. I decided that the smart thing to do would be to –
first I looked at the OWASP Testing Guide which at the time this summer
was in version 2 and I went through and I enumerated every tool in there
and that was 70 tools. And then I looked in, actually, my download
directories on my personal box and said “What tools am I using” right
and I got about 51 tools that I was using or was familiar with and I
wanted to include on the CD. And there was also the Austin, or the
excuse me, the Phoenix Chapter of OWASP – one of the members posted this
tool list was large – it was 110 some odd tools. So I took that, stuck
them all together and had 331 tools and said, “Woo\! (laughs) What am I
going to do” It was sort of a - it was a bit daunting. At least as far
as the tools go, on the website, I have all of them listed, what their
license is, what their language is, so that's actually been a great
resource for me when I'm looking for something. You know, what's out
there, what exists. In the case of the Phoenix tools, I even have the
categorized into, sort of, their general purpose.

As far as tools, and the selection of tools, I'll be honest with you – I
have a slight bias toward OWASP tools. (laughs) Shouldn't be any
surprise. So currently, I've got

  - OWASP WebScarab on there. Its an older build but, actually
    yesterday, and today I've been working on doing the latest build.
    And I actually have that working now so I do have a build that I can
    put on the next release – the brand new release which actually came
    out of Portugal
  - WebGoat 5.2 which is the latest
  - w3af tool which is an automated web scanner. w3af stands for the web
    application attack and audit framework. Think of it as sort of
    Metasploit for web application security almost like an AppScan type
    scanner but GPL'ed And I actually pulled that from Subversion and it
    will do the text-based as well as the GUI. And because I pulled it
    from Subversion, you can actually – I wrote a script and there's a
    menu item to update that to the latest SVN so it will actually go
    and pull the latest from SVN. Its a Python app so it can pull the
    latest SVN and now have the latest version on your running Live CD
    which is pretty cool.
  - There is OWASP Cal9000
  - OWASP DirBuster
  - OWASP JBroFuzz
  - OWASP WSFuzzer
  - OWASP SQLiX

Beyond the OWASP tools, I've have

  - Burp proxy
  - Paros
  - Grendel Scan
  - Firefox with about, actually it has 19 add-ons added to it
  - Metasploit 3 that's pulled from SVN and is also update-able
  - nmap
  - tcpdump
  - wireshark

Those are all the big guys.

**Jim Manico:**

Excellent. So how active is this project? Are there other folks besides
you who are working and contributing on the Open \[OWASP\] Live CD
project?

**Matt Tesauro:**

Ah, definitely. Blissfully for me, I had two very good
reviewers\[[3](Podcast_3_transcript#Footnotes "wikilink")\] and both of
them have remained active in it, both providing feedback and suggestions
going forward. I did a presentation at OWASP Austin chapter on the Live
CD kind of in the middle of the Summer of Code while I was working on it
when it was in an early beta and one of the audience
members\[[4](Podcast_3_transcript#Footnotes "wikilink")\] came up to me
and it – one of the slides I had said “How can you help?” and I said “I
am terrible with graphics. If you know someone who is l33t with
graphics, come see me.” And Nishi came up after the, after my talk and
said “You know what I do graphic design and I'd love to help you” And
boom\! I got free graphics design for all of it and she's kept up with
me and is doing all of the new graphics as we move forward. I have
another fellow who is testing the VMware install off a VMware ESX server
for him and he's got a team of testers. So I've had a lot of good
response. I was actually surprised. I got an email from somebody in the
OWASP Egypt chapter asking me “Did it have WebGoat and could he use it
with that” And it does and I said “Go to town” And I got several other
people asking me about WebGoat so for the Portugal release I actually
created a little application called the “WebGoat Manager”. That's a
little GUI that helps you fire up, start, stop, and change the port of
WebGoat because, traditionally in Linux, its kind of a semi-crunchy
command-line script thing so I just tried to make it as easy as
possible.

**Jim Manico:**

So what if other folks from the OWASP community want to get involved in
the OWASP Live CD project? How do you advice that they jump in and
contribute?

**Matt Tesauro:**

Well first, of course, I'd like them to join the mail list. I use that
to sort of announce updates and what's new and where I'm going with it,
you know, in hopes to get feedback. There's never enough feedback when
you do any project. It great to have people say “I like this” or even
say “I hate this”because the end result is a much better end product,
right, which is kinda my goal.

I would love to have people down load the ISO and just give it a whirl,
right. Burn a CD of it and see what you think.

There's also the VMware image that I just released that's in beta. Its
rar'ed and up on the website. You're welcome to download that and give
that a try.

I've got an issue tracker on the Google Code site. I've had several
people put in issues and I've addressed most of them. I have a couple of
them that are still open.

If you look on the documentation site, I literally have step by step
commands that I did to create each module. And if somebody gets a wild
hair and wants to create a module for their favorite tool – more power
to them. I'd love to help somebody to that. You know, there's nothing
like expanding me as a resource.

I'll take suggestions for documentation or reference, you know, that
would be fantastic. And I could certainly use, if somebody wants to do a
screencast, or even a blog post – something about using the tools on the
Live CD and letting me know about it, I'll include it in the next
release as part of the documentation.

**Jim Manico:**

So what about you? What's next for you?

**Matt Tesauro:**

(Laughs) Ah, well there's a lot more just for the Live CD to be quite
hones with you – besides my day job. I just actually today arranged with
the OWASP Austin chapter that on February 5<sup>th</sup> we're going to
do an official release party. And we're looking for sponsors, so if
anybody wants to help sponsor that, that would be fantastic. I've got
one so far but you could never have enough.

I definitely have some new tools I want to include in there – OWASP
WebSlayer. Its a brute-force tool that came out of the Summer of Code.
That's a very nice, a very nice tool that I want to make sure gets on
the next release. A couple of the tools I have now, they've actually had
new releases since I pressed the last CD so I want to get those updated.

But to be qute honest with you, I've been overwhelmed. (laughs) And I
want to kind of take a deep breath and slow down a bit. I am moving, I
want move off of, its currently on mtesauro.com which is my first
initial and last name and my name, my last name is not like Smith – its
not exactly easy to type. So, I now am the proud owner of appseclive.org
and I will be migrating all of the mtesauro.com stuff over to a
significantly easier to remember URL.

I need to setup a good, uh better repository for when I'm doing module
development and I will probably do git or SVN. I'm kind of debating
those two currently.

I would like to take the 300 and some odd tools I have and work them
into something much better than a static wiki page list. I'm looking at
some content management systems so that I can actually post them, have
individual information about them. Maybe even have a rating system so
that you – people can vote on what they want to see next on the Live CD,
you know, the highest rated tool wins, kind of a deal.

And it would be nice to have a tracking, a method to track when new
releases are coming out because it, it getting to be – there's enough
tools on there that I have a hard time keeping track of “wait, has nmap
released a new release”, “Yes it has”, I've got to go get the code.

Two sort of big things I have planned going forward for the next, eh, I
don't know, lets say the mid-term. Something I'm called project “Tindy”
which by the way is the name of a little stuffed cat of my daughters.
This poor bedraggled and sad looking cat that she named Tindy. So
project Tindy was to continue testing the VMware instances and make sure
that this, the persistent install of the Live CD works and I've tested
it in VMware but I'd also like to test it in Parallels, Virtual Box,
Qemu is another virtualization software, maybe XEN. Just try and make
sure that if you do want to have a persistent install of it, that it
works well.

The other kind of big project on the horizon is what I'm calling project
“Aqua Dog” is the name of one of my son's – one of his dogs – which, my
goal there is to take a VM image, a VM engine rather so in this case it
will probably be Qemu because that's GPL'ed and that's – I can
distribute that without licensing issues. Take that, take a virtual
install, put that on an USB stick and then what you have is a portable
web testing environment and you don't even have to reboot. Pop in the
USB stick, fire up the VM, and there's your virtual install, and you're
off and running. Which would be really nice because you could do away
with the need to actually have to reboot a machine into a separate OS.
And I've also played with the idea of, part of that for the truly
paranoid, you could actually have that USB install be a TrueCrypt volume
which is an encrypted hard drive volume. That way you would have a
hidden toolkit that was in an encrypted volume. And, if nothing else, I
think I will add TrueCrypt to the VM instance so that for people that
are generating data that could potentially be sensitive during testing,
they have a way to encrypt it.

And then, actually out of Portugal at the OWASP Summit, I talked allot
with the education project people and if we work the Live CD correctly,
we can make, actually, a great ready made training environment.
Recently, actually, where I work, we had someone in to do some training,
they were borrowing some of our meeting space, you know, “Hey no
problem. Here's a computer lab. Go use it.” We find out two days before,
“well we need MS Server 2003, we need this, we need this, we need this”
There's all these things that had to get installed. Not only do they
have to get installed but there are licensing issues around them and
that almost killed the training because, you know, (laughs) we're not
going to skip out on licenses. At least with the Live CD and the tools
that are one it, they are all open source licenses so there no kind of
issue with distributing that, or sharing that or using that as an
educational environment.

**Jim Manico:**

Before we finish up, are there any closing notes you'd like to include?

**Matt Tesauro:**

Yeah, there's a couple things. One thing, for people who are testers,
because, I've been, you know the whole builder, breaker. I've been on
both sides of that. And for the breakers out there that are familiar
with Backtrack, I explicitly want to say that OWASP Live CD is not
Backtrack and it never will be. Backtrack is a fantastic toolkit for pen
testers but it goes way beyond the app sec realm. I mean it does
wireless and all sorts of other stuff beyond application security.

The other thing I wanted to mention, is there is another Live CD called
Samurai, that the Inteliguardian people have put out, that is actually a
very nice Live CD and to be painfully honest, has more tools currently
than are on the OWASP Live CD. The one thing that I'm running into with
the Live CD and this is ends up being a limitation of SLAX is that when
you install packages, its not – the package manager for SLAX is not
very, is not very intelligent actually. It basically just drops things
onto the file system and there no way to run any sort of script or code
after an install. So if you need to update the list of libraries or
anything like that you can't with the built in package manager for SLAX.
And I'm running into issue now where I really need to be able to do that
to properly set up an environment. So I've actually been looking at
moving SLAX to having Debs, a Debian packages, which selfishly, I can
use on the Ubuntu boxes that I use. And there is a converter which will
convert those Debs to SLAX. So hopefully going forward, the Live CD will
be even more update-able and even more modifiable.

The kind of pie in the sky kind of idea I have is to actually have
profiles that you could use with the Live CD. So you could say, “I'm a
Java guy and I want to do static analysis” and it would know that these
are the tools that, you know, it has in its tool belt that do Java and
do static analysis. Go get them and add them to the Live CD. Or you
could say, “I want to only do dynamic testing and I don't care what the
underlying language is” Fine, here's all the dynamic language tests, er
tools. So that's sort of the end goal. The pie in the sky crazy (laughs)
goal.

**Jim Manico:**

Well Matt I really think that this is a critical project for OWASP and
I'd be real thankful if you could join us possibly in three or six
months and give us another update as to the status of the OWASP Live CD
project.

**Matt Tesauro:**

I would love to. I would love to. This is quickly becoming my little
baby. (laughs) so yeah, I would love to talk about it some more.

And I've been really surprised with the amount of traction its gotten
because I've done – this will be my first quasi-marketing anything
because I've been so busy doing, I haven't actually talked about it
much. And I was blow away in preparing for this podcast, I went and
looked at the Google code site and, each of the packages that I create –
the SLAX modules, I post individually up on a Google code site so if you
want to grab them and not bother with the Live CD, you're welcome to get
them. I have some of those modules that have been downloaded 21 hundred
times. Its crazy. And I looked at the web traffic and the, what, I've
used 248 Gig of bandwidth. Luckily my host hasn't found out or notice
yet. Shhh. (laughs)

**Jim Manico:**

I think they just found out Matt. (laughs)

**Matt Tesauro:**

Well, if you read the terms, it does say its unlimited bandwidth and I'm
making them live up to that – until they kick me off. (laughs) But so
far, I've had, what was the downloads for the Portugal release - the ISO
has been downloaded 7300 times, and the release prior to that was 7000
times and the beta1 was another 8000 times so that's allot of people
downloading this Live CD. I've been really surprised.

**Jim Manico:**

This is fantastic and something that is really useful to the entire
community.

**Matt Tesauro:**

Well, I'll tell you, if anybody is thinking about getting involved in
OWASP, from somebody who's very fresh at it and, what, last April was
when I put in my app, my application to to the Live CD project. Its been
a fantastic ride. I've met tons of amazingly smart people. And
interacted, shockingly, just random people contacted me, “Hey you're
doing the Live CD, I'd like you to include this tool.” Grendel Scan
that's in there was demo'ed at Blackhat. I just got an email out of the
blue from the project lead on that. “Hey do you want to put Grendel Scan
on there?” Well heck, if you're going to talk to me, I sure will. Its on
there. Its been really surprising and quite nice.

**Jim Manico:**

Well, you've been listening to Matt Tesauro and OWASP Podcast \#3
recorded on December 30<sup>th</sup> 2008

OWASP: The Open Web Application Security Project is a world wide free
and open community focused on improving the security of application
software. For more information, please visit www.owasp.org

[Back to the show notes](Podcast_3 "wikilink")

-----

## Footnotes

\[1\] Kent Poots was the reviewer who suggested that the documentation
include how I created the OWASP Live CD.

\[2\] Kent Poots created the first VMware installation and wrote up how
he did it.

\[3\] Dustin Dykes and Kent Poots were the reviewers for the Summer of
Code OWASP Live CD project

\[4\] Nishi Kumar was the volunteer who did the excellent graphics work
on the OWASP Live CD