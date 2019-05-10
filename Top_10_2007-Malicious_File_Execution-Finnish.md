**Esimerkki** Sovellus ottaa yhtenä parametrinaan osaksi sivuston
generoivaa koodia sisältävän tiedoston nimen. Oletus on, että käytetään
jotakin sivuston omista tiedostoista, mutta hyökkääjä vaihtaa nimen
osoittamaan omalle palvelimelleen. Hyökkääjän tiedosto sisältää
kuitenkin koodia, joka avaa hänelle pääsyn sovellusta isännöivään
järjestelmään.

**Suositus** Tarkasta, että syötteenä käytetyt tiedostot eivät sisällä
suoritettavaa koodia tai että tiedostojen alkuperä on tunnettu.

TODO: Käännä seuraavat

Malicious file execution vulnerabilities are found in many applications.
Developers will often directly use or concatenate potentially hostile
input with file or stream functions, or improperly trust input files. On
many platforms, frameworks allow the use of external object references,
such as URLs or file system references. When the data is insufficiently
checked, this can lead to arbitrary remote and hostile content being
included, processed or invoked by the web server.

This allows attackers to perform:

  - Remote code execution
  - Remote root kit installation and complete system compromise
  - On Windows, internal system compromise may be possible through the
    use of PHP’s SMB file wrappers

This attack is particularly prevalent on PHP, and extreme care must be
taken with any stream or file function to ensure that user supplied
input does not influence file names.

## Environments Affected

All web application frameworks are vulnerable to malicious file
execution if they accept filenames or files from the user. Typical
examples include: .NET assemblies which allow URL file name arguments,
or code which accepts the user’s choice of filename to include local
files.

**PHP is particularly vulnerable** to remote file include (RFI) attack
through parameter tampering with any file or streams based API.

## Vulnerability

A common vulnerable construct is:

`include $_REQUEST['filename’];`

Not only does this allow evaluation of remote hostile scripts, it can be
used to access local file servers (if PHP is hosted upon Windows) due to
SMB support in PHP’s file system wrappers.

Other methods of attack include:

  - Hostile data being uploaded to session files, log data, and via
    image uploads (typical of forum software)
  - Using compression or audio streams, such as zlib:// or ogg:// which
    do not inspect the internal PHP URL flag and thus allow access to
    remote resources even if allow_url_fopen or allow_url_include is
    disabled
  - Using PHP wrappers, such as php://input and others to take input
    from the request POST data rather than a file
  - Using PHP’s data: wrapper, such as
    <data:;base64,PD9waHAgcGhwaW5mbygpOz8+>

As this list is extensive (and periodically changes), it is vital to use
a properly designed security architecture and robust design when dealing
with user supplied inputs influencing the choice of server side
filenames and access.

Although PHP examples have been given, this attack is also applicable in
different ways to .NET and J2EE. Applications written in those
frameworks need to pay particular attention to code access security
mechanisms to ensure that filenames supplied by or influenced by the
user do not allow security controls to be obviated.

For example, it is possible that XML documents submitted by an attacker
will have a hostile DTD that forces the XML parser to load a remote DTD,
and parse and process the results. An Australian security firm has
demonstrated this approach to port scanning behind firewalls. See
\[SIF01\] in this chapter’s references for more information.

The damage this particular vulnerability causes is directly related to
the strength of the sandbox / platform isolation controls in the
framework. As PHP is rarely isolated and has no sandbox concept or
security architecture, the damage is far worse for an attack than other
platforms with limited or partial trust, or are contained within a
suitable sand box, such as when a web app is running under a JVM with
the security manager properly enabled and configured (which is rarely
the default).

## Verifying Security

Automated approaches: Vulnerability scanning tools will have difficulty
identifying the parameters that are used in a file include or the syntax
for making them work. Static analysis tools can search for the use of
dangerous APIs, but cannot verify that appropriate validation or
encoding might be in place to protect against the vulnerability.

Manual approaches: A code review can search for code that might allow a
file to be included in the application, but there are many possible
mistakes to recognize. Testing can also detect these vulnerabilities,
but identifying the particular parameters and the right syntax can be
difficult.

## Protection

Preventing remote file include flaws takes some careful planning at the
architectural and design phases, through to thorough testing. In
general, a well-written application will not use user-supplied input in
any filename for any server-based resource (such as images, XML and XSL
transform documents, or script inclusions), and will have firewall rules
in place preventing new outbound connections to the Internet or
internally back to any other server. However, many legacy applications
will continue to have a need to accept user supplied input.

Among the most important considerations are:

  - **Use an indirect object reference map** (see section A4 for more
    details). For example, where a partial filename was once used,
    consider a hash of the partial reference. Instead of :

<code><select name=”language”>
`   `<option value=”English”>`English`</option></code>

use

<code><select name=”language”>
`   `<option value=”78463a384a5aa4fad5fa73e2f506ecfc”>`English`</option></code>

Consider using salts to prevent brute forcing of the indirect object
reference. Alternatively, just use index values such as 1, 2, 3, and
ensure that the array bounds are checked to detect parameter tampering.

  - **Use explicit taint checking mechanisms**, if your language
    supports it. Otherwise, consider a variable naming scheme to assist
    with taint checking:

`$hostile = &$_POST; // refer to POST variables, not $_REQUEST`
`$safe[‘filename’]= validate_file_name($hostile[‘unsafe_filename’]); //
make it safe`

Therefore any operation based upon hostile input is immediately obvious:

` WRONG:
 `<span style="color: red">`require_once($_POST[‘unsafe_filename’] .
‘inc.php’);`</span>` `
`RIGHT: require_once($safe[‘filename’] . ‘inc.php’);`

  - **Strongly validate user** input using "accept known good" as a
    strategy
  - **Add firewall** rules to prevent web servers making new connections
    to external web sites and internal systems. For high value systems,
    isolate the web server in its own VLAN or private subnet
  - **Check any user supplied files or filenames** taken from the user
    for legitimate purposes, which cannot obviate other controls.
    Otherwise be obviated, tainting could include user supplied data in
    the session object, avatars and images, PDF reports, temporary
    files, and so on [What is meant by "otherwise be obviated"? I think
    there's a problem here](category:FIXME "wikilink")
  - '''Consider implementing a chroot jail '''or other sand box
    mechanisms such as virtualization to isolate applications from each
    other
  - **PHP:** **Disable allow_url_fopen and allow_url_include** in
    php.ini and consider building PHP locally to not include this
    functionality. Very few applications need this functionality and
    thus these settings should be enabled on a per application basis
  - **PHP: Disable register_globals and use E_STRICT to find
    uninitialized variables**
  - **PHP: Ensure that all file and streams functions (stream_\*)**
    **are carefully vetted**. Ensure that the user input is not supplied
    any function which takes a filename argument, including:

`include() include_once() require() require_once() fopen()
imagecreatefromXXX() file() file_get_contents() copy() delete() unlink()
upload_tmp_dir() $_FILES move_uploaded_file()`

  - PHP: Be extremely cautious if data is passed to system() eval()
    passthru() or \` (the backtick operator).
  - With J2EE, ensure that the security manager is enabled and properly
    configured and that the application is demanding permissions
    appropriately
  - With ASP.NET, please refer to the documentation on partial trust,
    and design your applications to be segmented in trust, so that most
    of the application exists in the lowest possible trust state
    possible

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0360>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5220>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4722>

## References

  - CWE: CWE-98 (PHP File Inclusion), CWE-78 (OS Command Injection),
    CWE-95 (Eval injection), CWE-434 (Unrestricted file upload)
  - WASC Threat Classification:

<http://www.webappsec.org/projects/threat/classes/os_commanding.shtml>

  - OWASP Development Guide, [Includes and Remote
    Files](File_System#Includes_and_Remote_files "wikilink")
  - OWASP Testing Guide, [Testing for Path
    Traversal](Testing_for_Path_Traversal_\(OWASP-AZ-001\) "wikilink")
  - OWASP PHP Top 5, [Remote Code
    Execution](PHP_Top_5#P1:_Remote_Code_Execution "wikilink")
  - Stefan Esser,

<http://blog.php-security.org/archives/45-PHP-5.2.0-and-allow_url_include.html>

  - \[SIF01\] SIFT,Sift Networks, Web Services: Teaching an old dog new
    tricks,
    <http://www.ruxcon.org.au/files/2006/web_services_security.ppt>
  - [Defining a Java Security
    Policy](OWASP_Java_Table_of_Contents#Defining_a_Java_Security_Policy "wikilink")
  - Microsoft - Programming for Partial Trust,
    \[<http://msdn2.microsoft.com/en-us/library/ms364059(VS.80>).aspx
    <http://msdn2.microsoft.com/en-us/library/ms364059(VS.80>).aspx\]