Code Review Approach

When planning to execute a security code review, there are multiple
factors to consider since every code review is unique to its context.
Some of these elements are further discussed in the following sections.
In addition, consider also unique factors that might impact the
analysis. These factors among others, might ultimately decide the course
of the code review and the most effective way to execute it. Some are
technical but others are related to business decisions such as deadlines
and resources

## Risks

It is impossible to secure everything at a 100 percent, furthermore it
is essential to prioritize what features and components must be
reviewed. In addition, we need to assess the kind of risks and the
business priorities. Code review based on risk based assessments
provides effectiveness to the analysis

## Purpose & Context: focusing on risks

Computer Programs have different purposes, consequently the grade of
security will vary depending for what it was built. A payment web
application will have higher security standards than a promotional
website. One must ask: what do we want to protect? In the case of a
payment application, data such as credit cards has the highest priority
however in the case of a promotional website, one of the most important
things to protect, for example, is the connection credentials to the web
servers. This is another way to place context into a risk based
approach.

## Complexity

Are we reviewing Spaghetti code or a properly created Object Oriented
Program? Is the program using a clear defined pattern or is it necessary
to spend time to understand what the developer built? Complexity comes
in many forms, the more difficult is to understand the program the more
difficult it becomes to spot issues in it. Therefore, try to determine
the grade of difficulty involved and especially, how much time it will
take to clearly define the duration of the review. The next item
increases the complexity ratio in software development.

## Lines of Code

In order to properly asses the amount of work, an indicator of this
property is the number of lines of code that must be reviewed. IDEs
(Interface Development Environments) such as Visual Studio or Eclipse
contain features which allows us to verify the amount of lines a class
has. Programs written in high level languages are divided in classes and
each class is equivalent to ‘pages’ full of code. Also the exact line
number helps us to pinpoint the exact location of the code that must be
corrected and it is very useful when reviewing corrections done by a
developer, such as the history in a repository. The more lines of code a
program contains, the more are the chances that errors are present in
the code. A calculation based on statistics is to take the value of 5 to
50 bugs per KLOC (Thousand lines of code). Most commercial software will
contain 50 bugs per KLOC (Hoglund and McGraw, 2004) When doing a code
review, keep in mind this factor which can help determine the potential
amounts of bugs present in the program

## Programming language

Programs written in typed safe languages (such as C\# or Java) are less
vulnerable to certain security bugs such as buffer overflows than others
that are not, like C and C++. When executing code review, the kind of
language will determine the types of expected bugs. Throughout this
guide, you can find the most common issues surrounding the specific
programming language code to be reviewed, use this as a reference to
spot specific security issues in the code.

## Resources: Time & Deadlines

This is a fundamental factor. A proper code review for a complex program
might take longer and it will need higher analysis skills than a simple
one. System owners might expect to finish and use less time to execute
the code review than it actually needs. The risks involved if resources
are not properly provided are high. Make sure that this is clearly asses
when executing a review.

## Reference

Hoglund & McGraw, 2004 “Exploiting Software How to Break Code” –Addison
Wesley