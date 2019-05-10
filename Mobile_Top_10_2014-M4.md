<center>

[Back To The Mobile Top Ten Main
Page](https://www.owasp.org/index.php/Projects/OWASP_Mobile_Security_Project_-_Top_Ten_Mobile_Risks)

</center>

`    <td ``>Agents that may exploit this vulnerability include the following: mobile malware, modified versions of legitimate apps, or an adversary that has physical access to the victim's mobile device.`

</td>

`    <td ``>An agent that has physical access to the device will use freely available forensic tools to conduct the attack. An agent that has access to the device via malicious code will use fully permissible and documented API calls to conduct this attack.`

</td>

`    <td colspan=2  ``>Unintended data leakage occurs when a developer inadvertently places sensitive information or data in a location on the mobile device that is easily accessible by other apps on the device. First, a developer's code processes sensitive information supplied by the user or the backend. During that processing, a side-effect (that is unknown to the developer) results in that information being placed into an insecure location on the mobile device that other apps on the device may have open access to. Typically, these side-effects originate from the underlying mobile device's operating system (OS). This will be a very prevalent vulnerability for code produced by a developer that does not have intimate knowledge of how that information can be stored or processed by the underlying OS.`

It is easy to detect data leakage by inspecting all mobile device
locations that are accessible to all apps for the app's sensitive
information.

</td>

`    <td ``>This vulnerability may result in the following technical impacts: extraction of the app's sensitive information via mobile malware, modified apps, or forensic tools.`

</td>

`    <td ``>The nature of the business impact is highly dependent upon the nature of the information stolen. Sensitive information theft may result in the following business impacts:`

  - Privacy Violations
  - PCI Violations
  - Reputational Damage; or
  - Fraud.
    </td>

Unintended data leakage (formerly side-channel data leakage) includes
vulnerabilities from the OS, frameworks, compiler environment, new
hardware, etc. without a developers knowledge.

In mobile development, this is most seen in undocumented (or
under-documented) internal processes such as:

  - The way the OS caches data, images, key-presses, logging, and
    buffers.
  - The way the development framework caches data, images, key-presses,
    logging, and buffers.
  - The way or amount of data ad, analytic, social, or enablement
    frameworks cache data, images, key-presses, logging, and buffers.

It is important to threat model your OS, platforms, and frameworks, to
see how they handle the following types of features:

  - URL Caching (Both request and response)
  - Keyboard Press Caching
  - Copy/Paste buffer Caching
  - Application backgrounding
  - Logging
  - HTML5 data storage
  - Browser cookie objects
  - Analytics data sent to 3rd parties

It is especially important to discern what a given OS or framework does
by default. By identifying defaults and applying mitigating controls,
you can avoid unintended data leakage.

## OS: iOS

  - URL Caching (Both request and response)
  - Keyboard Press Caching
  - Copy/Paste buffer Caching
  - Application backgrounding
  - Logging
  - HTML5 data storage
  - Browser cookie objects
  - Analytics data sent to 3rd parties

## OS: Android

  - URL Caching (Both request and response)
  - Keyboard Press Caching
  - Copy/Paste buffer Caching
  - Application backgrounding
  - Logging
  - HTML5 data storage
  - Browser cookie objects
  - Analytics data sent to 3rd parties

References