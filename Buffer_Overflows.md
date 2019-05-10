[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__'''

## Objective

To ensure that:

  - Applications do not expose themselves to faulty components.

<!-- end list -->

  - Applications create as few buffer overflows as possible.

<!-- end list -->

  - Developers are encouraged to use languages and frameworks that are
    relatively immune to buffer overflows.

## Platforms Affected

Almost every platform, with the following notable exceptions:

  - Java/J2EE – as long as native methods or system calls are not
    invoked.

<!-- end list -->

  - .NET – as long as unsafe or unmanaged code is not invoked (such as
    the use of P/Invoke or COM Interop).

<!-- end list -->

  - PHP, Python, Perl – as long as external programs or vulnerable
    extensions are not used.

## Relevant COBIT Topics

DS11.9 – Data processing integrity.

## Description

Attackers generally use [buffer overflows](Buffer_Overflow "wikilink")
to corrupt the execution stack of a web application. By sending
carefully crafted input to a web application, an attacker can cause the
web application to execute arbitrary code, possibly taking over the
machine. Attackers have managed to identify buffer overflows in a
staggering array of products and components.

Buffer overflow flaws can be present in both the web server and
application server products that serve the static and dynamic portions
of a site, or in the web application itself. Buffer overflows found in
commonly-used server products are likely to become widely known and can
pose a significant risk to users of these products. When web
applications use libraries, such as a graphics library to generate
images or a communications library to send e-mail, they open themselves
to potential buffer overflow attacks. Literature detailing buffer
overflow attacks against commonly-used products is readily available,
and newly discovered vulnerabilities are reported almost daily.

Buffer overflows can also be found in custom web application code, and
may even be more likely, given the lack of scrutiny that web
applications typically go through. Buffer overflow attacks against
customized web applications can sometimes lead to interesting results.
In some cases, we have discovered that sending large inputs can cause
the web application or the back-end database to malfunction. It is
possible to cause a denial of service attack against the web site,
depending on the severity and specific nature of the flaw. Overly large
inputs could cause the application to display a detailed error message,
potentially leading to a successful attack on the system.

Buffer overflow attacks generally rely upon two techniques (and usually
the combination):

  - Writing data to particular memory addresses

<!-- end list -->

  - Having the operating system mishandle data types

<!-- end list -->

  - This means that strongly-typed programming languages (and
    environments) that disallow direct memory access usually prevent
    buffer overflows from happening.

| Language/Environment | Compiled or Interpreted          | Strongly Typed | Direct Memory Access | Safe or Unsafe |
| -------------------- | -------------------------------- | -------------- | -------------------- | -------------- |
|                      | Java, Java Virtual Machine (JVM) |                | Both                 |                |
|                      | .NET                             |                | Both                 |                |
|                      | Perl                             |                | Both                 |                |
|                      | Python - interpreted             |                | Intepreted           |                |
|                      | Ruby                             |                | Interpreted          |                |
|                      | C/C++                            |                | Compiled             |                |
|                      | Assembly                         |                | Compiled             |                |
|                      | COBOL                            |                | Compiled             |                |
|                      |                                  |                |                      |                |

Table 8.1: Language descriptions

## General Prevention Techniques

A number of general techniques to prevent buffer overflows include:

  - Code auditing (automated or manual)

<!-- end list -->

  - Developer training – bounds checking, use of unsafe functions, and
    group standards

<!-- end list -->

  - Non-executable stacks – many operating systems have at least some
    support for this

<!-- end list -->

  - Compiler tools – StackShield, StackGuard, and Libsafe, among others

<!-- end list -->

  - Safe functions – use strncat instead of strcat, strncpy instead of
    strcpy, etc

<!-- end list -->

  - Patches – Be sure to keep your web and application servers fully
    patched, and be aware of bug reports relating to applications upon
    which your code is dependent.

<!-- end list -->

  - Periodically scan your application with one or more of the commonly
    available scanners that look for buffer overflow flaws in your
    server products and your custom web applications.

## Stack Overflow

Stack overflows are the best understood and the most common form of
buffer overflows. The basics of a stack overflow is simple:

  - There are two buffers, a source buffer containing arbitrary input
    (presumably from the attacker), and a destination buffer that is too
    small for the attack input. The second buffer resides on the stack
    and somewhat adjacent to the function return address on the stack.

<!-- end list -->

  - The faulty code does *not* check that the source buffer is too large
    to fit in the destination buffer. It copies the attack input to the
    destination buffer, overwriting additional information on the stack
    (such as the function return address).

<!-- end list -->

  - When the function returns, the CPU unwinds the stack frame and pops
    the (now modified) return address from the stack.

<!-- end list -->

  - Control does not return to the function as it should. Instead,
    arbitrary code (chosen by the attacker when crafting the initial
    input) is executed.

The following example, written in C, demonstrates a stack overflow
exploit.

    #include <string.h>

    void f(char* s) {
        char buffer[10];
        strcpy(buffer, s);
    }

    void main(void) {
        f("01234567890123456789");
    }

    [root /tmp]# ./stacktest

    Segmentation fault

### How to determine if you are vulnerable

If your program:

  - is written in a language (or depends upon a program that is written
    in a language) that allows buffer overflows to be created (see Table
    8.1) AND

<!-- end list -->

  - copies data from one buffer on the stack to another without checking
    sizes first AND

<!-- end list -->

  - does not use techniques such as canary values or non-executable
    stacks to prevent buffer overflows THEN

it is likely that the application is vulnerable to attack.

### How to protect yourself

1.  Deploy on systems capable of using non-executable stacks, such as:
    1.  AMD and Intel x86-64 chips with associated 64-bit operating
        systems
    2.  Windows XP SP2 (both 32- and 64-bit)
    3.  Windows 2003 SP1 (both 32- and 64-bit)
    4.  Linux after 2.6.8 on AMD and x86-64 processors in 32- and 64-bit
        mode
    5.  OpenBSD (w^x on Intel, AMD, SPARC, Alpha and PowerPC)
    6.  Solaris 2.6 and later with the “noexec_user_stack” flag
        enabled
2.  Use higher-level programming languages that are strongly typed and
    that disallow direct memory access.
3.  Validate input to prevent unexpected data from being processed, such
    as being too long, of the wrong data type, containing "junk"
    characters, etc.
4.  If relying upon operating system functions or utilities written in a
    vulnerable language, ensure that they:
    1.  use the principle of least privilege
    2.  use compilers that protect against stack and heap overflows
    3.  are current in terms of patches

## Heap Overflow

Heap overflows are problematic in that they are not necessarily
protected by CPUs capable of using non-executable stacks. A heap is an
area of memory allocated by the application at run-time to store data.
The following example, written in C, shows a heap overflow exploit.

```
 #include <stdio.h>
 #include <stdlib.h>
 #include <unistd.h>
 #include <string.h>

 #define BSIZE 16
 #define OVERSIZE 8 /* overflow buf2 by OVERSIZE bytes */

 void main(void) {
    u_long b_diff;
    char *buf0 = (char*)malloc(BSIZE);      // create two buffers
    char *buf1 = (char*)malloc(BSIZE);

    b_diff = (u_long)buf1 - (u_long)buf0;   // difference between locations
    printf("Initial values:  ");
    printf("buf0=%p, buf1=%p, b_diff=0x%x bytes\n", buf0, buf1, b_diff);

    memset(buf1, 'A', BUFSIZE-1), buf1[BUFSIZE-1] = '\0';
    printf("Before overflow: buf1=%s\n", buf1);

    memset(buf0, 'B', (u_int)(diff + OVERSIZE));
    printf("After overflow:  buf1=%s\n", buf1);
}

[root /tmp]# ./heaptest

Initial values:  buf0=0x9322008, buf1=0x9322020, diff=0xff0 bytes
Before overflow: buf1=AAAAAAAAAAAAAAA
After overflow:  buf1=BBBBBBBBAAAAAAA
```

The simple program above shows two buffers being allocated on the heap,
with the first buffer being overflowed to overwrite the contents of the
second buffer.

### How to determine if you are vulnerable

If your program:

  - is written in a language (or depends upon a program that is written
    in a language) that allows buffer overflows to be created (see Table
    8.1) AND

<!-- end list -->

  - copies data from one buffer on the stack to another without checking
    sizes first AND

<!-- end list -->

  - does not use techniques such as canary values to prevent buffer
    overflows THEN

it is likely that the application is vulnerable to attack.

### How to protect yourself

1.  Use higher-level programming languages that are strongly typed and
    that disallow direct memory access.
2.  Validate input to prevent unexpected data from being processed, such
    as being too long, of the wrong data type, containing "junk"
    characters, etc.
3.  If relying upon operating system functions or utilities written in a
    vulnerable language, ensure that they:
    1.  use the principle of least privilege
    2.  use compilers that protect against stack and heap overflows
    3.  are current in terms of patches

## Format String

Format string buffer overflows (usually called "format string
vulnerabilities") are highly specialized buffer overflows that can have
the same effects as other buffer overflow attacks. Basically, format
string vulnerabilities take advantage of the mixture of data and control
information in certain functions, such as C/C++'s printf. The easiest
way to understand this class of vulnerability is with an example:

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <string.h>

    void main(void) {
        char str[100] = scanf("%s");
        printf("%s", str);
    }

This simple program takes input from the user and displays it back on
the screen. The string `%s` means that the other parameter, str, should
be displayed as a string. This example is *not* vulnerable to a format
string attack, but if one changes the last line, it becomes exploitable:

`   printf(str);`

To see how, consider the user entering the special input:

*%08x.%08x.%08x.%08x.%08x*

By constructing input as such, the program can be exploited to print the
first five entries from the stack.

### How to determine if you are vulnerable

If your program:

  - uses functions such as printf, snprintf directly, or indirectly
    through system services (such as syslog) or other AND

<!-- end list -->

  - the use of such functions allows input from the user to contain
    control information interpreted by the function itself

it is highly likely that the application is vulnerable to attack.

### How to protect yourself

1.  Use higher-level programming languages that are strongly typed and
    that disallow direct memory access.
2.  Validate input to prevent unexpected data from being processed, such
    as being too long, of the wrong data type, containing "junk"
    characters, etc. Specifically check for control information
    (meta-characters like '%')
3.  Avoid the use of functions like printf that allow user input to
    contain control information
4.  If relying upon operating system functions or utilities written in a
    vulnerable language, ensure that they:
    1.  use the principle of least privilege
    2.  use compilers that protect against stack and heap overflows
    3.  are current in terms of patches

## Unicode Overflow

Unicode exploits are a bit more difficult to do than typical buffer
overflows as demonstrated in Anley’s 2002 paper, but it is wrong to
assume that by using Unicode, you are protected against buffer
overflows. Examples of Unicode overflows include Code Red, a devastating
Trojan with an estimated economic cost in the billions of dollars.

### How to determine if you are vulnerable

If your program:

  - is written in a language (or depends upon a program that is written
    in a language) that allows buffer overflows to be created (see Table
    8.1) AND

<!-- end list -->

  - takes Unicode input from a user AND

<!-- end list -->

  - fails to sanitize the input AND

<!-- end list -->

  - does not use techniques such as canary values to prevent buffer
    overflows THEN

it is highly likely that the application is vulnerable to attack.

### How to protect yourself

1.  Deploy on systems capable of using non-executable stacks, such as:
    1.  AMD and Intel x86-64 chips with associated 64-bit operating
        systems
    2.  Windows XP SP2 (both 32- and 64-bit)
    3.  Windows 2003 SP1 (both 32- and 64-bit)
    4.  Linux after 2.6.8 on AMD and x86-64 processors in 32- and 64-bit
        mode
    5.  OpenBSD (w^x on Intel, AMD, SPARC, Alpha and PowerPC)
    6.  Solaris 2.6 and later with the “noexec_user_stack” flag
        enabled
2.  Use higher-level programming languages that are strongly typed and
    that disallow direct memory access.
3.  Validate input to prevent unexpected data from being processed, such
    as being too long, of the wrong data type, containing "junk"
    characters, etc.
4.  If relying upon operating system functions or utilities written in a
    vulnerable language, ensure that they:
    1.  use the principle of least privilege
    2.  use compilers that protect against stack and heap overflows
    3.  are current in terms of patches

## Integer Overflow

When an application takes two numbers of fixed word size and perform an
operation with them, the result may not fit within the same word size.
For example, if the two 8-bit numbers 192 and 208 are added together and
stored into another 8-bit byte, the result will not fit into an 8-bit
result:

'' 1100 0000''

'' + 1101 0000''

'' = 0001 1001 0000''

Although such an operation will usually cause some type of exception,
your application must be coded to check for such an exception and take
proper action. Otherwise, your application would report that 192 + 208
equals 144.

The following code demonstrates a buffer overflow, and was adapted from
[Blexim's Phrack
article](http://www.phrack.org/issues.html?issue=60&id=10#article):

    #include <stdio.h>
    #include <string.h>

    void main(int argc, char *argv[]) {
        int i = atoi(argv[1]);         // input from user
        unsigned short s = i;          // truncate to a short
        char buf[50];                  // large buffer

        if (s > 10) {                  // check we're not greater than 10
            return;
        }

        memcpy(buf, argv[2], i);       // copy i bytes to the buffer
        buf[i] = '\0';                 // add a null byte to the buffer
        printf("%s\n", buf);           // output the buffer contents

        return;
    }

    [root /tmp]# ./inttest 65580 foobar
    Segmentation fault

The above code is exploitable because the validation does not occur on
the input value (65580), but rather the value after it has been
converted to an unsigned short (45).

Integer overflows can be a problem in any language and can be exploited
when integers are used in array indices and implicit short math
operations.

### How to determine if you are vulnerable

  - Examine use of signed integers, bytes, and shorts.

<!-- end list -->

  - Are there cases where these values are used as array indices after
    performing an arithmetic operation (+, -, \*, /, or % (modulo))?

<!-- end list -->

  - How would your program react to a negative or zero value for integer
    values, particular during array lookups?

### How to protect yourself

  - If using .NET, use David LeBlanc’s SafeInt class or a similar
    construct. Otherwise, use a "BigInteger" or "BigDecimal"
    implementation in cases where it would be hard to validate input
    yourself.

<!-- end list -->

  - If your compiler supports the option, change the default for
    integers to be unsigned unless otherwise explicitly stated. Use
    unsigned integers whenever you don't need negative values.

<!-- end list -->

  - Use range checking if your language or framework supports it, or be
    sure to implement range checking yourself after all arithmetic
    operations.

<!-- end list -->

  - Be sure to check for exceptions if your language supports it.

## Further reading

  - Team Teso, *Exploiting Format String Vulnerabilities*

<u><http://crypto.stanford.edu/cs155/papers/formatstring-1.2.pdf></u>

  - Newsham, Tim, ''Format String Attacks

''<u><http://hackerproof.org/technotes/format/FormatString.pdf></u>

  - w00 w00 and Matt Conover, *Preliminary Heap Overflow Tutorial*

<u><http://www.w00w00.org/files/articles/heaptut.txt></u>

  - Chris Anley, *Creating Arbitrary Shellcode In Unicode Expanded
    Strings*

<u><http://www.ngssoftware.com/papers/unicodebo.pdf></u>

  - David Leblanc, ''Integer Handling with the C++ SafeInt Class ''

<u><http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dncode/html/secure01142004.asp></u>

  - Aleph One, *Smashing the Stack for fun and profit*

<u><http://www.phrack.org/issues.html?issue=49&id=14#article></u>

  - Mark Donaldson, *Inside the buffer Overflow Attack: Mechanism,
    method, & prevention*

<u><http://www.sans.org/reading_room/whitepapers/securecode/buffer-overflow-attack-mechanism-method-prevention_386></u>

  - *NX Bit*, Wikipedia article

<u><http://en.wikipedia.org/wiki/NX_bit></u>

  - Horizon'', How to bypass Solaris no execute stack protection

''<u><http://www.secinf.net/unix_security/How_to_bypass_Solaris_nonexecutable_stack_protection_.html></u>

  - Alexander Anisimov*, Defeating Microsoft Windows XP SP2 Heap
    protection and DEP bypass*, Positive Technologies

<u><http://www.ptsecurity.com/download/defeating-xpsp2-heap-protection.pdf></u>

  - Matt Conover, w00w00 on Heap Overflows, w00w00 Security Team

<u><http://www.w00w00.org/files/articles/heaptut.txt></u>

  - Blexim, ''Basic Integer Overflows

''<u><http://www.phrack.org/issues.html?issue=60&id=10#article></u>

  - StackShield

<u><http://www.angelfire.com/sk/stackshield/index.html></u>

  - StackGuard

<u><https://en.wikibooks.org/wiki/GNU_C_Compiler_Internals/Stackguard_4_1></u>
<u><http://static.usenix.org/publications/library/proceedings/sec98/full_papers/cowan/cowan_html/cowan.html></u>

  - Libsafe

<u><http://directory.fsf.org/wiki/Libsafe></u>


[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")