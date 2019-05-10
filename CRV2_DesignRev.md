## Introduction

This project highlights some of the vital areas of design security. We
are all aware of “secure coding” and practice it to great extent while
developing applications. But do we give equal attention to – “Secure
Design”? Most of us would probably say, NO. Design level flaws are
lesser known concepts but their presence is a very big risk to the
applications. Such flaws are hard to find in static or dynamic
application scans and instead require deep understanding of application
architecture and layout to uncover them manually. With increasing
business needs the complexities in application design and architecture
are also increasing. There is a rise in the use of custom design
techniques and diverse technologies in the applications today, which
makes the need for design reviews imperative. This project focuses on
highlighting some important secure design principles that developers and
architects must adapt to build a secure application design. With the
help of some design flaws we will see the areas of design that are
exposed to security risks and what measures can be taken to avoid them
in our design. It also includes mitigation techniques that can be
implemented in the applications to prevent them.

## Understanding the design

### What is an application design?

A design is a blueprint of an application; it lays a foundation for its
development. It illustrates the layout of the application and identifies
different application components needed for it. It is a structure that
determines execution flow of the application. Most of the application
designs are based on a concept of MVC. In such designs different
components interact with each other in an ordered sequence to serve any
user request.

### Why should be review the design?

Design review should be an integral part of secure software development
process. If the application is reviewed for security at the design level
many inherent backdoors can be uncovered. Design reviews also help to
implementing the security requirements in a better way.

## Methodology

The methodology to be followed for design reviews is explained below:

**Image one**

### Collection of Design Documents:

This phase involves collecting required information of the proposed
design. It would involve all kinds of documentation maintained by the
development team about the design like flow charts, sequence diagrams,
class diagrams etc. Requirements documents are also needed to understand
the objective of the proposed design.

### Design Study:

In this phase the design is thoroughly studied mainly with respect to
the data flow, different application components and their interactions,
data handling etc. This is achieved through manual analysis and
discussions with the design or technical architect’s team. The design
and the architecture of the application must be understood thoroughly to
analyse vulnerable areas that can lead to security breaches in the
application. The key areas of the design that must be considered during
threat analysis are given below.

  - Data Flow/Code Layout
  - Access control
  - Existing/Built-in Security controls
  - Entry points of non-user inputs
  - Integrations with external services
  - Location of configurations file and data sources
  - Add-ons and customization present (in case of built-in design
    framework)

This will help in identifying the trust boundaries for an application
and thus aid in taking decisions about the vulnerabilities and their
risk levels posed to the application.

### Design Analysis:

After understanding the design the next phase is to analyse the threats
for the design. This phase involves “threat modelling” the design.

The threats must be identified for different design areas that were
identified in the previous step. It involves observing the design from
an attacker’s perspective and uncovering the backdoors and insecure
areas present in it. The analysis can be done broadly on the basis of 2
important criteria: 1. Insecure Implementation – This would mean the
design has a loophole which can lead to a security breach in the
application. For instance, insecure reference to business logic
functions. 2. Lack of secure implementation – This would mean the design
has not incorporated secure practices. For instance, in connection to
external server different security requirements to protect
confidentiality and integrity of the data are not present.

Similar instances are listed below to illustrate the points that should
be broadly considered while analysing different design areas:

  - Data Flow -

a. Are user inputs used to directly reference a business logic
class/function b. Is there a data binding flaw? c. Does it expose any
backdoor parameter to invoke business logic? d. Is the execution flow of
the application correct?

  - Authentication and access control -

a. Does the design implement access control for all the files? b. Does
it handle session securely? c. Is there SSO, does it leave any backdoor?

  - Existing/built-in Security Controls -

a. Weakness in any existing security control b. Is the placement of the
security controls correct?

  - Architecture –

a. Is there validation for all input sources? b. Is the connection to
external servers secure?

  - Configuration/code files and datastores -

a. Are sensitive data present in configuration files? b. Does it support
any insecure data source?

A detailed checklist is available here - Excel Doc was Here At the end
of this activity we get a list of threats or insecure areas applicable
to the design.

### Propose Security Requirements:

After analysing the insecure areas in the design in this step a list of
security requirements corresponding to them must be created.
Requirements are high level changes or additions to be incorporated in
the design, for instance: Validate the inputs fetched from the
webservice response before processing them. Any protection that is
needed for resolving the vulnerable area identified in the design would
go as a security requirement for the design. This phase involves listing
all the security requirements for the design along with security risk
associated with them. This risk based approach would help the
development teams in prioritizing the security requirements.

### Recommend Design Changes:

In this phase every security requirement must be associated with a
security control. A security control best suited for the design is
proposed and documented. These security controls are an elaborate view
of the security requirements. Here, we would identify exact changes or
additions to be incorporated in the design that are needed to meet any
requirement or mitigate a threat. The changes or controls recommended
for the design should be clear and detailed, as given in the instances
below: a. Elaborate validation strategy with respect to: a. Identifying
right application component like servlet filters, interceptors,
validator classes etc. b. Placement of check c. Validation mechanism d.
Use of 3rd party security API’s or inbuilt design features of the
frameworks b. Encryption techniques c. Design Patterns And so on
depending on the control to be built in the design.

### Discussion with the design team:

The list of security requirements and proposed controls must be then
discussed with the development teams. The queries of the teams should be
addressed and feasibility of incorporating the controls must be
determined. Exceptions, if any must be taken into account and alternate
recommendations should be proposed. In this phase a final agreement on
the security controls is achieved.

### Design Finalization:

The final design incorporated by the development teams must be reviewed
again and finalized for further development process.

## Design flaws

This section describes some of the important design flaws that can leave
a backdoor in the application to access it without authentication or
manipulate its business logic. We will understand such flaws and secure
design recommendations in detail.

#### Business Logic Decision

During testing it is crucial to identify the key parameters related to
business logic and understand how application handles them. This section
will focus on insecure business logic decisions that are based on such
parameters. Two such cases are listed below, it is important to look for
such scenarios in the application while testing. 1. Use of non-editable
controls – Applications may use the values of non-editable controls,
drop-down menus, hidden fields or query string parameters for business
logic processing. If such fields contain values like the type of the
user, nature of the request, status of the transaction, etc. the
attackers will get a chance to manipulate them and perform unauthorized
operations. The application developers must understand that such fields
are non-editable only in the context of the proxy tool. The attackers
can easily modify their values using a proxy editor tool and try to
manipulate business logic.

2\. Business logic decision based on presence or absence of certain
parameters - This is especially observed in ASP.NET applications where
there is provision to make the server side controls hidden/invisible for
certain users. However, in most cases it has been observed that if the
users add the parameters corresponding to the UI elements that are kept
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
fields that are hidden from them. Secure Design Recommendation:

  - The application must not expose such parameters to the users.
  - If they are exposed, the application must not rely on request
    parameters for logical decisions. It must

maintain a separate copy of such values at the server side and use the
same for business logic processing.

  - Apply proper authorization checks on the server side for all
    transactions, wherever necessary. Do not

depend on presence of a user input for such decisions.

#### Business Logic Invocation Technique

##### Introduction

In most of the design techniques the request parameters or the URL’s
serve as sole factors to determine the processing logic. In such a
scenario the elements in the request which are used for such
identifications may be subject to manipulation attacks to obtain access
to restricted resources or pages in the application.

Consider a design below; here the business logic class is identified
based on a configuration file that keeps the mapping of the request URL
and the business logic class i.e. action class. **Image two**

##### What is the flaw?

A flaw in such a design could be unused configurations present in the
configuration file. Such configurations that are not exposed as valid
features in the application and could serve as a potential backdoor to
it. An unused configuration present in the configuration file of the
application is shown below: Image three

Observe that the “TestAction” has an insecure logic to delete records
from the system. This can act as a potential backdoor to the
application. **Image four**

##### Consider another scenario

In the some designs request parameters are used to identify business
logic methods. In the figure shown below a request parameter named
“event” is used to identify and invoke the corresponding event
handling methods of the business logic/action class. **Image five**

##### What is the flaw?

Here, the user can attempt to invoke the methods of the events that are
not visible to the user.

##### Secure Design Recommendation:

The applications must ensure to:

  - Remove ALL redundant/test/unexposed business logic configurations
    from the file
  - Apply necessary authorization check before processing business logic
    method
  - Maintain a mapping of method/class/view names with the privilege
    level of the users, wherever

applicable and restrict access of the users to restricted
URLs/methods/views.

##### Review Criteria

Understand the business logic invocation technique used in the design of
any application. Check if the user inputs are directly (i.e. without any
restriction) used to determine any of the following elements (as
applicable):

  - Business logic class
  - Method names
  - View component

#### Data Binding Technique

##### Introduction

Another popular feature seen in most of the design frameworks today is
data binding, where the request parameters get directly bound to the
variables of the corresponding business/command object. Binding here
means that the instance variables of such classes get automatically
initialized with the request parameter values based on their names.
Consider a sample design given below; observe that the business logic
class binds the business object with the request parameters. **Image
five**

##### What is the flaw?

The flaw in such design is that the business objects may have variables
that are not dependent on the request parameters. Such variables could
be key variables like price, max limit, role etc. having static values
or dependent on some server side processing logic. A threat in such
scenarios is that an attacker may supply additional parameters in
request and try to bind values for unexposed variable of business object
class. As illustrated in the figure below, the attacker sends an
additional “price” parameter in the request and binds with the unexposed
variable “price” in business object, thereby manipulating business
logic. **Image six**

##### Secure Design Recommendation:

  - An important point to be noted here is that the
    business/form/command objects must have only

those instance variables that are dependent on the user inputs.

  - If additional variables are present those must not be vital ones
    like related to the business rule for the

feature.

  - In any case the application must accept only desired inputs from the
    user and the rest must be

rejected or left unbound. And initialization of unexposed of variables,
if any must take place after the binding logic.

##### Review Criteria

Review the application design and check it is incorporates a data
binding logic. In case it does, check if business objects/beans that get
bound to the request parameters have unexposed variables that are meant
to have static values. If such variables are initialized before the
binding logic this attack will work successfully.

#### Placement of Security Controls

##### Introduction

Placement of security checks is a vital area of review in an application
design. Incorrect placements can render the applied security controls
null and void. So, it is important to study the application design and
spot the correctness of such checks in the overall execution flow of the
design. Most of the application designs are based on the concept of
Model-View-Controller (MVC). They have a central controller, which
listens to all incoming request and delegates control to appropriate
form/business processing logic. And ultimately the user is rendered with
a view. In such a layered design, when there are many entities involved
in processing a request, developers often go wrong in placing the
security controls at the right place. Most application developers feel
“view” is the right place to have the security checks like
authentication check etc. **Image seven**

##### What is the flaw?

It thus seems logical that if you restrict the users at the page/view
level they won’t be able to perform any operation in the application.
But what if instead of requesting for a page/view an unauthorized user
tries to request for an internal action like to action to add/modify any
data in the application? It will get processed but the resultant view
will be denied to the user; because the flaw lies in just having a view
based access control in the applications. I am sure you will agree that
a lot of processing for a request is done before the “view” comes into
picture in any design. So the request to process any action will get
processed successfully without authorization.

Consider a MVC based given in the figure below. Observe in the figure
that the authentication check is present only in the view pages.

**Image eight**

Observe that neither the controller servlet (central processing entity)
nor the action classes have any access control checks. So here, if the
user requests for an internal action like add user details, etc. without
authentication it will get processed, but the only difference is that
the user will be shown an error page as resultant view will be
disallowed to the user. **Image nine**

Insecure POST-BACK’s in ASP.NET A similar flaw is predominantly observed
in ASP.NET applications where the developers tend to mix the code for
handling POSTBACK’s and authentication checks. Usually it is observed
that the authentication check in the ASP.NET pages are not applied for
POSTBACKs, as indicated below. Here, if an attacker tries to access the
page without authentication an error page will be rendered. Instead, if
the attacker tries to send an internal POSTBACK request directly without
authentication it would succeed. A detailed explanation is present here.
**Image ten**

##### Secure Design Recommendation:

It is imperative to place all validation checks before processing any
business logic and in case of ASP.NET applications independent of the
POSTBACKs.

##### Review criteria

Check if the placement of the security checks is correct. The security
controls like authentication check must be place before processing any
request.

#### Execution Flow

##### Introduction

Execution flow is another important consideration of design. The
execution flow must terminate appropriately in case of an error
condition. However, due to mishandling of some programming entities
there could be a big hole in the application which would allow
unrestricted access to applications. One such flaw is related to –
“sendRedirect” method in J2EE applications.

`      response.sendRedirect(“home.html”);`

This method is used to send a redirection response to the user who then
gets redirected to the desired web component who’s URL is passesd an
argument to the method. One such misconception is that execution flow in
the Servlet/JSP page that is redirecting the user stops after a call to
this method. Take a look at the code snippet below, it checks for
authenticated session using an “if” condition. If the condition fails
the response.sendRedirect() is used to redirect the user to an error
page. **Image 11**

Note that there is code present after the If condition, which continues
to fetch request parameters and processes business logic for instance
adding a new branch entry of a bank in this case.

##### What is the flaw?

This flaw manifests as a result of the misconception that the execution
flow in the JSP/Servlet page stops after the “sendRedirect” call.
However it does not; in this case the execution of the servlet would
continue even if an invalid session is detected by the “if” condition
and thus the business logic will get processed for unauthenticated
requests.

Note: The fact that execution of a servlet or JSP continues even after
sendRedirect() method, also applies to Forward method of the
RequestDispatcher Class. However, <jsp:forward> tag is an exception, it
is observed that the execution flow stops after the use of <jsp:forward>
tag.

##### Secure Design Recommendation:

Since this flaw results from the assumption made by developers that
control flow execution terminates after a sendRedirect call, the
recommendation would be to terminate the flow using a “return”
statement.

##### Review criteria

Check if there is an appropriate logic to terminate the execution flow
is present in case of an error condition. Check for similar instances of
insecure security controls built using “sendRedirect” method.

## References:

''<http://artechtalks.blogspot.in/>

''<http://packetstormsecurity.com/files/119129/Insecure-Authentication-Control-In-J2EE.html>