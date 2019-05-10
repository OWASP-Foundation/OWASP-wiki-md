The library being demonstrated here is based off the ideas presented the
article
[How_to_add_validation_logic_to_HttpServletRequest](How_to_add_validation_logic_to_HttpServletRequest "wikilink"),
but fleshed out to be more flexible and easy to deploy. We call this
library the (unimaginatively named) Parameter Validation Filter, or PVF.

PVF is implemented as a Servlet filter that intercepts requests to web
pages, runs submitted parameters through a configurable sequence of
validation rules, and either sanitises the parameters before they are
sent through to the web application, or returns a HTTP error code if
validation errors were detected.

We have made the following assumptions when developing this library:

  - Client side validation will prevent legitimate users from submitting
    invalid data.
  - The PVF library should prevent further processing if invalid data is
    submitted in the majority of cases.
  - Occasionally it might be appropriate to sanitise submitted data, but
    any sanitisation should be trivial (like the removal of whitespace).

To make use of the PVF library, you’ll need to add it to your project.
This artifact is currently in the Sonatype staging repo, so you'll need
to add that repo to your Maven config. See
<http://stackoverflow.com/questions/13945757/how-do-you-import-a-maven-dependency-from-sonatype-org>
for details.

<dependency>
`  `<groupId>`com.matthewcasperson`</groupId>
`  `<artifactId>`parameter_validation_filter`</artifactId>
`  `<version>`1.0.0-SNAPSHOT`</version>
</dependency>

The filter then needs to be added to the web.xml file with the following
settings. You may want to configure the url-pattern to match the pages
that you actually want to protect.

<filter>
`  `<filter-name>`ParameterValidationFilter`</filter-name>
`  `<filter-class>`com.matthewcasperson.validation.filter.ParameterValidationFilter`</filter-class>
`  `<init-param>
`    `<param-name>`configFile`</param-name>
`    `<param-value>`/WEB-INF/xml/pvf.xml`</param-value>
`  `</init-param>` `
</filter>
<filter-mapping>
`  `<filter-name>`ParameterValidationFilter`</filter-name>
`  `<url-pattern>`*.jsp`</url-pattern>
</filter-mapping>

Finally you need to create a file called WEB-INF/xml/pvf.xml. This file
defines the custom validation rules applied to the parameters being sent
to your web applications.

<?xml version="1.0" encoding="UTF-8" standalone="yes"?>

<ParameterValidationChainDatabase>
`   `
`   `<EnforcingMode>`true`</EnforcingMode>
`   `
`   `<ParameterValidationChains>
`       `
`       `
`       `<ParameterValidationDefinition>
`           `
`           `<ParameterValidationRuleList>
`               `<ParameterValidationRule>
`                   `
`                   `
`                   `<validationRuleName>`com.matthewcasperson.validation.ruleimpl.TrimTextValidationRule`</validationRuleName>
`               `</ParameterValidationRule>
`               `<ParameterValidationRule>
`                   `
`                   `<validationRuleName>`com.matthewcasperson.validation.ruleimpl.FailIfNotCanonicalizedValidationRule`</validationRuleName>
`               `</ParameterValidationRule>
`               `<ParameterValidationRule>
`                   `
`                   `<validationRuleName>`com.matthewcasperson.validation.ruleimpl.FailIfContainsHTMLValidationRule`</validationRuleName>
`               `</ParameterValidationRule>
`           `</ParameterValidationRuleList>
`           `
`           `<paramNamePatternString>`.*`</paramNamePatternString>
`           `
`           `<requestURIPatternString>`.*`</requestURIPatternString>
`                      `
`           `<paramNamePatternNegated>`false`</paramNamePatternNegated>
`           `
`           `<requestURIPatternNegated>`false`</requestURIPatternNegated>
`       `</ParameterValidationDefinition>`        `
`   `</ParameterValidationChains>
</ParameterValidationChainDatabase>

There are a few interesting elements in this XML configuration:

  - paramNamePatternString, which has been configured to enable the
    validation chain to match all parameters

<!-- end list -->

  - requestURIPatternString, which has been configured to enable the
    chain to match all URIs

<!-- end list -->

  - The three elements called validationRuleName, which reference the
    full class name of the validation rules that will be applied to each
    parameter passed into our web application

Although this is a simple example, the three validation rules that have
been implemented (TrimTextValidationRule,
FailIfNotCanonicalizedValidationRule and
FailIfContainsHTMLValidationRule) are quite effective at preventing a
malicious user from submitting parameters that contain XSS code.

The first rule, TrimTextValidationRule, simply strips away any
whitespace on either side of the parameter. This uses the trim()
function any developer should be familiar with.

The second rule, FailIfNotCanonicalizedValidationRule, will prevent
further processing if the supplied parameter has already been encoded.
No legitimate user will have a need to supply text like
%3Cscript%3EdoEvil()%3B%3C%2Fscript%3E, so any time encoded text is
found we simply return with a HTTP 400 error code. This rule makes use
of the ESAPI library supplied by OWASP.

Like the second rule, the third rule will prevent further processing if
the supplied parameter has any special HTML characters. If you would
like your customers to be able to pass through characters like &, this
rule is too broad. However, it is almost always valid to block special
HTML characters.

If you want to see how effective this simple validation chain is, check
out the live demo at <http://pvftest-matthewcasperson.rhcloud.com/>. You
may want to take a look at
<https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet> to find
some XSS patterns that are often used to bypass XSS filters.

Moving forward we will be looking to implement more targeted validation
rules, especially those that can’t be easily implemented as regex
matches (like making sure a date if after today, or that a number is
between two values etc).

If you have any suggestions, or find any bugs, feel free to fork the
code from our GitHub repo at
<https://github.com/mcasperson/ParameterValidationFilter> . We do hope
to get some public feedback in order to make this library as robust as
it can be.

[Category: How To](Category:_How_To "wikilink")
[Category:Java](Category:Java "wikilink") [Category: OWASP Validation
Project](Category:_OWASP_Validation_Project "wikilink")