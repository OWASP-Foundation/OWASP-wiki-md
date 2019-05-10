# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p><span style="color:#ff0000"> </span></p>
<h2 id="owasp_resource_securitization_language_re">OWASP Resource Securitization Language (R/E)</h2>
<p>R/E is a version of E, an influential language to model/afford secure programming practices and designs, based on a Lisp E implementation. R/E uses a recent embedded Lisp dialect and is intrinsically oriented to modern (and "semantic") web patterns.</p>
<h2 id="description">Description</h2>
<p>The R/E (Resource Securitization Language) is envisioned as a modern adaptation of the E programming language and is intended to extend the Common Lisp implementation of E. E is one of the oldest "security" languages, as a language specifically designed for secure coding and to promote good security practices through language affordances. Originally implemented in Java, a Common Lisp version of E was developed (beginning 2008) by Kevin Reid (it should be noted that regardless of implementations in Lisp, E itself has a C-style syntax arguably easier for most programmers to use; however Common Lisp integration can support powerful Lisp-based extensions). The new R/E dialect is based on Clasp, a very recent Common Lisp implementation created by Christian Schafmeister of Temple University, which itself is based on Embedded Common Lisp and is designed for efficient embedding and integration with C++ applications and, in particular, with LLVM (a compiler and development toolkit whose initials originally stood for "Low Level Virtual Machine", which despite being officially obsolete is a good four-word summary). By being based on a Lisp intended for embedding, R/E as a dialect of E is suitable for embedded programming in which it integrates into applications primarily written in a different language: R/E can be used just for components which provide certain sensitive capabilities, like database and filesystem access (by fortuitous coincidence, the name Clasp is also used by the OWASP Comprehensive, Lightweight Application Security Process Project, and conceivably E-based code can be used to implement parts of CLASP-informed applications). Aside from using Clasp as a back-end, R/E is concerned to adapt Clasp to be easier to use as a cross-platform language environment and foundation for other languages. In particular, extending both Lisp and E implementations, R/E is based on a Semantic Networking or Semantic Web style compilation model which separates source-level syntax from canonical syntax, and uses Semantic Web compatible data structures to express pre- (or partly-) compiled code. This allows R/E components to be coded in extended (or alternate) syntaxes which may be more readily integrated into existing projects, based on the languages and data structures they favor. Semantic Network models of source code also allow for Semantic Web tools to gather and process information about code projects, documentation, requirements, and policies. In addition to the core language, this project will provide simple examples of a database, http client and server, and GUI integration that can be used for prototyping applications which may use R/E components. Finally, R/E will provide an OWL ontology (likely published in RDFa) to model the concepts relevant to creating, compiling, using, and evaluating R/E code and the components or applications which use it, with links as appropriate to other ontologies/taxonomies/vocabularies in the code security, privatization, and trust-description domains.</p>
<h2 id="licensing">Licensing</h2>
<p>Boost Software License (amended)</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="project_resources">Project Resources</h2>
<p><span> Some information is discussed on the website <a href="http://www.scignscape.appspot.com">http://www.scignscape.appspot.com</a>. However, a R/E-specific web site is under development.<br />
<br />
Please also visit pages about Clasp and E, for example:</p>
<ul>
<li>Clasp: <a href="https://github.com/drmeister/clasp">https://github.com/drmeister/clasp</a></li>
<li>E in a nutsehll: <a href="http://www.skyhunter.com/marcs/ewalnut.html">http://www.skyhunter.com/marcs/ewalnut.html</a></li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<p><a href="mailto:osrworkshops@gmail.com">Nathaniel Christian</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><span style="color:#ff0000"> </span></p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<p><span> Although not specifically an OWASP meeting, I will be talking about R/E at two meetups co-organized by OWASP Brooklyn and Semiotics Web, on April 18th and 25th at 10:30 am, Morningside Heights Library community room in Manhattan. I'll post links when they're available. </span></p></td>
</tr>
</tbody>
</table>

# FAQs

<span style="color:#ff0000"> </span>

# Acknowledgements

## Volunteers

<span style="color:#ff0000"> </span>

The first contributors to the project were:

  - [Nathaniel Christen](mailto:osrworkshops@gmail.com)

# Road Map and Getting Involved

## Roadmap

Whereas E-on-Common-Lisp relies on the original (Java) version of E for
some core functionality, R/E will completely replace these components
with Lisp, C++, or (in a single-language version) Ruby equivalents. In
particular, the existing ANTLR-based parsing mechanism has been replaced
by a Semantic-Network grammar engine which allows R/E code and
components to be integrated with Semantic Web tools and concepts. I
envision the development roughly as follows:

  - Basic language implementation: (all of these stages have been
    partially completed, so the basic development strategies involved
    are in place, but there are many details to sort out)
    1.  Establish an R/E grammar, first informally and then a formal
        specification using a Semantic Web-based grammar and parsing
        system. This also involves polishing code for such a grammar and
        providing this code on github. The idea of such a grammar is
        that users of R/E can customize the language for their purposes,
        including (eventually) embedding callbacks to R/E code within
        parsing itself.
    2.  Implement (at least a large part of) R/E basic data and function
        structures in the form of a generator for C++ code.
    3.  Using this base, build a version in Ruby which allows both the
        parsing and runtime interpretation to be carried out in a single
        language. Compile this into a gem and use a Rails application to
        demonstrate it.
    4.  Port the same base to Clasp itself, adding the necessary C++
        code to the underlying Clasp and using a “Semantic Readtable” to
        hook into the Clasp runtime for executing R/E code.
  - Implement many E feature for R/E:
    1.  Port E-on-Common-Lisp to the embedded Clasp platform, or at
        least determine how extensively this can be accomplished.
    2.  Ensure cross-platform consistency by solidifying the Clasp base
        itself (since Clasp in turn is a very new language, R/E is being
        built with/alongside a modified Clasp version that is easier to
        use in different contexts; for example, minimize differences
        between Window/Unix and 32-bit/64-bit environments).
    3.  Provide sample components, expected to use the Qt and UnQLite
        libraries, demonstrating how the language may be used to provide
        components isolating sensitive capabilities, such as
        database/filesystem access and http networking, integrated into
        other projects.
  - Promote customization and cross-language support:
    1.  Integrate a markup language for code documentation,
        serialization, embedded rich text, etc., parsed directly by R/E
    2.  Provide a mechanism for developing alternate grammars that may
        be more suited for integrating into existing projects, including
        “host languages” other than the primary Clasp/C++ (or “R/Z”)
        runtime or the single-language Ruby host.

<li>

Publish an Ontology of R/E coding constructs and concerns; the R/E
compiler will be guaranteed to compile any source whose internal
representation conforms to the ontology, even if its surface syntax
differs considerably from either R/E or E proper.

## Getting Involved

### Feedback

# Minimum Viable Product

R/E (the Resource Securitization Language) is a modern adaptation of the
E programming language (one of the first and most influential languages
specifically designed to address security concerns and
"Capability-Oriented Programming"), intended to extend the Common Lisp
implementation of E, by using a very recent embedded version of Common
Lisp, called Clasp. R/E will be available in source code form and in the
form of binaries for platforms for which Clasp itself is also available
(or perhaps additional platforms as well, since R/E can be configured to
use a simplified subset of Clasp/Lisp to focus on building components
for sensitive capabilities like database, networking, and filesystem
access, which are then embedded into application written in other
languages).

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")