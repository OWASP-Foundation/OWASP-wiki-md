## Status

**Content to be finalized. First draft**

## Overview

[Struts](https://www.owasp.org/index.php/Category:OWASP_Java_Project) is
an [Apache](Apache "wikilink") framework aimed at simplifying the
creation of dynamic web applications in [Java](Java "wikilink").

Struts is built on a MVC architecture, which means the application is
arranged into 3 primary types of code. These are know as a Model, View
and Controller. The Model defines the structure of your data being
processed. The View defines everything that a end user can see. The
controller take the model as submitted from the page, performs business
logic on the data, then decides what view should be responsible for
displaying the result.

I will not spend any more time talking about the architecture of struts.
If you would like to have more information on that topic, I suggest
going to the [official website](http://struts.apache.org/).

## Security in the Model

### Validation

The Struts Validation Framework is the primary method of validating a
struts based application. Struts validation consists of a few elements
to be setup. To properly use Struts validation your application should
have the following...

  - A validator-rules.xml file in the WEB-INF folder.
  - A validator.xml in the WEB-INF folder.
  - All ActionForms should extend
    org.apache.struts.validator.ValidatorForm or
    org.apache.struts.validator.ValidatorActionForm instead of
    org.apache.struts.action.ActionForm.
  - The commons-validator.jar in WEB-INF. This can be obtained
    [here](http://commons.apache.org/validator/).
  - The Validator plug-in should be enabled in struts-config.xml
        <plug-in className="org.apache.struts.validator.ValidatorPlugIn">
            <set-property property="pathnames" value="/WEB-INF/validator-rules.xml,/WEB-INF/validator.xml"/>
        </plug-in>

#### Examples

[Struts Validation in an
ActionForm](Struts_Validation_in_an_ActionForm "wikilink")

[Struts Validation in validator.xml using an
ActionForm](Struts_Validation_in_validator.xml_using_an_ActionForm "wikilink")

[Struts Validation in validator.xml using a
DynaValidatorForm](Struts_Validation_in_validator.xml_using_a_DynaValidatorForm "wikilink")

## Security in the View

### Output Sanitation

[Output sanitation](Output_sanitation "wikilink") is the process of
ensuring that your output does not contain HTML or XML specific
characters. So, for example a '\<' becomes '\<'. This should be used as
a secondary [XSS](Cross-site_Scripting_\(XSS\) "wikilink") prevention
method. Primary method of prevention should be validation. Luckily some
Struts tags include output sanitation by default. If you're tag is not
here, then you should implement sanitation manually.

#### Sanitized tags

  - bean:Write (may be overwritten by setting filter to false)
  - html:Hidden
  - html:Messages (if the value is of type String)
  - html:Multibox
  - html:OptionsCollection (may be overwritten by setting filter to
    false)
  - html:Options (may be overwritten by setting filter to false)
  - html:Option **(you must set filter to true)**
  - html:Radio
  - html:TextArea
  - html:File
  - html:Hidden
  - html:Password
  - html:Text

## Security in the Controller

### Roles

In the struts-config.xml configuration file it is possible to specify a
roles attribute, a comma-delimited list of security role names that are
allowed access to the ActionMapping object. This is pretty much all that
you get out of the box.

    <action
         roles="administrator,contributor"
         path="/article/Edit"
         parameter="org.article.FindByArticle"
         name="articleForm"
         scope="request">
           <forward
                 name="success"
                 path="article.jsp"/>
    </action>

### Custom Action Mappings

It is possible to implement far more complex security models if you
extend the action mappings.

    TODO: Lots more detail here.

### Error Handling

    TODO: Put some info here

## Common errors and vulnerabilities

[Form Field Without
Validator](Improper_Data_Validation#Struts:_Form_Field_Without_Validator "wikilink")

[Plug-in Framework Not In
Use](Improper_Data_Validation#Struts:_Plug-in_Framework_Not_In_Use "wikilink")

[Unused Validation
Form](Improper_Data_Validation#Struts:_Unused_Validation_Form "wikilink")

[Unvalidated Action
Form](Improper_Data_Validation#Struts:_Unvalidated_Action_Form "wikilink")

[Validator Turned
Off](Improper_Data_Validation#Struts:_Validator_Turned_Off "wikilink")

[Validator Without Form
Field](Improper_Data_Validation#Struts:_Validator_Without_Form_Field "wikilink")

[Form Does Not Extend Validation
Class](Improper_Data_Validation#Struts:_Form_Does_Not_Extend_Validation_Class "wikilink")

[Erroneous validate()
Method](Improper_Data_Validation#Struts:_Erroneous_validate.28.29_Method "wikilink")

[Duplicate Validation
Forms](Improper_Data_Validation#Struts:_Duplicate_Validation_Forms "wikilink")

## Auditing Tools

[Struts XSLT Viewer](Struts_XSLT_Viewer "wikilink")

[Category:Java](Category:Java "wikilink")
[Category:Struts](Category:Struts "wikilink")