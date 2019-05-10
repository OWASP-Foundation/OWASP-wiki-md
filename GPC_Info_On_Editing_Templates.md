for an example of this in action see
[OWASP_Project_Details_Table](OWASP_Project_Details_Table "wikilink")
which uses the
[Template:OWASP_Project_Details_Row](Template:OWASP_Project_Details_Row "wikilink")
to create the row table from each project information page, for example:

  - [Template:Project Details/OWASP Flash Security
    Project](Template:Project_Details/OWASP_Flash_Security_Project "wikilink")
  - [Template:Project Details/OWASP Live
    CD](Template:Project_Details/OWASP_Live_CD "wikilink")

The content should be on a page called: GPC_Project_Details/{project
name} , for example the content for the [:Category:OWASP XML Security
Gateway Evaluation Criteria
Project](:Category:OWASP_XML_Security_Gateway_Evaluation_Criteria_Project "wikilink")
should be at the page [GPC_Project_Details/OWASP XML Security Gateway
Evaluation
Criteria](GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria "wikilink")
and you have to make sure that the template is set to:

```

  {{Template:<includeonly>{{{1}}}</includeonly><noinclude>OWASP Project Identification Tab</noinclude>

| project_name = OWASP XML Security Gateway Evaluation Criteria Project

| project_description =
 .....
 }}
 __NOTOC__ <headertabs />
```

The good news of the way this template is now set-up is that the user
can view the 'template driven page' with a nice table format
[GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria](GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria "wikilink")
and at the same time we can use that same information on other pages,
for example on
[OWASP_Project_Details_Table](OWASP_Project_Details_Table "wikilink")
by simply pointing to the content page and the template to use:

```
 {{:GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria
| OWASP Project Details Row}}
```

what the above line is doing is transforming the content of
[GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria](GPC_Project_Details/OWASP_XML_Security_Gateway_Evaluation_Criteria "wikilink")
with the template [template:OWASP Project Details
Row](template:OWASP_Project_Details_Row "wikilink") Note the : on the
GPC_Project_Details since without it the name has to start with
Template, for example: Template:GPC_Project_Detail