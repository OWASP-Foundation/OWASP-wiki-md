`#REDIRECT `[`Failure``   ``to``   ``follow``
 ``guideline/specification`](Failure_to_follow_guideline/specification "wikilink")

Last revision (mm/dd/yy): **//**

## Description

JSP 2.0 introduced a new capability allowing one to use JSP Expressions
directly within the template text (i.e. outside of tag libraries or tag
files) of a web page. However, improper use of the expressions will
leave an application open to [XSS Attacks](XSS_Attacks "wikilink").

**Consequences**

  - Failing to use JSP Expressions properly will leave an application
    open to [XSS Attacks](XSS_Attacks "wikilink").

**Exposure period** This vulnerability has existed since servlet
containers and application servers began implementing the
\[<http://jcp.org/en/jsr/detail?id=152>| JSP 2.0 standard\]

**Platform**

  - Languages: Java/JSP

**Severity** High

**Likelihood of exploit** If a developer uses JSP Expressions to write
unsanitized, user-entered data to a page, the likelihood of exploit is
very high.

## Risk Factors

TBD

## Examples

JSP 2.0 expressions allow developers to expose data and objects stored
in application, session, request, or page scope using an Ant-style
syntax. It allows you to replace this

    <table>
        <c:forEach var="book" items="${books}">
            <tr>
                <td><c:out value="${book.title}"/></td>
                <td><c:out value="${book.author}"/></td>
                <td><c:out value="${book.isbn}"/></td>
            </tr>
        </c:forEach>
    </table>

with this

    <table>
        <c:forEach var="book" items="${books}">
            <tr>
                <td>${book.title}</td>
                <td>${book.author}</td>
                <td>${book.isbn}</td>
            </tr>
        </c:forEach>
    </table>

As you can see, the syntax in the second example is more succinct.
However, it may also expose a Cross Site Scripting
[XSS](XSS_Attacks "wikilink") vulnerability. The problem that few
tutorials (including \[<http://java.sun.com/javaee/5/docs/tutorial/doc>|
Sun's Java EE 5 Tutorial\]) mention is that the expression syntax does
not escape HTML characters. Therefore, any web application using JSP
Expressions to output unsanitized, user-entered data will be vulnerable
to Cross Site Scripting (XSS) attacks.

## Related [Attacks](Attacks "wikilink")

  - [Attack 1](Attack_1 "wikilink")
  - [Attack 2](Attack_2 "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")
  - [Vulnerabiltiy 2](Vulnerabiltiy_2 "wikilink")

## Related [Controls](Controls "wikilink")

The safest cure for this XSS vulnerability leads one right back to the
first example. As section 2.2.2 of the JSP 2.0 Specification reads, “In
cases where escaping is desired (for example, to help prevent cross-site
scripting attacks), the JSTL core tag c:out can be used.”

To be sure your code is not vulnerable to the potential XSS
vulnerability described herein, use JSP Expressions only as tag library
attribute values and stick to using JSTL‘s c:out tag for writing text to
a page. Deciding which instances of template text expression usage are
safe and which are not is error prone and the consequences of a mistake
are grave.

## Related [Technical Impacts](Technical_Impacts "wikilink")

  - [Technical Impact 1](Technical_Impact_1 "wikilink")
  - [Technical Impact 2](Technical_Impact_2 "wikilink")

## References

Note: A reference to related [CWE](http://cwe.mitre.org/) or
[CAPEC](http://capec.mitre.org/) article should be added when exists.
Eg:

  - [CWE 79](http://cwe.mitre.org/data/definitions/79.html).
  - <http://www.link1.com>
  - [Title for the link2](http://www.link2.com)