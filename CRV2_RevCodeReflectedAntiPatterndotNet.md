The classes in the System.Reflection namespace and with System.Type,
enable us to obtain information about loaded assemblies and the types
defined within them, such as classes, interfaces, and value types.
Reflection can be used to create type instances at run time, and to
invoke and access them.

Depending on the .Net framework version, the use of Reflection could
represent a major security risk.

The risk with using Reflection is that the original application code
could be replaced by malicious code. The use of .NET framework 4 and on
offers a higher level of protection since only trusted code can use
reflection to access security-critical members. Furthermore, only
trusted code can use reflection to access nonpublic members that would
not be directly accessible to compiled code. Finally, code that uses
reflection to access a safe-critical member must have whatever
permissions the safe-critical member demands, just as with compiled
code.

For other .NET framework versions beneath version 4, there are important
recommendations to follow

## Recommendations

### Avoid writing public APIs that take MethodInfo parameters

Avoid it especially for highly trusted code. Such APIs might be more
vulnerable to malicious code. For example, consider a public API in
highly trusted code that takes a MethodInfo parameter. Assume that the
public API indirectly calls the Invoke method on the supplied parameter.
If the public API does not perform the necessary permission checks, the
call to the Invoke method will always succeed, because the security
system determines that the caller is highly trusted. Even if malicious
code does not have the permission to directly invoke the method, it can
still do so indirectly by calling the public API.

### using ReflectionPermission class

To discover information about nonpublic members, callers must have the
ReflectionPermission that represents the ability to obtain type
information. Without this permission, code cannot use reflection to
obtain information about nonpublic members (even of its own class)
through the Get methods on Type, Assembly, and Module.(MSDN)

To use reflection to invoke methods or access fields that are
inaccessible according to the common type system accessibility rules,
the code must be granted the ReflectionPermission for member access.

### security policy deny ReflectionPermission to code that originates from the Internet

Because ReflectionPermission can provide access to non-public types and
members,it is recommend that you do not grant ReflectionPermission to
Internet code, except with the
ReflectionPermissionFlag.RestrictedMemberAccess flag.
RestrictedMemberAccess allows access to non-public members, with the
restriction that the grant set of the non-public members must be equal
to, or a subset of, the grant set of the code that accesses the
non-public members.

### Reference

MSDN, "ReflectionPermission Class" available at
<http://msdn.microsoft.com/library/system.security.permissions.reflectionpermission(v=vs.110>).aspx