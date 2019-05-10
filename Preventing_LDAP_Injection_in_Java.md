## Approach

The best way to prevent LDAP injection is to use a positive validation
scheme for ensuring that the data going into your queries doesn't
contain any attacks. You can read more in [the OWASP Development
Guide](:Category:OWASP_Guide_Project "wikilink") about input validation.

However, in some cases, it is necessary to include special characters in
input that is passed into an LDAP query. In this case, using escaping
can prevent the LDAP interpreter from thinking those special characters
are actually LDAP query. Rather, the encoding lets the interpreter treat
those special characters as data.

Here are a few methods for escaping certain meta-characters in LDAP
queries. Both the distinguished name (DN) and the search filter have
their own sets of meta-characters. In the case of Java, it is also
necessary to escape any JNDI meta-characters, since java uses JNDI to
perform LDAP queries.

`   public static String escapeDN(String name) {`
`       StringBuffer sb = new StringBuffer(); // If using JDK >= 1.5 consider using StringBuilder`
`       if ((name.length() > 0) && ((name.charAt(0) == ' ') || (name.charAt(0) == '#'))) {`
`           sb.append('\\'); // add the leading backslash if needed`
`       }`
`       for (int i = 0; i < name.length(); i++) {`
`           char curChar = name.charAt(i);`
`           switch (curChar) {`
`               case '\\':`
`                   sb.append("\\\\");`
`                   break;`
`               case ',':`
`                   sb.append("\\,");`
`                   break;`
`               case '+':`
`                   sb.append("\\+");`
`                   break;`
`               case '"':`
`                   sb.append("\\\"");`
`                   break;`
`               case '<':`
`                   sb.append("\\<");`
`                   break;`
`               case '>':`
`                   sb.append("\\>");`
`                   break;`
`               case ';':`
`                   sb.append("\\;");`
`                   break;`
`               default:`
`                   sb.append(curChar);`
`           }`
`       }`
`       if ((name.length() > 1) && (name.charAt(name.length() - 1) == ' ')) {`
`           sb.insert(sb.length() - 1, '\\'); // add the trailing backslash if needed`
`       }`
`       return sb.toString();`
`   }`

Escaping the search filter:

`   public static final String escapeLDAPSearchFilter(String filter) {`
`       StringBuffer sb = new StringBuffer(); // If using JDK >= 1.5 consider using StringBuilder`
`       for (int i = 0; i < filter.length(); i++) {`
`           char curChar = filter.charAt(i);`
`           switch (curChar) {`
`               case '\\':`
`                   sb.append("\\5c");`
`                   break;`
`               case '*':`
`                   sb.append("\\2a");`
`                   break;`
`               case '(':`
`                   sb.append("\\28");`
`                   break;`
`               case ')':`
`                   sb.append("\\29");`
`                   break;`
`               case '\u0000': `
`                   sb.append("\\00"); `
`                   break;`
`               default:`
`                   sb.append(curChar);`
`           }`
`       }`
`       return sb.toString();`
`   }`

Test class:

`       //escapeDN`
`       assertEquals("No special characters to escape", "Helloé", escapeDN("Helloé"));`
`       assertEquals("leading #", "\\# Helloé", escapeDN("# Helloé"));`
`       assertEquals("leading space", "\\ Helloé", escapeDN(" Helloé"));`
`       assertEquals("trailing space", "Helloé\\ ", escapeDN("Helloé "));`
`       assertEquals("only 3 spaces", "\\  \\ ", escapeDN("   "));`
`       assertEquals("Christmas Tree DN", "\\ Hello\\\\ \\+ \\, \\\"World\\\" \\;\\ ", Test.escapeDN(" Hello\\ + , \"World\" ; "));`

`       assertEquals("No special characters to escape", "Hi This is a test #çà", SecTool.escapeLDAPSearchFilter("Hi This is a test #çà"));`
`       assertEquals("LDAP Christams Tree", "Hi \\28This\\29 = is \\2a a \\5c test # ç à ô", SecTool.escapeLDAPSearchFilter("Hi (This) = is * a \\ test # ç à ô"));`

[Category:Java](Category:Java "wikilink")