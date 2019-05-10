## Abstract

The .NET framework is a powerful development environment which became
the de-facto environment for software development. With .NET you can
develop web applications, windows applications, web services and more.

As a managed code environment, .NET enables the code to run inside its
virtual machine - the CLR – while abstracting the low level calls,
allowing MSIL code to benefit from the services it gives.

Since the code the developer writes, whether it's in c\#, vb.net,
cobol.net must be compiled to MSIL, and afterwards to the CPU's
instruction set on the fly ("JIT – Just In Time"), .NET EXE's and DLL's
it is easy to reverse engineer it and extract the MSIL code from .NET
compiled code. This is a well known fact.

But what happens if we will use this fact to modify the Framework's code
itself and recompile the code..? We can change the .NET language\!

This talk will cover various ways to develop rootkits for the .NET
framework, so that every EXE/DLL that runs on a modified Framework will
behave differently than what it's supposed to do. Code reviews will not
detect backdoors installed inside the framework since the payload is not
in the code itself, but rather it is inside the framework
implementation.

We will see how to write rootkits for the framework, that will enable
the attacker to install a reverse shell inside the framework, to steal
valuable information, to fixate encryption keys, disable security checks
and more.

In addition, a new tool for building MSIL rootkits will be released that
will enable the user to inject preloaded/custom payload to the Framework
core DLL. Also, a whitepaper describing the methods and tools will be
released, called ".NET Framework rootkits - backdoors inside your
Framework".

## Bio

Erez is a frequent speaker at our conferences and gets great feedback
scores. The only complaint is that he needs more time, which we can
easily solve now by having a full day two tracks event.

Erez is a senior application security consultant, working as the
application security department manager at 2BSecure. He has extensive
hands-on experience performing security assessments, secure development
consulting & training for clients in Israel and abroad such as banks,
financial organizations, military, software development companies,
telecom, and more. Erez graduated his BSc computer science at Ben-Gurion
University, and is toward graduation of Msc in computer science. He also
holds a CISSP certification (Certified Information Systems Security
Professional) from the British (ISC)2 organization.

Erez is also a leading instructor for many information security
training, especially on secure software development methodologies &
techniques. He had lectured on advanced .NET security (and other
development platforms) for worldwide organizations and is constant
speaker for conferences such as Microsoft .NET Security User Group,
OWASP (Open Web Application Security Project), and more.