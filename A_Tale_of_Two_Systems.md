## Overview

In the previous column we talked about some of the characteristics of
Web services systems that have implications for Information Security and
identified some of the kinds of security problems that arise in systems
that are implemented in this paradigm. One of the sets of problems that
was mentioned was Emergent Risks. In this article, we will talk a little
more about them and give examples from two different kinds of systems
and system architectures. This problem deserves special attention, not
because it is "more important" than others, but because it rarely seems
to get very much attention at all. Information security as a discipline
exists because of organizations' need to manage risk. Any risk that is
not managed leaves an organization exposed. It is appropriate to elect
leave some risks unmanaged if, after assessing the exposure it is
determined that effect of leaving the risk unmanaged is minimal. It is
not appropriate (and potentially even negligent) to simply ignore risks.
One of the goals of this article is to show that this is a class of
risks that usually are serious, though they are rarely acknowledged.

In order to keep the column to a managable length, the examples will be
kept simple and the discussion brief. Those with experience in doing
this kind of systems integration will appreciate that things are usually
much more complex than the discussion would suggest.

## Emergent Risk (Re)defined

We will begin our discussion with a reminder of a couple of the
properties of Web services systems that challenge security architects:

:\* Web services provide for a loose coupling of systems in which the
endpoint systems have no direct knowledge of each other nor any
relationship with each other.

:\* The endpoint systems were not originally designed as pieces of an
integrated system nor were they originally designed to participate in
the provision of a service to "strangers."

The focus for this column will be on how Web services introduce a new
universe of threats and risks to these legacy endpoint systems and the
implications for designers of Web services systems. In order to do so,
we need some terms introduced in the last column. Rather than require
the reader to reread that column, I will replicate the definitions here
and introduce a couple more.

When a system is designed and implemented, it is done implicitly or
explicitly against a set of requirements, and, explicitly or implicitly,
some of the requirements include controls that protect the system
against risks that were known or anticipated at the time. In order to
determine the optimum set of controls for the system, it is necessary to
understand the environment in which the system will be operating, and
model it. This exercise may be/have been undertaken formally or may have
"fallen out of" the usual requirements gathering process. Whatever the
case, the exercise results in some understanding of the threats the
system is expected to face, the risks associated with that exposure and
some notion of what controls to put into place that will allow the
organization to address those risks. Depending upon the severity of the
exposure and the cost of managing it, controls can be selected to:

:\# Prevent a negative event from occurring,

:\# React to a negative event, or

:\# Detect and report on the occurrence of a negative event.

There are many kinds of controls and each can be implemented in many
different ways. They can run the gamut from physical and logical access
control mechanisms to policies to business and technical processes. Some
of the factors that influence the selection of controls are:

:\* The value of the asset being protected.

:\* The nature of the threat.

:\* The nature of the vulnerability to the threat.

:\* The risk to the business if an attack is successful and is publicly
known.

:\* Whether to prevent, react to or simply monitor the attack.

:\* The cost of the control.

By the end of the requirements gathering process, enough should be known
about the (IT) risk profile of the system that the selection of controls
can be made. One way to categorize this information is as follows:

:\* Design threat/risk model - The characterization of the threats/risks
that exist or which are anticipated at the time the system was designed
and implemented.

:\* Design control assumptions - The assumptions made about the efficacy
of the selection of controls to be implemented by the system. The
assumptions are based on the design threat/risk model and the selection
of threats to be prevented, managed and monitored. (Controls are not
limited to physical and technical access control mechanisms. They also
include business and technical processes as well as policy).

:\* Design control set - The set of (risk management) controls selected
for the system. This selection is based on the design threat/risk model
and the design control assumptions.

:\* Design trust model - The characterization of the entities that are
expected to be a part of The System; what their (trust) responsibilities
are, and the degree to which they can be expected to fulfill them. In
this case, The System includes hardware, software, business and
technical processes and human beings.

:\* Design trust boundaries - The "line" that separates aspects of the
system that are subject to the system controls from those that are not.

:\* Design trust domain - The elements of the system that are subject to
the design system controls.

One of the challenges for Web services security is that this information
is rarely formalized and captured in the analysis and design
documentation or in a system security architecture. It is much more
likely to be found in organizations that have a good system security
engineering program and have reached Level 3 or higher in the SSE-CMM or
which have a certification and accreditation process in place. Even in
those organizations there is a possibility that the documentation may
not be available for some of the legacy systems. The absence of explicit
documentation just means a lot of reverse engineering for the analysts
and designers of the Web services that will be talking to these legacy
systems.

Before we go any farther, I need to talk about how I am going to use a
couple of words. The word "trust" will appear frequently, and it will be
overloaded. It will mean different things depending upon the context. A
search of the InfoSec literature will show the same thing. Unless there
could be some confusion about the meaning in a particular situation, I
am going to let the context provide the meaning.

The other word I will use loosely will be "endpoint." An endpoint could
be a legacy system or an individual user. In most cases, it will not
matter or it will be obvious from the context which it is. If the
context is ambiguous and it is important that the distinction be made, I
will. It is possible that endpoints can be built from scratch
specifically to participate in a Web services-based system. One would
expect that those endpoints would not be subject to the problem being
addressed in this article.

The trouble for an endpoint begins when the legacy system is recruited
into participating in a system in which there are elements that exist
outside the legacy system's trust domain. This changes the operating
environment of the existing system. With very few exceptions, this has
the effect of introducing risks that are not present in the system's
design risk model and for which there are no controls in place that
would allow the risks to be managed. The greater the difference between
the "old" environment and the "new" environment, the greater the
probability that there will be some risks in the "new" environment that
are not included in the legacy system's design risk and threat models.
With respect to Web services and legacy systems, the emergent risks are
those risks that arise for the legacy system when it is confronted with
becoming part of a larger system.

In the next few paragraphs we will look at two systems whose
environments were changed enough that the change induced emergent risks.
These systems were chosen because they are of varying vintage and
architecture. The idea is to show that the problem is not specific to a
particular class of application. It really does not matter exactly which
system it is. In fact, the message I would like to convey is that these
are patterns in the Gang of Four sense of the term. The examples are
taken from real applications. However, I have tried to omit enough
detail so that the identity of the specific system is not apparent while
preserving enough to make the examples meaningful.

## A Mainframe Batch Application

This first example will illustrate how "putting a Web front end" onto a
legacy banking system can create emergent risks for the legacy system.
First we will introduce the salient aspects of the mechanics of a
typical checking account system and a typical savings account system.
Then we will plug a naive Web application into the system and examine
what can happen.

### Setting the Stage

Consider a classical Demand Deposit Account (DDA) banking application.
One that was designed to support the typical checking account and the
typical banking day. The salient aspects of an archetypal DDA system are
these:

:\#When a customer opens a DDA account, among other things they do is
sign a signature card. This card is kept on file and used (when
necessary) to:

::\* Verify the identity of the account-holder and

::\*Verify that the person who is requesting activity on the account
(making a deposit or cashing a check) really is who they represent
themselves to be.

:\#Bank tellers are responsible for identifying and authenticating
accountholders and authorizing transactions on a given account. They do
this visually and by verifying signatures against the signature card if
necessary.

:\#When a customer makes a deposit they fill out a deposit slip and
present it along with the items to be deposited and after the teller has
recorded the deposit, he/she then gives the customer a receipt. Thus
there is a paper trail of the transaction activity. (In some systems,
part of the process of recording the deposit is for the teller to make
an entry into an intra-day transaction activity file on the mainframe).

:\#Cashing a check is somewhat different. The customer presents a signed
or endorsed check and, after the teller verifies the account balance and
records the transaction, the teller gives the customer their money. In
systems that maintain an intra-day transaction activity file, the
transaction is recorded there.

:\#At the end of the business day, all transactions are batched up and
totalled. Specifics about what crosschecks are done vary from system to
system, but one way or another, the activity of the tellers is
crossfooted against the reported activity of the branch and the paper
trail of checks and deposit slips is verified against the electronic
transaction log.

:\#Again, details may vary, but if there is an intra-day transaction
file, information in that is sometimes crossfooted with information in
the daily batch. It might be that the intra-day activity file actually
takes the place of the daily batch file.

:\#The exact contents of the daily batch file and/or the intra-day
transaction log varies, but the data that are of interest for this
discussion are the account number, the amount and the presence of some
audit trail information.

:\#ATM transactions are a variation on the theme. In the branch, the
teller is responsible for identifying and authenticating the user and
authorizing transactions. ATMs have the same responsibilities, but they
use different "tokens." Tellers use signature cards and visual
identification and ATMs use the ATM card/PIN combination. The difference
is that ATMs must eventually communicate with the mainframe in order to
get account information. The specifics of the mechanism vary from system
to system, but in the end, the ATM must consult with the DDA system in
order to get account balance information, etc. Eventually, the ATM
transactions that occur during the banking day end up being captured in
the intra-day transaction log. Typically, either the ATM itself or an
intermediary system will also log ATM transactions. Usually, the
customer has the option of receiving a transaction ticket.

:\#ATM transactions can take place "over a longer wire" than
branch-based transactions, but (theoretically, at least) they are done
over secure circuits and are usually encrypted over the wire. (This is
slowly changing, though. Earlier in the year, the Sapphire/SQL Slammer
worm took out some 13,000 of Bank of America's ATMs. There is a lesson
in there somewhere . . .). In the end, though, ATMs end up communicating
with the same back-end transactions that are used by the branch-based
systems.

:\#There is some kind of communication protocol/infrastructure that
allows branch terminals and ATMs to communicate with the mainframe
transaction/data set. Typically, organizations employ some kind of
message-based protocol, which in IBM shops is usually based on MQSeries.
This example will use it. In this case, the branch application or the
ATM gateway would build a query message or a transaction message and put
it on an MQ queue. A receiving process on the mainframe would take the
incoming message off the queue and route it to the appropriate IMS/CICS
or whatever transaction. If a reply were needed, the mainframe
transaction would create it and hand it to the routing process to be put
on an outbound queue.

:\#At some time in the middle of the night during the batch runs, the
day's transactions are posted to the account file and the account
balances are updated. After any error processing, the batch/intra-day
file is cleared and ready for the next day's activity. (There is usually
some magic going on behind the scenes in order to not lock out
middle-of-the night ATM transactions but that does not matter for this
discussion).

The mechanics of a typical savings account are for, purposes of this
discussion, the same as for a DDA account. The major difference being
that, when the customer wishes to withdraw from the savings account,
he/she presents a withdrawal slip rather than a check made out to cash.
To transfer funds from a savings account to a checking account basically
entails the customer filling out a withdrawal slip and a deposit slip
and gives them to the teller. This results in two messages: a
"withdrawal" message containing the "from account" number and the amount
to be withdrawn to the savings account system and a "deposit" message to
the DDA system which has in it the account number to which the deposit
is to be made along with the amount to be deposited. Transfers the other
way work similarly, except this time the customer fills out a deposit
slip for the savings account and writes a check to cash or him/herself.
This time, the "from account" would be the DDA account and the "to
account" would be the savings account.

A typical bank has some means of defining "relationships" in which a
bank customer identifier is associated with all of the accounts that
that customer has with the bank. This makes life much easier for
Customer Service Representatives and ATMs. If an ATM is going to allow a
person to transfer money between accounts, there must be a mechanism
available for it to determine the accounts to which the user has
legitimate access. With the relationship information, the ATM system can
construct the inquiry and transaction messages with the appropriate
account numbers to the legacy system.

### Some Design Assumptions

From the last section, we can infer some of the assumptions that
designers of the system could make about risks and controls.

:\#The batch program trusts that the sources of the transactions
(tellers or ATMs) have:

:\#\#identified and authenticated the requester of the transaction,

:\#\#verified the account number(s) in the transaction and

:\#\#authorized the transaction.

:\#The teller could be "trusted" to exercise due diligence in the
identification, authentication and authorization processes because of
the paper trails and the crosschecking of paper records and electronic
records.

:\#The ATM can be "trusted" in the identification, authentication and
authorization processes because it relies on dual-factor authentication
of the customer, it is only able to offer transactions against accounts
that wer in the customer's relationship, and, theoretically, the
communication channel is secure.

:\#So a core design assumption is that the transactions that are sent to
the batch update file are valid and trusted. (They must be. There simply
isn't any way for the batch update program to be able to tell a bogus
transaction from a valid one. Essentially, the only information it has
is an account number and an amount. There may be some audit trail
information there, too, like maybe a branch identifier and a timestamp .
. . or even a teller id . . . but the update program has to accept on
faith that the account number that it is using is the correct one).

:\#The assumption about being able to trust the data (specifically, the
account number) that appears in the batch file depends upon the tacit
assumption that there is no means by which a customer can affect the
contents of the transaction.

The design trust domain encompasses tellers, ATM machines, the ATM
network, the internal network, and operating processes and procedures
(controls) that implement the necessary checks and balances.

### The Paradigm Shift

Now the bank decides that it wants to allow on-line access to its
services. It wants to let its retail customers inquire on account
balances, transfer funds between accounts, pay bills, etc. The bank
decides to use Web services to implement the system. It will give its
retail customers access to bank transactions via the Web and will
provide a B2B "back-end" with payees in order to facilitate the bill-pay
process. In this scenario, we will only focus on the customer-facing
part of the system.

The Web services development team talks with the mainframe support group
and learns of the message set that the branch and ATM systems use and
adopt them. They talk with the ATM support team and learn how that
system uses the relationship mechanism to select the correct accounts to
present to the customer. The then build an online banking application
that, among other things allows a customer to transfer money between
accounts. The (abbreviated) scenario looks something like this:

:\#The customer logs into the online application using a combination of
ID and password.

:\#The customer selects the "Transfer Funds" option.

:\#The Web application sends the account numbers in the relationship out
to the browser which are displayed in drop-down lists that allow the
customer to select the "from" account, the "to" account and the amount.

:\#The selection is then sent back to the Web services application which
then builds the messages for the mainframe application and sends them
out.

From a system behavior perspective, this looks almost identical to the
way the ATMs work, and it is possible to reuse almost all the applicable
ATM logic. However, there are a couple of aspects of this implementation
that, unless one is really looking for them, create a significant threat
to the system. These threats exist only because of the new operating
environment in which the legacy system finds itself operating.

### The Risks Emerge

One of the vulnerabilities/risks falls out of the identification and
authentication process. Tellers and ATMs use multi-factor
authentication. The application uses single-factor authentication; a
user ID and a passcode. This mechanism is subject to shoulder surfing,
but that is reasonably easily managed, although harder than at an ATM
machine. Worse by far is that it is also subject to keyboard monitoring
attacks. See the articles on The Register and the Washington Post about
a recent exploit in which the attacker used a spyware program to glean
login ids and passwords to his victim's brokerage account. This was an
attack of limited scope only because the purpose of the attack was
limited in scope. It is only a matter of time before someone tweaks one
of the mass-mailing worms to deliver a keystroke logger. Then it is only
a matter of harvesting the logs and grepping through them for activity
on online banking/trading/commercial sites . . . See these articles at
News.Com and The New York Times (requires free registration) for
glimpses of the tip of the iceberg.

Another risk that arises for the first time is that the customer has
control over (part of) the data stream. In this naive application, the
Web services layer sent the customer's account numbers and balances out
to the browser. The customer then POSTed transactions back to the Web
services layer. The Web services layer then constructed a message using
the account and amount information from the POST and sent it to the
mainframe . . . just like in the ATM world. There was never any need for
the system to question anything it got from the ATM. Theoretically, the
ATM was a secure machine, it implemented dual-factor authentication, and
communications were encrypted. No one could get access to the data
stream. This is not the case in the wonderful world of the World Wide
Web. There are client-side proxies everywhere. In the new universe, it
is not possible to trust the data stream. End-users can change the data
stream at will, even that "protected" by SSL . . . see for instance,
@stake's WebProxy or Packet Storm's Achilles. Given the way this
application was written, it was possible to transfer funds between any
two accounts in the system . . . because the services layer assumed that
it was not going to get anything back that it didn't send out. It did
not know that it could not trust the data coming back to it.

A third risk is the absence of the paper trail that is available from
branch- and ATM-based applications. If the Web service does not log
activity, there is no trail. Non-repudiation is much harder to establish
in this environment also. Banks and ATMs have surveillence cameras. The
Web services environment does not have that. Even if the Web application
does log activity, the single factor authentication is so weak that the
audit trail is worth little.

The only thing that saves this from being really bad is that, these
days, most Web banking applications only allow funds transfer among
accounts in the customer's relationship. So the monetary risk to the
bank is minimal. The two major risks are:

:\#Reputational risk for the bank.

:\#Loss of privacy and identity theft for the customer.

Once an attacker gets a person's online banking ID and password, they
have access to a signficant amount of information. They can see how and
where that person spends their money. They can see their credit card
balance. If the person has a trading account, they have access to much
more information. That is the risk a bank customer takes in using the
online system. The bank faces several risks that follow from this. If
one customer's account is cracked, the bank must deal with managing its
relationship with that customer and hope that the customer does not make
a big deal of the situation. If the attacker succeeds in getting access
to several or hundreds of the bank's customers' information, the problem
becomes very different for the bank. The context will shift from
"accident on the part of the customer" to "negligence on the part of the
bank."

### Implications for the Mainframe and the Web Services Layer

These are serious threats to the legacy system. The Web services
application is far outside of its trust domain. As described above, the
mainframe cannot trust anything it gets from the Web services layer. The
designers of the Web services layer did not understand what the
mainframe's risk and trust models were. They didn't know that it was not
OK to just "write to the interface." They did not understand that there
were no controls in the mainframe system's design control set that could
address the risks introduced by this new layer.

This was a deliberately simple example of a naive implementation. In
this example, the Web services layer violated the mainframe system's
design control assumptions because it did not verify that the account
numbers that were being tendered by the endpoint were valid for that
customer. It was easy to miss this because it was part of the business
process in the branch and, in the case of the ATMs, was done implicitly.
It only shows up in the Web services environment because of specific
properties of that environment. The risks that the system creates by
using single-factor authentication don't have a parallel in the branch-
and ATM-based world. This is what makes identifying emergent risks so
challenging.

## A Two-tier Client-server Application

This tale is about what happens when a manufacturer decides to share the
information that is kept in a typical early-'90s client-server
line-of-business application with its customers.

### Setting the Stage

This was an Oracle-based system that was a combination of off-the-shelf
and internally developed code. The user interface was built using
SQL\*Forms and application logic was implemented in Forms triggers and
database triggers and stored procedures. (I am only naming these
products because they are a relevant part of the design of the system).
The system provided of the basic functions the manufacturer needed;
basic accounting, inventory management, sales order processing, standard
routing, QA, shipping, etc. This was a specialist operation that
provided custom processing to customers' goods, so the inventory
management, shop floor control, QA and shipping subsystems tracked
customers' goods from the time they were received, through the
manufacturing process all the way through shipping, in more or less real
time. Order status was updated as goods flowed through the process and
Accounts Receivable was updated whenever an order was shipped and
billed. Following are some of the aspects of the system that are
pertinent to this discussion.

This was an integrated system which at any time could provide current:

:\* Customer order status

:\* Customer inventory by location

:\* Customer inventory status by state (raw, in-process, QA, finished)

:\* Customer inventory by location

:\* Work in process by manufacturing order

:\* Work in process by machine and by process

:\* Work in process by manufacturing department

:\* Work in process by customer

:\* Aged Accounts Receivable by customer

:\* Ad-hoc inquiries on various combinations of the above information

The industry of which this organization was a part is intensely
competitive and the margins are very low. Corporate management was
interested in finding ways to distinguish itself from its competition.
In a commodity market, quality and price are not differentiators
(unless, of course quality is low or price is high). It was felt that
giving customers the opportunity to do their own Just-In-Time inventory
management would be a great way to generate customer allegiance. So the
decision was made to "open up the system" and let the customers do their
own Just-in-Time inventory management. They would be able to enter their
own manufacturing orders, set processing priorities, follow their orders
through the manufacturing process and enter their own shipping orders.

### Some Design Assumptions

The application design was more or less standard for the time. It was
modular; each module could stand alone but the modules all worked
against a system-level data model and could work with one another if
configured to do so. Also typical of systems of this genre were the
assumptions about how and by whom the modules would be used. These
assumptions are the ones that will be violated by the paradigm shift.
Lets take a look at some of them.

There were several modules that were affected by this decision:

:\* Accounts Receivable

:\* Order Entry

:\* Inventory Management

:\* Shop Floor Control

:\* Scheduling

:\* Quality Assurance

:\* Warehouse

:\* Shipping and Receiving

Each module made the following assumption: Only people who worked "in
the department" would be given access to the module, and these users
have access to all the functionality of the module. This is not unusual,
and follows the way organizations work in general. The assumption is,
for instance, that anyone who has legitimate access to the Order Entry
system could and would be expected to be able to manage orders for any
customer. (It may be the case that particular individuals within a
department "have their own customers," but that is a matter of
convenience for the department, not a system requirement).

Since there was no formal relationship between modules, any individual
could be authorized to use more than one. Access to system function was
managed in a table that associated system user IDs with menu items.
Through this mechanism it was possible to construct "personalized" menus
for each user. When users initiated sessions, they were presented with a
system menu that gave them access to whatever functions were assigned to
them, across modules. "Normal" users saw only one module, and sometimes,
only a subset of the functionality available in that module. The
important thing to keep in mind, though, is that no matter how few
functions and individual might be able to perform, the user could
perform that function on any customer/account/inventory item or whatever
in the system. Herein lies the problem.

### The Paradigm Shift

Out of the box, a user who could run an aged receivables report could
run that report on any, all, or a subset of all customers. A user who
could query the status of work in process on the manufacturing floor
could do so for any, all or a subset of machines, customers, etc. A user
who could schedule shipments could do so for any or all customers, etc.,
etc., etc. Now we want to make some of the system functionality and data
available to customers. The paradigm shift is that now the customer will
be allowed to:

:\* Get a quotation online

:\* Enter a new order

:\* Check on the status of existing orders

:\* Locate inventory

:\* Issue shipping instructions

:\* Check pricing

:\* See current aged receivables

:\* etc.

### The Risks Emerge

All of that functionlity is already available. The problem is that the
system design assumes that the only entities that are going to be using
the system are employees who need to be able to work with all customers'
accounts. The system design also assumes that the company employees will
not discuss one customer's information with another customer. As was
mentioned previously, the industry is intensely competitive and
processing secrets and cost and pricing schedules are jealously guarded.
All of this information is readily avaliable on the system, and there
are controls in place to protect it, given the way the system was
originally designed. However, giving customers direct access to the
system invalidates the design threat, risk and trust models. Customers
are outside the design trust domain. There are no controls in place to
manage the risks that are incurred by giving customers access to the
system. Some of the risks are that customers could:

:\* See each other's manufacturing secrets.

:\* See each other's cost structures.

:\* See the company's cost and pricing structures.

:\* See the company's manufacturing secrets.

:\* See each other's work in process.

:\* Reprioritize each other's orders.

:\* Issue bogus shipping instructions for other customers' goods.

:\* etc.

In short, just giving customers direct access to the existing system or
"writing to the interface" would be tantamount to creating a platform
for industrial espionage.

### Implications for the Legacy System and the Design of the Customer-facing Subsystem

Giving customers access to the system had the effect of defining a class
of user and type of system access that was orthogonal to that for which
the system was originally designed. It meant adding a whole new
dimension to the control space. It created the necessity for introducing
role-based access control into the system. There is not the space to go
into the details of the surgery that had to be done to implement the new
system. The move to allow customers access to the system violated one of
the cornerstone assumptions of the original system design. Suffice it to
say that the job was made much easier because of Oracle's understanding
of roles.

## Lessons Learned

In this article, I have tried to give a couple of real-world examples of
emergent risks. If I succeeded in presenting them in the right way, the
response of many readers will be something like: "Well, duh\! Of
course\!" I expect that by the time readers finished the sections on
design assumptions, they would have an idea of what was coming next and
the glimmerings of a solution. The tale that wasn't told is the one
about the "journey to enlightenment . . ."

As noted early in the article, the probability of the existence of a
design document that details threat and risk models, the control set,
and the trust model against which the system was designed is slim to
negligible. The older the legacy system, the less likely it is. (At
least in the commercial universe. There is more of that sort of
information available in some military and intelligence systems. But for
Joe Sixpack Webspert who is trying to build an HR portal, that
information is not there). Every organization is different, but if one
reads the mailing lists and newgroups, one comes away with the
overwhelming impression that there is no one who, at the beginning of a
Web services project, says: "Guys, before we start designing this thing,
we need to understand the security assumptions that are being made by
the systems to which we are going to connect so that we be sure that we
don't violate them with our system." Not once have I experienced that.
The thing is, if it is not done, the Web services application is very
likely to become the legacy system's greates threat. I do not believe
that there is an intentional decision not go through the process. In
almost all situations, it has just been a case of no one thinking about
it. Simply a lack of awareness.

Compounding the lack of awareness on the part of the Web services
development team management is the chasm between them and the team which
supports the legacy systems. Though there might be no written
documentation on the assumptions made by the design of the legacy
system, that information usually is available, but it's in the heads of
the people who are supporting the legacy system. In large organizations,
there is usually considerable distance, both organizational and
geographic, between the two teams. Sometimes the Web services
development team is part of a business unit in one city and the
mainframe support team is in the Corporate IT group at corporate
headquarters. Even worse, the mainframe application support team may be
outsourced and the people who really know the system are half a world
and twelve time zones away. In situations like this, communication
between the teams is likely to be cumbersome and painful, making it very
hard to establish the kind of interaction that facilitates the discovery
process. In the end, this situation becomes yet another of the emergent
risks that has to be managed.

### Getting Through the First Pass of the Discovery Process

It would be nice to be able to produce a list of emergent risks that
could be handed to the Web services development team. Given that every
situation is going to be different, that is impossible. There are some
general classes of controls that can form the basis for research. If the
team is lucky enough to establish a good dialogue with the legacy system
support team, detailed information will fall out of the disucssions. A
way to get started would be to ask the following questions about the
controls listed below: Are there any? What are they? What was the threat
and risk profile against which they were chosen? What risks are they
intended to manage? What are the design trust assumptions? What are the
design trust boundaries?

:\* Identification controls

:\* Authentication controls

:\* Authorization/access controls

:\* Non-repudiation controls

:\* Confidentiality controls

:\* Integrity controls

:\* Availability controls

Good discussions around them should give the design team an idea of what
the legacy system thought it had to defend itself against and how it
went about doing it. The next step is to understand what new threats and
risks will be created by introducing the Web services subsystem into the
legacy system's environment. Then comes the challenge of figuring out
how to design the Web services subsystem so that it manages those risks
and insulates the legacy system from them. It may take several
iterations of this process to nail things down, and of course, some
things will be overlooked, but that is to be expected. Hopefully the
major risks will have been identified. In the end, though, introducing
Web services into the operating environment of a legacy system should
not introduce significant new risks to the legacy system, and there must
be a way to demonstrate that due diligence was done.

Organizations that have mature (IT) risk management programs already do
this or something like it. The ones that have a robust Information
Assurance program probably have much of the necessary information in
formal documentation and have representatives from IA/InfoSec on all
development and support teams. For these organizations, this is probably
not news. However, there are many more organizations that do not have
mature risk management programs and robust Information Assurance progams
than there are those that do. In the past, it has just not been
necessary for these organizations to develop them. Introducing Web
services into a system can introduce significant new risks to legacy
systems. It is for concerned individuals in those organizations that
this article was written.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:Web Services](Category:Web_Services "wikilink")