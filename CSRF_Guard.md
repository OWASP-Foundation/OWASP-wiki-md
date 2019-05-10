1.  REDIRECT [:Category:OWASP CSRFGuard
    Project](:Category:OWASP_CSRFGuard_Project "wikilink")

## Overview

Just when developers are starting to run in circles over [Cross Site
Scripting Flaw](Cross_Site_Scripting_Flaw "wikilink"), the ['sleeping
giant'](http://www.darkreading.com/document.asp?doc_id=107651&WT.svl=news1_2)
awakes for yet another web-catastrophe. [Cross-Site Request
Forgery](Cross-Site_Request_Forgery "wikilink") (CSRF) is an attack
whereby the victim is tricked into loading information from or
submitting information to a web application for which they are currently
authenticated. The problem is that the web application has no means of
verifying the integrity of the request.

## Recommended Prevention Measure: Unique Request Tokens

The core issue with CSRF attacks is that form submission can be imitated
with forged requests. The application must be able to differentiate
between legal requests and forged requests. Since all headers, cookies,
and credentials will be submitted with both legal and forged requests,
the only method of truly verifying the integrity of the request is with
a uniquely identifiable token in the form of an HTTP parameter. When the
user first visits the site, the application will generate and store a
*session specific* unique request token. This session specific unique
request token is then placed in each form and link of the HTML response,
ensuring that this value will be submitted with the next request. For
each subsequent request, the application must verify the existence of
the unique token parameter and compare its value to that of the value
stored in the user's session. The security of the approach is based on
the fact that this unique token value is specific to a user's session
and is *hard to guess.* Therefore, it is imperative that this value is
large and cryptographically secure.

:\***UPDATE:** There have been discussions suggesting that the unique
request token can be compromised using JavaScript. This attack implies
that the application also contains a Cross-Site scripting vulnerability,
which is a more severe issue than Cross-Site request forgery. The first
Myspace worm worked in this manner where it used a Cross Site Scripting
vulnerability to forge requests to update a user's profile, where the
user profile update mechanism was protected with an antiCSRF defense
mechanism similar to what is provided by this filter. You can mitigate
this risk somewhat by making your form key AND value a CSRF Guard-type
token.

## Example: The Java CSRF Guard

### Java EE Filter

Java EE filters provide the ability to intercept, view, and modify both
the request and associated response for the requesting client. Filters
are inserted and executed by the Java EE container's deployment
descriptor (web.xml) file. For example, if an HTTP request for a JSP
page hits our Apache web server, the request is sent to Tomcat for
processing. Before Tomcat executes the code inside of the JSP, the
request must be passed along a chain of Java EE filters. The following
snippet illustrates how to declare and map a filter to a particular
URI-space in web.xml:

<filter>
`   `<filter-name>`CSRFGuard`</filter-name>
`   `<filter-class>`org.owasp.csrf.CSRFGuard`</filter-class>
`     `<init-param>
`       `<param-name>`error-page`</param-name>
`       `<param-value>`error.jsp`</param-value>
`     `</init-param>
</filter>

<filter-mapping>
`  `<filter-name>`CSRFGuard`</filter-name>
`  `<url-pattern>`/*`</url-pattern>
</filter-mapping>

Implementing the CSRF Guard as a Java EE Filter gives us the ability to
verify the integrity of the request before it ever hits our web
application.

### Secure Random

When implementing the CSRF Guard, we must ensure that the unique request
token is cryptographically strong. After all, our implementation relies
on the principle that the unique token is difficult to guess. If the
unique request token can be easily guessed then a CSRF attack can be
executed.

The following code snippet generates a BASE64 encoded string of 'size'
bytes:

`   private String generateCSRFToken(int size) {`
`       SecureRandom sr = null;`
`       byte[] random = new byte[size];`
`       BASE64Encoder encoder = new BASE64Encoder();`
`       String digest = null;`
`       `
`       try {`
`           sr = SecureRandom.getInstance("SHA1PRNG");`
`           `
`           sr.nextBytes(random);`
`           `
`           digest = encoder.encode(random);`
`       } catch (Exception e) {`
`           e.printStackTrace();`
`       }`
`       `
`       return digest;`
`   }`

### Implementation

The following Java EE Filter will attempt to verify the integrity of the
request by comparing the OWASP_CSRFTOKEN HTTP parameter value with that
of the OWASP_CSRFTOKEN session attribute. If the two values do not
match, then the request is forged and we invoked the doError() method.
This method will invalidate the existing session and redirect the user
to a page specified by the filter init-parameter "error-page". If the
parameter value equals the corresponding session attribute value, then
we call doChain() and pass the request to the webapplication. Once the
web application is finished processing the request, the
buildLinkParameters() method will search the HTML response for forms and
links and insert the appropriate OWASP_CSRFTOKEN parameter value.
Unfortunately, the dependency on an HTML response means that the current
filter may not work with some Web 2.0 applications. Furthermore, the
filter only modifies response objects whose "Content-Type" header is
text based. If your web application neglects to set the appropriate
value for the "Content-Type" header, then the CSRF Guard will not make
the appropriate changes to the HTML response and each subsequent request
will be considered a violation.

`/*`
` * CSRFGuard.java`
` *`
` * Created on January 2, 2007, 11:35 AM`
` *`
` * Copyright (C) 2007 Eric Sheridan`
` *`
` * This library is free software; you can redistribute it and/or`
` * modify it under the terms of the GNU Lesser General Public`
` * License as published by the Free Software Foundation; either`
` * version 2.1 of the License, or (at your option) any later version.`
` *`
` * This library is distributed in the hope that it will be useful,`
` * but WITHOUT ANY WARRANTY; without even the implied warranty of`
` * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU`
` * Lesser General Public License for more details.`
` *`
` * You should have received a copy of the GNU Lesser General Public`
` * License along with this library; if not, write to the Free Software`
` * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA`
` */`

`package org.owasp.csrf;`
` `
`import java.io.OutputStream;`
`import java.io.IOException;`
`import java.security.SecureRandom;`
`import java.util.regex.Pattern;`
`import javax.servlet.Filter;`
`import javax.servlet.FilterChain;`
`import javax.servlet.FilterConfig;`
`import javax.servlet.ServletException;`
`import javax.servlet.ServletRequest;`
`import javax.servlet.ServletResponse;`
`import javax.servlet.http.HttpSession;`
`import javax.servlet.http.HttpServletRequest;`
`import javax.servlet.http.HttpServletResponse;`
`import sun.misc.BASE64Encoder;`
`import org.owasp.csrf.http.MutableHttpResponse;`

`/**`
` *`
` * @author esheridan`
` */`
`public class CSRFGuard implements Filter {`
`   public final static String OWASP_CSRFTOKEN = "OWASP_CSRFTOKEN";`
`   `
`   public final static Pattern FORM_PATTERN = Pattern.compile("(?i)`

</form>

");

`   public final static Pattern SKIPPABLE_PATTERN = Pattern.compile(".*\\.(gif`

|jpg |png |css |js |ico |swf |axd.\*)$");

`   private String errorPage = null;`
`   `
`   public void init(FilterConfig config) {`
`       errorPage = config.getInitParameter("error-page");`
`   }`
`   `
`   public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) {`
`       if(request instanceof HttpServletRequest && response instanceof HttpServletResponse) {`
`           try {`
`               HttpServletRequest hRequest = (HttpServletRequest)request;`
`               MutableHttpResponse mResponse = new MutableHttpResponse((HttpServletResponse)response);`
`               HttpSession session = hRequest.getSession(false);`
`               `
`               if(session != null) {`
`                   if(!hasCSRFToken(session)) {`
`                       setCSRFToken(session);`
`                       doChain(hRequest, mResponse, response, chain);`
`                   } else if(isSkippable(hRequest) `

| | isValidRequest(session, hRequest)) {

`                       doChain(hRequest, mResponse, response, chain);`
`                   } else {`
`                       doError(session, (HttpServletResponse)response);`
`                   }`
`               } else {`
`                   chain.doFilter(request, response);`
`               }`
`           } catch (Exception e) {`
`               e.printStackTrace();`
`           }`
`       }`
`   }`
`   `
`   public void destroy() {`
`       `
`   }`
`   `
`   private void doError(HttpSession session, HttpServletResponse response) throws IOException {`
`       session.invalidate();`
`       response.sendRedirect(errorPage);`
`   }`
`   `
`   private void doChain(HttpServletRequest request, MutableHttpResponse mResponse, ServletResponse response, FilterChain chain) throws IOException, ServletException {`
`       OutputStream out = response.getOutputStream();`
`       `
`       chain.doFilter(request, mResponse);`
`       `
`       String contentType = mResponse.getContentType();`
`       String token = getCSRFToken(request.getSession());`
`       `
`       if(contentType != null && contentType.startsWith("text")) {`
`           String content = new String(mResponse.getContent());`
`           content = getModifiedResponse(token, content);`
`           byte[] result = content.getBytes();`
`           `
`           response.setContentLength(result.length);`
`           out.write(result);`
`       } else {`
`           out.write(mResponse.getContent());`
`       }`
`       `
`       out.close();`
`   }`
`   `
`   private String getModifiedResponse(String token, String content) {`
`       content = buildFormParameters(content, token);`
`       content = buildLinkParameters(content, token);`
`       `
`       return content;`
`   }`
`   `
`   private String getCSRFToken(HttpSession session) {`
`       return (String)session.getAttribute(OWASP_CSRFTOKEN);`
`   }`
`   `
`   private boolean hasCSRFToken(HttpSession session) {`
`       return getCSRFToken(session) != null;`
`   }`
`   `
`   private void setCSRFToken(HttpSession session) {`
`       session.setAttribute(OWASP_CSRFTOKEN, generateCSRFToken());`
`   }`
`   `
`   private String generateCSRFToken() {`
`       return generateCSRFToken(32);`
`   }`
`   `
`   private String generateCSRFToken(int size) {`
`       SecureRandom sr = null;`
`       byte[] random = new byte[size];`
`       BASE64Encoder encoder = new BASE64Encoder();`
`       String digest = null;`
`       `
`       try {`
`           sr = SecureRandom.getInstance("SHA1PRNG");`
`           `
`           sr.nextBytes(random);`
`           `
`           digest = encoder.encode(random).replace('+', '_');`
`       } catch (Exception e) {`
`           e.printStackTrace();`
`       }`
`       `
`       return digest;`
`   }`
`   `
`   private boolean isSkippable(HttpServletRequest request) {`
`       return SKIPPABLE_PATTERN.matcher(request.getRequestURI()).matches();`
`   }`
`   `
`   private boolean isValidRequest(HttpSession session, HttpServletRequest request) {`
`       String original = (String)session.getAttribute(OWASP_CSRFTOKEN);`
`       String now = (String)request.getParameter(OWASP_CSRFTOKEN);`
`       boolean result = false;`
`       `
`       if(now != null && now.equals(original)) {`
`           result = true;`
`       }`
`       `
`       return result;`
`   }`
`   `
`   private String buildFormParameters(String content, String token) {`
`       return FORM_PATTERN.matcher(content).replaceAll("<input type=\"hidden\" name=\"" + OWASP_CSRFTOKEN + "\" value=\"" + token + "\">\n`

</form>

");

`   }`
`   `
`   private String buildLinkParameters(String content, String token) {`
`       content = buildLinkParameters(content, token, "href=\"", '"');`
`       content = buildLinkParameters(content, token, "src=\"", '"');`
`       `
`       return content;`
`   }`
`   `
`   private String buildLinkParameters(String content, String token, String pattern, char termChar) {`
`       StringBuffer buffer = new StringBuffer();`
`       int i=0;`
`       int index = 0;`
`       int length = content.length();`
`       `
`       while(i < length) {`
`           index = content.toLowerCase().indexOf(pattern, i);`
`           `
`           if(index != -1) {`
`               int offset = 0;`
`               int n = 0;`
`               boolean parameters = false;`
`               String tokenString = null;`
`               buffer.append(content.substring(i, index+pattern.length()));`
`               `
`               for(n=index+pattern.length(), offset=n; n<=length && content.charAt(n) != termChar; n++) {`
`                   buffer.append(content.charAt(n));`
`                   `
`                   if(content.charAt(n) == '?') {`
`                       parameters = true;`
`                   }`
`               }`
`               `
`               if(parameters) {`
`                   tokenString = "&" + OWASP_CSRFTOKEN + "=" + token;`
`               } else {`
`                   tokenString = "?" + OWASP_CSRFTOKEN + "=" + token;`
`               }`
`               `
`               buffer.append(tokenString);`
`               `
`               i = index + pattern.length() + (n - offset);`
`           } else {`
`               buffer.append(content.substring(i, length));`
`               `
`               i = length;`
`           }`
`       }`
`       `
`       return buffer.toString();`
`   }`
`}`

### Download

The Proof-of-Concept implementation of the Cross-Site Request Forgery
Guard discussed in this article can be downloaded here:
[CSRF_Guard.zip](:Image:CSRF_Guard.zip "wikilink")

### Related Projects

A Proof-of-Concept implementation of the CSRF Guard for the PHP platform
is under development: [PHP CSRF Guard](PHP_CSRF_Guard "wikilink")

A Proof-of-Concept implementation of the CSRF Guard for the ASP.Net
platform (as an ASP.Net Module/Filter) is under development as part of
the OWASP .Net project toolset. [.Net CSRF
Guard](.Net_CSRF_Guard "wikilink")

## References

:\*
<http://news.com.com/Netflix+fixes+Web+2.0+bugs/2100-1002_3-6126438.html?tag=cd.lede>

:\* <http://shiflett.org/articles/foiling-cross-site-attacks>

:\*
<http://java.sun.com/j2se/1.4.2/docs/api/java/security/SecureRandom.html>