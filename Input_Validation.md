

Using black and/or white lists which defines valid input data. Such
approach is more accurate and provides better risk analysis, when there
is need of modification of the lists.

E.g. When we expect digits as an input, then we should perform accurate
input data validation.

```

#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main(int argc, char **argv)
{
       char a[256];
       strncpy(a, argv[1], sizeof(a)-1);

       int b=0;

       for(b=0; b<strlen(a); b++) {
               if(isdigit((int)a[b])) printf("%c", a[b]);
       }

       printf("\n");
       return 0;
}
```

In PHP for input data validation we may use e.g. preg_match() function:

    <?php
      $clean = array();
      if (preg_match("/^[0-9]+:[X-Z]+$/D", $_GET['var'])) {
         $clean['var'] = $_GET['var'];
      }
    ?>

For special attention deserves modifier "/D", which additionally
protects against HTTP Response Splitting type of attacks.

Avoid using of environment variables if the attacker may alter their
values.

Check [:Category:Input
Validation](:Category:Input_Validation "wikilink") for contents

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category: Control](Category:_Control "wikilink") [Category:Input
Validation Control](Category:Input_Validation_Control "wikilink")