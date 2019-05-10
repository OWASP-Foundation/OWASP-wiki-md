## Summary

The File Inclusion vulnerability allows an attacker to include a file,
usually exploiting a "dynamic file inclusion" mechanisms implemented in
the target application. The vulnerability occurs due to the use of
user-supplied input without proper validation.

This can lead to something as outputting the contents of the file, but
depending on the severity, it can also lead to:

  - Code execution on the web server
  - Code execution on the client-side such as JavaScript which can lead
    to other attacks such as cross site scripting (XSS)
  - Denial of Service (DoS)
  - Sensitive Information Disclosure

**Local File Inclusion** (also known as LFI) is the process of including
files, that are already locally present on the server, through the
exploiting of vulnerable inclusion procedures implemented in the
application. This vulnerability occurs, for example, when a page
receives, as input, the path to the file that has to be included and
this input is not properly sanitized, allowing directory traversal
characters (such as dot-dot-slash) to be injected. Although most
examples point to vulnerable PHP scripts, we should keep in mind that it
is also common in other technologies such as JSP, ASP and others.

## How to Test

Since LFI occurs when paths passed to "include" statements are not
properly sanitized, in a blackbox testing approach, we should look for
scripts which take filenames as parameters.

Consider the following example:

    http://vulnerable_host/preview.php?file=example.html

This looks as a perfect place to try for LFI. If an attacker is lucky
enough, and instead of selecting the appropriate page from the array by
its name, the script directly includes the input parameter, it is
possible to include arbitrary files on the server.

Typical proof-of-concept would be to load passwd file:

    http://vulnerable_host/preview.php?file=../../../../etc/passwd

If the above mentioned conditions are met, an attacker would see
something like the following:

    root:x:0:0:root:/root:/bin/bash
    bin:x:1:1:bin:/bin:/sbin/nologin
    daemon:x:2:2:daemon:/sbin:/sbin/nologin
    alex:x:500:500:alex:/home/alex:/bin/bash
    margo:x:501:501::/home/margo:/bin/bash
    ...

Very often, even when such vulnerability exists, its exploitation is a
bit more complex. Consider the following piece of code:

    <?php “include/”.include($_GET['filename'].“.php”); ?>

In the case, simple substitution with arbitrary filename would not work
as the postfix 'php' is appended. In order to bypass it, a technique
with null-byte terminators is used. Since %00 effectively presents the
end of the string, any characters after this special byte will be
ignored. Thus, the following request will also return an attacker list
of basic users attributes:

    http://vulnerable_host/preview.php?file=../../../../etc/passwd%00
    http://vulnerable_host/preview.php?file=../../../../etc/passwd%00jpg

## References

  - Wikipedia - <http://www.wikipedia.org/wiki/Local_File_Inclusion>
  - Hakipedia - <http://hakipedia.com/index.php/Local_File_Inclusion>

## Remediation

The most effective solution to eliminate file inclusion vulnerabilities
is to avoid passing user-submitted input to any filesystem/framework
API. If this is not possible the application can maintain a white list
of files, that may be included by the page, and then use an identifier
(for example the index number) to access to the selected file. Any
request containing an invalid identifier has to be rejected, in this way
there is no attack surface for malicious users to manipulate the path.