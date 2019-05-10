ESAPI is easy to build yourself using [Git](https://git-scm.com/) and
[Maven](http://maven.apache.org/). Ensure that you are using UTF-8 for
all source code.

` $ git clone `<https://github.com/ESAPI/esapi-java-legacy.git>`    # This will clone the 'develop' branch.`
` $ cd esapi-java-legacy`
` $ mvn -Dmaven.test.skip=true package  # Build ESAPI`

Maven will generate a "target" directory that contains the ESAPI jar
file.

To generate project reports use:

` $ mvn site`

To generate documentation use:

` $ mvn javadoc:jar`

__NOTOC__

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")