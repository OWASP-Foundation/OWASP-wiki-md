  - Autor: Daniel Muñiz

## Why Internationalization

This document is intended to be a guide for OWASP tool projects
developed or to be developed in Java. As part of its always growing
effort [OWASP
Internationalization](OWASP_Internationalization "wikilink") project
pretends to provide the basic guidelines necessary to create software
ready to be translated in other languages with the unique purpose of
empowering its spread on thw world and reach as many people as possible.

## Introduction to Java Internationalization

Usually, programs are written in only one language such as English or
Spanish and the user does not have the possibility to change it. Most of
the times, the initial purpose of the program changes and it needs to be
adapted to other different languages. The process of designing or
adapting software in order to be displayed in several languages and
regions easily, cost-effectively, and in particular without engineering
changes to the software, is called **internationalization**.
Localization can be performed by simply adding locale-specific
components such as translated text, data describing locale-specific
behaviour, fonts, and input methods.

In the Java SE Platform, internationalization support is fully
integrated into the stock classes and packages that provide language- or
culture-dependent functionality. Therefore, it is important to use these
tools to make the whole process easier.

Internationalizing a program is not too difficult, but it requires some
planning and extra coding. On the other hand, the benefits are huge.

This document tries to determine the requirements to internationalize a
program.

## Objectives

  - Use the same executable file around the world.
  - Text and data displayed in the user's language.
  - Easy way to add new languages.
  - Quickly localized
  - Spanish translation

## Check List

For this specific document, the application will be used as translation
case. A checklist has been redacted with the specific needs, in order to
internationalize the application.

### Identify Culturally Dependent Data

Text messages may change depending on the language or region. First of
all, it is important to determine which type of data varies and do a
list to translate it. For instance:

  - Messages
  - Help online
  - Hours
  - Numbers

### Isolating text in Resources Bundles.

The translation process is a hard work but it is possible to do it
easier. Nowadays, status messages, error messages and file logs
displayed to end users tend to be hardcoded into programs. At this
point, it is necessary to isolate the text that must be translated into
*ResourcesBundle* objects. This object is related to a Locale that
describes the language and location of the end user. Locales are defined
in the java.util package and they have numerous constructors and access
methods such as getLanguage and getCountry which give us information
about the user's culture.

By means of these objects, we can perform a controlled translation and
reduce its costs.

### Dealing with Compound messages

If the displayed message contains variable data, like a username or
password, the difficulty to translate the text increases. Whenever
possible, we should avoid construction compound messages or modify the
sentences since they are difficult to translate as we can see in the
examples below:

  - Black Box - Caja Negra (Different Order)
  - The program has one vulnerability - The program has five
    vulnerabilities (Countable)

### Formatting date and time

Date and time formats differ with region and language, therefore, it is
important to determine how to display this information. By using the
date-formatting classes we can solve this problem.

### Using Unicode character properties

Characters in Java programming language are encoded in Unicode and
provide utils and methods to deal with Unicode characters properly.
Methods like comparison or identifying a character may help us. A list
of Character API methods is:

  -   - isDigit()
      - isLetter
      - isLetterOrDigit
      - isSpaceChar
      - getType

### Treating exception messages

The text of the exceptions must be displayed in the user's language so
we must treat and manipulate exceptions correctly.

### Comparing strings properly

When sorting text we often compare strings. If the text is displayed, we
should not use the comparison methods of the String class. Instead of
the String class we should use the Collator class because it allows the
application to perform comparisons for different languages. Besides, the
collator class increases the efficiency of string comparisons.

### Use always Unicode text

If the program uses no-Unicode text then we must translate it to Unicode
in such a way that we can work easily.

### Detecting Text Boundaries

Applications that manipulate texts need to locate boundaries within the
text. For instance, consider some of the common functions of a word
processor: highlighting a character, cutting a word, moving the cursor
to the next sentence, and wrapping a word at a line ending. To perform
each of these functions, the word processor must be able to detect the
logical boundaries in the text. We can take advantage of the methods
provided by the
*BreakIterator*[](http://java.sun.com/javase/6/docs/api/java/text/BreakIterator.html)class
to perform boundary analysis.

## Bibliography and source.

If you need more information on how to implement internationalization

Java Internationalization
([<http://java.sun.com>](http://java.sun.com/))

WebGoat ( <http://code.google.com/p/webgoat/> )

Owasp ( [www.owasp.org](http://www.owasp.org/) )

[Category:OWASP_WebGoat_Project](Category:OWASP_WebGoat_Project "wikilink")