[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__
Inner classes have been called "dangerous" by several Java security
guidelines. However, there is no additional danger inherent in the use
of inner classes that is not inherent in the use of other types of
polymorphism. In general, use as little polymorphism as possible since
it, by definition, it exposes data.

Java Security Researcher Tom Hawtin sums up the "danger" of inner
classes in his blog at <http://jroller.com/page/tackline>

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")