While doing my Rooting the CLR research I found something which I thing
could be a 'Type Confusion issue' in .Net 1.1 (see more details about
these issues in this great document on Java Security published by the
LSD Research group <http://lsd-pl.net/papers.html#java>)

Here are my test:

1\) Compile this:

`using System;`
`namespace RootingTheClr`
`{`
`   class classTest`
`   {`
`       public static void Main()`
`       {`
`           Console.WriteLine("\n\n classTest \n\n");`
`           normalClass ncTest = new normalClass();                  `
`           maliciousClass mcTest = (maliciousClass)new maliciousClass();           `
`            normalClass ncTestTarget = ncTest;`
`           Console.WriteLine("Public = " + mcTest.iPublicVar + "    Private = " + mcTest.iPrivateVar );`
`       }`
`   }`

`   class normalClass`
`    {`
`       public int iPublicVar;`
`       private int iPrivateVar;`

`       public normalClass()`
`       {`
`           iPrivateVar = 100;`
`           iPublicVar = 999;`
`       }`
`   }`

`   class maliciousClass`
`   {`
`       public int iPublicVar;`
`       public int iPrivateVar;`

`       public maliciousClass()`
`       {`
`           iPrivateVar = 1;`
`           iPublicVar = 9;`
`       }`
`   }`
`}`

2\) and you should get this (note the value of Private):

`csc classtest.cs`
`Microsoft (R) Visual C# .NET Compiler version 7.10.3052.4`
`for Microsoft (R) .NET Framework version 1.1.4322`
`Copyright (C) Microsoft Corporation 2001-2002. All rights reserved.`

`classTest.cs(21,15): warning CS0169: The private field`
`       'RootingTheClr.normalClass.iPrivateVar' is never used`

`classTest.exe`

`classTest`

`Public = 9    Private = 1`

3\) run ILDASM on the exe:

`ildasm classTest.exe /out:classTest.il`

`// WARNING: Created Win32 resource file classTest.res`

4\) Notepad it and make this change:

`notepad classTest.il`

`replace`

`     IL_0010:  newobj     instance void RootingTheClr.maliciousClass::.ctor()`

`with`

`     IL_0010:  newobj     instance void RootingTheClr.normalClass::.ctor()`

5\) Ilasm the file

`ilasm classTest.il`

`Microsoft (R) .NET Framework IL Assembler.  Version 1.1.4322.573`
`Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.`
`Assembling 'classTest.il' , no listing file, to EXE --> 'classTest.EXE'`
`Source file is ANSI`

`Assembled method classTest::Main`
`Assembled method classTest::.ctor`
`Assembled method normalClass::.ctor`
`Assembled method maliciousClass::.ctor`
`Creating PE file`

`Emitting members:`
`Global`
`Class 1 Methods: 2;`
`Class 2 Fields: 2;      Methods: 1;`
`Class 3 Fields: 2;      Methods: 1;`
`Resolving member refs: 8 -> 8 defs, 0 refs`
`Writing PE file`
`Operation completed successfully`

6\) execute it (note the value of Private)

`classTest.exe`

`classTest`

`Public = 999    Private = 100`

7\) This means that we successuflly were able to cast an object of the
class normalClass into an object of the class maliciousClass. The attack
vector occours because iPrivateVar is a pubic var in maliciousClass and
a private var in normalClass

`class maliciousClass`
`   {`
`       public int iPublicVar;`
`       public int iPrivateVar;`

`...`

`   class normalClass`
`   {`
`       public int iPublicVar;`
`       private int iPrivateVar;`

`...`

`---------`

  - 8\) what is interresting is that this only works in Full Trust, if
    you try to run this in a partial trust environment like from a local
    network share) you will get the following error:

`classTest.exe`

`Unhandled Exception: System.Security.VerificationException: Operation could destabilize the runtime.`
`  at RootingTheClr.classTest.Main()`

This means that the CLR in partial trust does do some verification on
the compliled Byte code which is not done in Full Trust (which will mean
that Microsoft Security Response Team will say that this is not a
vulnerabiltiy and occours by design :)

[link not working](Category:FIXME "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink")