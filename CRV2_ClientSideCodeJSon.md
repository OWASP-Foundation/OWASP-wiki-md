JSON or JavaScript Object Notation is an open standard format that uses
easy to read text to transmit data between a server and web
applications. JSON data can be used by a large number of programming
Languages and is becoming the de-facto standard in replacing XML.

JSON main security concern is JSON text dynamically embedded in
JavaScript. This creates vulnerability in the program that may
inadvertently to run a malicious script or store the malicious script to
a database. This is a very real possibility when dealing with data
retrieved from the Internet.

The code reviewer needs to make sure the JSON is not used with
Javascript eval. Make sure JSON.parse(…) is used.

`Var parsed_object = eval(“(“ + Jason_text  + “)”);  // Red flag for the code reviewer.`
`JSON.parse(text[, reviver]); .. // Much better then using javascript eval function.`

Code reviewer should check to make sure the developer is not attempting
to reject known bad patterns in text/string data, Using regex or other
devices is fraught with error and makes testing for correctness very
hard. Allow only whitelisted alphanumeric keywords and carefully
validated numbers.

Do not allow JSON data to construct dynamic HTML. Always us safe DOM
features like innerText or CreateTextNode(…)