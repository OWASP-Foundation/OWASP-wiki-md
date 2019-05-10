## Introduction

JBroFuzz represents a stateless network protocol fuzzer for web
applications. The focus of this tool is around being able to manipulate
and submit a variety of different fuzzing requests over HTTP/S.

The long term goal of this project is to provide a stable fuzzing
platform that spans a number of operating systems: A tool that
penetration testers would want to have with them while testing a web
application or service.

Currently, JBroFuzz carries a number of payloads and a collection of
headers from different browsers on different platforms. The future of
this tool will be highly invested in actually grouping these elements
into categories of automated as well as manual testing.

## Version Structure

JBroFuzz increments version numbers in 0.1 fashion; there are no minor,
alpha or beta releases. Also the SVN repository carries a number of
pre-release candidates of release level quality.

Further to this, there are a number of core fuzzing APIs (implemented in
org.owasp.jbrofuzz.core) that allow for the custom implementation of
fuzzing scripts in the java programming language.

## Towards 2.5 - December 'Weekend of Code'

Version 2.5 of JBrofuzz is in the final throws of development and will
be released Q1 2011. The significant improvement will be an
implementation of a database back-end based on SQLite. The design is
intended to improve the performance of the fuzzer when conducting large
fuzzing sessions and to open the doorway for extensibility including
distributed fuzzing and 'Agent mode' to allow remote access.

In addition to this, expect to see user interface and functional
improvements throughout the application.

## Further Releases

There will always be incremental updates relating to UI components; from
text highlighting to the addition and removal of particular payload
values. The modular approach of JBroFuzz taken during its development,
yields the ability to further continue and add shortcuts and automations
of particular tasks.

## Request List

This roadmap presents a number of tasks which will carry JBroFuzz
through to its 2.0 release. Each of the tasks specified below, begins
with the likely version number at which the issue (bug or feature) will
be addressed. Generally, bugs take priority over features, yet some
features involve architectural changes that address a lot of bugs,
together.

Before diving into individual (and more technical) tasks we present a
list of goals and objectives for JBroFuzz:

  - **1.0** Achieve a stable fuzzing platform
  - **1.2** Establish a fuzzing file format
  - **1.3** Address logging functionality
  - **1.6** Bring all code up to java 6
  - **1.8** Expose the org.owasp.jbrofuzz API
  - **1.9** Focus on UI functionality
  - **2.0** Landmark release
  - **2.1** Address bugs/features
  - **2.2** Add the final "Testing" tab

On individual tasks that are requred for version 1.8 and later:

  - Create a preference for the fuzzing output panel to choose
    functionality when you double click
  - Right click on the output panel can clear the panel and create a new
    directory to strore data
  - Implement Encoder/Decoder window shortcuts (Ctrl+Enter) to Encode
    (Ctrl+Backspace) to decode
  - Implement an Encoder/Decoder right panel with information on each of
    the formats available
  - Alter the system tab to always report a count increment in the event
    of any event
  - Implement the XFuzzer being the cross product of two fuzzers
  - Right Click on Response Table in Fuzzing and Graphing
  - Format the source code to apache standards
  - Be able to stop a graph while plotting

## What not to Expect

As a tool JBroFuzz will not try to imitate the usage of other fuzzing
tools; still, the expansion, addition and different grouping of payload
values within the fuzzers.jbrofuzz file will continue to follow current
attack patterns and trends.

This standalone fuzzer, will not be the answer to all your fuzzing
worries. If you are willing to spend a bit of time in knowning and
selecting what you would like to fuzz and how, the future releases of
this tool should be of interest to those engaged in security testing.