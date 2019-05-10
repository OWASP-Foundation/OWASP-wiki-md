## JBroFuzz Frequently Asked Questions (FAQ)

### Q: What can I find within this section?

Frequently asked questions cover basic guidelines and pointers towards
aspects of using JBroFuzz, it's purpose and underlying philosophy.

More detailed information, can be found in the Help Topics section,
under `Help -> Topics`.

### Q: Fancy wording what does JBroFuzz actually do?

JBroFuzz has the ability to send intentionally malformed data to any web
server, recording the responses.

This yields testing certain aspects of the security of web servers, by
crafting corresponding requests and reviewing the responses received.

The term stateless simply implies that the different requests/replies
being generated do not depend on previous ones made.

### Q: What JBroFuzz is not claiming to be..

The automated answer to your problems regarding sending a bunch of AAA's
to a listening web service.

Unfortunately, you still have to know a bit about fuzzing web
applications, HTTP and HTTPS, headers GET and POST statements, etc.

## System Requirements

### Q: What operating systems has JBroFuzz been tested on?

JBroFuzz has been tested on the following operating systems: Mac OSX,
Win32, RHEL 4, Centos 4.x, Backtrack 3.

Also, you will need to have Java 1.6 or greater installed on your
system. For more details, view the Java FAQ section, below.

### Q: What permissions do I need to run JBroFuzz?

You will require write permissions within the directory that you execute
JBroFuzz from.

Each time you run JBroFuzz a directory structure for holding all the
corresponding files generated while using the tool is created.

## Java

### Q: How do I run the .jar file?

Say the file you want to run is named: JBroFuzz.jar

From the command line type the following:

`>>java -jar JBroFuzz.jar`

You will need to have Java installed on your system. It's probably worth
checking: <http://www.java.sun.com>

### Q: Do I need a Java Runtime Environment (JRE)?

Yes. JBroFuzz will run on any platform for which a JRE is available.

JREs for Windows, Linux and Solaris can be obtained for free from
<http://java.sun.com/j2se/downloads.html>

### Q: How much memory should I launch JBroFuzz with?

By default the JRE settings are typically limited to 64 Mb of memory. If
JBroFuzz is to be used for memory intensive operations, it is advised to
use 256 Mb of memory.

Say the file you want to run with 256Mb of available memory is named:
JBroFuzz.jar

From the command line type the following:

`>>java -jar -Xmx256m JBroFuzz.jar`

You will need to have Java installed on your system. It's probably worth
checking: <http://www.java.sun.com>

### Q: What version of Java does JBroFuzz require to run?

JDK/JRE 1.6 or later.

## Installation

### Q: What files is JBroFuzz released in?

There is a standalone executable (.exe), a standalone java archive
(.jar) and an installer (.msi) for win32 platforms.

  - JBroFuzz.exe The standalone executable requiring no further
    installation, simply run the file.
  - JBroFuzz.jar The standalone, platform independent java archive
    requiring no further installation, simply run the file.
  - JBroFuzz.msi An installer available for win32 platforms.

### Q: Do I need to install JBroFuzz?

No. JBroFuzz can be run as a standalone executable or java archive with
all the functionality and features enabled.

### Q: I run the exe or jar and the folder jbrofuzz does not get created, what's wrong?

For most browsers, if you select to run the exe / jar after it has
finished downloading through the web browser, you will be limited to the
security policy in place.

Typically, this will not allow the application to create any files or
folders within the downloaded location.

Run the exe or jar file through the operating system, instead of the
browser. Alternatively, download and install JBroFuzz using the msi
installer.

### Q: How can I download the latest copy of JBroFuzz?

JBroFuzz is an OWASP Project. It is free to download and open source.

To make sure you are running the latest version select "Check for
Updates..." from the Options menu, within the application.

## Files & Directories

### Q: What files and directories get created when I launch JBroFuzz?

At launch JBroFuzz creates the following folders within the directory in
which it is.

`jbrofuzz` `| fuzz` `| 001 2009-01-01 10-10-50`

The final directory (a timestamp) is where all file fuzzing data is
stored in individual files.

## Fuzzers & Payloads

### Q: What is a Fuzzer?

A fuzzer is a collection of payloads. A fuzzer contains a particular
character set which will be tested against the specified range of the
request.

Some examples of fuzzers:

  - Sending all requests of : 0000 to 1111 (binary prototype over 4
    characters)
  - Sending all requests of : 00 to 99 (decimal prototype over 2
    characters).

To get a better understanding of how fuzzers work, view the tutorial
demo that is available for download.

### Q: Where are all the fuzzer definitions stored?

All fuzzer definitions are loaded from the file fuzzers.jbrf

This is an internal file within JBroFuzz and can be found inside the
JBroFuzz.jar java archive.

### Q: How do I learn more about fuzzing?

An attempt to define the term can be found on the spike mailing list:

<http://marc2.theaimsgroup.com/?l=spike&m=105606327823227&w=2>

<http://www.scadasec.net/secwiki/FuzzingTools>

## Older Features/Versions

### Q: Where is the "Web Directories" tab?

The "Web Directories" tab was removed in version 1.2.

The original list of directories (directories.jbrofuzz) that was being
used in JBroFuzz can still be found in distributions of
[DirBuster](http://www.owasp.org/index.php/Category:OWASP_DirBuster_Project).

As
[DirBuster](http://www.owasp.org/index.php/Category:OWASP_DirBuster_Project)
is a dedicated tool focusing on directory enumeration, it is suggested
you use that tool.

[Category:OWASP JBroFuzz](Category:OWASP_JBroFuzz "wikilink")