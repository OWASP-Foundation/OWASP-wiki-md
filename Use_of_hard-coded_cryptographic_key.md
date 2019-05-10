## Overview

The use of a hard-coded cryptographic key tremendously increases the
possibility that encrypted data may be recovered

## Consequences

  - Authentication: If hard-coded cryptographic keys are used, it is
    almost certain that malicious users will gain access through the
    account in question.

## Exposure period

  - Design: For both front-end to back-end connections and default
    account settings, alternate decisions must be made at design time.

## Platform

  - Languages: All

<!-- end list -->

  - Operating platforms: All

## Required resources

Any

## Severity

High

## Likelihood of exploit

High

## Avoidance and mitigation

  - Design: Prevention schemes mirror that of hard-coded password
    storage.

## Discussion

The main difference between the use of hard-coded passwords and the use
of hard-coded cryptographic keys is the false sense of security that the
former conveys. Many people believe that simply hashing a hard-coded
password before storage will protect the information from malicious
users. However, many hashes are reversible (or at least vulnerable to
brute force attacks) - and further, many authentication protocols simply
request the hash itself, making it no better than a password.

## Examples

In C\\C++:

    int VerifyAdmin(char *password) {
      if (strcmp(password,"68af404b513073584c4b6f22b6c63e6b")) {
        printf("Incorrect Password!\n");
        return(0)
      }

      printf("Entering Diagnostic Mode�\n");
      return(1);
    }

In Java:

    int VerifyAdmin(String password) {

      if (passwd.Eqauls("68af404b513073584c4b6f22b6c63e6b")) {
        return(0)
      }
      //Diagnostic Mode
      return(1);
    }

## Related problems

  - [Use of hard-coded password](Use_of_hard-coded_password "wikilink")

[Category:Cryptographic
Vulnerability](Category:Cryptographic_Vulnerability "wikilink")