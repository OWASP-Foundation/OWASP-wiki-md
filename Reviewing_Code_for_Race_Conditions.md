__TOC__

## Introduction

Race Conditions occur when a piece of code does not work as it is
supposed to (like many security issues). They are the result of an
unexpected ordering of events, which can result in the finite state
machine of the code to transition to a undefined state, and also give
rise to contention of more than one thread of execution over the same
resource. Multiple threads of execution acting or manipulating the same
area in memory or persisted data which gives rise to integrity issues.

## How They Work

With competing tasks manipulating the same resource, we can easily get a
race condition as the resource is not in step-lock or utilises a token
based multi-use system such as semaphores.

Say we have two processes (Thread 1, T1) and (Thread 2, T2). The code in
question adds 10 to an integer X. The initial value of X is 5.

`X = X + 10`

With no controls surrounding this code in a multithreaded environment,
we get the following problem:

`T1 places X into a register in thread 1`
`T2 places X into a register in thread 2`
`T1 adds 10 to the value in T1's register resulting in 15`
`T2 adds 10 to the value in T2's register resulting in 15`
`T1 saves the register value (15) into X.`
`T1 saves the register value (15) into X.`

The value should actually be 25, as each thread added 10 to the initial
value of 5. But the actual value is 15 due to T2 not letting T1 save
into X before it takes a value of X for its addition.

## How to Locate the Potentially Vulnerable Code

### .NET

Look for code which used multithreaded environments:

`Thread`
`System.Threading`
`ThreadPool`
`System.Threading.Interlocked`

### Java

`java.lang.Thread`
`start()`
`stop()`
`destroy()`
`init()`
`synchronized `
`wait()`
`notify()`
`notifyAll()`

### Classic ASP

Multithreading is not a directly supported feature of classic ASP, so
this kind of race condition could be present only when using COM
objects.

## Vulnerable Patterns for Race Conditions

Static methods (One per class, not one per object) are an issue
particularly if there is a shared state among multiple threads. For
example, in Apache, struts static members should not be used to store
information relating to a particular request. The same instance of a
class can be used by multiple threads, and the value of the static
member can not be guaranteed.

Instances of classes do not need to be thread safe as one is made per
operation/request. Static states must be thread safe.

1.  References to static variables, these must be thread locked.
2.  Releasing a lock in places other then finally{} may cause issues
3.  Static methods that alter static state

## Related Articles

<http://msdn2.microsoft.com/en-us/library/f857xew0(vs.71>).aspx

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")
[TOCTTOU](Category:Data_Integrity "wikilink") [the second category
doesn't exist; which should be there?](Category:FIXME "wikilink")
[Category:Externally Linked
Page](Category:Externally_Linked_Page "wikilink")