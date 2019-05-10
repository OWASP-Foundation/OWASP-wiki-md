Change log of current development version: [ORG (Owasp Report Generator)
- Change Log](ORG_\(Owasp_Report_Generator\)_-_Change_Log "wikilink")

## ORG To-do

Note: This section needs better formating

**Current Main To-Do list**

**\* Number Difficulty Priority Request**

  - *6 Intermediate High* Verify all current data against a schema and
    ensure that consistency is maintained (especially with IP Address /
    DNS Name fields)
  - *16 Minor High* Change the window menu to have the current open
    windows in the actual menu, rather than as a sub menu
  - *17 Intermediate Low* Add a find function to the source code editor
  - *22 Minor Low* Correct redundancy of report reviewers now that we
    have a document information page (remove these redundant tags)
  - *23 Minor Low* Verify metadata that we currently store is correct
    and valuable
  - *24 Minor Low* Correct spelling of confidenciality Rating in
    document information page
  - *5 Intermediate Medium* Enable verification against a schema within
    the tool to ensure that data is of a consistent form
  - *9 Intermediate Medium* Add a drop down menu to the findings screen
    to allow for the selection of a recommendation from the
    recommendations database
  - *13 Intermediate Medium* Create a Microsoft Word version of the
    report
  - *20 Intermediate Medium* Paste tables into Appendix
  - *21 Intermediate Medium* Paste images into Appendix
  - Add SpellCheking capabilities (using Authentic's component support
    for it)
  - Add support for saving GUI Settings (for example the Spliter sizes)
  - Fix bugs in additional details. Hitting return doesn't not enter a
    newline.
  - When adding a finding like "Bug found @ hehe/hehe.aspx" it does not
    work because of the information entered in (it doesn't like the
    "/"). Need to validate and sanitize the information.
  - Write unit tests

## ORG To-do (in table format)

**Priority High**

<table>
<caption>TODO</caption>
<thead>
<tr class="header">
<th><p>ID</p></th>
<th><p>Task</p></th>
<th><p>Comment</p></th>
<th><p>Complexity</p></th>
<th></th>
<th><p>Assigned</p></th>
<th><p>Status</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td><p>Issues with new Authentic 2007 OCX control</p></td>
<td></td>
<td><ul>
<li>Report Contents SPS is not working (conflict with XSD) ,</li>
<li>Keyboard hock not working properly (in axActiveAuthenticControl.@event.ctrlKey , axActiveAuthenticControl.@event.ctrlKey doesn't contain the correct value (i.e. in the case where is ctrlKey pressed and ctrlKey should be true)</li>
</ul></td>
<td></td>
<td><p>Medium</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><p>Enable templates in executive summary to save copying and pasting in new projects</p></td>
<td></td>
<td><p>There is an easy and a hard way to do this. The easy is to implement this using template xml files which are copied to the target location (for example a finding or 'Report Content') from a default location (in the current plan the output of a plug-in). The hard way (but much more powerfull) will be to implement this templates using dinamic manipulation of the autentic object (which is something that I haven't figure out how to do)</p></td>
<td></td>
<td><p>Medium</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><p>Convert Export functionality into a Plug-in</p></td>
<td></td>
<td><p>Should be easy to do since all code is already there</p></td>
<td></td>
<td><p>Low</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><p>Verify all current data against a schema and ensure that consistency is maintained (especially with IP Address / DNS Name fields)</p></td>
<td></td>
<td><p>Basicaly the issue here is that everytime an xml file is saved, a quick check to the schema should be made. The code to do this already exists (it is in the export data code). This can be done using the authentic component. No need to write code. - Mike</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

**Priority Medium**

|   |                                                                      |         |                                                   |  |          |        |
| - | -------------------------------------------------------------------- | ------- | ------------------------------------------------- |  | -------- | ------ |
|   | Task                                                                 | Comment | Complexity                                        |  | Assigned | Status |
| 1 | Add a default profile with the project files maped to the local disk |         | this way the first time user can just click Start |  |          |        |

**Priority Low**

|  |      |                                                                  |            |                                                                                                                                                                                                                                   |          |         |
|  | ---- | ---------------------------------------------------------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------- |
|  | Task | Comment                                                          | Complexity |                                                                                                                                                                                                                                   | Assigned | Status  |
|  |      | generated Pdf reports don't appear in the respective ORG window. |            | \[DC\]: this doesn't occour all the time and it is due to the fact that the current way used to display the pdf is to open it in the embebed IE control (which sometimes opens the pdf inside it and others in an external window |          | no idea |
|  |      | Remember the UI dimensions for every window when it closes.      |            | The windows need to remember how they were set so that the next time the program is ran people do not have to resize the windows again. This would be a nice usability addition                                                   |          | easy    |

|- \! x | | {Template} | | {...} | | Medium | | Not Assigned

**To Map to Priority Tables**

<table>
<tbody>
<tr class="odd">
<td></td>
<td><p>Task</p></td>
<td><p>Comment</p></td>
<td><p>Assigned</p></td>
<td><p>Status</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Del Key should delete newline (and other elements)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Add ability to move findings to other targets</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Sort of tracking views by Issue ID</p></td>
<td></td>
<td><p>Enable sorting in the issue tracking screens, to enable easier finding of issues when retests are occurring</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>Search (for Issue IDs)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>Select contacts from a db</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>Automatic Import data (like DSN info)</p></td>
<td></td>
<td><p>This can also include task / default messages with links to areas like the OWASP vulnerability pages</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Data feed for global database spreadsheets</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>Sign application and FOP engine</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>Ensure that within the same project, image folders are unique</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>Add Backup feature for XSLT changes</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p>Add upgrade tool</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p>Add XSLT search feature</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>Project level tags</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p>Image's path are hardcoded on the PDF xslt</p></td>
<td></td>
<td><ul>
<li>Monthly CISO Report.xslt</li>
<li>test.xslt</li>
<li>Bespoke Brief.xslt</li>
<li>Monthly RISO Report.xslt</li>
<li>Outstanding Issues.xslt</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td><p>16</p></td>
<td><p>Document the installation procedure of the Altova XML engine (used for xslt2 queries)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>17</p></td>
<td><p>Add to FAQ the fact that the errors that show on the current main FOP transformation are ok</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>18</p></td>
<td><p>Convert the current xslt/FOP to the altova engine so that we can use xslt2 queries</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>19</p></td>
<td><p>Modify the tabs on the "Current and Archived Projects" screen so that whenever you click on one it reloads the data</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>20</p></td>
<td><p>Only show up tabs that we have the data set up for</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>21</p></td>
<td><p>Remove all those empty try/catches in authentic.cs</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>23</p></td>
<td><p>Create a Microsoft Word report option</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>24</p></td>
<td><p>Perform a validation against a schema of all current _consolidatedReports files to ensure they are compliant (check in particular dates, IPs and DNS names)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>25</p></td>
<td><p>Manage the exceptions that occur when you add a finding with a duplicate name more effectively</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>26</p></td>
<td><p>Change the Window menu to have the current open windows in the main menu, rather than as a sub menu</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>27</p></td>
<td><p>Add a find function to the source code editor</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>28</p></td>
<td><p>Add drop down menus to the recommendations section (which links to the recommendations database)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>29</p></td>
<td><p>Enable schema-safe copy and paste between the project meta data tab and the executive summary tab (the xml attribute copying bug)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>30</p></td>
<td><p>Allow for defaults and templates to be used (especially in the executive summary where all executive summaries should follow the same format)</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>31</p></td>
<td><p>Add in unit tests</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>32</p></td>
<td><p>Implement the deleting of issue xml file</p></td>
<td></td>
<td><p>Currently in issue tracking there is a delete button that has not been implemented. Also, on the "Report PDF" tab of the projects form there is a button that will create the issue tracking file which errors out if a version of the file has already been created.</p></td>
<td></td>
</tr>
</tbody>
</table>

## To add to to-do

  - Default headers auto populated in "Report Contents". Executive
    Summary, Background, Scope
  - Paste tables into Appendix
  - Paste images into Appendix
  - Bug report, sequence of events:
      - do findings
      - then do exec sumamry
      - then make a pdf
      - then try to change a finding (exception will occur)
      - if you reload the project the issue will go away
  - feature: in the reports -\> 2. choose a data filter: add the
    capabilty to define extraparameters for the external xslt
    transformation (this is needed for the new XSLT 2 xslts)

## TODO Future Versions

  - Add in the ability to import in stock findings
  - Add in tool tips to the forms.

-----

back to [ORG (Owasp Report
Generator)](ORG_\(Owasp_Report_Generator\) "wikilink")