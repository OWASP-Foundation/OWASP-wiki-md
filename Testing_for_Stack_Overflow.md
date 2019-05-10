## Summary

[Stack overflows](Stack_overflow "wikilink") occur when variable size
data is copied into fixed length buffers located on the program stack
without any bounds checking. Vulnerabilities of this class are generally
considered to be of high severity since their exploitation would mostly
permit arbitrary code execution or Denial of Service. Rarely found in
interpreted platforms, code written in C and similar languages is often
ridden with instances of this vulnerability. In fact almost every
platform is vulnerable to stack overflows with the following notable
exceptions:

  - J2EE – as long as native methods or system calls are not invoked
  - .NET – as long as /unsafe or unmanaged code is not invoked (such as
    the use of P/Invoke or COM Interop)
  - PHP – as long as external programs and vulnerable PHP extensions
    written in C or C++ are not called can suffer from stack overflow
    issues.

Stack overflow vulnerabilities often allow an attacker to directly take
control of the instruction pointer and, therefore, alter the execution
of the program and execute arbitrary code. Besides overwriting the
instruction pointer, similar results can also be obtained by overwriting
other variables and structures, like Exception Handlers, which are
located on the stack.

## How to Test

### Black Box testing

The key to testing an application for stack overflow vulnerabilities is
supplying overly large input data as compared to what is expected.
However, subjecting the application to arbitrarily large data is not
sufficient. It becomes necessary to inspect the application’s execution
flow and responses to ascertain whether an overflow has actually been
triggered or not. Therefore, the steps required to locate and validate
stack overflows would be to attach a debugger to the target application
or process, generate malformed input for the application, subject the
application to malformed input, and inspect responses in a debugger. The
debugger allows the tester to view the execution flow and the state of
the registers when the vulnerability gets triggered.

On the other hand, a more passive form of testing can be employed, which
involves inspecting assembly code of the application by using
disassemblers. In this case, various sections are scanned for signatures
of vulnerable assembly fragments. This is often termed as reverse
engineering and is a tedious process.

As a simple example, consider the following technique employed while
testing an executable “sample.exe” for stack overflows:

    #include<stdio.h>
    int main(int argc, char *argv[])
    {
      char buff[20];
      printf("copying into buffer");
      strcpy(buff,argv[1]);
      return 0;
    }

File sample.exe is launched in a debugger, in our case OllyDbg.

[image:stack overflow
vulnerability.gif](image:stack_overflow_vulnerability.gif "wikilink")

Since the application is expecting command line arguments, a large
sequence of characters such as ‘A’, can be supplied in the argument
field shown above.

On opening the executable with the supplied arguments and continuing
execution the following results are obtained.

[image:stack overflow vulnerability
2.gif](image:stack_overflow_vulnerability_2.gif "wikilink")

As shown in the registers window of the debugger, the EIP or Extended
Instruction Pointer, which points to the next instruction to be
executed, contains the value ‘41414141’. ‘41’ is a hexadecimal
representation for the character ‘A’ and therefore the string ‘AAAA’
translates to 41414141.

This clearly demonstrates how input data can be used to overwrite the
instruction pointer with user-supplied values and control program
execution. A stack overflow can also allow overwriting of stack-based
structures like SEH (Structured Exception Handler) to control code
execution and bypass certain stack protection mechanisms.

As mentioned previously, other methods of testing such vulnerabilities
include reverse engineering the application binaries, which is a complex
and tedious process, and using fuzzing techniques.

### Gray Box testing

When reviewing code for stack overflows, it is advisable to search for
calls to insecure library functions like gets(), strcpy(), strcat() etc
which do not validate the length of source strings and blindly copy data
into fixed size buffers.

For example consider the following function:-

    void log_create(int severity, char *inpt) {

    char b[1024];

    if (severity == 1)
    {
    strcat(b,”Error occurred on”);
    strcat(b,":");
    strcat(b,inpt);


    FILE *fd = fopen ("logfile.log", "a");
    fprintf(fd, "%s", b);
    fclose(fd);

    . . . . . .
    }

From above, the line strcat(b,inpt) will result in a stack overflow if
inpt exceeds 1024 bytes. Not only does this demonstrate an insecure
usage of strcat, it also shows how important it is to examine the length
of strings referenced by a character pointer that is passed as an
argument to a function; In this case the length of string referenced by
char \*inpt. Therefore it is always a good idea to trace back the source
of function arguments and ascertain string lengths while reviewing code.

Usage of the relatively safer strncpy() can also lead to stack overflows
since it only restricts the number of bytes copied into the destination
buffer. If the size argument that is used to accomplish this is
generated dynamically based on user input or calculated inaccurately
within loops, it is possible to overflow stack buffers. For <example:->

    void func(char *source)
    {
    Char dest[40];
    …
    size=strlen(source)+1
    ….
    strncpy(dest,source,size)
    }

where source is user controllable data. A good example would be the
samba trans2open stack overflow vulnerability
(http://www.securityfocus.com/archive/1/317615).

Vulnerabilities can also appear in URL and address parsing code. In such
cases, a function like memccpy() is usually employed which copies data
into a destination buffer from source until a specified character is not
encountered. Consider the function:

    void func(char *path)
    {
    char servaddr[40];
    …
    memccpy(servaddr,path,'\');
    ….
    }

In this case the information contained in path could be greater than 40
bytes before ‘\\’ can be encountered. If so it will cause a stack
overflow. A similar vulnerability was located in Windows RPCSS subsystem
(MS03-026). The vulnerable code copied server names from UNC paths into
a fixed size buffer until a ‘\\’ was encountered. The length of the
server name in this case was controllable by users.

Apart from manually reviewing code for stack overflows, static code
analysis tools can also be of great assistance. Although they tend to
generate a lot of false positives and would barely be able to locate a
small portion of defects, they certainly help in reducing the overhead
associated with finding low hanging fruits, like strcpy() and sprintf()
bugs. A variety of tools like RATS, Flawfinder and ITS4 are available
for analyzing C-style languages.

## Tools

  - OllyDbg: "A windows based debugger used for analyzing buffer
    overflow vulnerabilities" - <http://www.ollydbg.de>
  - Spike, A fuzzer framework that can be used to explore
    vulnerabilities and perform length testing -
    <http://www.immunitysec.com/downloads/SPIKE2.9.tgz>
  - Brute Force Binary Tester (BFB), A proactive binary checker -
    <http://bfbtester.sourceforge.net/>
  - Metasploit, A rapid exploit development and Testing frame work -
    <http://www.metasploit.com>

## References

**Whitepapers**
\* Aleph One: "Smashing the Stack for Fun and Profit" -
<http://insecure.org/stf/smashstack.html>

  - The Samba trans2open stack overflow vulnerability -
    <http://www.securityfocus.com/archive/1/317615>
  - Windows RPC DCOM vulnerability details -
    <http://www.xfocus.org/documents/200307/2.html>