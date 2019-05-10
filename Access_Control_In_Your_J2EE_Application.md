**Author: [Jeff Williams](:User:Jeff_Williams "wikilink"), [Aspect
Security](http://www.aspectsecurity.com)**

## Overview

I'm not sure ***how*** the web application development community got
started using the term "authorization"-- but I'm not crazy about it. The
simple problem is that developers frequently confuse it with
"authentication" -- especially when it is abbreviated "auth". But, more
fundamentally, people have used the term "access control" for the past
30 years on every type of system except web applications, and it's
confusing to change. For this article, I'm going to talk about "access
control" -- just remember that there are a whole bunch of people who
like to call it "authorization."

Whatever you call it, controlling access is an incredibly important
security mechanism. It's critical in any site where users shouldn't
access other users' information, or any site where there are different
roles and privileges -- basically any enterprise web site. Yet we've
uncovered a stunning number of poorly conceived and implemented access
control schemes. We frequently find flawed implementations that would
allow users to access other user's data and invoke unauthorized
functions. Many of the access control implementations we've seen look
like the set of rules controlling how power is shared between parts of
the U.S. power grid -- a Byzantine labyrinth of rules, roles,
privileges, access control lists, and exceptions.

Implementing access control is a relatively simple problem in theory.
Once you authenticate a user, you need a mechanism to control the
resources and functions that user can access. Those of you thinking --
"Well isn't that what JAAS is for?" -- well, sort of. JAAS provides a
sophisticated authentication framework supporting a number of different
methods. And JAAS also includes some access control support. But JAAS
requires some serious development to use for access control in a web
application -- it's very difficult to customize. And as we'll see,
that's the most important thing for an access control mechanism.

Let's start at the beginning. There is an enormous body of literature on
the design of access control mechanisms. There are also a huge number of
examples of time-tested approaches to controlling access. Think of
access control lists on files in most operating systems. Or the Java
Security Manager that controls access of programs to Virtual Machine
functions. Unfortunately, many of the access control schemes used in web
application environments haven't taken advantage of this history.
Instead they tend to be haphazardly designed. All the previous access
control theory was developed in the context of operating systems and
databases, so the mechanisms don't match up perfectly with web
applications, making them difficult to apply.

## Background

I strongly recommend that you centralize your access control mechanism
-- it's just way too easy to make a mistake in a distributed mechanism.
So, instead of doing a little access control checking in each servlet or
JSP, use a "front-door" servlet to do the access control checking. But
you're going to need some information to make those decisions. You need
to have information about who is doing the accessing. You also need
information about what is being accessed. The time-honored way of
representing this information is called an "access control matrix."

Okay, so let's work through an example of a simple access control matrix
for a typical web application. Then we'll discuss a few of the options
for implementing the model. As it turns out, the First National Bank of
OWASP (FNBO) is starting to design their new online banking site.
They're building a deluxe site with features including bill pay, account
management, tax planning, mortgages, and remote administrative
functions. At the outset, all they know for sure is that they are
subject to the GLBA and COPPA, so they're going to have to be careful
with people's personal information.

An access control matrix lists the users, groups and roles down the
left-hand side, and all the resources and functions across the top. The
matrix is a concise way to represent fairly sophisticated rules,and,
once it is finished, it should be a relatively simple matter to
implement the rules as described in the matrix. FNBO has already decided
that they will be using the standard J2EE authentication mechanisms
built into JAAS, and so they will have access to role information. They
have already come up with an initial set of roles:

:\*Administrators can access only the administrative pages

:\*Guests can access all the public areas of the site

:\*Owners can access their account, move funds, and review transactions

:\*Users can view an Owner's account, but not make changes

:\*Planners can access the sites financial planning and tax preparation
functions

:\*Payers can use the site's bill paying function

They've put together an access control matrix that looks like this:

<center>

![Image:Acm.png](Acm.png "Image:Acm.png")

</center>

## Designing Your Access Control Mechanism

The example above is very simple and the whole approach may even seem
trivial, but the exercise of working out the users, roles, assets,
capabilities, and how to choose rows and columns can get complicated. If
you can't even articulate the access control rules for your web
application, it is very unlikely that it is implemented correctly.

### 1\. Label Your Users

Access control is dependent on good authentication. You have to know who
you're dealing with before you can say whether they're allowed to see a
resource or access a function. But you may want to base your access
control decision on additional details about that person. Ordinarily,
access control is based on the fact that the user has a particular role
or group membership. But you can do access control based on age, sex,
height, number of contributions in the past 30 days, or anything else
you want to label your users with.

Labeling is just a concept -- it means that you've associated a piece of
metadata with a resource.To build something like this, you'll want to
augment your user repository to store these attributes. You may want to
identify groups for some of these attributes to make them easier to
manage. For example, you may want to label users as short, normal, or
tall instead of tracking their actual height. Managing these attributes
can be difficult, so you'll want to take user storage seriously.
Attempting to use a fancied up version of a passwd file is not going to
meet the needs of many sites.

### 2\. Label Your Resources and Functions

You also need some way to get information about the resource or function
that was requested by a user. The naive approach is to use the URL, like
<http://www.example.com/documentation?id=8834>. But there's typically
not enough information there, typically just the document number. You
probably would prefer to have more information about that document.
Maybe you want to restrict access to documents written by a particular
author, or by date, or by size, or by whether there's a charge for the
document or not. So you should be thinking about where you're going to
store that information.

Also, many web sites are not just about content anymore. They provide
functions to buy, sell, copy, delete, move, and anything else you can
think of. Controlling access to functions is a little different from
controlling access to content. This is the reason why many of the
traditional access control mechanisms don't work so well for web
applications. If your site offers functions, you better include them in
the access control matrix. And that means you'll need to mark them with
all the information you'll need to make access decisions.

### 3\. Capture the Rules

The last piece is the most important. Once you've got all the
information together, you need a way to specify who can access what. You
want to articulate the rules in the most succinct, expressive way
possible. There's no universally right way to do this. ACL's or
capabilities lists are the most popular approaches, but they can be
difficult to maintain. If your access control rules don't change much,
you can write them in Java and compile them into your application. Many
times this is the most clear and concise way to do things. The
AccessController plus security.policy file built into J2SE is another
strong model.

One more thing. Some sites will want to be able to specify how the
access will be performed. Perhaps some users are only allowed to read,
while others can read and write. Your list of access methods will be
custom to your site. Typical access methods for content are things like
read, write, edit, and delete. Access methods for functions are more
likely to be things like start, interrupt, check status, or debug. This
requires a small extension to the access control matrix shown above.
Rather than marking each cell with an "X", you'll need to list the
appropriate permissions in each cell.

## How to Test a Site's Access Control Scheme

Far too many sites use only their HTML interface to enforce access
control -- if there's no button on the screen, then there's no way for a
user to get to it, right? In these sites, there really is no access
control mechanism. The only protection is a touch of security by
obscurity. The OWASP Testing project is going to detail how to test
access control, but here's a short preview.

Without getting too technical, the basic idea in testing a site's access
control scheme is to attempt actions that should not be allowed (based
on a real or presumed access control matrix) to see if they work. You'll
need accounts for each of the account types in the access control
matrix. The first step is to identify how each function is accessed.
You'll want to use a proxy like OWASP's WebScarab to see what's going on
under the hood. Then all you have to do is replay those functions while
logged in as another user who should be denied access. I think you'll be
surprised at what you find out.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")