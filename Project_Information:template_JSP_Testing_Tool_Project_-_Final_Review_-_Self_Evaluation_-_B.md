# Summer of Code 2008 Report

| colspan="3" align="center" style="background:\#4058A0; color:white" | <font color="white">**FINAL REVIEW**                                                                                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| style="width:25%; background:white" align="center"                  | **PART I**                                                                                                                                                                                                                                                                                                                                 |
| style="width:25%; background:\#7B8ABD" align="center"               | Project Deliveries & Objectives                                                                                                                                                                                                                                                                                                            |
| style="width:25%; background:\#4058A0" align="center"               | <font color="white">**QUESTIONS**                                                                                                                                                                                                                                                                                                          |
| style="width:25%; background:\#7B8ABD" align="center"               | 1\. At what extent have the project deliveries & objectives been accomplished? Having in consideration [**the assumed ones**](OWASP_Summer_of_Code_2008_Applications#P028_-_OWASP_UI_Component_Verification_Project_\(a.k.a._OWASP_JSP_Testing_Tool\) "wikilink"), please exemplify writing down those of them that haven't been realised. |
| style="width:25%; background:\#7B8ABD" align="center"               | 2\. At what extent have the project deliveries & objectives been accomplished? Having in consideration [**the assumed ones**](OWASP_Summer_of_Code_2008_Applications#P028_-_OWASP_UI_Component_Verification_Project_\(a.k.a._OWASP_JSP_Testing_Tool\) "wikilink"), please quantify in terms of percentage.                                 |
| style="width:25%; background:\#7B8ABD" align="center"               | 3\. What kind of help is required either from the Reviewers or from the OWASP Community?                                                                                                                                                                                                                                                   |
| style="width:25%; background:white" align="center"                  | **PART II**                                                                                                                                                                                                                                                                                                                                |
| style="width:25%; background:\#7B8ABD" align="center"               | Assessment Criteria                                                                                                                                                                                                                                                                                                                        |
| style="width:25%; background:\#4058A0" align="center"               | <font color="white">**QUESTIONS**                                                                                                                                                                                                                                                                                                          |
| style="width:25%; background:\#7B8ABD" align="center"               | 1\. Having into consideration the [OWASP Project Assessment Methodology](:Category:OWASP_Project_Assessment "wikilink") which criteria, if any, haven’t been fulfilled in terms of **Alpha Quality** status?                                                                                                                               |
| style="width:25%; background:\#7B8ABD" align="center"               | 2\. Having into consideration the [OWASP Project Assessment Methodology](:Category:OWASP_Project_Assessment "wikilink") which criteria, if any, haven’t been fulfilled in terms of **Beta Quality** status?                                                                                                                                |
| style="width:25%; background:\#7B8ABD" align="center"               | 3\. Having into consideration the [OWASP Project Assessment Methodology](:Category:OWASP_Project_Assessment "wikilink") which criteria, if any, haven’t been fulfilled in terms of **Release Quality** status?                                                                                                                             |
| style="width:25%; background:\#7B8ABD" align="center"               | 4\. What kind of help is required either from the Reviewers or from the OWASP Community?                                                                                                                                                                                                                                                   |

# Detailed Status Report

The following contains a detailed report on the status of the project.
All current code and Java documentation has been updated to the
Subversion repository hosted by Google Code.

## Project Goals

The goals for the project were as follows:

  - **Identify or Create Tag Library Parser** (achieved in 50% review
    goal)
  - **Basic Test of Tags** (achieved in 50% review goal)
  - **Design Report Format** (achieved in 50% review goal)
  - **Refine Tag Testing** (see below)
  - **Refine Report Format** (see below)
  - **Documentation and Release** (see below)

In addition, the 50% Review added the following goals:

  - **Implement Deployment Method** (see below)
  - **Implement Invocation Method** (see below)

### Refine Tag Testing

To improve on the ability to test tags, the concept of a tag properties
configuration file was introduced. This allows users to specify values
for required attributes or embed tags in the proper context, which
reduces the errors in tag execution, improving the test results.

### Refine Report Format

Several minor changes were made to the report to improve perceived
performance. At the 50% Review, the report waited for all test case
iframes to load and executed the results all at once. For an entire tag
library report, this could take an extremely long time to load (even
when the report files are serialized locally) during which time the
report would appear empty. By executing when an test case iframe loads
(using the onload event), incremental progress can displayed as the
results of each test are populated.

Additionally, JavaScript event handlers were invoked in the 50% Review
version without regard to the contents (proactively invoking all events
to see if they triggered the attack). This can lead to scripts getting
executed that are not related to the test case. As a result, the code
exercising event handlers was improved to only invoke event handlers
that contained the test case attack.

Finally, given that the full tag library report for the JSF HTML Basic
tag library takes an extremely long time to load, the report process
also generates sub-reports on individual tags in addition to the full
report on the entire library.

### Implement Deployment Method

The new code uses an embedded instance of Tomcat to deploy the test
cases and serializes them locally by downloading them from the embedded
Tomcat instance.

### Implement Invocation Method

An Ant Build File encapsulates the tasks of compiling and running the
various components that make up the tool.

### Documentation and Release

Documentation on the main project page has been updated with the new
features and how to invoke them.

## Assessment Criteria

  - Agree to OWASP's open source license

(*BSD License*)

  - The "main" page for any OWASP tool must be on the OWASP website.
    This page must:
      - describe the tool, the project leader, contact info, and include
        all relevant links, including a download link for the code and
        the executable version,
      - includes a roadmap/guideline pointing out the steps to achieve
        the purpose of project.
      - include the Alpha Quality Tool project tag. (Which we still need
        to define)
      - be placed at OWASP Project page.

(*[Project Page](:Category:OWASP_JSP_Testing_Tool_Project "wikilink")*)

  - Have its code and any documentation in Googlecode, or Sourceforge

(*[Google Code](http://code.google.com/p/owasp-jsp-testing-tool/)*)

  - Mailing list for project created

(*[owasp-jsp-testing-tool-project](https://lists.owasp.org/mailman/listinfo/owasp-jsp-testing-tool-project)*)

  - Solves a core application security need

\`(*[OWASP Project Request
P028](OWASP_Request_for_Proposal_List#P028_-_OWASP_UI_Component_Verification_Project "wikilink")*)

  - Have an easy to use installer (Goal: Fully automated installer) (or
    stand alone executable version)

(*binary JAR is standalone*)

  - Include user documentation in Project's OWASP Wiki page(s)

(*[included](:Category:OWASP_JSP_Testing_Tool_Project#Overview "wikilink")*)

  - Add a common About Box or help menu in the tool itself
      - (which lists name of tool, author, e-mail address of author,
        current version number and/or release date)

(*included*)

  - Include documentation on how to build it from code, starting with
    getting it directly from the code repository. (Ideally, this would
    include easy to use build scripts, which is required for Release
    Quality)

(*[Ant build file
included](http://code.google.com/p/owasp-jsp-testing-tool/source/browse/trunk/owasp-jsp-testing-tool/build.xml)*)

  - This documentation must stored be in the same repository as the
    code.

(*[Documentation @
Googlecode](http://owasp-jsp-testing-tool.googlecode.com/svn/trunk/owasp-jsp-testing-tool/docs/api/index.html)*)

### Standalone Executable Version

A Windows standalone version was created and distributed to the
reviewers for evaluation. However, this standalone is large in size and
currently not permitted to be loaded into Google Code. Every effort will
be made to make this standalone executable available once storage
limitations are no longer an issue.