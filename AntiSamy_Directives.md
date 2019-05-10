This page explains the purpose of the "directives" in AntiSamy policy
files, and what support they have in different versions.

<table>
<thead>
<tr class="header">
<th><p>align="center"</p></th>
<th><p>Directive<br />
</p></th>
<th><p>align="center"</p></th>
<th><p>Type<br />
</p></th>
<th><p>align="center"</p></th>
<th><p>Default Value<br />
(in Java)<br />
</p></th>
<th><p>align="center"</p></th>
<th><p>Supported in AntiSamy Java?<br />
</p></th>
<th><p>align="center"</p></th>
<th><p>Supported in AntiSamy .NET?<br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>useXHTML<br />
</strong>When this feature is on, AntiSamy will output the sanitized data in XHTML format as opposed to just regular HTML.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>false<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>omitXMLDeclaration</strong><br />
When "useXHTML" is turned on, AntiSamy will automatically prepend the XML header. Enabling this feature will tell AntiSamy not to do that.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>true<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>formatOutput</strong><br />
When enabled, AntiSamy will automatically format the output according to some basic rules and indentation. Kind of like "pretty print."<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>true<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>maxInputSize</strong><br />
This directive specifies the maximum size (in bytes) of user input before it's validated.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>integer<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>100K<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>embedStyleSheets</strong><br />
When the developer chooses to allow CSS, this directive will specify whether or not remote stylesheets found referenced in the user's input will be pulled down and embedded into the current user input.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>false<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>maxStyleSheetImports</strong><br />
This feature allows developers to specify how many remote stylesheets can be downloaded from any one input.</p></td>
<td><p>align="center"</p></td>
<td><p>integer</p></td>
<td><p>align="center"</p></td>
<td><p>1</p></td>
<td><p>align="center"</p></td>
<td><p>Yes</p></td>
<td><p>align="center"</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>connectionTimeout</strong><br />
When "embedStyleSheets" is enabled, this timeout value (in milliseconds) will be used when fetching the offsite resource in question. This should be used to prevent validation threads from blocking when connecting to 3rd party systems that may purposefully act really, really slowly.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>integer<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>1K<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>preserveComments</strong><br />
When enabled, AntiSamy will keep HTML comments supplied in the input.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>false<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>nofollowAnchors</strong><br />
When enabled, AntiSamy will append <em>rel="nofollow"</em> attributes to all anchor (<a>) tags supplied in the input. This is useful for telling search engines not to associate your site with sites that are under the control of your users.<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>false<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>validateParamAsEmbed</strong><br />
When enabled, AntiSamy will treat attributes of</p>
<embed>
<p>tags in the policy the same as any <param> tags nested inside the the</p>
<embed>
<p>. This allows users to, according to policy, pass in data in either of those two methods with equal security. This is needed for sites that allow users to supply videos, etc.</p></td>
<td><p>align="center"</p></td>
<td><p>boolean<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>false<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>Yes<br />
</p></td>
<td><p>align="center"</p></td>
<td><p>No<br />
</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><strong>preserveSpace</strong><br />
When enabled, this feature is intended to preserve spaces as specified in the input without normalization. Right now it only works as according to <a href="http://xerces.apache.org/xerces-j/apiDocs/org/apache/xml/serialize/OutputFormat.html#setPreserveSpace%28boolean%29">this method</a>.</p></td>
<td><p>align="center"</p></td>
<td><p>boolean</p></td>
<td><p>align="center"</p></td>
<td><p>false</p></td>
<td><p>align="center"</p></td>
<td><p>Yes</p></td>
<td><p>align="center"</p></td>
<td><p>No</p></td>
<td></td>
</tr>
</tbody>
</table>