__TOC__

Code review is an excellent source of metrics that can be used to
improve your software development process. There are two distinct
classes of these software metrics: Relative and Absolute.

Absolute metrics are numerical values that describe a trait of the code
such as the number of references to a particular variable in an
application, or the number of lines of code (LOC). Absolute metrics,
such as the number of lines of code, do not involve subjective context
but are material fact.

Relative metrics are a representation of an attribute that cannot be
directly measured, and are subjective and reliant on the context of
where the metric was derived. There is no definitive way to measure such
an attribute. Multiple variables are factored into an estimation of the
degree of testing difficulty, and any numeric representation or rating
is only an approximation and is subjective.

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

### Path complexity/complexity-to-defect/cyclomatic complexity

Cyclomatic complexity can help establish risk and stability estimations
on an item of code, such as a class or method or even a complete system.
It was defined by Thomas McCabe in the 70's and it easy to calsulate and
apply, hence its usefulness.

CC = Number of decisions +1

A decision could be considered commands such as:

If....else
switch
case
catch
while
do
and so on.....

As the decision count increases, so does the complexity. Complex code
leads to less stability and maintainability.

The more complex the code, the higher risk of defects. One could
establish thresholds for Cyclomatic complexity:

0-10: Stable code. Acceptable complexity
11-15: Medium Risk. More complex
16-20: High Risk code. Too many decisions for a unit of code.

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
and prevent logic errors.

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