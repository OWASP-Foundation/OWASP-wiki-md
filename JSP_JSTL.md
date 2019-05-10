## Status

Finished 3/11/08 - in need of review.

## Brief Overview of JSP Architecture

JSPs are delivered to a container that provides services like life-cycle
management and runtime support. A JSP gets translated to a servlet class
which is instantiated at runtime. A request headed for a particular JSP
will be directed by the container to its corresponding servlet class
(aka jsp implementation object). It then handles requests and generates
responses. The default request response objects are HttpServletRequest
and HttpServletResponse. JSP makes use of implicit objects that can be
considered taint sources, sinks and propagators. I won't discuss further
details since that is outside the scope of this project. For further
information try this [reference
guide](http://download.oracle.com/docs/cd/A97336_01/buslog.102/a83726/genlovw1.htm).

## JSP In Light of Security

There’s not much to say here except that JSPs can act as both a model
and view. It can operate fairly well without a distinct service or
business layer because it doesn’t quite enforce separation of logic and
concerns (hence the advent of development frameworks).

I won’t discuss details of web app design here, but one should
understand that lack of separation can have negative effects on web-app
stability and security. But even so, lack of input validation can lead
to easy security vulns in JSP, namely XSS.

Commonly, JavaBeans are used in conjunction with JSP to store parameters
and implement business logic. Most of my examples will use beans to
demonstrate taint propagation and proper cleansing.

For more data on design with JSP and servlets, see this [best
practices](http://java.sun.com/developer/technicalArticles/javaserverpages/servlets_jsp/)
article

## JSP Standard Actions

### Propagators

**<jsp:usebean>**
\* Makes a Java Bean available to the rest of the page by instantiating
the object and binding it to a variable.

  - Once you have that you can modify and access it using the jsp
    setProperty and getProperty tags.
  - You can also call methods on it in scriptlets.

<!-- end list -->

    <jsp:useBean id="user" class="SessionBeans.UserSessionBean" scope="session"/>
    <%=user.getStrParam%>

**<jsp:setProperty>**
\* Sets one or more bean property values in a bean defined by
<jsp:usebean>. *Different ways to set bean properties with request
parameters and supplied values*

    <%--set all bean properties with matching request parameters--%>
    <jsp:setProperty name="user" property="*"/>

    <%--set one property with matching request parameter--%>
    <jsp:setProperty name="user" property="strParam"/>

    <%--set one property with supplied value--%>
    <jsp:setProperty name="user" property="strParam" value="blah" />

### Sinks

**<jsp:getProperty>**
\* Gets a value from a bean object and writes to the page.

**<jsp:include>**
Displays contents of another page within current. Only a problem if
included page contains xss.

### Example: Using standard actions to produce xss.

*Set the bean properties with request parameters on one page.*

    <jsp:useBean id="user" class="SessionBeans.UserSessionBean" scope="session"/>
    <jsp:setProperty name="user" property="*"/>

*Later on another page...*

    <jsp:useBean id="user" class="SessionBeans.UserSessionBean" scope="session"/>
    <jsp:getProperty name="user" property="strParam"/>

## JSP Implicit Objects

There are a handful of objects made available in JSPs which are
susceptible to security flaws. Their corresponding java class functions
are used as is in scriptlets. All the same security rules should apply.

<table>
<thead>
<tr class="header">
<th><p>Implicit Object</p></th>
<th><p>Java Class</p></th>
<th><p>Relevant Functions</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>request</p></td>
<td><p>javax.servlet.ServletRequest</p></td>
<td><p>getParameter(String parametername) getParameterValues()</p>
<p>getParameterMap()</p></td>
</tr>
<tr class="even">
<td><p>session</p></td>
<td><p>javax.servlet.http.HttpSession</p></td>
<td><p>setAttribute(String name, Object value) getAttribute(String name) removeAttribute(String name)</p></td>
</tr>
<tr class="odd">
<td><p>out</p></td>
<td><p>javax.servlet.jsp.JspWriter</p></td>
<td><p>print(char[] s) print(java.lang.String s)</p>
<p>println(java.lang.String x)</p>
<p>println(char[] x)</p></td>
</tr>
</tbody>
</table>

Examples:
saveinfo.jsp

    <%
        String name = request.getParameter("username");
        session.setAttribute("taintedAttribute", name);
    %>

displayinfo.jsp

    my xss varible: <%=session.getAttribute(name)%>

## Unified EL

Unified EL is a feature of JSP 2.1 it is a union of JSP 2.0 and JSF
expression languages. Expressions enclosed in ${…} are immediately
evaluated and printed to the page. Expressions consist of EL implicit
objects and bean names defined with jsp:usebean.
All EL implicit objects are propagators that can be sunk for XSS as an
expression.

  - param
  - paramValues
  - header
  - headerValues
  - cookie?

The examples for each implicit object demonstrates xss.
**param**

  - References a request parameter by name.
  - Equivalent to request.getParameter(“asdf”);

<!-- end list -->

    Welcome ${param.userName}!

**paramValues**

  - A String\[\] of parameter values.
  - Equivalent to request.getParameterValues().

*Using JSTL tags for this example.*

    <c:forEach var='parameter' items='${paramValues}'>
        <c:out value='${parameter.key}'/> =
        <c:forEach var='value' items='${parameter.value}'>
            <c:out value='${value}' escapeXml="false"/><br>
        </c:forEach>
    </c:forEach><br>

**header**

  - Maps a request header name to a single value.
  - Equivalent to request.getHeader.

<!-- end list -->

    ${header.cookie}

**headerValues**

  - A String\[\] array of header values.
  - The following example is the same as above.

<!-- end list -->

    <c:forEach var="head" items="${headerValues}">
            <c:out value="${head.key}" /> =
                 <c:forEach var="val" items="${head.value}">
                <c:out escapeXml="false" value="${val}" /><br>
            </c:forEach>
        </c:forEach><br>

**cookie**

Not sure if there's anything juicy here...

**pageScope**

  - Maps page-scoped variable names to their values.

The following example uses the JSTL <c:set> tag so you know where the
tainted variable comes from, I’ll cover c:set details in JSTL core
section.

    <c:set var="PageScopeVar" value="${param.fwd_last}" scope="page"/>
    ${pageScope.PageScopeVar}

**requestScope**

  - Maps request-scoped variable names to their values.
  - Looks exactly the same as pageScope.

<!-- end list -->

    <c:set var="ReqScopeVar" value="${param.fwd_last}" scope="request"/>
    ${requestScope.ReqScopeVar}

**sessionScope**

  - Maps session-scoped variable names to their values.
  - You can create a session variable with c:set as above OR you can use
    session.setAttribute.

<!-- end list -->

    <%session.setAttribute("sa_first", request.getParameter("first")); %>
    ${sessionScope.sa_first }

**applicationScope**

  - Maps application-scoped variable names to their values.

<!-- end list -->

    <c:set var="scopeVar" value="${param.addr}" scope="application"/>
    ${applicationScope.scopeVar }

## JSTL Tags

  - There are 5 tag libraries in JSTL: core, sql, fmt, xml.
  - This section will cover core and sql tags.

### Sinks

**<c:out>**
\*Like \<%= ... \>, but for expressions.

  - Has a boolean attribute escapeXml that converts \<,\>,&,'," to their
    corresponding entities. Defaults to true so it's really not an issue
    unless explicitly set to be false.

<!-- end list -->

    <c:out escapeXml="false" value="${param.first}"/>

**<c:redirect>**
Possibly susceptible to splitting?

    <c:redirect url="/include.jsp?lang=${param.first}"/>

### Propagators

**<c:url>**
\*Used to construct a string url. A contrived example.

    <c:url var="url2" value="/account.jsp?lang=${param.username}"/>
        <a href='${url2}'>yes this is dumb</a>

**<c:import>**
\* Imports the contents of a page, only a vuln if included page has a
vuln. (only tested with xss)

    <c:import url="/include.jsp"/>

**<c:param>**

    <c:url var="url1" value="/include.jsp?lang=">
        <c:param name="someParameter" value="${param.last}"/>
    </c:url>
    <a href='<c:out value="${url1}"/>'>Link back to some page (<c:out value="${url}"/>)</a>

**<c:set >**
\*Sets a variable to a value.

  - Can have page, application, request, or session scope.
  - Can be retrieved through use of scope objects or just by referencing
    the “var” in an expression.

<!-- end list -->

    <c:set var="appScopeVar" value="${param.addr}" scope="application"/>
    ${appScopeVar}

## Cleansers

## JSTL Functions

### Cleansers

**fn:escapeXml**
\* & \< \> “ ‘  \&amp \&lt \&gt &\#034 &\#039

```
    ${fn:escapeXml(taint) }
```

**fn:replace**
\*Potential cleanser if used correctly

  - ${fn:replace(taint, "\<", "\&lt")} replaces all “\<” with “\&lt”

<!-- end list -->

    ${fn:replace(taint,"<","HAH") }

[ the page linked below is marked for deletion: See also
<http://www.owasp.org/index.php/J2EE_Bad_Practices:_JSP_Expressions>
J2EE Bad Practices: JSP Expressions](Category:FIXME "wikilink")
[Category:Java](Category:Java "wikilink")