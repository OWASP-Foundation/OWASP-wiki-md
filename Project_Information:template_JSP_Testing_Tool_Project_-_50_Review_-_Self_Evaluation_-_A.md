# Summer of Code 2008 Report

| colspan="3" align="center" style="background:\#4058A0; color:white" | <font color="white">**50% REVIEW PROCESS**                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| style="width:25%; background:\#7B8ABD" align="center"               | Project Deliveries & Objectives                                                                                                                                                                                                                                                                                                            |
| style="width:25x%; background:\#4058A0" align="center"              | <font color="white">**QUESTIONS**                                                                                                                                                                                                                                                                                                          |
| style="width:25%; background:\#7B8ABD" align="left"                 | 1\. At what extent have the project deliveries & objectives been accomplished? Having in consideration [**the assumed ones**](OWASP_Summer_of_Code_2008_Applications#P028_-_OWASP_UI_Component_Verification_Project_\(a.k.a._OWASP_JSP_Testing_Tool\) "wikilink"), please exemplify writing down those of them that haven't been realised. |
| style="width:25%; background:\#7B8ABD" align="left"                 | 2\. At what extent have the project deliveries & objectives been accomplished? Having in consideration [**the assumed ones**](OWASP_Summer_of_Code_2008_Applications#P028_-_OWASP_UI_Component_Verification_Project_\(a.k.a._OWASP_JSP_Testing_Tool\) "wikilink"), please quantify in terms of percentage.                                 |
|                                                                     |                                                                                                                                                                                                                                                                                                                                            |
| style="width:25%; background:\#7B8ABD" align="left"                 | 3\. What kind of help is required either from the Reviewers or from the OWASP Community?                                                                                                                                                                                                                                                   |

# Detailed Status Report

The following contains a detailed report on the status of the project.
All current code has been added to a Subversion repository hosted by
Google Code. The packaged [source
code](http://owasp-jsp-testing-tool.googlecode.com/files/owasp-jsp-testing-tool-0.5-src.zip)
along with
[required](http://owasp-jsp-testing-tool.googlecode.com/files/required-libs.zip)
libraries is available at the project's [Google Code
home](http://code.google.com/p/owasp-jsp-testing-tool/). Also available
is a [demo WAR
file](http://owasp-jsp-testing-tool.googlecode.com/files/JspTestingTool.war)
containing the generated report of the JSF Core tag `h:outputLink` from
the HTML Basic library. The demo was created by running the `main`
method from the `JspTester` class which currently contains test code to
invoke the tool on a subset.tld file which contains the single
`h:outputLink` tag. The resulting JSP files were then packaged along
with the necessary XML configuration files and JAR libraries into the
WAR file.

## "Stage One" Objectives

The following For convenience, the development goals outlined in the
[original
proposal](OWASP_Summer_of_Code_2008_Applications#Development_Stages "wikilink")
are reproduced here:

  - **Identify or Create Tag Library Parser**: The first step of this
    project is to determine a way to parse tag libraries and instantiate
    tag objects for testing. The Java EE API includes interfaces to
    parse and instantiate JSP tags so an initial investigation into
    existing implementations of tag parsers may yield an adequate
    source. However, since the interfaces are specified as protected and
    application server implementation specific, the interdependencies
    may require the creation of such a parser from scratch
  - **Basic Test of Tags**: The second step is to use the parser and
    apply some basic initial test cases to test the protection of
    attributes from tainted input
  - **Design Report Format**: The third step is to tabulate the results
    and create a simple format to convey those results.

### Identify or Create Tag Library Parser

At the onset of the project, I was not aware of the various different
versions of the JSP Tag Library specification. There are currently four
versions of the specification: 1.1, 1.2, 2.0 and 2.1. Currently, the
code parses all of the necessary code from a TLD File from a JSP Tag
Library version 1.1 or 1.2 in order to generate tag test cases for all
attributes. Some information such as listeners, validators, etc. are not
parsed. The 2.x specifications are a superset of the elements used in
the 1.2 specification and as a result, the parser can generally handle
2.x form TLDs. For example, the Sun provided JSF 1.2 TLDs have served as
the de facto test case and the parser handles these TLDs gracefully.
However, by ignoring the extra information provided in 2.x TLDs, the
tool ignores information that can be used to improve successful
generation of tags. For example, some of the information provided by a
2.x TLD includes type information on attributes and example tag usage.
As a result, I have rated the percentage completion rate as 75%. Note
that of all the work remaining, handling 2.x TLDs represents the easiest
task and will likely take very little time to complete.

### Basic Test of Tags

Tag generation is currently done by blind population of attributes using
Jakarta ECS to generate the text itself. This at least allows for basic
testing of most tags. More information about the basic testing is
[here](:Category:OWASP_JSP_Testing_Tool_Project#How_the_Report_Works "wikilink").
Again, while this strategy is relatively blind, the majority of the JSF
HTML Basic components can be generated using this strategy and results
in at least proof of concept. While there is much work to be done to
improve the success rate in tag generation, this was expected and hence
the "stage one" goal was extremely rudimentary. As a result, I have
rated the percentage completion rate as 100%. Note that "stage two"
objectives include work to improve tag generation.

Initial ideas for improving this strategy include:

  - Tying into an existing JSP container to construct Tag classes
    directly.
  - Using a JSP compiler to compile and run the JSPs currently generated
    by the tool. The report is currently "dynamic" which can result in
    resource exhaustion when multiple test case JSPs fail to compile.
    There is no reason for these pages to be constructed on each
    invocation as the content itself is static. By compiling and running
    the JSPs in a separate process, the generated HTML can be saved and
    resources deallocated. This also removes the need for the final
    report to be deployed in a JSP container as the report is pure HTML.

### Design Report Format

The initial design of the report is complete and the basic strategy is
unlikely to change going forward. The report format is described in
greater detail
[here](:Category:OWASP_JSP_Testing_Tool_Project#The_Report "wikilink").
While there are possible aesthetic and usability improvements,
functionally the report format is complete and as a result I have rated
the percentage completion rate as 100%. Note that the
[stated](OWASP_Summer_of_Code_2008_Applications#Development_Stages "wikilink")
"stage two" objectives include improvements to the report design.

## Known Limitations

The following is a list of known limitations as of the 50% Review.

### Full TLD Support

As stated above, the tag library parser does not currently handle all
information provided by TLDs.

### Advanced Tag Generation

As stated above, the current tag generation strategy is blind and
results in cases where tags are not generated correctly.

#### Out of Heap Space

As a side effect of blind tag generation, incorrect tag generation
results in unhandled exceptions which propagate to the global error
handler. Currently the errors are not handled gracefully which has
resulted in memory exceptions related to the heap space. As a result,
the provided
[demo](http://owasp-jsp-testing-tool.googlecode.com/files/JspTestingTool.war)
only tests one tag from the JSF Core tag library. Even with this limited
test, heap space exceptions tend to occur. Addressing this issue is two
fold:

1.  Improve tag generation to reduce errors
2.  Improve error handling strategy to clean up errors so they do not
    exhaust heap space

## Additional Objectives

In addition to addressing the known limitations cited above, the
following additional objectives will be added to the "stage two"
objectives

  - **Implement Deployment Method**: As stated
    [here](:Category:OWASP_JSP_Testing_Tool_Project#How_the_Report_is_Generated "wikilink"),
    in order to view the report, a user must deploy the set of generated
    HTML/JSP files in a JSP container. This process is currently done
    manually. This new objective will be the creation of some mechanism
    to simplify the deployment of the report. One possible strategy is
    the creation of an Ant task to create a WAR file containing all
    necessary resources to deploy the report.
  - **Implement Invocation Method**: The tool needs a way for users to
    invoke the operation on a given tag library. An initial strategy is
    providing a command line interface to interact with the tool.

[Click here to return to the previous
page](Project_Information:template_JSP_Testing_Tool_Project "wikilink").