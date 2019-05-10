## Introduction

In software engineering, a design pattern is a reusable solution to a
common occurring problem that can be generalized to be used a numerous
contexts of software design.

Anti-patterns are commonly used patterns used in software engineering
but are ineffective, counterproductive, and may result in software
vulnerabilities.

The Code Review Guide will focus on anti-design patterns that help
create in-secure code/applications.

## Information Disclosure Through Exception:

Error information for a hacker is like a bone to a dog; “Something good
to chew on“. Without controlling what error information is shown to a
user the application may release information such as platform target
code is running on, database being used, computer language, etc. The
significance of each piece of information allows the hacker to quickly
narrow what tools he uses and what vulnerabilities he might try to
exploit.

### .Net

##### What is the flaw?

`} catch (exception e) {YourLogger.Log(e);}`

This exception was not handled. The exception was log but the program is
allow to continue executing. This is contrary to good secure design.
When exceptions occur the code needs to handled the exception not just
log it. Programs need to fail and fail fast and securely. If the program
is not allow to fail because of business rules it needs to know how to
handled it's state to be able to recover in a secure manner.

`} catch (exception e) { YourLogger.Log(e); throw e; } `

is incorrect.

`} catch (exception e) { YourLogger.Log(e); throw new Exception("Your exception description");`

is incorrect.

`} catch (exception e) { YourLogger.Log(e); throw new Exception("Your exception description ",e); `

Throw new Exception could be valid if you want to hide the original
error, perhaps a security related issue.

##### Secure Design Recommendation:

At minimum exception handling should have...

`} catch (Exception ex) {YourLogger.Log(ex); throw;}`

##### Review Criteria

Static analysis tools like Cat.Net or FxCop are good at finding
information leakage from exceptions. Code reviewer needs to understand
how exceptions and unhanded exceptions are handled by the program.

**Need link here on what information is valid to log**