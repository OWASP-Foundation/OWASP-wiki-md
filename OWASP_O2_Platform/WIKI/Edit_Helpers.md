### Standard template

standard footer: When creating new pages add the following template tag
to the bottom of the page (this will append the link to the main OWASP
O2 Platform page:

    {{:OWASP_O2_Platform/WIKI/bottom}}

  - usage:

<!-- end list -->

```
When no variable is set, the template will be shownn

{{:OWASP_O2_Platform/WIKI/bottom}}


When the noShow is set to an empty value,  the template will NOT be shown

 {{:OWASP_O2_Platform/WIKI/bottom
| noshow=}}
```

  - Wiki template code in page [OWASP O2
    Platform/WIKI/bottom](OWASP_O2_Platform/WIKI/bottom "wikilink")

<!-- end list -->

    {{{noshow
    |
    -----
    go back to the main [[OWASP_O2_Platform|OWASP O2 Platform]] page

    [[Category:OWASP_O2_Platform|Category:OWASP_O2_Platform]]
    | aaaa
    }}}

## WIKI redirects

use \#Redirect

for example

    #Redirect [[OWASP_O2_Platform|OWASP O2 Platform]]

## mark as WIKI Stub page

    {{template:Stub}}