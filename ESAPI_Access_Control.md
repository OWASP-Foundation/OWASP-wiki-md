# Access Control 2.0

At the ESAPI summit, we discussed changing Access Control 2.0 to use the
command pattern. The following are the current design goals for Access
Control 2.0. Enough proof of concept development has been completed for
me to believe that these goals are achievable. I’d appreciate your input
as to whether they are both desirable and sufficient. Below the goals
are the answers to outstanding questions, the sequence of execution and
some code snippets to give a better feel for the current direction.
Feedback is welcome. I’m happy to make changes.
\==Current Design Goals:==

1.  Allow developers to implement access control rules (ACR) using
    arbitrary java code.
      -
        Benefit: Allowing arbitrary java code gives ACR developers as
        much flexibility to write ACRs as they do throughout the normal
        code base.
2.  Facilitate integration with frameworks to enforce ACRs automatically
    and default to deny access.
      -
        Benefit: Automatically making the call reduces developer error,
        because both the call will be made correctly and the developer
        is forced to provide the security check.
3.  Allow developers to call ACRs for evaluation or enforcement
    manually.
      -
        Benefit: Allowing manual calls for both uses increases
        flexibility and facilitates reuse for access control and flow
        control.
4.  Allow ACRs to make decisions based on arbitrary runtime parameters
    and deployment parameters.
      -
        Benefit: The policy file stores deployment parameters. Accepting
        an arbitrary runtime parameter allows stateless ACRs, which
        decreases object creation costs.

## Proposed Additional Design Goals

The following were not in the original set of goals, but I would like us
to consider whether they should be included:

1.  Keep the Access Control Matrix (ACM) synchronized throughout the
    SDLC by making the ACM specification drive the integration framework
    that calls the ACRs.
      -
        Benefit: Understanding of permissions is clearer and more
        accurate throughout requirements and test phases.
2.  Allow resource names to be grouped and ensure that ACR selection is
    deterministic.
      -
        Benefit: Grouping similar resources makes the ACM clearer and
        easier to manage.
3.  Integration with Struts 2, Struts 1, JSR 115, Spring ?.?, JBoss
    Seam, JBossAop, Aspect J. I’m currently using the
    Struts2Spring2JtaJpa quickstart for the integration tests.

## Outstanding Questions from the ESAPI Summit and their Answers:

**Question**: Can the runtimeParameter
AccessController.isAuthorized(“Resource”, runtimeParameter) be
strongly typed in the ACR definition class?
**Answer**: Yes. Java versions 1.5 and above can leverage Generics.
AccessControlRules written for 1.4 and below will need to use Object as
parameters and then cast appropriately. The current version of Access
Control 2.0 is written without generics for backwards compatibility, but
I plan to add generics compatible version.

## Sequence:

IntegrationComponent -\> AccessController -\> ACR -\> Access is granted
or an AccessControlException is thrown.

1.  When the system starts, the ACM is read and resources are linked to
    an ACR.
2.  The IntegrationComponent (e.g. a Struts2 Interceptor) calls
    AccessController.enforceAuthorization(key, runtimeParameter).
3.  AccessController maps the key to an ACR and passes it the runtime
    parameters and static policy file parameters.
4.  The ACR executes Java code to evaluate an arbitrarily complex rule
    set. Note that an ACR could evaluate unusually complex role
    requirements by assigning it to all roles for a given resource. Also
    note that ACRs can delegate to other ACRs or even a rules engine.

## Code Samples:

What follows is a partial strawman implementation from some proof of
concept code that I’ve been working on. Code has been removed to help
focus on the critical path. I’d appreciate any feedback and I’m looking
especially interested in feedback on usability from a developer’s point
of view. Would this help you to implement Access Control for large
projects? What can I do to make it safer and easier for developers? To
help illustrate the mappings, I’ve used <span style="color:red">**bold
red**</span> to represent the resource identifier and
<span style="color:green">**bold green**</span> to represent the ACR
throughout the files. Only the first 3 files (ACM, Policy file and ACR)
are implemented by the developer. The rest are provided by the
AccessController infrastructure.

### ACM: Access Control Matrix

This table is (roughly) what the Access Control Matrix looks like. It
would probably be a .csv file or database file and would have options to
group resources using regular expressions, String.startsWith, etc. The
ACM and Policy File (below) combine to define which ACR is executed by
AccessController.

|                                              | Role1 | Role2 | Role3 |
| -------------------------------------------- | ----- | ----- | ----- |
| <span style="color:red">**Resource1**</span> |       | Deny  |       |
| Resource2                                    |       | Grant |       |

### Policy File

This xml file is (roughly) what the ACR definitions would look like. It
handles what would normally be “footnotes” in an ACM requirements
specification document. The name correlates to an ACM cell. The
AccessControlRule.class specifies the Java code that will execute. The
parameters are passed to the ACR at runtime. Note that this shows the
default name-value pair parameter loader, but other parameter loaders
(not shown) can be specified. An enhancement would be to allow ACRs to
be tagged using annotations so that the Policy file isn't required.

<?xml version="1.0" encoding="ISO-8859-1" ?>

<AccessControlPolicy>
`     `<AccessControlRules>
`           `
`           `<AccessControlRule
                  name="Grant"
                  description="Access is always granted"
                  class="org.owasp.esapi.accesscontrol.AlwaysTrueACR">
`           `</AccessControlRule>
`           `<AccessControlRule
                  name="Deny"
                  description="Access is always denied"
                  class="org.owasp.esapi.accesscontrol.AlwaysFalseACR">
`           `</AccessControlRule>
`           `
`           <AccessControlRule`
`                 name="`<span style="color:green">**`SpecialCaseAccessControlRule`**</span>`"`
`                 description="Access depends on the value of the policy parameter: isTrue"`
`                 class="org.owasp.esapi.accesscontrol.policy.`<span style="color:green">**`EchoDynaBeanPolicyParameterACR`**</span>`">`
`                 `<Parameters>
`                       `<Parameter name="isTrue" type="Boolean" value="true"/>
`                 `</Parameters>
`           `</AccessControlRule>
`     `</AccessControlRules>
</AccessControlPolicy>

### ACR: Access Control Rule

The following class is (roughly) what a simple ACR could look like. Note
that the runtimeParameter can leverage generics for type safety.
Developers would implement this.

`public class `<span style="color:green">**`EchoDynaBeanPolicyParameterACR`**</span>` extends DynaBeanPolicyBaseACR {`
`     /**`
`      * @return true iff policyParameter isTrue is a Boolean set to true.`
`      * throws ClassCastException if runtimeParameter is not a Boolean.`
`      */`
`     public boolean isAuthorized(Object runtimeParameter) throws ClassCastException{           `
`           return getPolicyParameters().getBoolean("isTrue");`
`     }`
`}`

### IntegrationComponent

This class is (roughly) what a framework integration using a Struts2
interceptor would look like. This is part of the framework, developers
don’t implement this. However, if a developer wants to execute an ACR,
they can do so as demonstrated in the intercept method.

`public class AccessControlEnforcementInterceptor extends AbstractInterceptor {`
`   public String intercept(ActionInvocation invocation) throws Exception {`
`         ESAPI.accessController().enforceAuthorization(`<span style="color:red">**`invocation.getAction()`**</span>`, //assume that getAction() returns “Resource1”`
`                 invocation.getInvocationContext()); //Note that this line may change to facilitate `
`                                                     //mappings between Framework Integrations and multi-purpose ACRs`
`      return invocation.invoke();`
`   }`
`}`

### AccessController

This class is (roughly) what the enforceAuthorization method in
AccessController could look like. The key is the resource. In our
example “Resource1.” This method will need to be enhanced to handle
resource groups. This is part of the framework, developers don’t
implement this. This doesn’t currently take the user’s role into
account, but could.

`public void enforceAuthorization(Object `<span style="color:red">**`key`**</span>`, Object runtimeParameter)`
`     throws org.owasp.esapi.errors.AccessControlException {`
`     boolean isAuthorized = false;`
`     try {`
`           AccessControlRule `<span style="color:green">**`rule`**</span>` = (AccessControlRule)ruleMap.get(`<span style="color:red">**`key`**</span>`);`
`           if(rule == null) {`
`                 throw new AccessControlException(`
`                             "AccessControlRule was not found for key: " + key,`
`                             ""); `
`           }`
`           System.out.println("Enforcing Authorization Rule \"" + key + "\" Using class: " + rule.getClass().getCanonicalName());`
`           isAuthorized = `<span style="color:green">**`rule`**</span>`.isAuthorized(runtimeParameter);`
`     } catch(Exception e) {`
`           throw new AccessControlException("An unhandled Exception was " +`
`                       "caught, so we are recasting it as an " +`
`                       "AccessControlException.", `
`                       "",`
`                       e);`
`     }`
`     if(!isAuthorized) {`
`           throw new AccessControlException("Access Denied for key: " + key +`
`                       " runtimeParameter: " + runtimeParameter, "");`
`     }`
`}`

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")