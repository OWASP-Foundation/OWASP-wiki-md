#### Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

At the moment exchanging data between pentest tools it is far too
difficult.

So ... the purpose of this project is to define a simple, open format
for exchanging data between pentest tools\!

Involvement is encouraged, so if you would like to contribute to this
project then please join the [mailing
list](https://lists.owasp.org/mailman/listinfo/owasp-data-exchange-format)
and / or contact one of the project leaders.

At the moment this project is hosted at GitHub:
<https://github.com/TomStageDK/OWASP-DEF>

New Project leader [Tom Stage](User:Tom_Stage "wikilink"), and I am
working on updating this Wiki, and I will do so when I have the time.

Old Project Leader(s) Contact [Simon](User:Psiinon "wikilink") or
[Dinis](User:Dinis_Cruz "wikilink").

### Requirements

The format must be open, and licensed so that it can be adopted by all
products, whether open, closed, free or commercial.

It must be as simple to adopt as possible, and ideally based on existing
open formats.

#### Roadmap

The high level roadmap is:

1.  Tom Stage to document a strawman proposal
2.  Map known XML format outputs from known vulnerability scanners to
    the strawman, and if these can not be mapped document / implement
    changes to the strawman.
3.  All - rip the strawman to pieces and agree an improved format
4.  Finalize DEF v1.0
5.  Supporting project leaders to adopt the format in their tools
6.  Publicize and drive adoption in other tools
7.  Learn from our experiences and start on the next version, repeat ;)

#### Strawman

The strawman as it looks today (03-06-2014), for the latest strawman
visit the above GitHub page.

This tab documents a strawman proposal for all concerned to rip to
pieces :)

This Strawman supports 3 different types of scans, these are: Dynamic,
Static and Info

    <?xml version="1.0"?>
    <OWASP-DEF SpecVersion="0.1">
        <Session-Reference>Scan specific reference</Session-Reference>
        <Date-Time>Date and time the session was started</Date-Time>
        <Scan type="dynamic">
            <Host name="Hostname" ip-address="Either IPv4 or IPv6 Address">
                <Port protocol="The Protocol used" portid="The Port Number">
                    <Service name="Name of the Service" product="Product Name" version="Product Version" />
                    <Software-Name>Name of the tool that found the issue</Software-Name>
                    <Software-Version>Version of the tool that found the issue</Software-Version>
                    <Software-Arguments>Arguments used to perform the scan</Software-Arguments>
                    <Software-Additional>
                        <Data name="The name">Value of the Additional Data</Data>
                    </Software-Additional>
                    <Vulnerability Severity="The Severity">
                        <Finding NativeID="The internal Test ID" IdentifiedTimestamp="DateTime stamp for when we found this vulnerability" UniqueID="The Software unique ID for this Finding">
                            <Summary>A sort (one line) description</Summary>
                            <Description>More detailed description</Description>
                            <Confidence>One of an agreed list of values</Confidence>
                            <Background>More info on the type of issue</Background>
                            <Remediation>Advise on how to fix the issue</Remediation>
                            <Further-Information>
                                <Further-Info name="The name" url="The URL to further information" />
                            </Further-Information>
                            <Classifications>
                                <Classification type="The Classification System" id="Classification ID" href="The URL to the Classification description">The Title for the Clasasification</Classification>
                            </Classifications>
                            <Additional-Data>
                                <Data name="The name">Value of the Additional Data</Data>
                            </Additional-Data>
                            <Page>
                                <Page-Reference>Product specific reference e.g. Page Title</Page-Reference>
                                <URL>The UTL that the Vulnerability was found on</URL>
                                <Method>HTTP method (GET, POST, etc)</Method>
                                <HTTPVersion>The HTTP Version</HTTPVersion>
                                <StatusCode>The HTTP Status code</StatusCode>
                                <Language>The detected Language of the Web Application</Language>
                                <Parameters>
                                    <Parameter>The parameter the vulnerability was found with</Parameter>
                                </Parameters>
                                <Request-Response>
                                    <Request>
                                        <Request-Raw>The RAW HTTP Request</Request-Raw>
                                        <Request-Headers>
                                            <Data name="The name of the Header Data">The value for the Header Data</Data>
                                        </Request-Headers>
                                        <Request-Cookie>
                                            <Data name="The name of the Cookie Data">The value for the Cookie Data</Data>
                                        </Request-Cookie>
                                        <Additional-RequestData>
                                            <Data name="The name of the Additional Data">The value for the Additional Data</Data>
                                        </Additional-RequestData>
                                    </Request>
                                    <Response>
                                        <Response-Raw>The RAW HTTP Response</Response-Raw>
                                        <Response-Headers>
                                            <Data name="The name of the Header Data">The value for the Header Data</Data>
                                        </Response-Headers>
                                        <Response-Cookie>
                                            <Data name="The name of the Cookie Data">The value for the Cookie Data</Data>
                                        </Response-Cookie>
                                        <Additional-ResponseData>
                                            <Data name="The name of the Additional Data">The value for the Additional Data</Data>
                                        </Additional-ResponseData>
                                        <Response-ScreenShot>Base64 Encoded Screen Shot</Response-ScreenShot>
                                    </Response>
                                </Request-Response>
                            </Page>
                        </Finding>
                    </Vulnerability>
                </Port>
            </Host>
        </Scan>
        <Scan type="static">
            <Software-Name>The name of the Software that did the scan</Software-Name>
            <Software-Version>The version of the Software that did the scan</Software-Version>
            <Software-Arguments>Arguments used to perform the scan</Software-Arguments>
            <Software-Additional>
                <Data name="The name">Value of the Additional Data</Data>
            </Software-Additional>
            <Vulnerability Severity="The Severity">
                <Finding NativeID="The internal Test ID" IdentifiedTimestamp="DateTime stamp for when we found this vulnerability" UniqueID="The Software unique ID for this Finding">
                    <Summary>A sort (one line) description</Summary>
                    <Description>More detailed description</Description>
                    <Confidence>One of an agreed list of values</Confidence>
                    <Background>More info on the type of issue</Background>
                    <Remediation>Advise on how to fix the issue</Remediation>
                    <Further-Information>
                        <Further-Info>More information about this specific issue</Further-Info>
                    </Further-Information>
                    <Classifications>
                        <Classification type="The Classification System" id="Classification ID" href="The URL to the Classification description">The Title for the Classification</Classification>
                    </Classifications>
                    <DataFlowElement SourceFileName="The path and filename of the file the vulnerability was found in" LineNumber="The line number" ColumnNumber="The Colum number" Sequence="The sequence">
                        <LineText>The line where the vulnerability was found (This could be with X number of lines around it)</LineText>
                    </DataFlowElement>
                </Finding>
            </Vulnerability>
        </Scan>
        <Scan type="info">
            <Software-Name>Name of the tool that found the issue</Software-Name>
            <Software-Version>Version of the tool that found the issue</Software-Version>
            <Software-Arguments>Arguments used to perform the scan</Software-Arguments>
            <Software-Additional>
                <Data name="The name">Value of the Additional Data</Data>
            </Software-Additional>
            <Host name="Hostname" ip-address="Either IPv4 or IPv6 Address">
                <Scan-Info>
                    <Data name="Scan Info name">The value for the Scan-Info Data</Data>
                </Scan-Info>
                <Port protocol="tcp / udp" portid="The Port Number">
                    <Service name="Name of the Service" product="Product Name" version="Product Version" />
                    <Scan-Data>
                        <Data name="Name of the Scan Data">The value for the Scan Data</Data>
                    </Scan-Data>
                </Port>
            </Host>
        </Scan>
    </OWASP-DEF>

#### Supporting projects

The following project leaders have agreed to support this format and
(once it has been agreed) adopt it within their projects.

If you would like your project added to this list then feel free to
update it, or contact one of the project leaders to update it for you.

| scope="col"                                                                       | Project                                                 | scope="col" | Leader |
| --------------------------------------------------------------------------------- | ------------------------------------------------------- | ----------- | ------ |
| [Burp Suite](http://portswigger.net/burp/)                                        | Dafydd Stuttard (PortSwigger)                           |             |        |
| [O2 Platform](https://www.owasp.org/index.php/OWASP_O2_Platform)                  | [Dinis Cruz](User:Dinis_Cruz "wikilink")                |             |        |
| [WebScarab](https://www.owasp.org/index.php/Category:OWASP_WebScarab_Project)     | [Daniel Brzozowski](User:Daniel_Brzozowski "wikilink")  |             |        |
| [Zed Attack Proxy](http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) | [Simon Bennetts (Psiinon)](User:Psiinon "wikilink")     |             |        |
| [Yasca](http://www.owasp.org/index.php/OWASP_Yasca_Project)                       | [Michael Scovetta (Scovetta)](User:Scovetta "wikilink") |             |        |

#### Project About


__NOTOC__ <headertabs />

[Data Exchange Format Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")