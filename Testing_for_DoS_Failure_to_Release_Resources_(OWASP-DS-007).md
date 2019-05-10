## Brief Summary

With this test, we check that the application properly releases
resources (files and/or memory) after they have been used.

## Description of the Issue

If an error occurs in the application that prevents the release of an
in-use resource, that resource can become unavailable for further use.
Possible examples include:

  - An application locks a file for writing, but when an exception
    occurs, it does not explicitly close and unlock the file
  - Memory leaking in languages where the developer is responsible for
    memory management such as C and C++. In the case where an error
    causes the normal logic flow to be circumvented, the allocated
    memory may not be removed and may be left in such a state that the
    garbage collector does not know it should reclaim it
  - Use of DB connection objects where the objects are not being freed
    if an exception is thrown. A number of such repeated requests can
    cause the application to consume all the DB connections, as the code
    will still hold the open DB object, never releasing the resource.

The following is an example of vulnerable code in Java. In the example,
both the Connection and the CallableStatement should be closed in a
finally block.

    public class AccountDAO {
        … …
        public void createAccount(AccountInfo acct)
                     throws AcctCreationException {
           … …
        try {
           Connection conn = DAOFactory.getConnection();
           CallableStatement  calStmt = conn.prepareCall(…);
              … …
              calStmt.executeUpdate();
           calStmt.close();
              conn.close();
           }  catch (java.sql.SQLException e) {
           throw AcctCreationException (...);
           }
        }
    }

## Black Box Testing and Examples

Generally, it will be very difficult to observe these types of resource
leaks in a pure black box test. If you can find a request that you
suspect is performing a database operation, and that will cause the
server to throw an error which may not be properly handled, then you can
automate the process of sending a few hundred of these requests very
quickly. Observe any slowdown or new error messages from the application
while using it during normal, legitimate use.

## Gray Box Testing and Examples

It might be possible, in some cases, to monitor the disk space and/or
the memory usage of the target. That can happen usually when the test is
performed over a local network. Possible ways to obtain this information
include the following scenarios:

1.  The server that hosts the application allows the tester to mount its
    filesystem or some parts of it
2.  The server provides disk space and/or memory usage information via
    SNMP

In such cases, it may be possible to observe the memory or disk usage on
the server while trying to inject data into the application, with the
intent of causing an exception or error that may not be handled cleanly
by the application. Attempts to cause these types of errors should
include special characters that may not have been expected as valid data
(e.g., \!, |, and ‘).


[category:Denial of Service
Attack](category:Denial_of_Service_Attack "wikilink")