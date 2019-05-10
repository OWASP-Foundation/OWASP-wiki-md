__TOC__

## Introduction

A lot of open source projects exist in the wild, performing static code
review analysis. This is good, it means that source code testing for
security issues is becoming a constraint.

Such tools bring a lot of valuable points:

  - community support
  - source code freely available to anyone
  - costs

On the other side, these tools don't share the most valuable point among
them: the security knowledge. All these tools have their own security
library, containing a lot of checks, without sharing such knowledge.

In 2006, the Owasp Orizon project was born to provide a common
underlying layer to all opensource projects concerning static analysis.

Orizon project includes:

  - a set of APIs that developers can use to build their own security
    tool performing static analysis.
  - a security library with checks to apply to source code.
  - a tool, Milk, which is able to static analyze a source code using
    Orizon Framework.

## The Owasp Orizon Architecture

In the following picture, the Owasp Orizon version 1.0 architecture is
shown. As you may see, the framework is organized in engines that
perform tasks over the source code and a block of tools that are
deployed out of the box in order to use the APIs in a real world static
analysis.

![Owasp_Orizon_Architecture_v1.0.png](Owasp_Orizon_Architecture_v1.0.png
"Owasp_Orizon_Architecture_v1.0.png")

With all such elements, a developer can be scared to use the framework;
that's why a special entity called SkyLine was created. Before going
further into SkyLine analysis, it's very important to understand all the
elements Orizon is made of.

### Your personal butler: the SkyLine class

Named **core** in the architectural picture, the SkyLine object is one
of the most valuable services in Orizon version 1.0.

The idea behind SkyLine is simple: as the Orizon architecture becomes
wider, regular developers may be scared about understanding a lot of
APIs in order to build their security tool, so we can help them
providing "per service" support.

Using SkyLine object, developers can request services from the Orizon
framework waiting for their accomplishment.

The main SkyLine input is:

**`public``   ``boolean``   ``launch(String``   ``service)`**

Passing the requested service as string parameter, the calling program
will receive a boolean true return value if the service can be
accomplished or a false value otherwise.

The service name is compared to the ones understood by the framework:

`'''private int goodService(String service) {`
`'''  int ret = -1;`
`'''  if (service.equalsIgnoreCase("init"))`
`'''      ret = Cons.OC_SERVICE_INIT_FRAMEWORK;`
`'''  if (service.equalsIgnoreCase("translate"))`
`'''      ret = Cons.OC_SERVICE_INIT_TRANSLATE;`
`'''  if (service.equalsIgnoreCase("static_analysis"))`
`'''      ret = Cons.OC_SERVICE_STATIC_ANALYSIS;`
`'''  if (service.equalsIgnoreCase("score"))`
`'''      ret = Cons.OC_SERVICE_SCORE;`
`'''  return ret;`
`'''}`

The secondary feature introduced in this first major framework release
is the support for command line option given to the user.

If the calling program passes command line option to Orizon framework
using SkyLine, the framework will be tuned accordingly to the given
values.

This example will explain better:

`'''public static void main(String[] args) {`
`'''   String fileName = "";`
`'''   OldRecipe r;`
`'''   DefaultLibrary dl;`
`'''`
`'''   SkyLine skyLine = new SkyLine(args);`

That's all folks\! Internally, the SkyLine constructor, when it creates
a code review session, uses the values it was able to understand from
command line.

The command line format must follow this convention

`''' -o orizon_key=value`

or the long format

`''' --orizon orizon_key=value`

And these are the keys that the framework cares about:

  - "input-name"
  - "input-kind"
  - "working-dir"
  - "lang"
  - "recurse"
  - "output-format"
  - "scan-type";

The org.owasp.orizon.Cons class contains a detailed section about these
keys with some comments and with their default value.

The only side effect is that calling program can use -o flag for its
purpose.

SkyLine is contained in the org.owasp.orizon package.

### Give me something to remind: the Session class

Another big feature introduced in Owasp Orizon version 1.0 is the code
review session concept. One of the missing features in earlier versions
was the capability to track the state of the code review process.

A Session class instance contains all the properties specified using
SkyLine and it is their owner giving access to properties upon request.
It contains a SessionInfo array containing information about each file
being reviewed.

Ideally, a user tool will never call Session directly, but it must use
SkyLine as interface. Of course anyone is free to override this
suggestion.

Looking at the launch() method code, inside the SkyLine class, you can
look how session instance is prompted to execute services.

`'''public boolean launch(String service) {`
`'''   int code, stats;`
`'''   boolean ret = false;`
`'''`
`'''   if ( (code = goodService(service)) == -1)`
`'''      return log.error("unknown service: " + service);`
`'''   switch (code) {`
`'''       // init service`
`'''       case Cons.OC_SERVICE_INIT_FRAMEWORK:`
`'''            ret = session.init();`
`'''            break;`
`'''       // translation service`
`'''       case Cons.OC_SERVICE_INIT_TRANSLATE:`
`'''            stats = session.collectStats();`
`'''            if (stats > 0) {`
`'''               log.warning(stats + " files failed in collecting statistics.");`
`'''               ret = false;`
`'''            } else`
`'''               ret = true;`
`'''            break;`
`'''       // static analysis service`
`'''       case Cons.OC_SERVICE_STATIC_ANALYSIS:`
`'''            ret = session.staticReview();`
`'''            break;`
`'''       // score service`
`'''       case Cons.OC_SERVICE_SCORE:`
`'''            break;`
`'''       default:`
`'''            return log.error("unknown service: " + service);`
`'''       }`
`'''       return ret;`
`'''}`

Internally, the Session instance will ask each SessionInfo object to
execute services. Let us consider the Session class method that executes
the static analysis service.

`'''/**`
`'''  * Starts a static analysis over the files being reviewed`
`'''  * `
`'''  * @return `<i>`true`</i>` if static analysis can be performed or `<i>`false`</i>
`'''  *         if one or more files fail being analyzed.`
`'''  */`
`'''public boolean staticReview() {`
`'''   boolean ret = true;`
`'''   if (!active)`
`'''      return log.error("can't perform a static analysis over an inactive session.");`
`'''   for (int i = 0; i < sessions.length; i++) {`
`'''       if (! sessions[i].staticReview())`
`'''          ret = false;`
`'''   }`
`'''   return ret;`
`'''}`

Where sessions variable is declared as:

`'''private SessionInfo[] sessions;`

As you may see, the Session object delegates service accomplishment to
SessionInfo once collecting the final results.

In fact, SessionInfo objects are the ones talking with Orizon internals
performing the real work.

The following method is stolen from org.owasp.orizon.SessionInfo class.

`'''/**`
`'''  * Perform a static analysis over the given file`
`'''  * `
`'''  * A full static analysis is a mix from:`
`'''  * `
`'''  *  * local analysis (control flow)`
`'''  *  * global analysis (call graph)`
`'''  *  * taint propagation`
`'''  *  * statistics`
`'''  * `
`'''  * `
`'''  * @return `<i>`true`</i>` if the file being reviewed doesn't violate any`
`'''  *         security check, `<i>`false`</i>` otherwise.`
`'''  */`
`'''  public boolean staticReview() {`
`'''     boolean ret = false;`
`'''     s = new Source(getStatFileName());`
`'''     ret = s.analyzeStats();`
`'''     ...`
`'''     return ret;`
`'''  }`

### The Translation Factory

One of the Owasp Orizon goals is to be independent from the source
language being analyzed. This means that Owasp Orizon will support:

  - Java
  - C, C++
  - C\#
  - Perl
  - ...

Such support is granted using an intermediate file format to describe
the source code and used to apply the security checks. Such format is
XML language.

A source code, before static analysis is started, is translated into
XML. Starting from version 1.0, each source code is translated in 4 XML
files:

  - an XML file containing statistical information
  - an XML file containing variables tracking information
  - an XML file containing program control flow (local analysis)
  - an XML file containing call graph (global analysis)

At the time this document is written (Owasp Orizon v1.0pre1, September
2008), only the Java programming language is supported, however other
programming language will follow soon.

Translation phase is requested from
org.owasp.orizon.SessionInfo.inspect() method. Depending on the source
file language, the appropriate Translator is called and the scan()
method is called.

`''' /**`
`'''   * Inspects the source code, building AST trees`
`'''   * @return`
`'''   */`
`'''   public boolean inspect() {`
`'''      boolean ret = false;`
`'''      switch (language) {`
`'''         case Cons.O_JAVA:`
`'''             t = new JavaTranslator();`
`'''             if (!t.scan(getInFileName())) `
`'''                return log.error("can't scan " + getInFileName() + ".");`
`'''                ret = true;`
`'''         break;`
`'''         default:`
`'''             log.error("can't inspect language: " + Cons.name(language));`
`'''         break;`
`'''      }`
`'''      return ret;`
`'''   }`

Scan method is an abstract method defined in
org.owasp.orizon.translator.DefaultTranslator class and declared as the
following:

`''' public abstract boolean scan(String in);`

Every class implementing DefaultTranslator must implement how to scan
the source file and build ASTs in this method.

Aside from scan() method, there are four abstract method needful to
create XML input files.

`''' public abstract boolean statService(String in, String out);`
`''' public abstract boolean callGraphService(String in, String out);`
`''' public abstract boolean dataFlowService(String in, String out);`
`''' public abstract boolean controlFlowService(String in, String out);`

All these methods are called in the translator() method, the one
implemented directly from DefaultTranslator class.

`''' public final boolean translate(String in, String out, int service) {`
`'''    if (!isGoodService(service))`
`'''       return false;`
`'''    if (!scanned)`
`'''       if (!scan(in))`
`'''          return log.error(in+ ": scan has been failed");`
`'''    switch (service) {`
`'''      case Cons.OC_TRANSLATOR_STAT:`
`'''          return statService(in, out);`
`'''      case Cons.OC_TRANSLATOR_CF:`
`'''          return controlFlowService(in, out);`
`'''      case Cons.OC_TRANSLATOR_CG:`
`'''          return callGraphService(in, out);`
`'''      case Cons.OC_TRANSLATOR_DF:`
`'''          return dataFlowService(in, out);`
`'''      default:`
`'''          return log.error("unknown service code");`
`'''    }`
`''' }`

So, when a language specific translator is prompted for translate()
method, this recalls the language specific service methods.

Every translator contains as private field, a language specific scanner
containing ASTs to be used in input file generation.

Consider org.owasp.orizon.translator.java.JavaTranslator class, it is
declared as follows:

`''' public class JavaTranslator extends DefaultTranslator {`
`'''   static SourcePositions positions;`
`'''   private JavaScanner j;`
`'''   ...`

JavaScanner is a class from org.owasp.orizon.translator.java package and
it uses Sun JDK 6 Compiler API to scan a Java file creating in memory
ASTs. Trees are created in scan() method, implemented for Java source
language as follow:

`''' public final boolean scan(String in) {`
`'''    boolean ret = false;`
`'''    String[] parms = { in };`
`'''    Trees trees;`
`'''        `
`'''    JavaCompiler compiler = ToolProvider.getSystemJavaCompiler();`
`'''    if (compiler == null) `
`'''       return log.error("I can't find a suitable JAVA compiler. Is a JDK installed?");`
`'''    `
`'''    DiagnosticCollector`<JavaFileObject>` diagnostics = new DiagnosticCollector`<JavaFileObject>`();`
`'''    StandardJavaFileManager fileManager = compiler.getStandardFileManager(diagnostics, null, null);`
`'''    Iterable<? extends JavaFileObject> fileObjects = fileManager.getJavaFileObjects(parms);`
`'''`
`'''    JavacTask task = (com.sun.source.util.JavacTask) compiler.getTask(null,fileManager, diagnostics, null, null, fileObjects);`
`'''`
`'''    try {`
`'''        trees = Trees.instance(task);`
`'''        positions = trees.getSourcePositions();`
`'''        Iterable<? extends CompilationUnitTree> asts = task.parse();`
`'''        for (CompilationUnitTree ast : asts) {`
`'''            j = new JavaScanner(positions, ast);`
`'''            j.scan(ast, null);`
`'''        }`
`'''        scanned = true;`
`'''        return true;`
`'''    } catch (IOException e) {`
`'''        return log.fatal("an exception occurred while translate " + in + ": " +e.getLocalizedMessage());`
`'''    }`
`''' }`

### Statistical Gathering

To implement statistic information gathering, DefaultTranslator abstract
method statService() must be implemented. In the following example, the
method is the JavaTranslator's. Statistics information is stored in the
JavaScanner object itself and retrieved by getStats() method.

`''' public final boolean statService(String in, String out) {`
`'''    boolean ret = false;`
`'''        `
`'''    if (!scanned)`
`'''       return log.error(in + ": call scan() before asking translation...");`
`'''    log.debug(". Entering statService(): collecting stats for: " + in);`
`'''    try {`
`'''        createXmlFile(out);`
`'''        xmlInit();`
`'''        xml("<source name=\"" + in+"\" >");`
`'''        xml(j.getStats());`
`'''        xml("`

</source>

");

`'''        xmlEnd();`
`'''`
`'''    } catch (FileNotFoundException e) {`
`'''    } catch (UnsupportedEncodingException e) {`
`'''    } catch (IOException e) {`
`'''        ret = log.error("an exception occurred: " + e.getMessage());`
`'''    }`
`'''    ret = true;`
`'''    log.debug("stats written into: " + out);`
`'''    log.debug(". Leaving statService()");`
`'''    return ret;`
`''' }`

## Reference

To anyone interested in Owasp Orizon framework, you can use the
following links:

  - main page @ Owasp: [OWASP Orizon
    Project](::Category:OWASP_Orizon_Project "wikilink")
  - main site @ SourceForge: <http://orizon.sourceforge.net>
  - blog:
    [<http://orizon.sourceforge.net/blog>](http://orizon.sourceforget.net/blog)
  - author page @ Owasp: <http://www.owasp.org/index.php/User:Thesp0nge>

You can drop also a line to Orizon author: <thesp0nge@owasp.org>

**`foo`**

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")