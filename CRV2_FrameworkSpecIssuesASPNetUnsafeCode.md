# C\# Unsafe Code

Even though C\# has a strong memory management infrastructure, there
will be times when is necessary to direct access memory:

  - Dealing with existing structures on disk
  - Advanced COM or Platform Invoke scenarios that involve structures
    with pointers in them
  - Performance-critical code (Microsoft, 2009)

Microsoft strongly discourages the use of the unsafe code when this is
not necessary. It is clear that even when using unsafe code might
improve performance in the program, the risks might overcome the
benefits. Definitely, this is no area for inexperienced programmers.

Unsafe is used by declaring the “unsafe” keyword in the program code.
For example:

`class UnsafeTest {`
`  // Unsafe method: takes pointer to int:`
`  unsafe static void SquarePtrParam(int* p)`
`  {`
`     *p *= *p;`
`  }`
`  unsafe static void Main()`
`  {`
`     int i = 5;`
`     // Unsafe method: uses address-of operator (&):`
`     SquarePtrParam(&i);`
`     Console.WriteLine(i);`
`  }`
`}`
`// Output: 25`

## Risks of using Unsafe Code

Major risk involves

  - Buffer overflows
  - Unverifiable code
  - Pointer errors

## References

Microsoft, 2009 , Unsafe Code , available
athttp://msdn.microsoft.com/en-us/library/aa288474%28v=VS.71%29.aspx
(accessed on 01-07-2013)