**Business Logic Decision** During testing it is crucial to identify the
key parameters related to business logic and understand how application
handles them. This section will focus on insecure business logic
decisions that are based on such parameters. Two such cases are listed
below, it is important to look for such scenarios in the application
while testing. 1. Use of non-editable controls – Applications may use
the values of non-editable controls, drop-down menus, hidden fields or
query string parameters for business logic processing. If such fields
contain values like the type of the user, nature of the request, status
of the transaction, etc. the attackers will get a chance to manipulate
them and perform unauthorized operations. The application developers
must understand that such fields are non-editable only in the context of
the proxy tool. The attackers can easily modify their values using a
proxy editor tool and try to manipulate business logic. 2. Business
logic decision based on presence or absence of certain parameters - This
is especially observed in ASP.NET applications where there is provision
to make the server side controls hidden/invisible for certain users.
However, in most cases it has been observed that if the users add the
parameters corresponding to the UI elements that are kept
hidden/invisible to them into the request, they are able to change the
behaviour of the server side logic. Consider a scenario where only admin
user can change password of other users of the system, as a result the
field to enter username is only made visible to the admin user. However,
if a normal a user tries to add username parameter in the request he/she
will be able to trick the server in believing that the request has come
from an admin user and try to change password of other users. Thus there
exists a hole in such applications where the server side behaviour can
be influenced with request parameters. Users can perform unauthorized
operations in the application by supplying the values for the inputs
fields that are hidden from them. Secure Design Recommendation: ● The
application must not expose such parameters to the client. ● If they are
exposed, the application must not rely on request parameters for logical
decisions. It must maintain a separate copy of such values at the server
side and use the same for business logic processing. ● Apply proper
authorization checks on the server side for all transactions, wherever
necessary. Do not depend on presence of a user input for such decisions.

**Business Logic Invocation Technique** Introduction In most of the
design techniques the request parameters or the URL’s serve as sole
factors to determine the processing logic. In such a scenario the
elements in the request which are used for such identifications may be
subject to manipulation attacks to obtain access to restricted resources
or pages in the application. Consider a design below; here the business
logic class is identified based on a configuration file that keeps the
mapping of the request URL and the business logic class i.e. action
class. Image two

What is the flaw? A flaw in such a design could be unused configurations
present in the configuration file. Such configurations that are not
exposed as valid features in the application and could serve as a
potential backdoor to it. An unused configuration present in the
configuration file of the application is shown below: Image three
Observe that the “TestAction” has an insecure logic to delete records
from the system. This can act as a potential backdoor to the
application. Image four. Consider another scenario In the some designs
request parameters are used to identify business logic methods. In the
figure shown below a request parameter named “event” is used to identify
and invoke the corresponding event handling methods of the business
logic/action class. Image five What is the flaw? Here, the user can
attempt to invoke the methods of the events that are not visible to the
user. Secure Design Recommendation: The applications must ensure to: ●
Remove ALL redundant/test/unexposed business logic configurations from
the file ● Apply necessary authorization check before processing
business logic method ● Maintain a mapping of method/class/view names
with the privilege level of the users, wherever applicable and restrict
access of the users to restricted URLs/methods/views. Review Criteria
Understand the business logic invocation technique used in the design of
any application. Check if the user inputs are directly (i.e. without any
restriction) used to determine any of the following elements (as
applicable): ● Business logic class ● Method names ● View component

**Data Binding Technique** Introduction Another popular feature seen in
most of the design frameworks today is data binding, where the request
parameters get directly bound to the variables of the corresponding
business/command object. Binding here means that the instance variables
of such classes get automatically initialized with the request parameter
values based on their names. Consider a sample design given below;
observe that the business logic class binds the business object with the
request parameters. Image five What is the flaw? The flaw in such design
is that the business objects may have variables that are not dependent
on the request parameters. Such variables could be key variables like
price, max limit, role etc. having static values or dependent on some
server side processing logic. A threat in such scenarios is that an
attacker may supply additional parameters in request and try to bind
values for unexposed variable of business object class. As illustrated
in the figure below, the attacker sends an additional “price” parameter
in the request and binds with the unexposed variable “price” in business
object, thereby manipulating business logic. Image six Secure Design
Recommendation: ● An important point to be noted here is that the
business/form/command objects must have only those instance variables
that are dependent on the user inputs. ● If additional variables are
present those must not be vital ones like related to the business rule
for the feature. ● In any case the application must accept only desired
inputs from the user and the rest must be rejected or left unbound. And
initialization of unexposed of variables, if any must take place after
the binding logic.

Review Criteria Review the application design and check if it
incorporates a data binding logic. In case it does, check if business
objects/beans that get bound to the request parameters have unexposed
variables that are meant to have static values. If such variables are
initialized before the binding logic this attack will work successfully.

**Execution Flow** Introduction Execution flow is another important
consideration of design. The execution flow must terminate appropriately
in case of an error condition. However, due to mishandling of some
programming entities there could be a big hole in the application which
would allow unrestricted access to applications. One such flaw is
related to the “sendRedirect” method in J2EE applications.

`   response.sendRedirect(“home.html”);`

This method is used to send a redirection response to the user who then
gets redirected to the desired web component whose URL is passed an
argument to the method. One such misconception is that execution flow in
the Servlet/JSP page that is redirecting the user stops after a call to
this method. Take a look at the code snippet below, it checks for
authenticated session using an “if” condition. If the condition fails
the response.sendRedirect() is used to redirect the user to an error
page. Image 11 Note that there is code present after the If condition,
which continues to fetch request parameters and processes business logic
for instance adding a new branch entry of a bank in this case. What is
the flaw? This flaw manifests as a result of the misconception that the
execution flow in the JSP/Servlet page stops after the “sendRedirect”
call. However it does not; in this case the execution of the servlet
would continue even if an invalid session is detected by the “if”
condition and thus the business logic will get processed for
unauthenticated requests. Note: The fact that execution of a servlet or
JSP continues even after sendRedirect() method, also applies to Forward
method of the RequestDispatcher Class. However, <jsp:forward> tag is an
exception, it is observed that the execution flow stops after the use of
<jsp:forward> tag.

Secure Design Recommendation: Since this flaw results from the
assumption made by developers that control flow execution terminates
after a sendRedirect call, the recommendation would be to terminate the
flow using a “return” statement. Review criteria Check if there is an
appropriate logic to terminate the execution flow is present in case of
an error condition. Check for similar instances of insecure security
controls built using “sendRedirect” method. References:
<http://artechtalks.blogspot.in/>
<http://packetstormsecurity.com/files/119129/Insecure-Authentication-Control-In-J2EE.html>