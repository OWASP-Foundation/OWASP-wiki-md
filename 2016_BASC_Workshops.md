__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

The Matasano Challenges were a collection of exercises to teach people
about mistakes in the implementation and use of cryptography. These
could be thought of as the homework problems in a course on how
cryptography goes wrong. In this training I selected challenges that I
think are illustrative of concepts that can be reused in multiple
contexts as well as attacks that can be done in the short time we have
for the training.

The format will alternate between a lecture portion explaining the
necessary concepts to understand the attack and a lab portion where we
will use what we just learned to attack CTF style versions of the
challenges. The lab portion will be time bound, but the challenges are
available over the internet so if you don't finish, you can continue
working after the training.

#### Topics

  - Introduction to Block Ciphers
  - ECB Mode Attacks
  - CBC Mode Attacks
  - Introduction to Public Key Cryptography
  - (EC)DSA Attacks
  - RSA Attacks

#### Technical Requirements

Laptop with the following:

  - Web testing tools such as a MITM proxy (e.g. burp suite), or browser
    extensions
  - Development environment ready to support making web requests, socket
    programming, and large integer arithmetic
  - Experience programming with web request programming and socket
    programming will be useful
  - I recommend Python as that is what I use and the PyCrypto library
    will be useful

This 1 hour workshop will help you to quickly get started in web and
mobile application penetration testing. There are go-to Linux based
penetration testing distributions that one can use but for beginners,
who are not familiar with Linux and virtualization software, it can be a
bit hard. We will see how easy it is to setup the testing environment on
any operating system. Although this workshop only covers the setup and
not the vulnerabilities, we will provide you with tons of resources and
other tools and tips for further study.

#### Outline

1.  Introduction and motivation for conducting this workshop
2.  Installation of ZAP’s CA certificate to observe encrypted traffic
3.  Overview of Google Chrome’s developer tools
4.  Walkthrough of ZAP features including context, searching, fuzzer
    etc.
5.  Setting up Android smartphone for mobile application testing.
6.  Recommendations about books, articles, videos for further study.

[Slides](https://docs.google.com/presentation/d/1rEL31aVjHnQh7zj4Bwy_Za5DUothJfqOVqf3Qi2L5Ao)

#### Technical Requirements

NOTE: The installation of the required software/tools will NOT be
covered in the workshop. Please prepare your system before the workshop.

*A laptop*

Any operating system is fine. 4 GB RAM is recommended for smooth
performance.

*A smartphone*

Android 5.0 and above. Although there won’t be any demo on any iOS
device, iOS users can follow similar steps.

*Google Chrome 53.x*

Please download and install the latest version of Google Chrome browser
from this link for your operating system:
<https://www.google.com/chrome/browser/desktop/index.html> Navigate to
settings \> People \> Add person. Name the new profile as ‘pentest’ or
anything you want and click ‘Add’.

*Java Runtime Environment 8*

Please download and install JRE from the following link:
<http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html>

OWASP ZAP requires JRE to run.

*OWASP ZAP 2.5.0*

Please download and install the OWASP Zed Attack Proxy (ZAP) from this
link for your operating system:
<https://github.com/zaproxy/zaproxy/wiki/Downloads> For Windows and Mac
OS, the installation is pretty straightforward (via executables).

For installation on Linux , please follow the instructions given here:
<https://samiux.blogspot.com/2015/08/howto-zap-on-ubuntu-1404-lts.html>

*FoxyProxy Standard Extension for Google Chrome*

Visit this link in Google Chrome and then install the extension.
<https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfnp>

Threat modeling is a way of thinking about what could go wrong and how
to prevent it. Instinctively, we all think this way in regards to our
own personal security and safety. When it comes to building software,
some teams either skip the important step of threat modeling in secure
software design or, they have tried threat modeling before but haven't
quite figured out how to connect the threat models to real world
software development and its priorities. Threat modeling should be part
of your secure software design process. Using threat modeling and some
principals of risk management, you can design software in a way that
makes security one of the top goals, along with performance,
scalability, reliability, and maintenance.

#### Objectives

In this workshop, attendees will learn about Threat Modeling through
understanding concepts and hands-on demos: Introduction to Threat
Modeling, including how to conduct a typical Threat Modeling session
Understand practical strategies in finding Threats, determine proper
Mitigations, and how to apply Risk Management with the Mitigations
Hands-on demo of one or two Real World Threat Modeling case studies
Hands-on demo of the Microsoft Threat Modeling Tool 2016

#### Materials

Laptop with Microsoft Threat Modeling Tool 2016 installed (highly
recommended, but not required)