__TOC__

## The Buffer

A Buffer is an amount of contiguous memory set aside for storing
information. Example: A program has to remember certain things, like
what your shopping cart contains or what data was inputted prior to the
current operation. This information is stored in memory in a buffer.

## Related Security Activities

### Description of Buffer Overflow

See the OWASP article on [Buffer
Overflow](Buffer_overflow_attack "wikilink") Attacks.

See the OWASP article on [Buffer Overflow](Buffer_Overflow "wikilink")
Vulnerabilities.

### How to Avoid Buffer Overflow Vulnerabilities

See the [OWASP Development
Guide](:Category:OWASP_Guide_Project "wikilink") article on how to
[Avoid Buffer Overflow](Buffer_Overflows "wikilink") Vulnerabilities.

### How to Test for Buffer Overflow Vulnerabilities

See the [OWASP Testing
Guide](:Category:OWASP_Testing_Project "wikilink") article on how to
[Test for Buffer
Overflow](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")
Vulnerabilities.

## How to Locate the Potentially Vulnerable Code

In locating potentially vulnerable code from a buffer overflow
standpoint, one should look for particular signatures such as:

**Arrays**:

` int x[20];`
` int y[20][5];`
` int x[20][5][3];`

**Format Strings:**

` printf() ,fprintf(), sprintf(), snprintf().`
` %x, %s, %n, %d, %u, %c, %f`

**Over flows:**

` strcpy (), strcat (), sprintf (), vsprintf ()`

## Vulnerable Patterns for Buffer Overflows

### ‘Vanilla’ buffer overflow:

Example: A program might want to keep track of the days of the week (7).
The programmer tells the computer to store a space for 7 numbers. This
is an example of a buffer. But what happens if an attempt to add 8
numbers is performed? Languages such as C and C++ do not perform bounds
checking, and therefore if the program is written in such a language,
the 8th piece of data would overwrite the program space of the next
program in memory, and would result in data corruption. This can cause
the program to crash at a minimum or a carefully crafted overflow can
cause malicious code to be executed, as the overflow payload is actual
code.

` void copyData(char *userId) {  `
`    char  smallBuffer[`**`10`**`]; // size of 10  `
`    `**`strcpy`**`(smallBuffer, userId);`
` }  `
` int main(int argc, char *argv[]) {  `
` char *userId = "`**`01234567890`**`"; // Payload of 11`
` copyData (userId); // this shall cause a buffer overload`
` }`

Buffer overflows are the result of stuffing more code into a buffer than
it is meant to hold.

### The Format String:

A format function is a function within the ANSI C specification. It can
be used to tailor primitive C data types to human readable form. They
are used in nearly all C programs to output information, print error
messages, or process strings.

Some format parameters:

` %x        hexadecimal (unsigned int)`
` %s        string ((const) (unsigned) char *)`
` %n        number of bytes written so far, (* int)`
` %d        decimal (int)`
` %u        unsigned decimal (unsigned int)`

Example:

` printf ("Hello: %s\n", a273150);`

The %s in this case ensures that the parameter (a273150) is printed as a
string.

Through supplying the format string to the format function we are able
to control the behaviour of it. So supplying input as a format string
makes our application do things it's not meant to\! What exactly are we
able to make the application do?

### Crashing an application:

` printf (User_Input);`

If we supply %x (hex unsigned int) as the input, the **printf** function
shall expect to find an integer relating to that format string, but no
argument exists. This cannot be detected at compile time. At runtime
this issue shall surface.

### Walking the stack:

For every % in the argument the printf function finds it assumes that
there is an associated value on the stack. In this way the function
walks the stack downwards reading the corresponding values from the
stack and printing them to the user.

Using format strings we can execute some invalid pointer access by using
a format string such as:

` printf ("%s%s%s%s%s%s%s%s%s%s%s%s");`

Worse again is using the **%n** directive in **printf()**. This
directive takes an **int\*** and **writes** the number of bytes so far
to that location.

Where to look for this potential vulnerability. This issue is prevalent
with the **printf()** family of functions, **printf(),fprintf(),
sprintf(), snprintf().** Also **syslog()** (writes system log
information) and setproctitle(*const char \*fmt*, *...*); (which sets
the string used to display process identifier information).

### Integer overflows:

1.  include \<stdio.h\>

`   int main(void){`
`           int val;`
`           val = 0x7fffffff;   /* 2147483647*/`
`           printf("val = %d (0x%x)\n", val, val);`
`           printf("val + 1 = %d (0x%x)\n", val + 1 , val + 1); /*Overflow the int*/`
`           return 0;`
`   }`

The binary representation of 0x7fffffff is
1111111111111111111111111111111; this integer is initialized with the
highest positive value a signed long integer can hold.

Here when we add 1 to the hex value of 0x7fffffff the value of the
integer overflows and goes to a negative number (0x7fffffff + 1 =
80000000) In decimal this is (-2147483648). Think of the problems this
may cause\!\! Compilers will not detect this and the application will
not notice this issue.

We get these issues when we use signed integers in comparisons or in
arithmetic and also when comparing signed integers with unsigned
integers.

Example:

int myArray\[100\];

`   int fillArray(int v1, int v2){`
`       if(v2 > sizeof(myArray) / sizeof(int)){`
`           return -1; /* Too Big !! */`
`       }`
`       myArray [v2] = v1;`
`       return 0;`
`   }`

Here if v2 is a massive negative number so the '''''if '''''condition
shall pass. This condition checks to see if v2 is bigger than the array
size. The line **myArray\[v2\] = v1** assigns the value v1 to a location
out of the bounds of the array causing unexpected results.

## Good Patterns and Procedures to Prevent Buffer Overflows:

Example:

`void copyData(char *userId) {`
`   char  smallBuffer[10]; // size of 10`
`   strncpy(smallBuffer, userId, 10); // only copy first 10 elements`
`   smallBuffer[9] = 0; // Make sure it is terminated.`
`}`

`int main(int argc, char *argv[]) {`
`   char *userId = "01234567890"; // Payload of 11`
`   copyData (userId); // this shall cause a buffer overload`
`}`

The code above is not vulnerable to buffer overflow as the copy
functionality uses a specified length, 10.

C library functions such as **strcpy (), strcat (), sprintf ()** and
**vsprintf ()** operate on null terminated strings and perform no bounds
checking. **gets ()** is another function that reads input (into a
buffer) from stdin until a terminating newline or EOF (End of File) is
found. The **scanf ()** family of functions also may result in buffer
overflows.

Using strncpy(), strncat(), snprintf(), and fgets() all mitigate this
problem by specifying the maximum string length. The details are
slightly different and thus understanding their implications is
required.

Always check the bounds of an array before writing it to a buffer.

The Microsoft C runtime also provides additional versions of many
functions with an _s suffix (strcpy_s, strcat_s, sprintf_s). These
functions perform additional checks for error conditions and call an
error handler on failure.

(See Security Enhancements in the CRT)

<http://msdn2.microsoft.com/en-us/library/8ef0s5kh(VS.80>).aspx

## .NET & Java

C\# or C++ code in the .NET framework can be immune to buffer overflows
if the code is managed. Managed code is code executed by a .NET virtual
machine, such as Microsoft's. Before the code is run, the Intermediate
Language is compiled into native code. The managed execution
environment’s own runtime-aware complier performs the compilation;
therefore the managed execution environment can guarantee what the code
is going to do. The Java development language also does not suffer from
buffer overflows; as long as native methods or system calls are not
invoked, buffer overflows are not an issue. Finally ASP pages are also
immune to buffer overflows due to Integer Overflow checks performed by
the VBScript interpreter while executing the code.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")