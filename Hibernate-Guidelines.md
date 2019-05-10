## Status

**In progress**

## Important

### SQL Injection

It is commonly thought that ORM layers, like Hibernate are immune to SQL
injection. This is not the case as Hibernate includes a subset of SQL
called HQL, and allows "native" SQL queries. Often the ORM layer only
minimally manipulates the inbound query before handing it off to the
database for processing.

### Transaction Scope

All database communication should occur within the scope of a
Transaction.

### Persisting Tainted Data

If an application sets tainted properties in an object, then makes that
object persistent, it is highly likely that data will be accessed at
some point and displayed. If database values are never displayed to the
user then obviously this is nullified. Better yet if we could figure out
which values from the db are tainted but I have a feeling it's not a
feasible scan.

### Rollback

When an exception occurs, roll back the Transaction and close the
Session. If you don't, Hibernate can't guarantee that in-memory state
accurately represents persistent state. If your Session is bound to the
application, you have to stop the application. Rolling back the database
transaction doesn't put your business objects back into the state they
were at the start of the transaction, so the database state and the
business objects do get out of sync. Objects that are manipulated after
a rollback as if they were synchronized.

-----

## Simple

### Don't use load() to determine existence

Do not use Session.load() to determine if an instance with the given
identifier exists on the database; use Session.get() or a query instead.

### Constructing Query Strings

Hibernate has a set of functions that are used internally to construct
their query strings, but there is no limit to using them in application
code - what if they were used with tainted data? This is pretty self
explanatory.

### Place each class mapping in its own file

Don't use a single monolithic mapping document. Map com.eg.Foo in the
file com/eg/Foo.hbm.xml. This makes particularly good sense in a team
environment. Nothing more than a app dev good practice.

### Use bind variables

As in JDBC, always replace non-constant values by "?". Never use string
manipulation to bind a nonconstant value in a query\! Even better,
consider using named parameters in queries.

### Load mappings as resources

Deploy the mappings along with the classes they map.

### Passwords in the hibernate.cfg.xml in plain text

Sensitive information such as passwords should be encrypted to prevent
attacks like connecting directly to the database, you can extend
Hibernate functionality to implement password encryption.

-----

## Detailed

### Transaction Timeout

  - Transaction timeouts ensure that no misbehaving transaction can
    indefinitely tie up resources while returning no response to the
    user.
  - Outside a managed (JTA) environment, Hibernate cannot fully provide
    this functionality. However, Hibernate can at least control data
    access operations, ensuring that database level deadlocks and
    queries with huge result sets are limited by a defined timeout.
  - In a managed environment, Hibernate can delegate transaction timeout
    to JTA.

<!-- end list -->

    Session sess = factory.openSession();
    try {
         //set transaction timeout to 3 seconds
         sess.getTransaction().setTimeout(3);
         sess.getTransaction().begin();
         // do some work
              ...
         sess.getTransaction().commit()
    }
    catch (RuntimeException e) {
         sess.getTransaction().rollback();
         throw e; // or display error message
    }
    finally {
         sess.close();
    }

### Identify natural keys

  - Even though we recommend the use of surrogate keys as primary keys,
    you should still try to identify natural keys for all entities.
  - A natural key is a property or combination of properties that is
    unique and non-null. If it is also immutable, even better.
  - Map the properties of the natural key inside the <natural-id>
    element. Hibernate will generate the necessary unique key and
    nullability constraints, and your mapping will be more
    selfdocumenting.
  - We strongly recommend that you implement equals() and hashCode() to
    compare the natural key properties of the entity.
  - This mapping is not intended for use with entities with natural
    primary keys.

Example in hbm.xml:

```
 <natural-id mutable="true|false"/>
     <property ... />
     <many-to-one ... />
     ......
 </natural-id>
```

### Parameter Binding

Hibernate parameter binding works like prepared statements. An edge case
it is, but say you had an already tainted string, and then used Query
setters to bind more parameters to the "?" placeholders.

Example of proper use:

```
     Query q = sess.createQuery("from DomesticCat cat where cat.name = ?");
     q.setString(0, "Izi");
     Iterator cats = q.iterate();
```

Improper use:

```
     Insert insert = new Insert(dialect);
     insert.setComment(taint);
     insert.addSelectColumn(columnName, alias);
     String sql = insert.toQueryString();
           ....
     Query query = sess.createQuery(sql); /*B00*///creating a Query with an already tainted string
     query.setString(position, val); //this doesn't cleanse the damage that's been done.
           ....
     transaction.commit(); //sink the ship
```

### Declare identifier properties on persistent classes

Hibernate makes identifier properties optional. There are all sorts of
reasons why you should use them. Mapped classes must declare the primary
key column of the database table. Most classes will also have a
Java-Beans-style property holding the unique identifier of an instance.
This is the easiest and most recommended route.

### Don't use session.find()

This pretty much looks like a duplicate of sql injection but using the
deprecated method find() instead. This rule was pulled straight from the
best practice list from the reference manual.

If using Hibernate, do not use the depreciated session.find() method
without using one of the query binding overloads. Using session.find()
with direct user input allows the user input to be passed directly to
the underlying SQL engine and will result in SQL injections on all
supported RDBMS.

```

  Payment payment = (Payment) session.
       find("from com.example.Payment as payment where payment.id = " + paymentIds.get(i));
```

The above Hibernate HQL will allow SQL injection from paymentIds, which
are obtained from the user. A safer way to express this is:

```

  int pId = paymentIds.get(i);

  TsPayment payment = (TsPayment) session.
       find("from com.example.Payment as payment where payment.id = ?", pId, StringType);
```

### Cache Management and \!OutOfMemoryException

  - The Session caches every object that is in persistent state (watched
    and checked for dirty state by Hibernate).
  - Whenever you pass an object to save(), update() or saveOrUpdate()
    and whenever you retrieve an object using load(), get(), list(),
    iterate() or scroll(), that object is added to the internal cache of
    the Session.
  - When flush() or commit() is subsequently called, the state of that
    object will be synchronized with the database.
  - Otherwise it grows endlessly until you get an OutOfMemoryException,
    if you keep it open for a long time or simply load too much data.
  - One solution for this is to call clear() and evict() to manage the
    Session cache, but you most likely should consider a Stored
    Procedure if you need mass data operations.
  - Some solutions are shown in Chapter 13, Batch processing. Keeping a
    Session open for the duration of a user session also means a high
    probability of stale data.

In this example, it would fall over with an OutOfMemoryException
somewhere around the 50 000th row. That's because Hibernate caches all
the newly inserted Customer instances in the session-level cache.

```
     Session session = sessionFactory.openSession();
     Transaction tx = session.beginTransaction();
     for ( int i=0; i<100000; i++ ) {
     Customer customer = new Customer(.....);
     session.save(customer);
     }
     tx.commit();
     session.close();
```

When making new objects persistent, you must flush() and then clear()
the session regularly, to control the

```
     size of the first-level cache.
     Session session = sessionFactory.openSession();
     Transaction tx = session.beginTransaction();
     for ( int i=0; i<100000; i++ ) {
          Customer customer = new Customer(.....);
          session.save(customer);
          if ( i % 20 == 0 ) { //20, same as the JDBC batch size
               //flush a batch of inserts and release memory:
               session.flush();
               session.clear();
          }
     }
     tx.commit();
     session.close();
```

### About StatelessSession

  - A StatelessSession has no persistence context associated with it and
    does not provide many of the higher-level life cycle semantics. In
    particular, a stateless session does not implement a first-level
    cache nor interact with any second-level or query cache.
  - This may be used as a solution for the cache out of memory problem.
  - Operations performed using a stateless session do not ever cascade
    to associated instances. Collections are ignored by a stateless
    session.
  - The insert(), update() and delete() operations defined by the
    StatelessSession interface are considered

to be direct database row-level operations, which result in immediate
execution of a SQL INSERT, UPDATE or DELETE respectively.

Example of proper use:

```
     StatelessSession session = sessionFactory.openStatelessSession();
     Transaction tx = session.beginTransaction();

     ScrollableResults customers = session.getNamedQuery("GetCustomers")
          .scroll(ScrollMode.FORWARD_ONLY);
     while ( customers.next() ) {
          Customer customer = (Customer) customers.get(0);
          customer.updateStuff(...);
          session.update(customer);
     }
     tx.commit();
     session.close();
```

### Aboot POJOs

  - You can tell what objects are the persistent ones by looking at the
    xxx.hbm.xml files.
  - Persistent objects are usually POJO's with a default no-arg
    constructor so that Hibernate can instantiate them using
    Constructor.newInstance().
  - It is recommended that these POJO's have a property that is
    explicitly mapped as a primary key.

<!-- end list -->

    <hibernate-mapping>
       <class entity-name="Customer">
          <id name="id"
             type="long"
             column="ID">
             <generator class="sequence"/>
          </id>
             ......

  - Accessors and mutators should be declared for persistent fields - it
    is optional but is good practice because Hibernate persists
    JavaBeans style properties.

### Session and Concurrency issues

  - A Session is not thread-safe.
  - Things which are supposed to work concurrently, like HTTP requests,
    session beans, or Swing workers, will cause race conditions if a
    Session instance would be shared.
  - If you keep your Hibernate Session in your HttpSession, you should
    consider synchronizing access to your Http session.
  - Otherwise, a user that clicks reload fast enough may use the same
    Session in two concurrently running threads.

### The equals() and hashCode() problem:

  - Most Java objects provide a built-in equals() and hashCode() based
    on the object's identity; so each new() object will be different
    from all others.
  - If all your objects are in memory, this is a fine model, but
    Hibernate's whole job, of course, is to move your objects out of
    memory.
  - Hibernate uses the Hibernate session to manage this uniqueness. When
    you create an object with new(), and then save it into a session,
    Hibernate now knows that whenever you query for an object and find
    that particular object, Hibernate should return you that instance of
    the object.
  - However, once you close the Hibernate session, all bets are off. If
    you keep holding onto an object that you either created or loaded in
    a Hibernate session that you have now closed, Hibernate has no way
    to know about those objects.
  - So if you open another session and query for "the same" object,
    Hibernate will return you a new instance. Hence, if you keep
    collections of objects around between sessions, you will start to
    experience odd behavior (duplicate objects in collections, mainly).
  - **Long story short equals() and hashCode() should be implemented to
    compare object properties and not just compare on the basis of
    identifier (the property mapped as the primary key see the above
    example). The problem is discussed in detail
    [here](http://www.hibernate.org/109.html).**

<!-- end list -->

    public class Cat {
    ...
     public boolean equals(Object other) {
       if (this == other) return true;
       if ( !(other instanceof Cat) ) return false;
       final Cat cat = (Cat) other;
       if ( !cat.getLitterId().equals( getLitterId() ) ) return false;
       if ( !cat.getMother().equals( getMother() ) ) return false;
       return true;
     }
     public int hashCode() {
       int result;
       result = getMother().hashCode();
       result = 29 * result + getLitterId();
       return result;
     }
    }

### Using Detached Objects

  - In a three tiered architecture, consider using detached objects.
  - When using a servlet / session bean architecture, you could pass
    persistent objects loaded in the session

bean to and from the servlet / JSP layer.

  - Use a new session to service each request.
  - Use Session.merge() or Session.saveOrUpdate() to synchronize objects
    with the database.

Usually update() or saveOrUpdate() are used in the following scenario:

  - the application loads an object in the first session
  - the object is passed up to the UI tier
  - some modifications are made to the object
  - the object is passed back down to the business logic tier
  - the application persists these modifications by calling update() in
    a second session

<!-- end list -->

    // in the first session
    Cat cat = (Cat) firstSession.load(Cat.class, catID);
    // in a higher tier of the application
    Cat mate = new Cat();
    cat.setMate(mate);
    // later, in a new session
    secondSession.saveOrUpdate(cat); // update existing state (cat has a non-null id)
    secondSession.saveOrUpdate(mate); // save the new instance (mate has a null id)

### Consider externalising query strings

This is a good practice if your queries call non-ANSI-standard SQL
functions. Externalising the query strings to mapping files will make
the application more portable. It also decreases the likelihood of
injection because the Query objects let you set individual parameters
but not the entire query string - you can only do that when you pass the
string into the Query implementation constructor or call
Session.createQuery.

#### Edge cases are still possibilities\!

  - Basically the application would have to be messy enough to be
    binding parameters here, and concatenating variables there to the
    same query string.
  - You can extract the query string using Query.getQueryString(), and
    although you can't manipulate the string and 'add' it back to the
    Query object, you could theoretically taint it and use it in another
    instance of Query. Dumb? yes. Possible? Yes.

#### So how to externalize?

You may define named queries in the mapping document.

```
  <query name="ByNameAndMaximumWeight"><![CDATA[
     from eg.DomesticCat as cat
     where cat.name = ?
     and cat.weight > ?
     ] ]></query>
```

Parameter binding and executing is done programatically:

```
     Query q = sess.getNamedQuery("ByNameAndMaximumWeight");
     q.setString(0, name);
     q.setInt(1, minWeight);
     List cats = q.list();
```

  - Note that the actual program code is independent of the query
    language that is used, you may also define native

SQL queries in metadata, or migrate existing queries to Hibernate by
placing them in mapping files.

  - Also note that a query declaration inside a <hibernate-mapping>
    element requires a global unique name for the

query, while a query declaration inside a <class> element is made unique
automatically by prepending the fully qualified name of the class, for
example eg.Cat.ByNameAndMaximumWeight.

[Category:Hibernate](Category:Hibernate "wikilink")
[Category:Java](Category:Java "wikilink")