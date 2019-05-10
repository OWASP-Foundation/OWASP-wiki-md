# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="abstract">Abstract:</h2>
<p>This is a free open source Development Framework created to support writing security tools and malware analysis tools. And to convert the security researches and ideas from the theoretical approach to the practical implementation.</p>
<p>This development framework created mainly to support the malware field to create malware analysis tools and anti-virus tools easily without reinventing the wheel and inspire the innovative minds to write their researches on this field and implement them using SRDF.</p>
<h2 id="introduction">Introduction:</h2>
<p>In the last several years, the malware black market grows widely. The statistics shows that the number of new viruses increased from 300,000 viruses to millions and millions nowadays.</p>
<p>The complexity of malware attacks also increased from small amateur viruses to stuxnet, duqu and flame.</p>
<p>The malware field is searching for new technologies and researches, searching for united community can withstand against these attacks. And that’s why SRDF</p>
<p>The SRDF is not and will not be developed by one person or a team. It will be developed by a big community tries to share their knowledge and tools inside this Framework</p>
<p>SRDF still not finished … and it will not be finished as it’s a community based framework developed by the contributors. We just begin the idea.</p>
<p>The SRDF is divided into 2 parts: User-Mode and Kernel-Mode. And we will describe each one in the next section.</p>
<p>'''SRDF is seeking contributors to help with the next releases . Contact <a href="mailto:amr.thabet@owasp.org">Amr Thabet</a> for more info.</p>
<p>'''We can help you create your own project based on SRDF .. just contact us from the email above</p>
<h2 id="licensing">Licensing</h2>
<p>SRDF is a free open source framework. It is licensed under the GPL v2</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="the_features">The Features:</h2>
<p>Before talking about SRDF Design and structure, I want to give you what you will gain from SRDF and what it could add to your project.</p>
<h3 id="in_malware">in Malware:</h3>
<p>• Assembler and Disassembler</p>
<p>• x86 Emulator</p>
<p>• x86 Debugger</p>
<p>• PE Analyzer, ELF Analyzer, PDF Analyzer (still in progress), Android APK Analyzer</p>
<p>• Process Analyzer (Loaded DLLs, Memory Maps … etc)</p>
<p>• MD5, SSDeep and Wildlist Scanner (YARA)</p>
<p>• API Hooker, IAT Hooking and Process Injection</p>
<p>• Backend Database, XML Serializer</p>
<p>• And many more</p>
<h3 id="in_network">in Network:</h3>
<p>• Packet capturing using winpcap</p>
<p>• Pcap file analysis and packet analyzer</p>
<p>• detecting malformed packets and packet generator</p>
<p>• Session analysis and session separation</p>
<p>• Protocol Analysis like tcp, udp, icmp .. etc</p>
<p>• Application layer protocol analysis like http and dns</p>
<p>• And many more</p>
<p>and the project is totally object oriented, very expandable and well organized</p>
<p>''' the project development still active and still expanding</p>
<h2 id="python_srdf_pysrdf">Python SRDF (pySRDF)</h2>
<p>it's an implementation for SRDF on python and very easy to use like this:</p>
<p><code>&gt;&gt;from pySRDF import *</code><br />
<code>&gt;&gt;dbg = Dbg("C:\\test.exe")</code><br />
<code>&gt;&gt;dbg.SetBp(0x401000)</code><br />
<code>&gt;&gt;dbg.Run()</code></p>
<p>OR Using the Emulator:</p>
<p><code>&gt;&gt; emu = Emulator("C:\\test.exe")</code><br />
<code>&gt;&gt; emu.SetBp("eip == 0x401000")</code><br />
<code>&gt;&gt; emu.Run()</code></p>
<p>OR</p>
<p><code>&gt;&gt; emu.SetBp("__isdirty(eip)") #which set bp on Execute on modified data </code><br />
<code>&gt;&gt; emu.Run()</code></p>
<p>Find it at:</p>
<p><a href="https://github.com/AmrThabet/pySRDF">pySRDF Github</a></p>
<p><a href="https://github.com/AmrThabet/pySRDF/tree/master/Examples">Examples</a></p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="source_code">Source Code:</h2>
<p><a href="https://github.com/AmrThabet/winSRDF">Github</a></p>
<p><a href="https://www.openhub.net/p/winSRDF">Openhub</a></p>
<p><a href="http://www.security-framework.com">Our Website</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="mailto:amr.thabet@owasp.org">Amr Thabet</a></p></td>
</tr>
</tbody>
</table>

# Design

## The Design:

the main design is:

![<File:SRDF-Design.png>](SRDF-Design.png "File:SRDF-Design.png")

### Infrastructure:

This includes the essential elements of any development framework and
it’s not related to security like: string, hash, list, serializer,
database, registry manipulation, sockets and so on.

We decided to create this part rather than depending on any development
framework to make this framework independent from any other development
frameworks and to be portable on any development framework

#### Targets:

This is the beginning of the SRDF. This part is simply the Target from
your security tool. What do you want to secure or secure from. And it
includes Files (PE Files and others), Processes and Packets.

#### Libraries:

That’s the security tools that the SRDF support. And it’s divided into
two namespaces: malware and network

Malware includes the assemblers and disassemblers, emulator, debugger,
API Hooker, Yara Scanner (wildcard scanner) file recursive scanner and
other tools

Network includes User-Mode capturing and Firewall

#### Core (The Application Interface):

The Core includes the Logging system and the back-end Database.

And also, it’s the Application Interface. Like cConsoleApp … and you can
inherit from it to create your own User-Interface.

We wish this part to be expanded to include more user interfaces and
management systems

## The Infrastructure:

### Elements:

It’s divided into three namespaces:

1\. String: it contains the string class, encoded string, hash and list

2\. Code: it contains the NativeCode class and StoredProcedure … and
they represents the shellcode and the code that stored in database. Like
a virus detection routines inside an Antivirus

3\. XML: and it contains the XML Encoder and the Serializer.

### Connections:

It’s divided into three namespaces:

1\. Internet: and it contains the internet communication protocols like
sockets, HTTP Sockets and so on.

2\. IPC: and it contains the Inter-Process Communication protocol

3\. User-Mode to Kernel-Mode Communication: and it contains the
communication protocol to communicate to the kernel-mode part of the
SRDF

### Storage:

It’s divided into three namespaces:

1\. Databases: and it contains the Database class and SQLiteDB and so
on.

2\. Files: and contains the File writing and logging classes

3\. Registry: and it contains the registry read and write

## The Targets:

### Files:

This namespace describes the File Formats of The Files that could
contain malicious code like: Executable Files (PE and ELF) and Document
Files (PDF, Docx …) and so on.

Until now it contains The PE Files parser

### Process:

And it includes one class only named cProcess. And, this class describes
a running process and parses its PEB and gives you the important
information about the process and its memory map. And support injecting
code and create a remote thread.

### Packets:

And it includes classes that describe an internet packets captured on
the wire or generated for an attack.

## Libraries:

It contains two namespaces:

### Malware:

This namespace contains the scanning, Hooking and emulation libraries
and contains Pokas Emulator wrapper class, Yara wrapper class (wildcard
scanner), a debugger and contains a directory recursive scanner and
other tools

And also, it contains the x86 assembler and disassembler (using Pokas
Emulator Assembler) and allow to contain other assemblers and for other
platforms.

### Network:

This namespace should contain the User-Mode Packet capture and firewall.
And should contain the Winpcap Packet capturing and firewall system. It
also should include Application Layer parsers for FTP, HTTP, IRC and all
known protocols and include Pcap Reader and writer.

## The Core:

And the core includes the cApp class that contains the back-end database
and logging and the User-Interface such as cConsoleApp

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")