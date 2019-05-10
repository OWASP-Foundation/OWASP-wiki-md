This page should collect together any resources relating to
[Perl](http://www.perl.org/) and OWASP or security in general.

It is perhaps odd that this page is so new:

1.  Perl has long been an [open source
    language](http://cpansearch.perl.org/src/DAPM/perl-5.10.1/Artistic)
    and often associated with the internet.
2.  It offers what seems to be a much under-used method of combating
    many sorts of exploit namely
    [taint](http://search.cpan.org/~dapm/perl-5.10.1/pod/perlsec.pod#Taint_mode)
    mode. This forces every "input" to the program to be checked for
    malign influences before it is allowed to effect the "outside" of
    the program.

## Possible perl OWASP projects

1.  Perl ports of multi-language OWASP projects, for example
    [AntiSamy](AntiSamy "wikilink").
2.  Review of CPAN modules according to OWASP standards, for example
    [CGI::Application::Plugin::Authentication](http://search.cpan.org/~silasmonk/CGI-Application-Plugin-Authentication-0.17/lib/CGI/Application/Plugin/Authentication.pm).
3.  A perl module to measure the [strength of
    passwords](http://en.wikipedia.org/wiki/Password_strength).

## Perl resources

1.  [OWASP ESAPI Perl Project](OWASP_ESAPI_Perl_Project "wikilink") has
    been started.
2.  Perl [security](http://perldoc.perl.org/perlsec.html) man page
3.  [Perl Monks](http://perlmonks.org)
4.  [Security Issues in Perl Scripts by Jordan
    Dimov](http://www.cgisecurity.com/lib/sips.html)

## Perl modules

An attempt to list and classify perl modules related to web security.
This should lead on to discussion of vulnerabilities.

### Web frameworks

Authentication modules will often be framework specific so let's list
those.

<table>
<caption>Perl web frameworks and their security mechanisms</caption>
<thead>
<tr class="header">
<th><p>scope="col"</p></th>
<th><p>Framework</p></th>
<th><p>scope="col"</p></th>
<th><p>Authentication</p></th>
<th><p>scope="col"</p></th>
<th><p>Authorization</p></th>
<th><p>scope="col"</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://www.catalystframework.org/">Catalyst</a></p></td>
<td><p>[<a href="http://search.cpan.org/perldoc?Catalyst">http://search.cpan.org/perldoc?Catalyst</a>::Plugin::Authentication Catalyst::Plugin::Authentication]<br />
</p></td>
<td><p>The same module also covers authorization via the concept of realms.<br />
</p></td>
<td><p>Catalyst seems to have issues with taint mode.</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="http://cgi-app.org/">CGI::Application</a></p></td>
<td><p>[<a href="http://search.cpan.org/perldoc?CGI">http://search.cpan.org/perldoc?CGI</a>::Application::Plugin::Authentication CGI::Application::Plugin::Authentication]</p></td>
<td><p>[<a href="http://search.cpan.org/perldoc?CGI">http://search.cpan.org/perldoc?CGI</a>::Application::Plugin::Authorization CGI::Application::Plugin::Authorization]</p></td>
<td><p>Not a very coherent framework, multiple authors</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="http://jifty.org/view/HomePage">Jifty</a></p></td>
<td><p><a href="http://search.cpan.org/~alexmv/Jifty-0.91117/lib/Jifty/Plugin/Authentication/Password.pm">Jifty::Plugin::Authentication</a></p></td>
<td><p>n/a</p></td>
<td><p>?</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="http://mojolicious.org/">Mojolicious</a></p></td>
<td><p>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::Authentication Mojolicious::Plugin::Authentication] - A plugin to make authentication a bit easier</p></td>
<td><ul>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::Authorization Mojolicious::Plugin::Authorization] - A plugin to make authorization a bit easier</li>
</ul>
<ul>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::BasicAuth Mojolicious::Plugin::BasicAuth] - Basic authorization helper</li>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::Bcrypt Mojolicious::Plugin::Bcrypt] - Bcrypt helper</li>
</ul>
<ul>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::DigestAuth Mojolicious::Plugin::DigestAuth] - HTTP digest authentication</li>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::ParamsAuth Mojolicious::Plugin::ParamsAuth] - Parameter authorization helper</li>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::SslAuth Mojolicious::Plugin::SslAuth] - SSL Client Certificate authorization helper</li>
<li>[<a href="https://metacpan.org/pod/Mojolicious">https://metacpan.org/pod/Mojolicious</a>::Plugin::SPNEGO Mojolicious::Plugin::SPNEGO] - Provides SSO by forwarding NTLM requests to an Active Directory Server</li>
</ul></td>
<td><p><br />
</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="http://perldancer.org/">Dancer</a></p></td>
<td><p><br />
</p></td>
<td><p><br />
</p></td>
<td><p><br />
</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Authentication

A lot of generic authentication modules can be found on
[CPAN](http://search.cpan.org/search?query=Authen&mode=all).

Also
[HTTPD::User::Manage](http://cpansearch.perl.org/src/LDS/HTTPD-User-Manage-1.66/user_manage.html).

### Authorization

I am not aware of anything generic.

### HTML validation/cleanup

Anything similar to [AntiSamy](AntiSamy "wikilink") should go here.

\[<http://search.cpan.org/perldoc?HTML>::Scrubber HTML::Scrubber\]

\[<https://metacpan.org/pod/HTML>::Tidy5 HTML::Tidy5\]

There is a discussion on this subject going on at [PerlMonks:Dynamic
HTML cleanup](http://perlmonks.org/?node_id=861639).

### Password strength

\[<http://search.cpan.org/perldoc?Data>::Password::Entropy
<Data::Password>::Entropy\]

\[<https://metacpan.org/pod/Data>::Password::zxcvbn
<Data::Password>::zxcvbn\] a port of Dropbox’s JavaScript
implementation. Discussed in detail in [How strong is your
password?](https://www.perl.com/article/how-strong-is-your-password-/)

### CAPTCHA alternatives

These are attempts to distinguish human and robot users. CAPTCHA is not
perfect at this and is highly inaccessible.

[Authen::Quiz](http://search.cpan.org/~lushe/Authen-Quiz-0.05/lib/Authen/Quiz.pm)

\[<https://metacpan.org/pod/Dancer>::Plugin::reCAPTCHA
Dancer::Plugin::reCAPTCHA\]
\[<https://metacpan.org/pod/Mojolicious>::Plugin::Recaptcha
Mojolicious::Plugin::Recaptcha\]

[Category:Language](Category:Language "wikilink")