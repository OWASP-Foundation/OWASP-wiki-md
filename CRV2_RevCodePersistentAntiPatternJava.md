# Java Persistence anti-patterns

## Spring –Hibernate Anti-patterns

Some of the following anti-patterns are an important concern in the
security area of Java applications. A related problem with these
anti-patterns is data integrity.

### Lazy loading

This feature reduces the handling of data in an asynchronous way, which
avoids unnecessary requests to the database, however it can causes
problems with persistence. Errors associated with Lazy loading are:

`org.hibernate.StaleObjectStateException: Row was updated or deleted by another transaction (or    `
`unsaved-value mapping was incorrect)`

#### N+1 Select issue

This problem occurs when the collection is returned from the database,
containing n+1 separate queries instead of a single join query. This
issue is quite challenging to solve because it depends on the specific
implementation of the code, therefore look for the following executions:

  - Control that mapping configurations are updated for affected domain
    classes
  - Add the @ManyToMany @Fetch(FetchMode.JOIN) as a query strategy to
    override the Lazy behavior if necessary
  - Review Tuning fetching strategies from Hibernate reference
    (http://docs.jboss.org/hibernate/core/3.3/reference/en/html/performance.html\#performance-fetching-custom)

### Sessions per Operation anti-pattern

This anti pattern is caused by the opening and closing of individual
sessions for each call executed to the database. In order to avoid this
issue, make sure the calls are planned in sequence. Control proper
implementation of persistence context. Problem occurs when DAO uses
different persistence context for each one, in other words, a different
Session or EntityManager.

Example of anti-pattern : Using the following code for each operation

`session = sessionFactory.openSession(); `
`session.close() `

### Open Conversation anti-pattern

Keeping a database session alive while a user 'a' is editing data
meanwhile, a lock is exerted to avoid concurrency issues can cause
serious performance and bottlenecks in the application. It is not
advisable to do this in order to keep data integrity. There are other
Hibernate features that allows the developer to handle sessions in a
much efficient way such as automatic optimistic concurrency

## Long Term Persistence Security Issues

Long-term persistence is a model that enables beans to be saved in XML
format.(Java Tutorial, 2013). For this purpose, a programmer can use
XMLEncoder class to pass through output files for textual representation
of Serializable objects.In the example provided in the Java Tutorial,
the programmer can invoke and create an instance of javax.swing.JButton
such as this

<object class="javax.swing.JButton">
`   `<void method="setText">
`       `<string>`Cancel`</string>
`           `</void>
`   `</object>

The vulnerability occurs when instead of passing acquitted XML code, the
attacker sends dangerous Payloads. This vulnerability was shown by Dinis
Cruz, Alvaro Muñoz and Abraham Kang in DefCon Conference 2013 “Resting
on Your Laurels will get you Pwned: Effectively Code Reviewing REST
Applications to avoid getting powned”

As explained by Dinis Cruz (2013) in his blog "there are two key
scenarios where this ‘feature’ becomes a spectacular vulnerability:

  - Server-side backend system that process attacker-controlled XML
    files using XMLDecoder
  - REST APIs that uses XMLDecoder to create strongly type objects from
    the HTTP Request data

And the 2nd case is exactly what happens with Restlet REST API , which
wraps XMLDecode in its
org.restlet.representation.ObjectRepresentation<T> feature/class."(Cruz,
2013)

An Example of an attack which can be fond in Github from many examples
created by Cruz , creates an item

<?xml version="1.0" encoding="UTF-8"?>

<java>` `
<object class="firstResource.Item">`    `
<string>`a aName`</string>
<string>`a Description`</string>
</object>
</java>`    `

## Recommendations

It's clear that proper understanding of certain features and Java
methods is essential to avoid certain vulnerabilities associated with
the use of Persistence in frameworks, ORM'S and specific Java classes

## References

NHibernate, 2013 "Transactions and concurrency control" available at
<http://docs.jboss.org/hibernate/orm/4.1/devguide/en-US/html/ch02.html#session-per-operation>
accessed on 4rd October 2013

Oracle, 2013 "Java Tutorials" available at
<http://docs.oracle.com/javase/tutorial/javabeans/advanced/longpersistence.html>
Accessed on 3rd October 2013

Dinis Cruz, 2013 "Using XMLDecoder to execute server-side Java Code on
an Restlet application (i.e. Remote Command Execution)" available at
<http://blog.diniscruz.com/2013/08/using-xmldecoder-to-execute-server-side.html>
Accessed on 3rd October 2013

<https://github.com/o2platform/DefCon_RESTing/blob/master/Demos/_O2_Scripts/XmlEncoder%20-%20Restlet/exploits/1%20-%20create%20item%20%28Simple%29.xml>