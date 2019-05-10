__TOC__

## Introduction:

Strings are not a defined Type in C or C++, but simply a contiguous
array of characters terminated by a null (\\0) character. The length of
the string is the amount of characters which precede the null character.
C++ does contain template classes which address this feature of the
programming language: **std::basic_string** and **std::string** These
classes address some security issues but not all.

*`'` `|W` `|E` `|L` `|C` `|O` `|M` `|E` `|\0` `|`*`'`

## Common String Errors

Common string errors can be related to mistakes in implementation, which
may cause drastic security and availability issues. C/C++ do not have
the comfort other programming languages provide, such as Java and C\#
.NET, relating to buffer overflows and such due to a String Type not
being defined.

Common issues include:

1.  Input validation errors
2.  Unbounded errors
3.  Truncation issues
4.  Out-of-bounds writes
5.  String Termination errors
6.  Off-by-one errors

Some of the issues mentioned above have been covered in the [Reviewing
Code for Buffer Overruns and
Overflows](Reviewing_Code_for_Buffer_Overruns_and_Overflows "wikilink")
section in this guide.

### Unbounded Errors

#### String Copies

Unbounded errors occur when data is copied from a unbounded source to a
fixed length character array.

`void main(void) {`
` char Name[10];`
` puts("Enter your name:");`
` gets(Name); <-- Here the name input by the user can be of arbitrary length over running the Name array.`
`...`
` }`

#### String Termination Errors

Failure to properly terminate strings with a null can result in system
failure.

`int main(int argc, char* argv[]) {`
` char a[16];`
` char b[16];`
` char c[32];`
` strncpy(a, "0123456789abcdef", sizeof(a));`
` strncpy(b, "0123456789abcdef", sizeof(b));`
` strncpy(c, a, sizeof(c));`
`}`

Verify that the following are used:

`strncpy() instead of strcpy()`
`snprintf() instead of sprintf()`
`fgets() instead of gets()`

#### Off by One Error

Looping through arrays should be looped in a n-1 manner, as we must
remember arrays and vectors start as 0. This is not specific to C/C++,
but Java and C\# also.)

Off-by-one errors are common to looping functionality, wherein a looping
functionality is performed on an object in order to manipulate the
contents of an object such as copy or add information. The off-by-one
error is a result of an error on the loop counting functionality.

`for (i = 0; i < 5; i++) {`
`   /* Do Stuff */`
`}`

Here i starts with a value of 0, it then increments to 1, then 2, 3 & 4.
When i reaches 5 then the condition i\<5 is false and the loop
terminates.

If the condition was set such that i\<=5 (less than or equal to 5), the
loop won’t terminate until i reaches 6, which may not be what is
intended.

Also, counting from 1 instead of 0 can cause similar issues, as there
would be one less iteration. Both of these issues relate to an
off-by-one error where the loop either under or over counts.

### Issues with Integers

#### Integer Overflows

When an integer is increased beyond its maximum range or decreased below
its minimum value, overflows occur. Overflows can be signed or unsigned.
Signed when the overflow carries over to the sign bit, unsigned when the
value being intended to be represented is no longer represented
correctly.

`int x;`
`x = INT_MAX; // 2,147,483,647`
`x++;`
*`Here``   ``x``   ``would``   ``have``   ``the``   ``value``   ``of``
 ``-2,147,483,648``   ``after``   ``the``   ``increment`*

It is important when reviewing the code that some measure should be
implemented such that the overflow does not occur. This is not the same
as relying on the value "never going to reach this value
(2,147,483,647)". This may be done by some supporting logic or a post
increment check.

`unsigned int y;`
`y = UINT_MAX; // 4,294,967,295;`
`y++;`
*`Here``   ``y``   ``would``   ``have``   ``a``   ``value``   ``of``
 ``0``   ``after``   ``the``   ``increment`*

Also, here we can see the result of an unsigned int being incremented,
which loops the integer back to the value 0. As before, this should also
be examined to see if there are any compensating controls to prevent
this from happening.

#### Integer Conversion

When converting from a signed to an unsigned integer, care must also be
taken to prevent a representation error.

`int x = -3;`
`unsigned short y;`
`y = x;`

*Here y would have the value of 65533 due to the loopback effect of the
conversion from signed to unsigned.*

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")