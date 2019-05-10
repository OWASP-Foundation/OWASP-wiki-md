# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![Incubator_big.jpg](Incubator_big.jpg "Incubator_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_secure_application_design_project">OWASP Secure Application Design Project</h2>
<p>OWASP Secure Application Design Project is...</p>
<h2 id="introduction">Introduction</h2>
<p>This project highlights some of the vital areas of design security. We are all aware of “secure coding” and practice it to great extent while developing applications. But do we give equal attention to – “Secure Design”? Most of us would probably say, NO. Design level flaws are lesser known concepts but their presence is a very big risk to the applications. Such flaws are hard to find in static or dynamic application scans and instead require deep understanding of application architecture and layout to uncover them manually. With increasing business needs the complexities in application design and architecture are also increasing. There is a rise in the use of custom design techniques and diverse technologies in the applications today, which makes the need for design reviews imperative. This project focuses on highlighting some important secure design principles that developers and architects must adapt to build a secure application design. With the help of some design flaws we will see the areas of design that are exposed to security risks and what measures can be taken to avoid them in our design. It also includes mitigation techniques that can be implemented in the applications to prevent them.</p>
<h2 id="description">Description</h2>
<p><strong>What is an application design?</strong> A design is a blueprint of an application; it lays a foundation for its development. It illustrates the layout of the application and identifies different application components needed for it. It is a structure that determines execution flow of the application. Most of the application designs are based on a concept of MVC. In such designs different components interact with each other in an ordered sequence to serve any user request.</p>
<p><strong>Why should be review the design?</strong> Design review should be an integral part of secure software development process. If the application is reviewed for security at the design level many inherent backdoors can be uncovered. Design reviews also help to implementing the security requirements in a better way.</p>
<h2 id="what_is_secure_application_design">What is Secure Application Design?</h2>
<p>Design level flaws are lesser known concepts but their presence is a very big risk to the applications. Such flaws are hard to find in static or dynamic application scans and instead require deep understanding of application architecture and layout to uncover them manually. Design level security is crucial and must be adopted at an early stage of application development to build a robust system. Thus the aim of this project is to impart secure design guidelines to application developers. The project will highlight vulnerable areas in application designs through real world examples and scenarios and touch up on different aspects of design level security. The focus will also be to explain measures to be taken to prevent such flaws while designing applications. The guidelines will cover core design concepts which can applicable to any application independent of the platform. Most of the design flaws will be discussed using sample code incorporated in an insecure design application. The project will also focus on releasing a secure design checklist for reviewing application designs or threat modelling them.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="licensing">Licensing</h2>
<p>OWASP Secure Application Design Project is free to use. It is under an Apache 2.0 License (fewest restrictions, even allowing proprietary modifications and proprietary forks of your project</p>
<h2 id="presentation">Presentation</h2>
<h2 id="project_leader">Project Leader</h2>
<p><a href="mailto:ashish.rao@owasp.org">Ashish Rao</a></p>
<h2 id="related_projects">Related Projects</h2>
<h2 id="ohloh">Ohloh</h2></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://www.owasp.org/images/f/f7/Checklist_For_Design.pdf">Secure Application Design Checklist</a></li>
</ul>
<h2 id="email_list">Email List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp_secure_application_design">Sign Up</a></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[20 Nov 2013] News 2</li>
<li>[30 Sep 2013] News 1</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="New_projects.png" title="New_projects.png" alt="New_projects.png" width="100" /><figcaption>New_projects.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_DOC.jpg" title="Project_Type_Files_DOC.jpg" alt="Project_Type_Files_DOC.jpg" /><figcaption>Project_Type_Files_DOC.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Methodology of Design Review

The methodology to be followed for design reviews is explained below:

![Image:Design.png](Design.png "Image:Design.png")

## **Collection of Design Documents**

This phase involves collecting required information of the proposed
design. It would involve all kinds of documentation maintained by the
development team about the design like flow charts, sequence diagrams,
class diagrams etc. Requirements documents are also needed to understand
the objective of the proposed design.

## **Design Study**

In this phase the design is thoroughly studied mainly with respect to
the data flow, different application components and their interactions,
data handling etc. This is achieved through manual analysis and
discussions with the design or technical architect’s team. The design
and the architecture of the application must be understood thoroughly to
analyse vulnerable areas that can lead to security breaches in the
application. The key areas of the design that must be considered during
threat analysis are given below.

1.  Data Flow/Code Layout
2.  Access control
3.  Existing/Built-in Security controls
4.  Entry points of non-user inputs
5.  Integrations with external services
6.  Location of configurations file and data sources
7.  Add-ons and customization present (in case of built-in design
    framework)

This will help in identifying the trust boundaries for an application
and thus aid in taking decisions about the vulnerabilities and their
risk levels posed to the application.

## **Design Analysis**

After understanding the design the next phase is to analyse the threats
for the design. This phase involves “threat modelling” the design.

The threats must be identified for different design areas that were
identified in the previous step. It involves observing the design from
an attacker’s perspective and uncovering the backdoors and insecure
areas present in it. The analysis can be done broadly on the basis of 2
important criteria:

**1. Insecure Implementation** – This would mean the design has a
loophole which can lead to a security breach in the application. For
instance, insecure reference to business logic functions.

**2. Lack of secure implementation** – This would mean the design has
not incorporated secure practices. For instance, in connection to
external server different security requirements to protect
confidentiality and integrity of the data are not present.

Similar instances are listed below to illustrate the points that should
be broadly considered while analysing different design areas:

1.  Data Flow -
    1.  Are user inputs used to directly reference a business logic
        class/function
    2.  Is there a data binding flaw?
    3.  Does it expose any backdoor parameter to invoke business logic?
    4.  Is the execution flow of the application correct?
2.  Authentication and access control -
    1.  Does the design implement access control for all the files?
    2.  Does it handle session securely?
    3.  Is there SSO, does it leave any backdoor?
3.  Existing/built-in Security Controls -
    1.  Weakness in any existing security control
    2.  Is the placement of the security controls correct?
4.  Architecture –
    1.  Is there validation for all input sources?
    2.  Is the connection to external servers secure?
5.  Configuration/code files and datastores -
    1.  Are sensitive data present in configuration files?
    2.  Does it support any insecure data source?

A detailed checklist is available here - [Secure Application Design
Checklist](https://www.owasp.org/images/f/f7/Checklist_For_Design.pdf).

At the end of this activity we get a list of threats or insecure areas
applicable to the design.

## **Propose Security Requirements**

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

## **Recommend Design Changes**

In this phase every security requirement must be associated with a
security control. A security control best suited for the design is
proposed and documented. These security controls are an elaborate view
of the security requirements. Here, we would identify exact changes or
additions to be incorporated in the design that are needed to meet any
requirement or mitigate a threat. The changes or controls recommended
for the design should be clear and detailed, as given in the instances
below:

1.  Elaborate validation strategy with respect to:
    1.  Identifying right application component like servlet filters,
        interceptors, validator classes etc.
    2.  Placement of check
    3.  Validation mechanism
    4.  Use of 3rd party security API’s or inbuilt design features of
        the frameworks
2.  Encryption techniques
3.  Design Patterns

And so on depending on the control to be built in the design.

## **Discussion with the design team**

The list of security requirements and proposed controls must be then
discussed with the development teams. The queries of the teams should be
addressed and feasibility of incorporating the controls must be
determined. Exceptions, if any must be taken into account and alternate
recommendations should be proposed. In this phase a final agreement on
the security controls is achieved.

## **Design Finalization**

The final design incorporated by the development teams must be reviewed
again and finalized for further development process.

# Design Flaws - Web

This section describes some of the important design flaws are lesser
known facts and can inadvertently leave a leave a backdoor in the
application. We will understand the security flaws that can creep in
while developing MVC applications.

A design of an application determines how different classes and files
interact with each other to serve any user request. It is a structure
that determines execution flow in the application. Most of the
application designs are based on a concept of MVC.

The design and the architecture of the application must be understood
thoroughly to analyze vulnerable areas that can lead to security
breaches in the application. The key areas of the design that must be
considered during threat analysis are given below. • Data Flow/Code
Layout • Placement of security controls • Entry points of non-user
inputs • Integrations with external services • Location of
configurations file and data sources • Add-ons and customization present
(in case of built-in design framework)

This will help in identifying the trust boundaries for an application
and thus aid in taking decisions about the vulnerabilities and their
risk levels posed to the application.

## Business Logic Invocation Technique

**Introduction**

In most of the design techniques the request parameters or the URL’s
serve as sole factors to determine the processing logic. In such a
scenario the elements in the request which are used for such
identifications may be subject to manipulation attacks to obtain access
to restricted resources or pages in the application.

Consider a design below; here the business logic class is identified
based on a configuration file that keeps the mapping of the request URL
and the business logic class i.e. action class.

![<File:Design1.png>](Design1.png "File:Design1.png")

**What is the flaw?**

A flaw in such a design could be that unused configurations may be
present in the configuration file that can be accessed by an attacker.
Such configurations that are not exposed as valid features in the
application and could serve as a potential backdoor to it. An unused
configuration present in the configuration file of the application is
shown below:

![<File:Design2.jpg>](Design2.jpg "File:Design2.jpg")

Observe that the “TestAction” has an insecure logic to delete records
from the system. This can act as a potential backdoor to the
application.

![<File:Design3.jpg>](Design3.jpg "File:Design3.jpg")

**Consider another scenario - Method Invocation** In the some designs
request parameters are used to identify business logic methods. In the
figure shown below a request parameter named “event” is used to identify
and invoke the corresponding event handling methods of the business
logic/action class. ![<File:Design4.png>](Design4.png
"File:Design4.png")

**What is the flaw?**

Here, the user can attempt to invoke the methods of the events that are
not visible to the user.

The applications must ensure to: • Remove ALL redundant/test/unexposed
business logic configurations from the file • Apply necessary
authorization check before processing business logic method • Maintain a
mapping of method/class/view names with the privilege level of the
users, wherever applicable and restrict access of the users to
restricted URLs/methods/views.

**Review Criteria**

With a view of the above mentioned factors we must carefully evaluate
the design of any application to determine whether user inputs are
directly (i.e. without any restriction) used to determine any of the
following elements (as applicable):

• Business logic class • Method names • View component

In such case identify unexposed configurations and business logic
methods as per the user privileges (wherever applicable) and attempt to
access them.

In the some designs request parameters are used to identify business
logic methods. In the figure shown below a request parameter named
“event” is used to identify and invoke the corresponding event
handling methods of the business logic/action class.

## Model Object Binding Technique

**Introduction**

Another popular feature seen in most of the design frameworks today is
binding of model objects with user inputs. Here the request parameters
get directly bound to the variables of the corresponding
business/command object. Binding here means that the instance variables
of such classes get automatically initialized with the request parameter
values based on their names. Consider a sample design given below;
observe that the business logic class binds the business object with the
request parameters.

![<File:Design5.png>](Design5.png "File:Design5.png")

**What is the flaw?**

The flaw in such design could be that the business objects may have
variables that are not dependent on the request parameters. Such
variables could be key variables like price, max limit, role etc. having
static values or dependent on some server side processing logic. A
threat in such scenarios is that an attacker may supply additional
parameters in request and try to bind values for unexposed variable of
business object class. As illustrated in the figure below, the attacker
sends an additional “price” parameter in the request and binds with the
unexposed variable “price” in business object, thereby manipulating
business logic.

![<File:Design6.png>](Design6.png "File:Design6.png")

**Secure Design Recommendation:**

  - An important point to be noted here is that the
    business/form/command objects must have only those instance
    variables that are dependent on the user inputs. If additional
    variables are present those must not be vital ones like related to
    the business rule for the feature.
  - In any case the application must accept only desired inputs from the
    user and the rest must be rejected or left unbound. And
    initialization of unexposed of variables, if any must take place
    after the binding logic.

**Review Criteria**

Review the application design and check it is incorporates a data
binding logic. In case it does, check if business objects/beans that get
bound to the request parameters have unexposed variables that are meant
to have static values. If such variables are initialized before the
binding logic this attack will work successfully.

## Placement of Security Controls

**Introduction**

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
authentication check etc.

**What is the flaw?**

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

Consider a MVC based given in the figure below.

![<File:Design7.png>](Design7.png "File:Design7.png")

Observe in the figure that the authentication check is present only in
the view pages. Observe that neither the controller servlet (central
processing entity) nor the action classes have any access control
checks. So here, if the user requests for an internal action like add
user details, etc. without authentication it will get processed, but the
only difference is that the user will be shown an error page as
resultant view will be disallowed to the user.

![<File:Design8.png>](Design8.png "File:Design8.png")

**Insecure POST-BACK’s in ASP.NET**

A similar flaw is predominantly observed in ASP.NET applications where
the developers tend to mix the code for handling POSTBACK’s and
authentication checks. Usually it is observed that the authentication
check in the ASP.NET pages are not applied for POSTBACKs, as indicated
below. Here, if an attacker tries to access the page without
authentication an error page will be rendered. Instead, if the attacker
tries to send an internal POSTBACK request directly without
authentication it would succeed. A detailed explanation is present here
-[1](http://artechtalks.blogspot.in/2013/02/insecure-postback-based-authentication.html)

![<File:Design9.png>](Design9.png "File:Design9.png")

**Secure Design Recommendation:**

Do not just restrict the access of the users only over views. It is
imperative to place all validation checks before processing any business
logic and in case of ASP.NET applications independent of the POSTBACKs.

**Review criteria**

Check if the placement of the security checks is correct. The security
controls like authentication check must be place before processing any
request.

## Execution Flow

**Introduction**

Execution flow is another important consideration of design. The
execution flow must terminate appropriately in case of an error
condition. However, due to mishandling of some programming entities
there could be a big hole in the application which would allow
unrestricted access to applications. One such flaw is related to –
“sendRedirect” method in J2EE applications.

*response.sendRedirect(“home.html”);*

This method is used to send a redirection response to the user who then
gets redirected to the desired web component, whose ULR is passed as an
argument to the method –in this case home.html. One such misconception
is that execution flow in the Servlet or JSP page that is redirecting
the user stops after a call to this method.

Take a look at the code snippet below, it checks for authenticated
session using an “if” condition. If the condition fails the
response.sendRedirect() is used to redirect the user to an error page.
Note that there is code present after the If condition, which continues
to fetch request parameters and processes business logic for instance
adding a new branch entry of a bank in this case.

**What is the flaw?**

This flaw manifests as a result of the misconception that the execution
flow in the JSP/Servlet page stops after the “sendRedirect” call.
However it does not; in this case the execution of the servlet would
continue even if an invalid session is detected by the “if” condition
and thus the business logic will get processed for unauthenticated
requests.

**Note:** The fact that execution of a servlet or JSP continues even
after sendRedirect() method, also applies to Forward method of the
RequestDispatcher Class. However, <jsp:forward> tag is an exception, it
is observed that the execution flow stops after the use of <jsp:forward>
tag.

**Secure Design Recommendation:**

Since this flaw results from the assumption made by developers that
control flow execution terminates after a sendRedirect call, the
recommendation would be to terminate the flow using a “return”
statement.

**Review criteria**

Check if there is an appropriate logic to terminate the execution flow
is present in case of an error condition. Check for similar instances of
insecure security controls built using “sendRedirect” method.

## Backdoor Parameters/ Business Logic Decision based on User input

During testing it is crucial to identify the key parameters related to
business logic and understand how application handles them. This section
will focus on insecure business logic decisions that are based on such
parameters. There are 3 such cases listed below:

**CASE 1:** The application must not depend on non-editable controls,
drop-down menus or hidden fields for business logic processing. It is a
secure practice to use the business logic parameters like price, max
limit etc. from the server side. Even if the application sends these
parameters as non-editable, select or hidden parameters it must maintain
a separate copy of such values at the server side and use the same for
business logic processing. The users can easily alter such parameter
values and try to manipulate business logic.

**CASE 2:** At times applications tend to make logical decisions merely
on the basis of the values of certain request parameters. Such
parameters are often the once indicating the type of the user, nature of
the request, status of the transaction, etc. The application must not
expose such parameters to the users. Even if they are exposed, the
application must not rely on request parameters for logical decisions
and analyse the same from server side processing. The users can easily
manipulate such parameter values and try to evade business logic
validations or elevate privileges in the application.

**CASE 3:** Some application developers believe in the concept of –
“what is hidden is secure”. They decide on the visibility of the some
input fields for the features based on the role/privilege level of the
logged-in user. This is especially observed in ASP.NET applications
where there is provision to make the server side controls
hidden/invisible for certain users. However, in most cases it has been
observed that if the users add the parameters corresponding to the UI
elements that are kept hidden/invisible to them into the request, they
are able to change the behaviour of the server side logic. Consider a
scenario where only admin user can change password of other users of the
system, as a result the field to enter username is only made visible to
the admin user. However, if a normal a user tries to add username
parameter in the request he/she will be able to trick the server in
believing that the request has come from an admin user and try to change
password of other users. Thus there exists a loophole in such
applications where the server side behaviour can be influenced with
request parameters. Users can perform unauthorized operations in the
application by supplying the values for the inputs fields that are
hidden from them.

# FAQs

  - Q1
    A1

<!-- end list -->

  - Q2
    A2

# Acknowledgements

## Volunteers

Secure Application Design is developed by a worldwide team of
volunteers. The primary contributors to date have been:

  - xxx
  - xxx

## Others

  - xxx
  - xxx

# Road Map and Getting Involved

As of May 2014, the priorities are:

  - xxx
  - xxx
  - xxx

Involvement in the development and promotion of the Secure Application
Design is actively encouraged\! You do not have to be a security expert
in order to contribute. Some of the ways you can help:

  - xxx
  - xxx

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")