## Brief Summary

With this test, we check that it is not possible to cause a DoS
condition by filling the target disks with log data.

## Description of the Issue

The goal of this DoS attack is to cause the application logs to record
enormous volumes of data, possibly filling the local disks.

This attack could happen in two common ways:

1.  The tester submits an extremely long value to the server in the
    request, and the application logs the value directly without having
    validated that it conforms to what was expected.
2.  The application may have data validation to verify the submitted
    value being well formed and of proper length, but then still log the
    failed value (for auditing or error tracking purposes) into an
    application log.

If the application does not enforce an upper limit to the dimension of
each log entry and to the maximum logging space that can be utilized,
then it is vulnerable to this attack. This is especially true if there
is not a separate partition for the log files, as these files would
increase their size until other operations (e.g., the application
creating temporary files) become impossible. However, it may be
difficult to detect the success of this type of attack, unless the
tester can somehow access the logs (gray box) being created by the
application.

## Black Box Testing and Examples

This test is extremely difficult to perform in a black box scenario
without some luck and a large degree of patience. Determine a parameter
that is submitted from the client to the server that does not seem to
have a length check (or has one that is extremely long) and that has a
high probability of being logged by the application. Textarea fields in
the client are likely to have very long acceptable lengths; however,
they may not be logged beyond a remote database. Use a script to
automate the process of sending the same request with a large value for
the field as fast as possible, and give it some time. Does the server
eventually begin reporting errors when it tries to write to the file
system?

## Gray Box Testing and Examples

It might be possible, in some cases, to monitor the disk space of the
target. That can happen usually when the test is performed over a local
network. Possible ways to obtain this information include the following
scenarios:

1.  The server that hosts the log files allows the tester to mount its
    filesystem or some parts of it
2.  The server provides disk space information via SNMP

If such information is available, the tester should send an overly large
request to the server and observe if the data is being written to an
application log file without any limitation of the length. If there is
no restriction, it should be possible to automate a short script to send
these long requests and observe at what speed the log file grows (or the
free space shrinks) on the server. This can allow the tester to
determine just how much time and effort would be required to fill the
disk, without the need of completely executing the DoS.