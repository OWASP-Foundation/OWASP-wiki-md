## Description

Web applications are particularly susceptible to denial of service
attacks. Note that network denial of service attacks, such as SYN
floods, are a separate problem that is outside the scope of this
document.

A web application can’t easily tell the difference between an attack and
ordinary traffic. There are many factors that contribute to this
difficulty, but one of the most important is that, for a number of
reasons, IP addresses are not useful as an identification credential.
Because there is no reliable way to tell where an HTTP request is from,
it is very difficult to filter out malicious traffic. For distributed
attacks, how would an application tell the difference between a true
attack, multiple users all hitting reload at the same time (which might
happen if there is a temporary problem with the site), or getting
“slashdotted”?

Most web servers can handle several hundred concurrent users under
normal use. A single attacker can generate enough traffic from a single
host to swamp many applications. Load balancing can make these attacks
more difficult, but far from impossible, especially if sessions are tied
to a particular server. This is a good reason to make an application’s
session data as small as possible and to make it somewhat difficult to
start a new session.

Once an attacker can consume all of some required resource, they can
prevent legitimate users from using the system. Some resources that are
limited include bandwidth, database connections, disk storage, CPU,
memory, threads, or application specific resources. All of these
resources can be consumed by attacks that target them. For example, a
site that allows unauthenticated users to request message board traffic
may start many database queries for each HTTP request they receive. An
attacker can easily send so many requests that the database connection
pool will get used up and there will be none left to service legitimate
users.

Other variants of these attacks target system resources related to a
particular user. For example, an attacker might be able to lock out a
legitimate user by sending invalid credentials until the system locks
out the account. Or the attacker might request a new password for a
user, forcing them to access their email account to regain access.
Alternatively, if the system locks any resources for a single user, then
an attacker could potentially tie them up so others could not use them.
Some web applications are even susceptible to attacks that will take
them offline immediately. Applications that do not properly handle
errors can even take down the web application container. These attacks
are particularly devastating because they instantly prevent all other
users from using the application.

There are a wide variety of these attacks, most of which can be easily
launched with a few lines of perl code from a low powered computer.
While there are no perfect defenses to these attacks, it is possible to
make it more difficult for them to succeed.

## Environments Affected

All web servers, application servers, and web application environments
are susceptible to denial of service attacks.

## Examples and References

[OWASP Guide](:Category:OWASP_Guide_Project "wikilink") to Building
Secure Web Applications and Web Services

## How to Determine If You Are Vulnerable

One of the hardest parts of denial of service attacks is determining
whether you are vulnerable. Load testing tools, such as JMeter can
generate web traffic so that you can test certain aspects of how your
site performs under heavy load. Certainly one important test is how many
requests per second your application can field. Testing from a single IP
address is useful as it will give you an idea of how many requests an
attacker will have to generate in order to damage your site.

To determine if any resources can be used to create a denial of service,
you should analyze each one to see if there is a way to exhaust it. You
should particularly focus on what an unauthenticated user can do, but
unless you trust all of your users, you should examine what an
authenticated user can do as well.

## How to Protect Yourself

Defending against denial of service attacks is difficult, as there is no
way to protect against these attacks perfectly. As a general rule, you
should limit the resources allocated to any user to a bare minimum. For
authenticated users, it is possible to establish quotas so that you can
limit the amount of load a particular user can put on your system. In
particular, you might consider only handling one request per user at a
time by synchronizing on the user’s session. You might also consider
dropping any requests that you are currently processing for a user when
another request from that user arrives.

For unauthenticated users, you should avoid any unnecessary access to
databases or other expensive resources. Try to architect the flow of
your site so that an unauthenticated user will not be able to invoke any
expensive operations. You might consider caching the content received by
unauthenticated users instead of generating it or accessing databases to
retrieve it.

You should also check your error handling scheme to ensure that an error
cannot affect the overall operation of the application.

__NOEDITSECTION__