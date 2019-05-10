Last revision (mm/dd/yy): **//**

## Description

Injection problems span a wide range of instantiations. The basic form
of this flaw involves the injection of control-plane data into the
data-plane in order to alter the control flow of the process.

**Consequences**

  - Confidentiality: Many injection attacks involve the disclosure of
    important information - in terms of both data sensitivity and
    usefulness in further exploitation
  - Authentication: In some cases injectable code controls
    authentication; this may lead to remote vulnerability
  - Access Control: Injection attacks are characterized by the ability
    to significantly change the flow of a given process, and in some
    cases, to the execution of arbitrary code.
  - Integrity: Data injection attacks lead to loss of data integrity in
    nearly all cases as the control-plane data injected is always
    incidental to data recall or writing.
  - Accountability: Often the actions performed by injected control code
    are unlogged.

**Exposure period**

  - Requirements specification: A language might be chosen which is not
    subject to these issues.
  - Implementation: Many logic errors can contribute to these issues.

**Platform**

  - Languages: C, C++, Assembly, SQL
  - Platforms: Any

**Required resources**

Any

**Severity**

High

**Likelihood of exploit**

Very High

Injection problems encompass a wide variety of issues - all mitigated in
very different ways. For this reason, the most effective way to discuss
these flaws is to note the distinct features which classify them as
injection flaws.

The most important issue to note is that all injection problems share
one thing in common - i.e., they allow for the injection of control
plane data into the user-controlled data plane. This means that the
execution of the process may be altered by sending code in through
legitimate data channels, using no other mechanism. While buffer
overflows, and many other flaws, involve the use of some further issue
to gain execution, injection problems need only for the data to be
parsed.

The most classing instantiations of this category of flaw are SQL
injection and format string vulnerabilities.

## Risk Factors

TBD

## Examples

Injection problems describe a large subset of problems with varied
instantiations. For an example of one of these problems, see the section
[Format String](Format_String "wikilink").

## Related [Attacks](Attacks "wikilink")

  - [Attack 1](Attack_1 "wikilink")
  - [Attack 2](Attack_2 "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [SQL injection](SQL_injection "wikilink")
  - [Format String](Format_String "wikilink")
  - [Command injection](Command_injection "wikilink")
  - [Log injection](Log_injection "wikilink")
  - [Reflection injection](Reflection_injection "wikilink")
  - [Interpreter Injection](Interpreter_Injection "wikilink")

## Related [Controls](Controls "wikilink")

  - Requirements specification: A language might be chosen which is not
    subject to these issues.
  - Implementation: As so many possible implementations of this flaw
    exist, it is best to simply be aware of the flaw and work to ensure
    that all control characters entered in data are subject to
    black-list style parsing.

## Related [Technical Impacts](Technical_Impacts "wikilink")

  - [Technical Impact 1](Technical_Impact_1 "wikilink")
  - [Technical Impact 2](Technical_Impact_2 "wikilink")

## References

TBD

__NOTOC__