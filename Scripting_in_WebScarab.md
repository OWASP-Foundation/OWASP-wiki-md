## Overview

WebScarab has built-in support for scripting. This is intended to allow
the advanced user to perform custom processing within WebScarab. This
scripting support is used/available in several places:

  - Proxy -\> BeanShell plugin
  - Tools -\> Script Manager
  - The Scripted plugin
  - The Search plugin

I will explain each of these in more detail below.

## How is the scripting implemented?

The Scripting functionality is implemented in two different ways,
depending on where it is being used.

In the Proxy -\> BeanShell plugin, and the Search plugin use the
BeanShell interpreter directly embedded into the plugin. The Script
Manager and the Scripted plugin make use of the Apache Bean Scripting
Framework. In theory, you should be able to make use of any language
supported by BSF in these two places, assuming you adjust the classpath
to appropriately include the right scripting jars.

## So, what can I do with it?

Well, you should take a look at the hooks that exist in the Script
Manager for a full list, but the major things are modifying proxied
conversations (Proxy -\> BeanShell or Script Manager -\> Intercept
{Request |Response} ) , or submitting your own requests using the
Scripted plugin.

### Modifying conversations using Proxy-\>BeanShell

This is the standard script that is installed by default in the
Proxy-\>BeanShell plugin.

`import org.owasp.webscarab.model.Request;`
`import org.owasp.webscarab.model.Response;`
`import org.owasp.webscarab.httpclient.HTTPClient;`
`import java.io.IOException;`

`public Response fetchResponse(HTTPClient nextPlugin, Request request) throws IOException {`
`   response = nextPlugin.fetchResponse(request);`
`   return response;`
`}`

As you can see, you can make use of any arbitrary Java classes (just
import them).

The default script obviously does nothing. Of course, you can easily
change that\! Simply make use of the methods defined for the Request and
Response objects (you'll have to [use the
source](http://dawes.za.net/gitweb.cgi), or else see [the online
docs](http://dawes.za.net/rogan/webscarab/docs/appendix.html)).

For example, you might want to change a GET to a POST. This untested
script sketches out how you might approach this:

`import org.owasp.webscarab.model.Request;`
`import org.owasp.webscarab.model.Response;`
`import org.owasp.webscarab.httpclient.HTTPClient;`
`import org.owasp.webscarab.model.HttpUrl;`
`import java.io.IOException;`

`public Response fetchResponse(HTTPClient nextPlugin, Request request) throws IOException {`
`   // check if we have parameters`
`   String query = request.getURL().getQuery();`
`   if (query != null) {`

`      // Construct a new HttpUrl object, since they are immutable`
`      // This is a bit of a cheat!`
`      String url = request.getURL().toString();`
`      url = url.substring(0,url.indexOf('?'));`
`      request.setURL(new HttpUrl(url));`

`      // now put the original query in the body`
`      // we need to update a couple of headers, too`
`      request.setMethod("POST");`
`      request.setHeader("Content-Type", "application/x-www-form-urlencoded");`
`      request.setHeader("Content-Length", "0");`
`      // the setContent method automatically updates the Content-Length header IF it exists`
`      request.setContent(query.getBytes());`
`   }`
`   response = nextPlugin.fetchResponse(request);`
`   return response;`
`}`

As you can see, you can do quite a lot in only a few lines of code.

### Modifying conversations using the Script Manager

The Script Manager interface is somewhat different to the Proxy -\>
BeanShell one. In the first place, intercepting a conversation is split
into two parts, intercepting the request, and intercepting the response.

The interface does give some rudimentary instruction. For example,
"Intercept Request" says "Called when a new request has been submitted
by the browser. Use connection.getRequest() and
connection.setRequest(request) to perform changes".

Here is the above script rewritten for the Script Manager interface:

`import org.owasp.webscarab.model.Request;`
`import org.owasp.webscarab.model.Response;`
`import org.owasp.webscarab.httpclient.HTTPClient;`
`import java.io.IOException;`

` // NB: This is only a COPY! See below`
` Request request = connection.getRequest();`

` // check if we have parameters`
` String query = request.getURL().getQuery();`
` if (query != null) {`
` `
`    // Construct a new HttpUrl object, since they are immutable`
`    // This is a bit of a cheat!`
`    String url = request.getURL().toString();`
`    url = url.substring(0,url.indexof('?'));`
`    request.setURL(new HttpUrl(url));`

`    // now put the original query in the body`
`    // we need to update a couple of headers, too`
`    request.setHeader("Content-Type", "application/x-www-form-urlencoded");`
`    request.setHeader("Content-Length", "0");`
`    // the setContent method automatically updates the Content-Length header IF it exists`
`    request.setContent(query.getBytes());`
`    `
`    // You have to use connection.setRequest() to make any changes take effect!`
`    connection.setRequest(request);`
` }`
` `

The important changes to note are the use of the "connection" object,
and the fact that the request object that you get is only a copy of the
real request. You HAVE to call connection.setRequest() to make your
changes effective.

## Ok, so what's this Scripted plugin good for, then?

The Scripted plugin is great for executing a series of requests, that
can be calculated. For example, brute forcing a login page using a
dictionary of usernames and passwords. Enumerating a site's users based
on differeng responses to existing or non-existing accounts. Finding an
existing session on a site that uses weak session identifiers. Fuzzing a
form. Essentially, the list is limited by your own imagination.

So why use this rather than bash and netcat?

Well, the Scripted plugin provides a nice OO interface to creating
requests and analysing responses, which you don't get in bash. But
probably the most compelling reasons are:

  - It is multi-threaded (currently 4 simultaneous threads, but that
    could be changed fairly easily). That is something that is not easy
    to do in shell, or even in Perl (e.g. with libwhisker)
  - You can archive interesting responses for later review. Simply call
    "scripted.addConversation(response)" to add it to the Summary.

The approach to using the Scripted plugin is quite simple. Use the
default script as a template, and modify it to suit. This default script
provides subroutines to fetch responses one at a time, or in parallel.
The easiest way to do it is to create a template request, possibly based
on a request from the summary (e.g. request = scripted.getRequest(17)
will return a copy of request \#17). Then modify the template to suit.

Then modify

`boolean hasMoreRequests()`

to return false when there are no more requests to fetch, and

`Request getNextRequest()`

to return the next request to be sent.

Finally, modify fetchSequentially() or fetchParallel() so you can
analyse the responses you get back. Yes, this should probably also be
put into a method, e.g. analyseResponse(Response response). I'll
consider that for a later version.

And you are done. Hit Start to execute your script, and watch it run.

There are a couple of examples in the scripts directory if you used the
-installer version, which might give you some ideas.

Here is a sample script that has been cleaned up a bit. Most notably
printRequest and printResponse methods have been added so you can easily
access all of the data without much additional coding. There are also
spots to print the time in long format. This is good if you are
performing some sort of timing attack or analysis. Just replace the code
in the scripted section with this code and then edit the information at
the bottom of the code. Feel free to email me with questions or comments
about this template: --[MichaelCoates](User:MichaelCoates "wikilink")
15:12, 2 July 2008 (EDT)

`import org.owasp.webscarab.model.HttpUrl;`
`import org.owasp.webscarab.model.Request;`
`import org.owasp.webscarab.model.Response;`

`// define subroutines BEFORE the main part of the script executes,`
`// otherwise they won't be found`

`void printRequest(Request request){`
`out.println("====`<REQUEST>`====");`
`out.println(request.getMethod());`
`out.println(request.getURL());`
`out.println(request.getVersion());`
`String[] headers=request.getHeaderNames();`
`for(String header : headers){`
`out.println(header+" : " + request.getHeader(header));`
`}`
`out.println("====`</REQUEST>`====");`
`}`

`void printResponse(Response response){`
`out.println("====`<RESPONSE>`====");`
`out.println(response.getStatus());`
`out.println(response.getMessage());`
`//print the headers`
`String[] headers=response.getHeaderNames();`
`for(String header : headers){`
`out.println(header+" : " + response.getHeader(header));`
`}`
`out.println("");`
`//print the content`
`byte[] data=response.getContent();`
`String data_response=new String(data);`
`out.println(data_response);`

`out.println("====`</RESPONSE>`====");`
`}`
`// call this to fetch the requests one after another`
`void fetchSequential() {`
`out.println("===================================");`
`while (hasMoreRequests()) {`
`request = getNextRequest();`
`printRequest(request);`
`response = scripted.fetchResponse(request);`
`printResponse(response);`

`//Print the time`
`Date now = new Date();`
`long nowLong = now.getTime();`
`out.println("Current Time " + nowLong);`
`out.println("");`
`}`
`//Print the time now that we're done`
`Date now = new Date();`
`long nowLong = now.getTime();`
`out.println("Done - Current Time " + nowLong);`
`out.println("");`
`out.println("");`
`}`

`// call this to fetch them in parallel`
`// the number of simultaneous connections is controlled by the Scripting plugin `
`// It is currently fixed at 4 simultaneous requests`
`void fetchParallel() {`
`while (hasMoreRequests() `

| | scripted.isAsyncBusy()) {

`while (scripted.hasAsyncCapacity() && hasMoreRequests()) {`
`request = getNextRequest();`
`scripted.submitAsyncRequest(request);`
`printRequest(request);`
`}`

`if (scripted.hasAsyncResponse()) {`
`while (scripted.hasAsyncResponse()) {`
`response = scripted.getAsyncResponse();`
`request = response.getRequest();    `
`  `
`}`
`} else Thread.sleep(100);`
`}`
`}`

`// a counter, so we can know when to stop`
`int i=0;`
`int TotalRequests;`
`boolean hasMoreRequests() {`
`return i<TotalRequests;`
`}`

`/******************************************************************************`
`***************** USER EDITABLE SCRIPT STARTS HERE ***************************`
`*                                                                            *`
`* Of course, you can modify the bits above, but you shouldn't need           *`
`* to, if you follow the algorithm suggested below.                           *`
`*                                                                            *`
`******************************************************************************/`
`//====Set the number below equal to the total number of requests====`
`TotalRequests=3;`

`// modify this routine to construct the next request - no changes needed`
`Request getNextRequest() {`
`// create a new request copied from the template`
`Request request = new Request(template);`
`i++;  //need to increment the counter`
`return request;`
`}`

`//====Edit this section====`
`// create a template that contains the basics`
`Request template = new Request();`
`template.setMethod("GET");`
`template.setURL(new HttpUrl("`<http://www.google.com>`"));  `
`template.setVersion("HTTP/1.0");`
`template.setHeader("User-Agent","WebScarab");`
`template.setHeader("Host","www.google.com:80");`
`template.setHeader("Accept"," text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5");`
`template.setHeader("Accept-Language"," en-us,en;q=0.5");`
`template.setHeader("Accept-Encoding"," gzip,deflate");`
`template.setHeader("Accept-Charset"," ISO-8859-1,utf-8;q=0.7,*;q=0.7");`
`template.setHeader("Keep-Alive"," 300");`
`template.setHeader("Proxy-Connection"," keep-alive");`
`//template.setHeader("Cookie"," Some cookie values here");`

`//====Choose Sequential or Parallel Requests====`
`// Choose how to submit the requests, sequentially, or in parallel`
`fetchSequential();`
`//fetchParallel();`

## And Search? I never managed to get that to work right

Well, the Search Plugin gives a lot of flexibility in terms of
identifying conversations, based on arbitrary criteria. Basically, all
you need to do is write a script that returns true for "interesting"
conversations, and false for others.

Normally you will use a simple expression such as:

`request.getMethod().equals("POST")`

to show only POSTs.

However, you can actually create arbitrarily complex scripts.

`String method = request.getMethod();`
`return "POST".equals(method);`

Or even import classes, etc.

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink")