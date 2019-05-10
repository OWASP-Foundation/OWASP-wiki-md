## Introduction

If you have read the OWASP Top Ten Vulnerabilities list or keep an eye
on application vulnerabilities at BugTraq, you are aware that many
security problems begin with input validation issues. When input
validation is performed, many applications implement input checking on
the client side through JavaScript and HTML form elements. Client side
checks can make for a more usable interface and can cut down on trips to
the server to check for missing or malformed input.

There are two basic security problems with client side validation
checks. The first is that while they do appear to restrict user input,
they actually offer no security benefit at all. All client side checks
can be easily bypassed by an attacker. The second issue is that client
side checks make it difficult to ensure that server side checks are in
place and are implemented correctly. Most testers will be able to
exercise the client side checks, but without "hacking" the application,
the server side checks may not be tested.

In this article, we are going to look at how to keep client and server
side validation checks in sync, so that the benefits of the client side
validation can be realized without the security side effects that are
normally present.

## When your client and server part ways

Tanya drank about half of her bottle of Mountain Dew, ate another
pretzel, and focused her attention back on the report she had been
reading. It was mid-afternoon, and while the report was actually quite
interesting, it was time for some caffeine and snacks. Tanya ate another
pretzel and began reading again.

The report had been produced by an application security specialist that
had been hired by the company to review one of their ASP applications.
It was this application that Tanya was working on. Her team was
re-writing the application in .NET, adding various enhancements, and as
her manager had indicated in the meeting this morning, "make sure we
don't get a report like this again".

The area that Tanya was responsible for dealing with involved the use of
client side validation checks. The security specialist had shown them
how the "security" checks that had been placed in the ASP application
had been easily circumvented and allowed the application to be
exploited. He had listed the client side checks that had been used by
the ASP team. Tanya ate another pretzel and began to take some notes on
her whiteboard. Soon she had consolidated the list to be those client
side checks that the team had expected to put in the new system.

<center>

![Jpoteet_story2-a.jpg](Jpoteet_story2-a.jpg "Jpoteet_story2-a.jpg")

</center>

Tanya looked at each of the groups she created and began to think about
how each one should be dealt with.

:\*HTML

  -
    This category included items that were implemented in HTML rather
    than in a scripting language. Some were subtle such as the use of
    the readonly or maxlength attributes. Often applications rely on
    attributes such as these to enforce business rules such as the
    length of fields. Other items included form fields that seem to
    enforce particular restrictions on user input due to their
    interface.

:\* Design

  -
    This category included validation rules that were embedded in the
    design of the application. For example, this included items such as
    only displaying links to pages that the user was allowed to access
    or filtering the data to only return data the user should be able to
    access.

:\* Javascript

  -
    This included various validation checks that were implemented in
    JavaScript in the user's browser. This included checking for
    required fields, making sure certain duplicate fields matched, and
    checking the format and allowed characters in input fields. This is
    where the bulk of the client validation was being performed in the
    application.

In the original ASP application, validation through the use of HTML
elements was very common. The security assessment had clearly shown how
attributes could be removed, hidden form fields could be modified and
drop down lists could be altered to allow new entries. Tanya realized
that many of these items tended to fall through the cracks since the
developers tended not to think of this as validation code because they
didn't actually write any code to produce the checks.

Design issues that involved trusting the client had been exposed in the
assessment as well. Many of these had been authorization issues such as
removing links that a user did not have access to, but failing to check
if the user was authorized if the URL was entered directly. Other
examples included items such as lists that only displayed the records
that the user was authorized to view, but the details page could be used
to pull up any record. Again the client was being trusted to provide the
correct data.

While all of the issues needed dealt with, Tanya decided to focus on the
JavaScript issue first. The amount of scripting validation was fairly
extensive. On the registration page alone, this included the following
checks.

:\* Make sure the first name was populated

:\* Only allow letters, -, ' and spaces in the first name

:\* Make sure the last name was populated

:\* Only allow letters, -, ' and spaces in the last name

:\* Make sure the middle initial was populated

:\* Only allow uppercase letters in middle initial

:\* Make sure the address was populated

:\* Make sure the city was populated

:\* Make sure the state was populated

:\* Make sure the zip code was populated

:\* Only allow numbers and - in the zip code

:\* Make sure zip code is \#\#\#\#\# or \#\#\#\#\#-\#\#\#\#

:\* Make sure the phone number was populated

:\* Only allow numbers and - in the phone number

:\* Make sure phone number is \#\#\#-\#\#\#\#-\#\#\#\#\#

:\* Make sure the email address was populated

:\* Make sure the email address contains an @

:\* Make sure the verify email address was populated

:\* Make sure the verify email address contains an @

:\* Make sure the email address and verify email address are a match

:\* Make sure the user name was populated

:\* Only allow letters and numbers in the user name

:\* Make sure the password was populated

:\* Make sure the verify password was populated

:\* Make sure the password does not match the user name

:\* Make sure the password and verify password are a match

:\* Make sure the customer id was populated

:\* Make sure the customer id only contains numbers and -

:\* Make sure customer id is \#\#-\#\#\#\#\#-\#\#\#-\#\#\#\#

These checks did help users input the data in a correct format. However,
as the assessment had shown, they added no value in terms of security.
Tanya knew she needed to implement these same checks on the server to
enforce the security of the validation checks. Tanya finished off her
Mountain Dew and headed down the hall for another one. Trying to keep
the client and server validation in sync could be a big task and this
was going to take some serious caffeine.

## A Match Made in Heaven (or Redmond)

Lucky for Tanya, there is a mechanism in .NET that can deal with many of
the issues she is facing. .NET offers a new programming model over what
was available in ASP development. Rather than always dealing directly
with HTML, this new model introduces an object model that allows for
some new ways of dealing with web development.

This new model is known as Web Forms. Web Forms is more similar to
developing in Visual Basic, Delphi or Visual C++ than typical web
development. Objects are instantiated that represent HTML elements and
can be referenced programmatically in the server code. One of the big
advantages to Web Forms is a cleaner separation between business logic
and presentation code.

Within the Web Forms model are a set of Validation Controls. These make
up the mechanisms we can use to produce robust validation that will
remain synced up between the client and server. The checks will be
performed on the server side for security purposes, but when a modern
browser such as Internet Explorer is used, the code will generate client
side checks as well.

:\* RequiredFieldValidator

::This validator is used to ensure that the specified control has been
populated

:\* RangeValidator

::Makes sure that the specified control falls with a range of values

:\* RegularExpressionValidator

::Makes sure the specified control is formatted properly

:\* CompareValidator

::Compares the specified control against a particular value or even
another control

:\* CustomValidator

  -

      -
        Used to hook in a custom validation routine

These validation controls can be used to cleanly validate the user input
and provide both client and server checks from the same source. The
validation checks for Tanya's registration page might look something
like this:

<center>

![Image:JpoteetHYC1.gif](JpoteetHYC1.gif "Image:JpoteetHYC1.gif")

</center>

## Conclusion

Using the Validation Controls that are part of Web Forms has a variety
of advantages. The controls provide a readable, robust mechanism for
validating user input. Also, by using the Validation Controls, the
problem of keeping the client and server checks in sync can be largely
mitigated. Web Forms should be a model that all ASP.NET programmers are
evaluating. The benefits of Validation Controls should be one of the
items that helps convince them to switch.

## For More Information

:\*[Validation Server
Controls](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpgenref/html/cpconASPNETSyntaxForValidationControls.asp)

:\*[Form Validation](http://builder.com.com/5100-6373-1044889.html)

-----

[Jeremy Poteet](mailto:jpoteet@appdefense.com?subject=feedback) is one
of the leaders for the OWASP Guide and an active member of the OWASP
Testing Methodology Project. He also acts as the liaison officer for the
WAS-TC at OASIS and is a member of the AVDL TC. He is the Chief Security
Officer for [appDefense](http://www.appdefense.com/) and a CISSP. Jeremy
is the co-author of "Extreme Programming with Ant" and was the winner of
eWeek's OpenHack IV competition.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:OWASP Validation
Project](Category:OWASP_Validation_Project "wikilink")