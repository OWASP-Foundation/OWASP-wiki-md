# The Orizon check XML schema

Security checks can be divided in:

  - design_check
  - keyword_check
  - execution_check
  - stats_check

## Statistics check

The stats check XML schema has been changed from version 1.0, so this
applies starting from version 1.1 and later

`<stats`
`    subj=[code | comment | complexity]`
`    verb=[lt | gt | le | ge | ne | eq | ratio]`
`    [ direct_object= [loc | loC] ]`
`    [modifier = "percentage"]`
`    value=`*`numeric``   ``value`*
`  />`

where:

  - Subject can be one of the following:
      - code: line of code
      - comment: line of comments
      - complexity: ciclomatic complexity index

<!-- end list -->

  - verb is the boolean comparison operator between the subject and the
    value:
      - lt: lesser than
      - gt: grater than
      - le: lesser or equal than
      - ge: greater or equal than
      - ne: not equal than
      - eq: equal than
      - ratio: indicates the ratio subj versus direct_object

## Design check

` This is a work in progress section. Actually I'm collecting all the security checks coming from other tools and trying to figure it out the XML schema to use to `
` describe security checks.`
` thesp0nge, 07.12.2008`

### Classes

` `<design
        subj="class"
        name=<i>`ignored`</i>
`       verb=[counts|contains|extends|implements|has]`
`       direct_object=[scope|attribute]`
`       value=`*`the``   ``value``   ``being``   ``checked`*
` >`
` `</design>

The class design will be evaluated for the number in the source file,
the classes it extends or implements and for modifiers such as scope and
attribute. With the <i>counts</i> verb, it will be evaluated how many
classes are contained into a specific source file. For a non object
oriented program, the class it will be ignored and inteded to be the
whole program.

` Example.`
` `
` If we need to have our J2EE applications comprised of source files containing 5 classes each, this is the correspondent security check`
` `<design subj="class" verb="counts" value="5" />

The <i>extends</i> verb must be used if a security check needs to
evaluate the class extended by the one being evaluated.

` Example`
` `
` If a security check needs to evaluate if a class extends org.owasp.orizon.About, the check can be written using the following notation`
` `<design subj="class" verb="extends" value="org.owasp.orizon.About" />

The <i>implements</i> verb is the same as the previous except that the
check is intended to be applied for interfaces or abstract classes the
one being reviewed implements.

The <i>has</i> verb is the only one that makes meaningful the
<i>direct_object</i> attribute with this rationale:

  - scope: the parameter to be evaluated is the class scope

` Example`
` `
` If in your organization you must check that all Java classes has to be public for such a reason we don't know to care about, you can write the security check this way`
` `<design subj="class" verb="has" direct_object="scope" value="public" />

  - attribute: an attribute can be if the class is inner or not

## keyword_check, about keyword specific checks

`  <keyword`
`    name=`*`keyword``   ``name`*
`  />`

## execution_check: extra care must be taken for parameter in this desing...

`  <exec`
`    caller_class=`*`a``   ``class``   ``name`*
`    caller_method=`*`a``   ``method``   ``name`*
`  />`

# The Orizon Input file XML schema

Orizon 1.0 will bring 3 new subsystems in Jericho engine:

  - local analisys (control flow graph)
  - global analisys (call graph)
  - taint propagation analisys (data graph)

Each of this subsystems will use a different input file provided by the
translator, so each source file will be translated in 3 different XML
files with different schema of course.

## Local analisys

## Global analisys

## Taint propagation analisys

This subsystem is devoted to analyze variable content and how data is
managed by the application.

Here is the schema to be used to describe a generic operation over a
variable or a socket or a generic I/O operation.

` <taint`
`      subj="[variable|socket|sql|file]"`
`      name="the variable name"`
`      type="the variable data type"`
`      verb="[created|modified|deleted|read_data|write_data]"`
`      constant="[yes|no]"`
`      must_reduce="[yes|no]"`
`      value"the value being used to fill the variable"`
` >`
`      expression to be reduced...`
` `</taint>

Here there are some example to understand better how instructions over
variable, will be translated to XML.

  -   - Variable declaration

To better describe variable declaration we must discriminate from simple
variable rather than complex objects in OO programming languages.

If we need to declare a brand new integer value,

`  int a;`

we will obtain

`  `<taint subj="variable" name="a" type="int" verb="created" constant="" value="" must_reduce="no" />

If we choose to create a new variable with a init value,

`  int b = 3;`

we will obtain

`  `<taint subj="variable" name="b" type="int" verb="created" constant="" value="3" must_reduce="no" />

Now lets create an object rather than a simple variable.

`  String c = new String("A new string");`

The correspondent XML will be

`  `<taint subj="variable" name="c" type="String" verb="created" constant="" value="A new string" must_reduce="no" />

What happens if some complex constructor call is issued

`  String d = new String((new Integer(3)).toString());`

This example is quite odd, but it's a common practice to have very
complex object constructor calls.

`  `<taint subj="variable" name="d" type="String" verb="created" constant="" value="" must_reduce="yes">
`      `<taint subj="variable" name="dyno1" type="Integer" verb="created" value="3" must_reduce="no">
`      `<call variable="dyno1" method="toString()">
`            `<result type="String">`3`</result>
`      `</call>`  `
`  `</taint>

  -   - Generic non constant assignment

Let a be an integer variable. We want to stuff volatile value of '5'
into it...

`  a = 5;`

it becomes

`  `<taint subj="variable" name="a" verb="modified" constant="no" value="5" />