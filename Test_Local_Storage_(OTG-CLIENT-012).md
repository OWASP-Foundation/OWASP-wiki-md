## Summary

Local Storage also known as Web Storage or Offline Storage is a
mechanism to store data as key/value pairs tied to a domain and enforced
by the same origin policy (SOP). There are two objects, localStorage
that is persistent and is intended to survive browser/system reboots and
sessionStorage that is temporary and will only exists until the window
or tab is closed.

On average browsers allow to store in this storage around 5MB per
domain, that compared to the 4KB of cookies is a big difference, but the
key difference from the security perspective is that the data stored in
these two objects is kept in the client and never sent to the server,
this also improves network performance as data do not need to travel
over the wire back and forth.

### localStorage

Access to the storage is normally done using the setItem and getItem
functions. The storage can be read from javascript which means with a
single XSS an attacker would be able to extract all the data from the
storage. Also malicious data can be loaded into the storage via
JavaScript so the application needs to have the controls in place to
treat untrusted data. Check if there are more than one application in
the same domain like example.foo/app1 and example.foo/app2 because those
will share the same storage.

Data stored in this object will persist after the window is closed, it
is a bad idea to store sensitive data or session identifiers on this
object as these can be accesed via JavaScript. Session IDs stored in
cookies can mitigate this risk using the httpOnly flag.

### sessionStorage

The main difference with localStorage is that the data stored in this
object is only accessible until the tab/window is closed, which makes
localStorage a perfect candidate for data that doesn't need to be
persisted between sessions. It shares most of the properties and the
getItem/setItem methods, so manual testing needs to be undertaken to
look for these methods and identify in which parts of the code the
storage is accessed.

## How to Test

### Black Box testing

Black box testing for issues within the Local Storage code is not
usually performed since access to the source code is always available as
it needs to be sent to the client to be executed.

### Gray Box testing

First of all, we need to check whether the Local Storage is used.

**Example 1: Access to localStorage:**
Access to every element in localStorage with JavaScript:

    for(var i=0; i<localStorage.length; i++) {
            console.log(localStorage.key(i), " = ", localStorage.getItem(localStorage.key(i)));
    }

same code can be applied to sessionStorage

Using Google Chrome, click on menu -\> Tools -\> Developer Tools. Then
under Resources you will see 'Local Storage' and 'Web Storage'.

![<File:storage-chrome.png>](storage-chrome.png
"File:storage-chrome.png")

Using Firefox with the Firebug add on you can easily inspect the
localStorage/sessionStorage object in the DOM tab.

![<File:storage-firefox.png>](storage-firefox.png
"File:storage-firefox.png")

Also, we can inspect these objects from the developer tools of our
browser.

Next manual testing needs to be conducted in order to determine whether
the website is storing sensitive data in the storage that represents a
risk and will increase dramatically the impact of an information leak.
Also check the code handling the Storage to determine if it is
vulnerable to injection attacks, common issue when the code does not
escape the input or output. The JavaScript code has to be analyzed to
evaluate these issues, so make sure you crawl the application to
discover every instance of JavaScript code and note sometimes
applications use third-party libraries that would need to be examined
too.

Here is an example of how improper use of user input and lack of
validation can lead to XSS attacks.

**Example 2: XSS in localStorage:**
Insecure assignment from localStorage can lead to XSS

    function action(){

    var resource = location.hash.substring(1);

    localStorage.setItem("item",resource);

    item = localStorage.getItem("item");
    document.getElementById("div1").innerHTML=item;
    }
    </script>

    <body onload="action()">
    <div id="div1"></div>
    </body>

URL PoC:

<http://server/StoragePOC.html#><img src=x onerror=alert(1)>

![<File:Storage-xss.png>](Storage-xss.png "File:Storage-xss.png")

## Tools

  - **Firebug** - <http://getfirebug.com/>
  - **Google Chrome Developer Tools** -
    <https://developers.google.com/chrome-developer-tools/>
  - **OWASP Zed Attack Proxy (ZAP)** -
    <https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project>

ZAP is an easy to use integrated penetration testing tool for finding
vulnerabilities in web applications. It is designed to be used by people
with a wide range of security experience and as such is ideal for
developers and functional testers who are new to penetration testing.
ZAP provides automated scanners as well as a set of tools that allow you
to find security vulnerabilities manually.

## References

**OWASP Resources**

  - **OWASP HTML5 Security Cheat Sheet**:
    <https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet>

**Whitepapers**

  - **Web Storage Specification**: <http://www.w3.org/TR/webstorage/>