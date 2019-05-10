__TOC__

## Preface

In this section, we will try to organize the most critical security
flaws you can find during a code review in order to have a finite set of
categories to evaluate the whole code review process.

## The 9 Flaw Categories

In terms of source code security, source code vulnerabilities can be
managed in a million ways.

Source code vulnerabilities must reflect Owasp Top 10 recommendations.
Applications are made of source code , so, in some way, source code
flaws can be re conducted to flaws in application.

The following family of categories are included as a default library in
Owasp Orizon Project v1.0 that was released in October 2008.

### The Nine Source Code Flaw Categories

  - Input validation
  - Source code design
  - Information leakage and improper error handling
  - Direct object reference
  - Resource usage
  - API usage
  - Best practices violation
  - Weak Session Management
  - Using HTTP GET query strings

As you can see 3 categories out of 9 are equivalent to the corresponding
Owasp Top 10.

Let's go more in detail, going deeper in describing the source code flaw
categories.

### Input Validation

This flaw category is the source code counterpart of the Owasp Top 10 A1
category.

This category contains the follow security flaw families: Input
validation

Input validation

  - Cross site scripting
  - SQL Injection
  - XPATH Injection
  - LDAP Injection
  - Cross site request forgery
  - Buffer overflow
  - Format bug

### Source Code Design

Security in source code starts from design, and from the choices made
before starting to code.

In the source code design flaw categories, you can find security check
families tied to scope and source code organization.

Source code design

  - Insecure field scope
  - Insecure method scope
  - Insecure class modifiers
  - Unused external references
  - Redundant code

### Information leakage and improper error handling

This category meets the correspondent Owasp Top 10 one. It contains
security check families about how source code manage errors, exception,
logging and sensitive information.

The following families are present:

Information leakage and improper error handling

  - Unhandled exception
  - Routine return value usage
  - NULL Pointer dereference
  - Insecure logging

### Direct object reference

This category is the same as the one stated in the Owasp Top 10 project.
It refers to the attacker's capability to interact with application
internals supplying an ad hoc crafted parameter.

The families contained in this category are:

Direct object reference

  - Direct reference to database data
  - Direct reference to filesystem
  - Direct reference to memory

### Resource usage

This category is related to all the unsafe ways a source code can
request operating system managed resources. Most of the vulnerability
families contained here, if exploited, will result in a some kind of
denial of service.

Resources can be:

  - filesystem objects
  - memory
  - CPU
  - network bandwidth

The families included are: Resource usage

  - Insecure file creation
  - Insecure file modifying
  - Insecure file deletion
  - Race condition
  - Memory leak
  - Unsafe process creation

### API usage

This section is about APIs provided by the system or by the framework in
use that can be used in a malicious way. In this category you can find:

  - insecure database calls
  - insecure random number creation
  - improper memory management calls
  - insecure HTTP session handling
  - insecure strings manipulation

### Best practices violation

This category is about all miscellaneous security violations that don’t
fit in the previous categories. Most, but not all, of these contain
warning-only source code best practices. This category includes:

  - insecure memory pointer usage
  - NULL pointer dereference
  - pointer arithmetic
  - variable aliasing
  - unsafe variable initialization
  - missing comments and source code documentation

### Weak Session Management

  - Not invalidating session upon an error occurring
  - Not checking for valid sessions upon HTTP request
  - Not issuing a new session upon successful authentication
  - Passing cookies over non SSL connections (no secure flag)

### Using HTTP GET query strings

Payload data is logged if contained in query strings. This information
can be logged in all nodes between client/browser and server. Passing
sensitive information using a query string and HTTP GET is a mortal sin.
SSL does not even protect you here.

  - Passing sensitive data over URL /querystring

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")