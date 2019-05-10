# .NET Anti-Pattern: Mishandled Concurrency

The correct concurrency management techniques is absolutely necessary in
order to guarantee data integrity. A way to implement proper concurrency
consists in creating a concurrency token which will be checked from the
moment the entity object in the database was read until the moment when
the submission will be executed. Prior to commit the final changes, the
application must execute control where the concurrency token will be
compared. If the token differs, conclusions can be drawn that indeed the
data has been changed by another user.

The Entity Framework supports optimistic concurrency, unfortunately
exceptions derived from errors encountered between the updates are not
automatically handled, neither this will protect your data from
corrupting.

## Fetching Strategy issues

Main purpose of the ORM (Object Relational Mapper) is to create an
abstraction, a representation of the database easier to manipulate and
access data contained in it than retrieving it using SQL statements.
Unfortunately, many developers assume that because the ORM is the middle
layer handling the communication and manipulation of records, the data
persistence will be handled without issues. The developer should analyze
and observe what occurs at the database level once the ORM in question
(such as EntityFramework, NHibernate or Ideablade for example) has been
implemented. Concurrency issues can arise from incorrect fetching
strategy implementations such as for example using ‘CachedOnly’ or
‘DataSourceThenCached’(IdeaBlade). It is highly recommended that the
developer revises the proper application depending on the implementation
scenario, such as multiple users accessing the same data at the same
time in order to avoid data corruption or when data is cached in an
action by a certain Entity but the another one is not aware of this
change.

## Avoid the DTO pattern

Known to many NHibernate developers, the use of DTO pattern seems as
something that sounds good but could be highly inconvenient. Main
reasons for not implementing are: Contrary to their name, DTO's are no
objects but a state which is defined through their behavior. By
replicating multiple objects, a developer might end up having to
implement multiple changes in the domain model and the DTO classes when
for example, introducing a new property in the domain model class.

## Avoid Locks

Another anti-pattern approach used by many developers is to lock regions
in the database.Most of the time , this is implemented as way to avoid
concurrency, however web applications are not properly suited for using
locking which will indeed freeze the application. Locking data for the
time the request takes place will not solve this problem. Using locks in
database are absolutely not recommend since they required careful
implementation planning and design.(Freeman, pg 179 ,2011)

## Race conditions

If the following is run on more than one thread, it will randomly crash.
It is not possible to know deterministically whether the code will throw
an ArgumentOutOfRangeException. Sometimes it will, sometimes it
won’t.(Mclean, 2010)

`IList`<string>` list = new List`<string>`(); `
`list.Add("Hello"); `
`… `
`// multi-threaded code `
`if(list.Count > 0) `
`{ `
`   list.RemoveAt(0); `
`} `

In that case a locking can be used, however using locks as mentioned
earlier should be consider as an option if it is absolutely necessary.

Example locking code

`object lockObj = new object(); `
`IList`<string>` list = new List`<string>`(); `
`list.Add("Hello"); `
`… `
` // multi-threaded code `
` lock(lockObj) `
` { `
`   if(list.Count > 0) `
`   { `
`       list.RemoveAt(0); `
`   } `
`  } `

## Recommendations

  - The best option in this case is to alert the user who initiated the
    second request that his changes cannot be applied. "This is largely
    because, by definition, the first request will already have

completed".(Freeman,pg 179,2011)

  - A recommended pattern when using the Entity Framework consists in
    "making a copy of the entity on the client and send back both the
    original version unmodified and the modified version or to write the
    client in such a way that it does not modify the concurrency
    token".(Simmons, 2009)

<!-- end list -->

  - Keep in mind that Detached objects (such as in the case of
    NHibernate or IdeaBlade ORM's)may no longer be guaranteed to be
    synchronized with database state; they’re no longer under the
    management of NHibernate.However they could still contain persistent
    data. These ORM's allow you to reuse these instance by associating
    them with a new Persistence manager.

<!-- end list -->

  - Avoid the use DTO pattern by properly handling detached objects

## References

  - Simmons, D. (2009, June ). Anti-Patterns To Avoid In N-Tier
    Applications. MSDN Magazine. Retrieved from
    <http://msdn.microsoft.com/en-us/magazine/dd882522.aspx#id0420025>

<!-- end list -->

  - Freeman, A (2011). Applied ASP .NET 4 in Context. Apress, New York,
    USA

<!-- end list -->

  - McLean, G. (2010).Pro WPF and Silverlight MVVM: Effective
    Application Development with Model-View-ViewModel. Apress, New York,
    USA