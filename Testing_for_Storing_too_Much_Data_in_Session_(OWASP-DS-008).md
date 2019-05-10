## Brief Summary

In this test, we check whether it is possible to allocate big amounts of
data into a user session object in order to make the server exhaust its
memory resources.

## Description of the Issue

Care must be taken not to store too much data in a user session object.
Storing too much information in the session, such as large quantities of
data retrieved from the database, can cause denial of service issues.
This problem is exacerbated if the session is populated when serving
unauthenticated users, because, in this case, an attacker can launch the
attack without having to obtain an account.

## Black Box Testing and Examples

This is again a difficult case to test in a pure black box setting.
Likely places to look for this vulnerability are those where a large
number of records are retrieved from a database, based on data provided
by the user during their normal application use. Good candidates may
also include paging code, i.e., the functionality of viewing a large
record set a portion at a time. The developer may have chosen to cache
the records in the session instead of returning to the database for the
next block of data. If this is suspected, create a script to automate
the creation of many new sessions with the server and run the request
that is suspected of caching the data within the session for each one.
Let the script run for a while, and then observe the responsiveness of
the application for new sessions. It may be possible that a Virtual
Machine (VM) or even the server itself will begin to run out of memory
because of this attack.

## Gray Box Testing and Examples

If available, SNMP can provide information about the memory usage of a
machine. Being able to monitor the target memory usage can greatly help
when performing this test, as the tester would be able to see what
happens when the script described in the previous section is launched.

[category:Denial of Service
Attack](category:Denial_of_Service_Attack "wikilink")