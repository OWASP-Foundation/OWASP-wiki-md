## Introduction

Application security isn't just a feature or an add-on. Security is
directly linked to how an application has been coded: bad designed
applications have bad security. Good software architecture and design is
therefore the foundation for secure code. Security also depends on how
it's been incorporated in the software development life cycle and
software maintenance processes. Summarized: architecture, design and
process are the 3 pillars for secure code:

### Architecture

  - Don’t glue your application together with code snippets from the
    Internet
  - Structure & Organize your code by using an architectural pattern
    and/or application framework

### Design

  - Don’t re-invent the wheel
  - Follow proven software design principles to avoid common pitfalls

### Process

  - The proof of the pudding is in the testing, before and after going
    live.
  - Maintain and improve your code till the end of its life by
    continuous bug fixing, patching, refactoring, etc.

## Architecture, patterns and frameworks

Good software architecture and design is the foundation for secure code
as it helps to structure and organize your code. Why ? Because
structuring and organizing your code reduces unnecessary complexity,
therefore it's less error prone, easier to debug, to maintain and to
change. Architectural patterns help you to accomplish this by providing
coding rules and guidelines while frameworks enforce architecture and
code structure. Before getting into detail about architecture and
security, first a short explanation about architecture, patterns,
frameworks and the relationship between them:

### Architecture

First of all a definition of software architecture. There are many to
find on the Internet but the most applicable one for web applications
is: "Software architecture is the description of the subsystems and
components of an application and the relationships between them". From
the perspective of programming, components can be seen here as modules,
classes, objects or even procedural functions. While a subsystem is a
set of components which work together to accomplish a specific task.

### Patterns

Patterns are standard architectures, they are the product of the
experience of many developers and are proven solutions which promote
good design practices. Patterns describe a set of predefined subsystems,
their responsibilities, and rules and guidelines for organizing the
relationships between them. The Model-View-Controller (MVC) pattern is
the most common used one for PHP web applications and PHP frameworks.

### Frameworks

Frameworks can be seen as prefab code, they make it easy for developers
to rapidly build web applications with ready to use components and
libraries. (Good) frameworks are based on a proven software architecture
and feature built-in best practices for software design. Current most
popular PHP frameworks are all MVC based. Though frameworks allow
developers less freedom, applications build without using a framework,
depend entirely on the developer's own interpretation of good
architecture and design.

![<File:Architecture-Patterns-Frameworks.jpg>](Architecture-Patterns-Frameworks.jpg
"File:Architecture-Patterns-Frameworks.jpg")

## Design considerations

PHP frameworks can speed up development with well organized, reusable
and maintainable code while they have also many built-in security
features. Nevertheless, you can still find many poorly secured PHP web
applications on the Internet which have been build by using a framework.
Most of the security issues with these web applications are caused by
misconfiguration and client code written on top of frameworks. This is
the downside to frameworks, developers may become too dependent upon
them, so they no longer understand how the code exactly works "under the
hood". There is even a new generation of web application developers who
don’t know how to code anymore as they are no longer a PHP developer but
a "framework XYZ" developer. Learning to code PHP from scratch is
therefore not only a good exercise to learn and understand MVC and good
design practices, it's also essential to get a real understanding of
secure coding.

### Design Principles

Good software architecture and design are the foundation for secure
code, but what is good software design? From security perspective, the
most important element of good software design is that your code should
be simple, well structured, modular and easy to maintain. This is
something known as code quality, clean code or "good" code. Good code
depends on developer skills but also results from following proven
design principles such as:

  - KISS: Keep it simple and avoid unnecessary complexity - Complexity
    is a potential source of security bugs
  - DRY: Avoid unnecessary repetition, implement functionality by a
    single piece of code - Vulnerabilities may continue to exist in
    overlooked duplicated code
  - YAGNI: Don't waiste effort on features you don't need - Reduce
    attack surface by leaving out unnecessary features
  - COCO: Follow Coding Conventions to ensure efficiency and consistency
    - Confusing and unmaintainable code contributes to errors and
    security issues

These principles are the foundation for secure code, security by design
principles are the next step to secure code.

### Architectural considerations

#### Middle tier

#### Web Services Middle tier

#### Middle tier

## Noteworthy Frameworks

### Zend Framework

### PEAR

### OWASP Filters

### CakePHP

[Category:PHP](Category:PHP "wikilink")