## Introduction

*“If you can’t fuzz with JBroFuzz, you probably do not want to fuzz\!”*

<div align="right">

Old JBroFuzz Motto

</div>

The art of teaching, Mark Van Doren said, is the art of assisting
discovery. Fuzzing is a representative discipline towards assisting the
discovery of security vulnerabilities, that is just beginning to come of
age. Over the last two years, through continuous development, JBroFuzz
has attempted to expose the intrinsic beauty of the subject: Constantly
submit a vast amount of payloads to a service, device or prompt, waiting
for the one response that makes all the difference. This is the
mentality that JBroFuzz embraces and attempts to offer back to security
professionals.

Fuzzing as a concept goes beyond a conventional work flow or a standard
methodology. I would argue that to know how to fuzz well, is to master a
new language. Thus, similar to the process of learning a programming (or
foreign) language, there are three things you must master:

• Grammar: How fuzzing as a process is structured
• Vocabulary: How to name fuzzing concepts you want to use
• Usage: Ways of achieving everyday effective results with fuzzing
![001-JBroFuzz-Tutorial.jpg](001-JBroFuzz-Tutorial.jpg
"001-JBroFuzz-Tutorial.jpg")From the pre-existing information available
for JBroFuzz, this tutorial focuses on the vocabulary: Through a baptism
of fire, this fuzzing tool had to develop a process for storing and
making different payloads available for fuzzing. This section details
the way this process has evolved during the continuous development of
JBroFuzz.

The type of syntax in this section does not relate to coding examples,
but more towards how fuzzers are grouped into categories and how the
corresponding categories form a collection of payloads for different
vulnerability types.

To summarise, this second part of the tutorial looks at what the
primitive concepts employed by JBroFuzz are and how they are put to use.
Without further redo, let’s get fuzzing\!

## Fuzzer Categories and Types

Fuzzing is all about different responses, substantially different
responses, ideally obtained through a single iterative process of
transmitting sequencial requests. What ties together in similarity these
requests defines a black art similar to the one seen in semiconductor
design. In the realm of predominately stateless web applications, during
a fuzzing session, your objective is to achieve the maximum difference
in responses, utilising the smallest possible sequence of requests. Each
request will carry a unique payload related to the previous as well as
the next request value. For the needs of penetration testing, defining
the shortest possible sequence of payloads to prove the existence of a
security vulnerability defines a good fuzzing session.

Thus, it could be argued that one the characteristics for the successful
fuzzing of web applications, follows Okkam's razor: it is vain to put
more payloads on the wire, than the sequence required for identifying a
particular vulnerability. In turn, cross combining common payload
characteristics for different vulnerability categories, actually could
prove the existence of more than one vulnerability (e.g. XSS and SQL
Injection) during a single fuzzing session. From this, it becomes
apparent that the number of payloads typically used for identifying the
presence of a security vulnerability vary in many orders of magnitude,
compared to the often single payload transmitted to illustrate its
existence.

### What is a Fuzzer?

The following list represents a number of axioms according to which
JBroFuzz defines and uses fuzzing concepts.

  - A fuzzer is a set of payloads
  - The algorithm that defines how the payloads of a fuzzer get combined
    in sequential order, defines the type of fuzzer
  - A prototype is the base form description (a bit like a signature)
    from which a fuzzer can be created

Ergo within JBroFuzz, prototype definitions are stored in a file called
fuzzers.jbrf. Each prototype corresponds to a fuzzer, containing
information such as the type of fuzzer, the number of payloads it has,
etc.

Finally, a fuzzing database is collection of fuzzers, as constructed by
a set of prototypes. Welcome to the org.owasp.jbrofuzz.core library\!

### Categories

JBroFuzz contains approximately 50 fuzzers, grouped in a number
categories. Each fuzzer is a collection of payloads that are used (at
fuzzing runtime) in different ways. There are also different types of
fuzzers.

In the eyes of a developer, a fuzzer in JBroFuzz is a java Iterator,
i.e. a piece of code that loops through the corresponding values it has.
Once the iteration is over, fuzzing stops.

In order to trigger this iteration process, a user must select their
fuzzer of choice, based on a number of categories that it belongs to.
Examples include, SQL Injection, to Cross Site Scripting (XSS) 101, to
the Octal number system.

Each fuzzer has a number of different payloads, these are numbered in a
set, thus forming an array. When defining a fuzzer, the order of
payloads is important.

### Types

The type of iteration that a fuzzer performs while being executed
corresponds to the type of fuzzer that it is. We have replacive fuzzers
that are values of payloads being executed by substituting for a
particular payload value, recursive fuzzers, such as the number system
of hexadecimal values as well as more exotic categories (like zero
fuzzers) that we shall investigate below.

Thus, if you want to perform a SQL injection check on a web application
or service, you need to know to use a replacive fuzzer that has as
payloads SQL injection payloads. On the other hand, if you want to
iterate through values 000 to 777, you need to know to use a recursive
fuzzer of length 3. Let's dig into each of the categories a bit more.

### Replacive Fuzzers

### Recursive Fuzzers

### Double Fuzzers

### Power Fuzzers

### Cross Product Fuzzers

### Zero Fuzzers

## The .JBRF File Format

JBroFuzz has an internal file format for representing fuzzers. Within
the JBroFuzz executable, there exists a file called fuzzers.jbrf that
carries all the fuzzer definitions. If you unzip the JBroFuzz.jar file
you will see it there. Let's look at a fuzzer definition example from
that file, namely the XPATH fuzzer:

    P:014-XPT-INJ:XPath Injection:10
    > Replacive Fuzzers
    | XPath Injection
    | Injection
    >>This is a comment line to be changed in the future
    ' or '1'='1
    ' or ''='
    x' or 1=1 or 'x'='y
    /
    //
    //*
    */*
    @*
    count(/child::node())
    x' or name()='username' or 'x'='y

Firstly, the fuzzers.jbrf file is flat ascii text file. It defines each
entity with an opening line of the following format:

    C:ddd-CCC-CCC:Name:d

Where:

  - C is an upper character corresponding to the fuzzer type. 'R' stands
    for recursive, 'P' for replacive, 'Z' for zero, etc.
  - ddd-LLL-LLL is the fuzzer id starting with 3 digits, followed by a
    dash (-), 3 upper case characters, followed by a second dash (-) and
    a final set of 3 upper case characters. This value needs to be
    unique for each fuzzer.
  - Name the fuzzer name
  - d: The number of payloads a fuzzer actually has.

...

[Category:OWASP JBroFuzz](Category:OWASP_JBroFuzz "wikilink")