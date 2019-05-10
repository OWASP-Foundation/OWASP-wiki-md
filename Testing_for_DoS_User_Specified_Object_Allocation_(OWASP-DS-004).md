## Brief Summary

In this test, we check whether it is possible to exhaust server
resources by making it allocate a very large number of objects.

## Description of the Issue

If users can supply, directly or indirectly, a value that will specify
how many copies of an object to create on the application server, and if
the server does not enforce a hard upper limit on that value, it is
possible to cause the environment to run out of available memory. The
server may begin to allocate the number of objects specified, but if
this is an extremely large number, it can cause serious issues on the
server, possibly filling its whole available memory and corrupting its
performance.

The following is a simple example of vulnerable code in Java:

    String TotalObjects = request.getParameter(“numberofobjects”);
    int NumOfObjects = Integer.parseInt(TotalObjects);
    ComplexObject[] anArray = new ComplexObject[NumOfObjects];  // wrong!

## Black Box Testing and Examples

As a tester, look for places where numbers submitted as a name/value
pair might be used by the application code in the manner shown above.
Attempt to set the value to an extremely large numeric value, and see if
the server continues to respond. You may need to wait for some small
amount of time to pass as performance begins to degrade on the server as
it continues allocation.

In the above example, by sending a large number to the server in the
“numberofobjects” name/value pair, an attacker would cause the servlet
to attempt to create that many complex objects. While most applications
do not have a user directly entering a value that would be used for such
purposes, instances of this vulnerability may be observed using a hidden
field, or a value computed within JavaScript on the client when a form
is submitted.

If the application does not provide any numeric field that can be used
as a vector for this kind of attack, the same result might be achieved
by allocating objects in a sequential fashion. A notable example is
provided by e-commerce sites: if the application does not pose an upper
limit to the number of items that can be in any given moment inside the
user electronic cart, you can write an automated script that keeps
adding items to the user cart until the cart object fills the server
memory.

## Gray Box Testing and Examples

Knowing some details about the internals of the application might help
the tester in locating objects that can be allocated by the user in
large quantities. The testing techniques, however, follow the same
pattern of the black box testing.

[category:Denial of Service
Attack](category:Denial_of_Service_Attack "wikilink")