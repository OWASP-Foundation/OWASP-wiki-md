__TOC__

No code metric will ever be able to substitute for a code review. There
is a long list of quality and security characteristics that can be
considered when reviewing code (such as but not limited to correctness,
efficiency, portability, maintainability, reliability, securability,
etc. sometimes called the '-ilities'). In this paper we will discuss
metrics to reach the quickest and best solution for a given code review.
No two code review sessions will be the same so some judgement will be
needed to decide the best path. Ideally all code needs to be reviewed,
but let's face it, not all code can be reviewed. So the best approach is
to review the code with the highest risk.

## Some Metric Benefits

The objective of code review is to detect development errors which may
cause vulnerabilities, and hence give rise to an exploit. Code review
can also be used to measure the progress of a development team in their
practice of secure application development. It can pinpoint areas where
the development practice is weak, areas where secure development
practice is strong, and give a security practitioner the ability to
address the root cause of the weaknesses within a developed solution. It
may give rise to investigation into software development policies and
guidelines and the interpretation of them by the users; communication is
the key.

Metrics can also be recorded relating to the performance of the code
reviewers and the accuracy of the review process, the performance of the
code review function, and the efficiency and effectiveness of the code
review function.

![Image:SCR Process.jpg](SCR_Process.jpg "Image:SCR Process.jpg")

The figure above describes the use of Metrics throughout the code review
process.

## Secure Development Metrics

### Defect Density

The average occurrence of programming faults per Lines of Code (LOC).
This gives a high level view of the code quality but not much more.
Fault density on its own does not give rise to a pragmatic metric.
Defect density would cover minor issues as well as major security flaws
in the code; all are treated the same way. Security of code can not be
judged accurately using defect density alone.

### Lines of Code (LOC)

The count of the executable lines of code. Commented-out code or spaces
don't count. This is another metric in an attempt to quantify the size
of the code. This gives a rough estimate but is not particularly
scientific. Some circles of thinking believe that the estimation of an
application size by virtue of LOC is professional malpractice\!

### Function Point

The estimation of software size by measuring functionality. The
combination of a number of statements which perform a specific task,
independent of programming language used or development methodology.

### Risk Density

Similar to defect density, but discovered issues are rated by risk
(high, medium & low). In doing this we can give insight into the quality
of the code being developed via a \[***X Risk / LoC***\] or \[***Y Risk
/ Function Point***\] value. (X\&Y being high, medium or low risks) as
defined by your internal application development policies and standards.

Example:
4 High Risk Defects per 1000 (Lines of Code)
2 Medium Risk Defects per 3 Function Points

### Cyclomatic Complexity

Cyclomatic complexity (CC) is just one static analysis metric used to
help establish risk and stability estimations on an item of code, such
as a class or method or even a complete system. It was defined by Thomas
McCabe in the 70's and it is easy to calculate and apply, hence its
usefulness.

The McCabe cyclomatic complexity metric is designed to indicate a
program's testability, understandability and maintainability, etc. This
is accomplished by measuring the control flow structure, in order to
predict the difficulty of understanding, testing, maintaining, etc. Once
the control flow structure is understood one can gain a realization of
the extent to which the program is likely to contain defects. The
cyclomatic complexity metric is intended to be independent of language
and language format that measures the number of linearly-independent
paths through a program module. It is also the minimum number of paths
that should be tested.

By knowing the cyclomatic complexity of the product, one can focus on
the module with the highest complexity. This will most likely be one of
the paths data will take, thus able to guide one to a potentially high
risk location for vulnerabilities. (This is where the OWASP Code Review
Top 9 comes in handy.
[1](https://www.owasp.org/index.php/The_Owasp_Code_Review_Top_9)) The
higher the complexity the greater potential for more bugs. The more bugs
the higher the probability for more security flaws.

Does cyclomatic complexity reveal security risk? One will not know until
after a review of the security posture of the module. The cyclomatic
complexity metric provides a risk based approach on where to begin to
review and analyse the code. Securing an application is a complex task
and in many ways, complexity is just one enemy of security. Software
complexity can make security and corruption hard to detect. Complexity
of software increases over time as the product is updated or maintained.

Security has become a major component of software quality. Functional
testing and software validation contribute to the quality of a given
body of code, and yet allow the software to remain insecure and
potentially vulnerable. An insecure product is not a quality product.

CC = Number of decisions +1

A decision could be considered commands such as:

If....else
switch
case
catch
while
do
and so on.....

As the decision count increases, so does the complexity and the number
of paths. Complex code leads to less stability and maintainability.

The more complex the code, the higher risk of defects. One could
establish thresholds for Cyclomatic complexity:

0-10: Stable code. Acceptable complexity
11-15: Medium Risk. More complex
16-20: High Risk code. Too many decisions for a unit of code.
Modules with a cyclomatic complexity higher than 30 are extremely
complex and should be split in smaller methods. Any module with a
complexity greater than 50 is considered untestable.

### Depth of Inheritance

Depth of inheritance: measures the inheritance level of a method. The
deeper the level the greater the complexity involved in predicting its
behavior and more importantly the impact changes will have.

### Bad Fix Probability

Bad fix probability: This is the probability of an error accidentally
inserted into a program while trying to fix a previous error.
Cyclomatic Complexity: 1 – 10 == Bad Fix Probability: 5%
Cyclomatic Complexity: 20 –30 == Bad Fix Probability: 20%
Cyclomatic Complexity: \> 50 == Bad Fix Probability: 40%
Cyclomatic Complexity: Approaching 100 == Bad Fix Probability: 60%
As the complexity of software increase so does the probability to
introduce new errors.

### Other aspects of software complexity

Thanks to John Wilander for pointing out that complexity in software has
five dimensions
[2](http://appsandsecurity.blogspot.com/2011/03/5-complexity-dimensions-of-software.html)
\#Scale. More lines of code means higher complexity. This is often hard
to avoid although code refactoring can reduce the code mass somewhat.
\#Diversity. The number of technologies, frameworks, languages,
versions, and even varying coding conventions -- they all drive
complexity. This can be handled with policies but often times developers
will oppose a strict list of what to use and what not.
\#Connectivity. On the code level it's about coupling and cohesion and
depth of inheritance. On a system level it's about the architecture
number of connections and functions. Even higher it's about
interconnecting systems and services both internally and across
organization. In the server room it is about switches, routers,
firewalls and other appliances which boils down to cabling complexity.
\#Dynamics. Could the system even be described in a state diagram? On
any reasonable level? As the number of states the system can in be
grows, so does its complexity. The verdict is still out on if we have
the tools or skills to manage software dynamics yet.
\#Refinement. Over time software is refined or maintained. Understanding
why things are done the way they are in a highly refined product is
complex. This kind of complexity can be lowered through documentation,
but not avoided.
\#\#There are four categories of maintenance according to ISO/IEC
14764:
\#\#\#Adaptive: Modification of a software product performed after
delivery to keep a software product usable in a changed or changing
environment.
\#\#\#Corrective: Reactive modification of a software product performed
after delivery to correct discovered problems.
\#\#\#Perfective: Modification of a software product after delivery to
improve performance or maintainability.
\#\#\#Preventive: Modification of a software product after delivery to
detect and correct latent faults in the software product before they
become effective faults.

These are just some of the metrics to consider in an attempt to improve
your code. From here things become more complex.

## Review Process Metrics

### Inspection Rate

This metric can be used to get a rough idea of the required duration to
perform a code review. The inspection rate is the rate of coverage a
code reviewer can cover per unit of time. From experience, a rate of 250
lines per hour would be a baseline. This rate should not be used as part
of a measure of review quality, but simply to determine duration of the
task.

### Defect Detection Rate

This metric measures the defects found per unit of time. Again, can be
used to measure performance of the code review team, but not to be used
as a quality measure. Defect detection rate would normally increase as
the inspection rate (above) decreases.

### Code Coverage

Measured as a % of LoC of function points, the code coverage is the
proportion of the code reviewed. In the case of manual review we would
aim for close to 100%, unlike automated testing wherein 80-90% is
considered good. In order to ensure that the code coverage standards are
met, some organizations might implement a safety check during the build
process, so the build will fail if there are any piece of code that has
not been tested or if it the coverage is under the desired percentage.
The higher the percentage of code coverage, the better to ensure quality
and prevent logic errors. When it comes to Unit Testing, code coverage
is an important element because one might determine how to write unit
test that covers all the possible execution paths and avoid any logic
error that might cause a wrong behaviour in a piece of software at
runtime.

### Defect Correction Rate

The amount of time used to correct detected defects. This metric can be
used to optimise a project plan within the SDLC. Average values can be
measured over time, producing a measure of effort which must be taken
into account in the planning phase.

### Reinspection Defect Rate

The rate at which upon re-inspection of the code more defects exist,
some defects still exist, or other defects manifest through an attempt
to address previously discovered defects.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")