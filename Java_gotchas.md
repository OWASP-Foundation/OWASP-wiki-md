__TOC__

## Equality

Object equality is tested using the == operator, while value equality is
tested using the .equals(Object) method.

For example:

`String one = new String("abc");`
`String two = new String("abc");`
`String three = one;`
`if (one != two) System.out.println("The two objects are not the same.");`
`if (one.equals(two)) System.out.println("But they do contain the same value");`
`if (one == three) System.out.println("These two are the same, because they use the same reference.");`

The output is:

`The two objects are not the same.`
`But they do contain the same value`
`These two are the same, because they use the same reference.`

Also, be aware that:

`String abc = "abc"`

and

`String abc = new String("abc");`

are different. For example, consider the following:

`String letters = "abc";`
`String moreLetters = "abc";`
`System.out.println(letters==moreLetters);`

The output is:

`true`

This is due to the compiler and runtime efficiency. In the compiled
class file only one set of data "abc" is stored, not two. In this
situation only one object is created, therefore the equality is true
between these object. However, consider this:

`String data = new String("123");`
`String moreData = new String("123");`
`System.out.println(data==moreData);`

The output is:

`false`

Even though one set of data "123" is stored in the class, this is still
treated differently at runtime. An explicit instantiation is used to
create the String objects. Therefore, in this case, two objects have
been created, so the equality is false. It is important to note that
"==" is always used for object equality and does not ever refer to the
values in an object. Always use .equals when checking looking for a
"meaningful" comparison.

## Immutable Objects / Wrapper Class Caching

Since Java 5, wrapper class caching was introduced. The following is an
examination of the cache created by an inner class, IntegerCache,
located in the Integer cache. For example, the following code will
create a cache:

`Integer myNumber = 10`

or

`Integer myNumber = Integer.valueOf(10);`

256 Integer objects are created in the range of -128 to 127 which are
all stored in an Integer array. This caching functionality can be seen
by looking at the inner class, IntegerCache, which is found in Integer:

```
 private static class IntegerCache
 {
   private IntegerCache(){}

   static final Integer cache[] = new Integer[-(-128) + 127 + 1];

   static
   {
     for(int i = 0; i < cache.length; i++)
     cache[i] = new Integer(i - 128);
   }
 }

 public static Integer valueOf(int i)
 {
    final int offset = 128;
    if (i >= -128 && i <= 127) // must cache
        {
        return IntegerCache.cache[i + offset];
    }
        return new Integer(i);
 }
```

So when creating an object using Integer.valueOf or directly assigning a
value to an Integer within the range of -128 to 127 the same object will
be returned. Therefore, consider the following example:

`Integer i = 100;`
`Integer p = 100;`
`if (i == p)  System.out.println("i and p are the same.");`
`if (i != p)   System.out.println("i and p are different.");    `
`if(i.equals(p))  System.out.println("i and p contain the same value.");`

The output is:

`i and p are the same.`
`i and p contain the same value.`

It is important to note that object i and p only equate to true because
they are the same object, the comparison is not based on the value, it
is based on object equality. If Integer i and p are outside the range of
-128 or 127 the cache is not used, therefore new objects are created.
When doing a comparison for value always use the “.equals” method. It is
also important to note that instantiating an Integer does not create
this caching. So consider the following example:

`Integer i = new Integer (100);`
`Integer p = new Integer(100);`
`if(i==p) System.out.println(“i and p are the same object”);`
`if(i.equals(p)) System.out.println(“ i and p contain the same value”);`

In this circumstance, the output is only:

`i and p contain the same value`

Remember that “==” is always used for object equality, it has not been
overloaded for comparing unboxed values.

This behavior is documented in the [Java Language
Specification](http://java.sun.com/docs/books/jls)
[section 5.1.7](http://java.sun.com/docs/books/jls/third_edition/html/conversions.html#5.1.7).
Quoting from there:

  -
    If the value *p* being boxed is true, false, a byte, a char in the
    range \\u0000 to \\u007f, or an int or short number between -128 and
    127, then let *r1* and *r2* be the results of any two boxing
    conversions of *p*. It is always the case that *r1* == *r2*.

The other wrapper classes (Byte, Short, Long, Character) also contain
this caching mechanism. The Byte, Short and Long all contain the same
caching principle to the Integer object. The Character class caches from
0 to 127. The negative cache is not created for the Character wrapper as
these values do not represent a corresponding character. There is no
caching for the Float object.

BigDecimal also uses caching but uses a different mechanism. While the
other objects contain a inner class to deal with caching this is not
true for BigDecimal, the caching is pre-defined in a static array and
only covers 11 numbers, 0 to 10:

`// Cache of common small BigDecimal values.`
`private static final BigDecimal zeroThroughTen[] = {`
`new BigDecimal(BigInteger.ZERO,        0,  0),`
`new BigDecimal(BigInteger.ONE,     1,  0),`
`new BigDecimal(BigInteger.valueOf(2),  2,  0),`
`new BigDecimal(BigInteger.valueOf(3),  3,  0),`
`new BigDecimal(BigInteger.valueOf(4),  4,  0),`
`new BigDecimal(BigInteger.valueOf(5),  5,  0),`
`new BigDecimal(BigInteger.valueOf(6),  6,  0),`
`new BigDecimal(BigInteger.valueOf(7),  7,  0),`
`new BigDecimal(BigInteger.valueOf(8),  8,  0),`
`new BigDecimal(BigInteger.valueOf(9),  9,  0),`
`new BigDecimal(BigInteger.TEN,     10, 0),`
`};`

As per Java Language Specification(JLS) the values discussed above are
stored as immutable wrapper objects. This caching has been created
because it is assumed these values / objects are used more frequently.

## Incrementing Values

Be careful of the post-increment operator:

` int x = 5;`
` x = x++;`
` System.out.println( x );`

The output is:

`5`

Remember that the assignment completes before the increment, hence
post-increment. Using the pre-increment will update the value before the
assignment. For example:

`int x = 5;`
`x = ++x;`
`System.out.println( x );`

The output is:

`6`

## Garbage Collection

Overriding "finalize()" will allow you to define you own code for what
is potentially the same concept as a destructor. There are a couple of
important points to remember:

  - "finalize()" will only ever by called once (at most) by the Garbage
    Collector.
  - It is never a guarantee that "finalize()" will be called i.e. that
    an object will be garbage collected.
  - By overriding "finalize()" you can prevent an object from ever being
    deleted. For example, the object passes a reference of itself to
    another object.
  - Garbage collection behaviour differs between JVMs.

## Boolean Assignment

Everyone appreciates the difference between "==" and "=" in Java.
However, typos and mistakes are made, and often the compiler will catch
them. However, consider the following:

`boolean theTruth = false;`
`if (theTruth = true)`
`{`
` System.out.println("theTruth is true");`
`}`
`else`
`{`
` System.out.println("theTruth is false;");`
`}`

The result of any assignment expression is the value of the variable
following the assignment. Therefore, the above will always result in
"theTruth is true". This only applies to booleans, so for example the
following will not compile and would therefore be caught by the
compiler:

`int i = 1;`
`if(i=0) {}`

As "i" is and integer the comparison would evaluate to (i=0) as 0 is the
result of the assignment. A boolean would be expected, due the "if"
statement.

## Conditions

Be on the look out for any nested "else if". Consider the following code
example:

`int x = 3;`
`if (x==5) {}`
`else if (x<9)`
`{`
`  System.out.println("x is less than 9");`
`}`
`else if (x<6)`
`{`
`  System.out.println("x is less than 6");`
`}`
`else`
`{`
`  System.out.println("else");`
`}`

Produces the output:

`x is less then 9`

So even though the second "else if" would equate to "true" it is never
reached. This is because once an "else if" succeeds the remaining
conditions will be not be processed.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")