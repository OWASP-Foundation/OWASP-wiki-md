## Brief Summary

In this test we check whether it is possible to force the application to
loop through a code segment that needs high computing resources, in
order to decrease its overall performance.

## Description of the Issue

Like the problem of [User Specified Object
Allocation](Testing_for_DoS_User_Specified_Object_Allocation_\(OWASP-DS-004\) "wikilink"),
if the user can directly or indirectly assign a value that will be used
as a counter in a loop function, this can cause performance problems on
the server.

The following is an example of vulnerable code in Java:

    public class MyServlet extends ActionServlet {
       public void doPost(HttpServletRequest request, HttpServletResponse response)
               throws ServletException, IOException {
        . . .
        String [] values = request.getParameterValues("CheckboxField");
          // Process the data without length check for reasonable range – wrong!
        for ( int i=0; i<values.length; i++) {
            // lots of logic to process the request
        }
        . . .

       }
       . . .
    }

As we can see in this simple example, the user has control over the loop
counter. If the code inside the loop is very demanding in terms of
resources, and an attacker forces it to be executed a very high number
of times, this might decrease the performance of the server in handling
other requests, causing a DoS condition.

## Black Box Testing and Examples

If a request is sent to the server with a number that will, for example,
be used to read many similar name/value pairs (for example, sending “3”
to read input1, input2 and input3 name/value pairs), and if the server
does not enforce a hard upper limit to this number, this can cause the
application to loop for an extremely long time. The tester in this
example may send an extremely large, yet well-formed number to the
server, such as 99999999.

Another problem is if a malicious user sends an extremely large number
of name/value pairs directly to the server. While the application cannot
directly prevent the application server from handling the initial
parsing of all the name/value pairs, to prevent a DoS, the application
should not loop over everything that has been submitted without putting
a limit on the number of name/value pairs to be handled. For example,
multiple name/value pairs can be submitted by the tester, each with the
same name, but with different values (simulating submission of checkbox
fields). So, retrieving the value of that particular name/value pair
will return an array of all the values submitted by the browser.

If it is suspected that such an error may have been made in the
application, the tester can submit an increasingly large number of
repeating name/value pairs in the request body with a small script. If
there is a noticeable difference in response times between submitting 10
repetitions and submitting 1000 repetitions, it may indicate a problem
of this type.

In general, be sure to check the hidden values that are passed to the
application, as they also could play a role in the number of executions
of some code segments.

## Gray Box Testing and Examples

Knowing some details about the internals of the application might help
the tester in locating input values that force the server to heavily
loop through the same code. The testing techniques, however, follow the
same pattern of the black box testing.

[category:Denial of Service
Attack](category:Denial_of_Service_Attack "wikilink")