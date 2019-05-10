__TOC__

## Flash Applications

Look for potential Flash redirect issues.

`clickTAG`
`TextField`
`TextArea`
`load`
`getURL`
`NetConnection.connect`
`NetServices.createGatewayConnection`
`NetSteam.play`
`XML.send`

## SandBox Security Model

**Flash player assigns SWF files to sandboxes based on their origin.**

**Internet SWF files sandboxed based on origin domains**

**Domain:** - Any two SWF files can interact together within the same
sandbox. - Explicit permission is required to interact with objects in
other sandboxes.

**Local**

**local-with-filesystem (default)** - The file system can read from
local files only

**local-with-networking** - Interact with other local-with-networking
SWF files

**local-trusted** - Can read from Local files, communicate to any server
and access any SWF file.

“The sandbox defines a limited space in which a Adobe Flash movie
running within the Adobe Flash Player is allowed to operate. Its primary
purpose is to ensure the integrity and security of the client’s machine,
and as well as security of any Adobe Flash movies running in the
player.”

Cross Domain Permissions: A Flash movie playing on a web browser is not
allowed access that is outside the exact domain from which it
originated. This is defined in the cross-domain policy file
crossdomain.xml. Policy files are used by Flash to permit Flash to load
data from servers other than its native domain. If a SWF file wishes to
communicate with remote servers it must be granted explicit permission:

<cross-domain-policy>` `
`    `<allow-access-from domain="example.domain.com"/>
</cross-domain-policy>

The API call System.security.loadPolicyFile(url) loads a cross domain
policy from a specified URL which may be different from the
crossdomain.xml file.

## Accessing JavaScript

A parameter called allowScriptAccess governs if the Flash object has
access to external scripts. It can have three possible values: **never,
same domain, always.** The default value is **sameDomain** which means
that the SWF must be hosted on the same FQDN as the calling HTML in
order to have access to the HTML's DOM. If allowScriptAccess is set to
**always** then the SWF is granted access to the HTML's DOM regardless
of where the SWF is hosted.

` `<object id="flash007">` `
`   `<param name=movie value="bigmovie.swf">
`   `

<embed AllowScriptAccess="'''always'''" name='flash007' src="bigmovie.swf"  type="application/x-shockwave-flash">

</embed>

` `</object>

Developers who allow end-users to upload content to their site should
consider allowing SWF uploads to be equivalent to allowing end-users to
upload HTML. The default **sameDomain** permission means that a SWF will
have access to the domain where it is hosted. If it is necessary to host
end-user SWFs, then the best practice is to host the SWF on a separate
domain that does not share cookies with the primary domain for the site.
For further protection, developers can set the "Content-Disposition:
attachment" header when serving the SWF which will instruct the browser
to create an Open/Save/Cancel download dialogue instead of executing the
SWF.

## Shared Objects

Shared Objects are designed to store up to 100kb of data relating to a
user’s session. They are dependent on host and domain name and SWF movie
name.

They are stored in binary format and are not cross-domain by default.
Shared objects are not automatically transmitted to the server unless
requested by the application.

It is worth noting that they are also stored outside the web browser
cache:

`C:\Documents and Settings\`<USER>`\Application Data\Macromedia\Flash Player\#Shared Objects\`<randomstring>`\`<domain>

When cleaning the browser cache, Flash sharedobjects survive such an
action.

Shared objects are handled by the Flash application and not the client’s
web browser.

## Permission Structure

**Domain** - Domain sandboxes are in effect when a SWF is hosted on a
web server.

  - Any two SWF files can interact when they are hosted on the same
    fully-qualified domain name (e.g. same-origin policy). They need
    explicit permission to read data from another sandbox.

**Local** - Local sandbox permissions are in effect when the SWF has
been saved to the end-user's hard drive.

  - local-with-filesystem (default) - can read from local files only
  - local-with-networking
      - Communicate with other local-with-networking SWF files
      - Send data to servers (e.g., using XML.Send() )

**local-trusted** - A SWF must be hosted on the end-user's machine and
the end-user must manually designate a folder to host local-trusted SWFs
through the Flash Player settings manager.

  - May read from local files; read or send messages with any server;
    and script and any other SWF file.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")