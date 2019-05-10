## Description

An API is a contract between a caller and a callee. The most common
forms of API abuse are caused by the caller failing to honor its end of
this contract. For example, if a program fails to call chdir() after
calling chroot(), it violates the contract that specifies how to change
the active root directory in a secure fashion. Another good example of
library abuse is expecting the callee to return trustworthy DNS
information to the caller. In this case, the caller abuses the callee
API by making certain assumptions about its behavior (that the return
value can be used for authentication purposes). One can also violate the
caller-callee contract from the other side. For example, if a coder
subclasses SecureRandom and returns a non-random value, the contract is
violated.

[Category:Vulnerability](Category:Vulnerability "wikilink")