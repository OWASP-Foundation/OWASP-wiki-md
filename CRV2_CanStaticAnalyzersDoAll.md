Secure code review is a process of enumerating the flaws in the
application. The flaws may exist in the application due to insecure
code, design or configuration. Out of which the flaws that arise due to
insecure code can be enumerated to a great extent through automated
analysis, as most of them are associated with insecure patterns.

Automated analysis can be carried out through any of the following three
options:

  - Static Code analyzers or scanners
  - Custom scripts based on some pattern search
  - Open source tools

Though some scripts and some open source tools are efficient enough in
finding insecure code patterns but they often lack the capability of
tracing the data flow. This limitation is fulfilled by the use of static
code analyzers or the scanners, which identify the insecure code pattern
along with source to the sink analysis.

**With this we come to the next big question i.e. Can scanners i.e.
static code analyzers do it all?**

Static code analyzers or the scanners are the most comprehensive options
to automate the process of review.

Some of the advantages of static code scanners are:

'''1. Reduction in manual efforts '''– Secure code review can be at
times be a tedious process of analyzing thousands of lines of code for a
host of vulnerabilities. Moreover as the type of patterns to be scanned
almost remains common across application the task also tends to get a
bit repetitive. In such a scenario, scanners play a big role is
automating the process of searching the vulnerabilities through big
numbers of lines of code.

'''2. Time efficient '''– Scanners are must time efficient than manual
reviews. In most cases the scanners have proved to be much faster than
manual process of reviewing the source code.

'''3.Finds all the instances of the vulnerabilities '''- Scanners are
very effective in identifying all the instances of a particular
vulnerability with their exact location. This is really helpful for
larger code base where tracing for flaws in all the files is difficult.

'''4. Source to sink analysis '''– Most scanners today trace the code
and identify the vulnerabilities through source to sink analysis. They
identify the inputs to the application and trace them thoroughly
throughout the code till they find them to be associated with any
insecure code pattern. Such a source to sink analysis helps the
developers in understanding the flaws better as they get a complete root
cause analysis of the flaw.

'''5. Exhaustive coverage of vulnerability patterns ''' – Most of the
scanners have well-defined set of test cases covering all the well-known
vulnerabilities. Thus through the use of scanners we can ensure that the
code gets thoroughly checked for all the pre-defined set of flaws.

'''6. Elaborate reporting format '''– Scanners provide a detailed report
on the observed vulnerabilities with exact code snippets, risk rating
and complete description of the vulnerabilities. This helps the
development teams to easily understand the flaws and implement necessary
controls.

**Limitations of static code analyzers:**

'''1.Business Logic Flaws remain untouched '''– The flaws that are
related to application’s logic, transactions, and specific sensitive
data remain untouched by the scanners. The security controls that needs
to be implemented in the application specific its features and design
are often not pointed by the scanners. This stands as a biggest
limitation of the static code analyzers.

'''2. Limited scope '''– Static code analyzers are often designed for
specific frameworks or certain set of vulnerable patterns, they fail to
address the issues not covered in their search pattern repository. So
the scanners often fail in catching up the vulnerabilities of the new
versions of the framework that keeps coming up.

'''3. Custom validations '''- Most of the static analyzers tool miss out
the custom validations added in the application while identifying the
flaws. These could include blacklist or whitelist validation present in
the application before the input sources. It could also mean the
customization added by the developers to the existing design frameworks
and inbuilt framework based API, the scanners that go by pattern based
search usually miss out in understanding such intricate details of the
code.

'''4. Design flaws '''– Design flaws are lessen known issues and static
code analyzers often focus more on the code than the design. Mainly if
the application design is custom built it becomes challenging for the
scanners to trace the code flow.

'''5. Application specific recommendations '''– Scanners usually provide
a generic solution and do not point out application specific code
changes. If the solutions are customized as per the design and the
feasibility of the application it will be clearer to the developers and
require less code change.

**Parameters to be considered for commercial scanners:** 1. Source to
sink analysis Capabilities 2. Support for frameworks 3. Ability to
understand customized code or validations 4. Coverage of Business logic
cases specially the ones related to authorization 5. Option to customize
the pattern search