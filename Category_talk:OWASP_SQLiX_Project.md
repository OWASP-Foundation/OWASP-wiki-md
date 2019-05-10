Several Perl modules are required for SQLix to work, which aren't
necessarily installed by default on your OS of choice.

For my install (Fedora Core 6) here's the commands I used to setup

perl -MCPAN -e shell

cpan\>install WWW::CheckSite

cpan\>install HTML::TreeBuilder

cpan\>install Tie::CharArray

cpan\>install Algorithm::Diff

## Using URL files

It isn't explained that the URL file e.g. crawler should be of the form:
method URL queryparams <lf>

For example

GET <http://www.example.com/hello/>

POST <http://www.example.com/hello/myform.php> qs1=val1\&qs2=val2

## cedri.cc down

cedri.cc appears to be having DNS issues. Is it possible to have this
code mirrored on the sourceforge or something similar for times like
these? :)

## This is NOT open source / available for us to use?

The source code of SQLiX.pl says

`Copyright 2006 Cedric COCHIN, All Rights Reserved.`

which would mean, especially in the absence of any GPL or other license,
that we do not have the right to download much less use or modify this
tool. So why bother listing it here? (Of course, you can't **see** the
copyright message until after you already made a copy and unzipped it.)

I can not get the -file option to work. I've created a text file with
the following line GET <http://test.accunetix.com>

But it does not return any results and the program ends much too quickly
for any scanning to take place.

If I run perl SQLiX.pl -crawl <http://test.acunetix.com> -exploit -all
-v=2

The program works as expected. Any ideas?

## If you're porting anyway why not add to an existing project?

If you're working on porting perl to python why not integrate this
functionality into OWASP ZAP?

<https://groups.google.com/forum/#!topic/zaproxy-develop/AIUd6MVS1PU>

Either as an extension or base addition to the project. I know it would
mean java development instead of python but it would get this out to a
wider community and improve things for everyone.
[Kingthorin](User:Kingthorin "wikilink")
([talk](User_talk:Kingthorin "wikilink")) 08:36, 19 March 2014 (CDT)