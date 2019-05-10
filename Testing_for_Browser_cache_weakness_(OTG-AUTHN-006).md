## Summary

In this phase the tester checks that the application correctly instructs
the browser to not remember sensitive data.

Browsers can store information for purposes of caching and history.
Caching is used to improve performance, so that previously displayed
information doesn't need to be downloaded again. History mechanisms are
used for user convenience, so the user can see exactly what they saw at
the time when the resource was retrieved. If sensitive information is
displayed to the user (such as their address, credit card details,
Social Security Number, or username), then this information could be
stored for purposes of caching or history, and therefore retrievable
through examining the browser's cache or by simply pressing the
browser's "Back" button.

## How to Test

**Browser History**
Technically, the "Back" button is a history and not a cache (see
<http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html#sec13.13>). The
cache and the history are two different entities. However, they share
the same weakness of presenting previously displayed sensitive
information.

The first and simplest test consists of entering sensitive information
into the application and logging out. Then the tester clicks the "Back"
button of the browser to check whether previously displayed sensitive
information can be accessed whilst unauthenticated.

If by pressing the "Back" button the tester can access previous pages
but not access new ones, then it is not an authentication issue, but a
browser history issue. If these pages contain sensitive data, it means
that the application did not forbid the browser from storing it.

Authentication does not necessarily need to be involved in the testing.
For example, when a user enters their email address in order to sign up
to a newsletter, this information could be retrievable if not properly
handled.

The "Back" button can be stopped from showing sensitive data. This can
be done by:

  - Delivering the page over HTTPS.
  - Setting Cache-Control: must-re-validate

**Browser Cache**
Here testers check that the application does not leak any sensitive data
into the browser cache. In order to do that, they can use a proxy (such
as WebScarab) and search through the server responses that belong to the
session, checking that for every page that contains sensitive
information the server instructed the browser not to cache any data.
Such a directive can be issued in the HTTP response headers:

  - Cache-Control: no-cache, no-store
  - Expires: 0
  - Pragma: no-cache

These directives are generally robust, although additional flags may be
necessary for the Cache-Control header in order to better prevent
persistently linked files on the filesystem. These include:

  - Cache-Control: must-revalidate, pre-check=0, post-check=0,
    max-age=0, s-maxage=0

<!-- end list -->

    HTTP/1.1:
    Cache-Control: no-cache

    HTTP/1.0:
    Pragma: no-cache
    Expires: <past date or illegal value (e.g., 0)>

For instance, if testers are testing an e-commerce application, they
should look for all pages that contain a credit card number or some
other financial information, and check that all those pages enforce the
no-cache directive. If they find pages that contain critical information
but that fail to instruct the browser not to cache their content, they
know that sensitive information will be stored on the disk, and they can
double-check this simply by looking for the page in the browser cache.

The exact location where that information is stored depends on the
client operating system and on the browser that has been used. Here are
some examples:

  - Mozilla Firefox:
      - Unix/Linux: \~/.mozilla/firefox/<profile-id>/Cache/
      - Windows: C:\\Documents and Settings\\<user_name>\\Local
        Settings\\Application
        Data\\Mozilla\\Firefox\\Profiles\\<profile-id>\\Cache

<!-- end list -->

  - Internet Explorer:
      - C:\\Documents and Settings\\<user_name>\\Local
        Settings\\Temporary Internet Files

## Gray Box testing

The methodology for testing is equivalent to the black box case, as in
both scenarios testers have full access to the server response headers
and to the HTML code. However, with gray box testing, the tester may
have access to account credentials that will allow them to test
sensitive pages that are accessible only to authenticated users.

## Tools

  - [OWASP Zed Attack
    Proxy](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)
  - Firefox add-on
    [CacheViewer2](https://addons.mozilla.org/en-US/firefox/addon/cacheviewer2/?src=api)



## References

**Whitepapers**
\* [Caching in
HTTP](http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html)