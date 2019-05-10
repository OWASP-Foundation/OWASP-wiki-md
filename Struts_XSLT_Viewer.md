Here is a quick'n'dirty xslt transformations to quickly visualize Struts
config files (very useful on security audits)

Dinis note: Java guys, please edit and link to the correct place

## sample_struts.xml

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<?xml-stylesheet type="text/xsl" href="strutsBasicMapping.xslt"?>

<!-- general USER mappings -->
<struts-config>
</struts-config>
```

## strutsBasicMapping.xslt

```

 <?xml version="1.0" encoding="UTF-8"?>
 <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xsl:output version="1.0" encoding="utf-8" omit-xml-declaration="no" indent="no" media-type="text/html"/>
    <xsl:template match="/struts-config">
        <html>
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
            <head>
                <style>
                        body { font-family: Arial; font-size: 14 }
                        b  { font-family: Arial;}
                        a { text-decoration: none}
                        i { font-family: verdana}
                        td { font-family: Arial; font-size: 11 }
                        li { font-family: Arial; font-size: 11 }
                        .td_small_font { font-family: Arial; font-size: 11 }
                        .td_LHS_Menu { font-family: Arial; font-size: 11; font-weight: bold; color: white; text-decoration: none}
                        .title { font-family: Arial; font-size: 22}
                        .smallItalic { font-family: verdana; font-size: 08; font-weight: normal;}
            </style>
            </head>

            <body>
                <h1>
                    <span style="font-family:@Arial Unicode MS; font-weight:bold; ">struts-config Basic Mappings</span>
                </h1>
                <br/>
                <h2>Form Beans</h2>
                <table border="1">
                    <tbody>
                        <tr bgcolor="navy">
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">Form Bean name</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">Form Bean properties</span>
                            </td>
                        </tr>
                        <xsl:for-each select="form-beans/form-bean">
                          <tr>
                            <td valign="top">
                                <b><xsl:value-of select="@name"/></b>
                            </td>
                            <td>
                                <ul><xsl:for-each select="form-property">
                                    <li>
                                        <b><xsl:value-of select="@name"/></b>
                                        : <xsl:value-of select="@type"/>
                                        <xsl:if test="count(@initial)>0">
                                            (initial = <xsl:value-of select="@initial"/>)
                                        </xsl:if>
                                    </li>
                                </xsl:for-each></ul>
                            </td>
                          </tr>
                        </xsl:for-each>
                    </tbody>
                </table>
                <br/>
                <h2> global-forwards</h2>
                <table border="1" width="100%">
                    <tbody>
                        <tr bgcolor="navy">
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">name</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">path</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">redirect</span>
                            </td>
                        </tr>

                        <xsl:for-each select="global-forwards/forward">
                          <tr>
                            <td valign="top">
                                <b><xsl:value-of select="@name"/></b>
                            </td>
                            <td valign="top">
                                <xsl:value-of select="@path"/>
                            </td>
                            <td valign="top">
                                <xsl:value-of select="@redirect"/>
                            </td>

                          </tr>
                        </xsl:for-each>
                    </tbody>
                </table>
                <br/>
                <h2>action-mappings</h2>
                <table border="1">
                    <tbody>
                        <tr bgcolor="navy">
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">path</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">name</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">validate</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">parameter</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">type</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">scope</span>
                            </td>
                            <td>
                                <span style="color:#FFFFFF; font-family:@Arial Unicode MS; font-weight:bold; ">Forward</span>
                            </td>
                        </tr>

                        <xsl:for-each select="action-mappings/action">
                          <tr>
                            <td valign="top">
                                <b><xsl:value-of select="@path"/></b>
                            </td>
                            <td valign="top">
                                <b><xsl:value-of select="@name"/></b>
                            </td>
                            <td valign="top">
                                <b><xsl:value-of select="@validate"/></b>
                            </td>
                            <td valign="top">
                                <b><xsl:value-of select="@parameter"/></b>
                            </td>
                            <td valign="top">
                                <b><xsl:value-of select="@type"/></b>
                            </td>
                            <td valign="top">
                                <b><xsl:value-of select="@scope"/></b>
                            </td>
                            <td>
                                <ul><xsl:for-each select="forward">
                                    <li>
                                        <b><xsl:value-of select="@name"/></b>
                                        : <xsl:value-of select="@path"/> : <xsl:value-of select="@redirect"/>
                                    </li>
                                </xsl:for-each></ul>
                            </td>
                          </tr>
                        </xsl:for-each>
                    </tbody>
                </table>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
```

[Category:Java](Category:Java "wikilink")