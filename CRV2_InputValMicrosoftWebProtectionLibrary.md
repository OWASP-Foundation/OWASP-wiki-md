### Microsoft Web Protection Library (STILL IN DRAFT)

Microsoft Web Protection Library or MWPL for short, provides a set of
Microsoft .NET assemblies that help you to protect Web applications
against Cross Site Scripting (XSS) and SQL Injection attacks. At the
heart of MVPL, there are two built-in mechanisms to protect your
applications. In one hand there is a library to protect against XSS
called AntiXSS Library and in the other hand there is Security Engine
Runtime that protects against XSS and SQL Injection attacks.

### AntiXSS Library V4.2.1

Microsoft AntiXSS Library helps you to protect against Cross Site
Scripting. This library provides encoding functions for input, including
HTML attributes, CSS and JavaScript. AntiXSS implements a whitelisting
approach, which means that any character that is not part of the white
list,is going to be encoded using rules based on the encoding type.
Namely, AntiXSS provides two interesting approaches : 1. It works as an
encoding library for the following types:

  - HTMLEncode
  - URLEncode
  - JavaScriptEncode
  - VisualBasicScriptEncode
  - XMLEncode

2\. It works as a HTML Sanitization library by :

  - Providing a white-list based sanitization
  - It sanitizes HTML pages or fragments

### How to get AntiXSS library

MWPL can be found at CodePlex <https://wpl.codeplex.com>. However, you
can get AntiXSS from NuGet <https://www.nuget.org/packages?q=AntiXSS>.
From Visual Studio and by using NuGet plug-in, you can add the library
to your application :

![<File:AntiXSSNuGet.png>](AntiXSSNuGet.png "File:AntiXSSNuGet.png")

There are some circumstances that you would like to allow some html tags
as a part of the user input, for example in a forum or a blog post, you
should provide a way that end users can enter some html tags to improve
the content.