# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="introduction">Introduction</h2>
<p><a href="https://en.wikipedia.org/wiki/Information_privacy">Privacy</a> is daily reality for many internet users. Eavesdropping user's content and using it for various reason is not desired by many of the application users. Putting trust on communication channel, service provider or government not to intercept your content is not a good idea.</p>
<p>OTR framework solves this problem by cryptographically processing the users content in transit and at rest. No eavesdropper can read the content, not even the service provider</p>
<h2 id="what_is_otr">What is OTR ?</h2>
<p><a href="https://github.com/JigarJoshi/otr/"><strong>OTR4J</strong></a> stands for off-the-record for Java. end-to-end encryption (off-the-record) is a system of communication where only communicating users can read the messages, neither eavesdropper nor communication facilitator channels can read messages.</p>
<p><strong>OTR4J</strong> provides simple framework and prototype that helps developers to easily implement end-to-end encryption into Java application. Example applications are messaging, file transfer, secure information transfer application</p>
<h2 id="why_use_otr4j">Why use otr4j ?</h2>
<p>It provides high degree of <strong>privacy and security</strong>.</p>
<h2 id="how_does_it_work">How does it work ?</h2>
<p><strong>OTR4J</strong> uses hybrid cryptography system. It uses <a href="https://en.wikipedia.org/wiki/RSA">RSA</a> and <a href="https://en.wikipedia.org/wiki/Elliptic_curve_Diffie%E2%80%93Hellman">ECDH</a>for key exchanges and <a href="https://en.wikipedia.org/wiki/Advanced_Encryption_Standard">AES</a> encryption. Technical details of protocol is explained <a href="https://github.com/JigarJoshi/otr/blob/master/README.md">here</a></p>
<h2 id="example_api">Example API</h2>
<p>Bob sends message to Alice</p>
<p><code>OTRClient bobClient = OTRClient.get(config);</code><br />
<code>bobClint.login("bob", "password");</code><br />
<code>bobClient.sendMessage("Hello Alice", ALICE_USER_ID);</code></p>
<p>Alice reads messages</p>
<p><code>OTRClient aliceClient = OTRClient.get(config);</code><br />
<code>aliceClient.login("alice", "password");</code><br />
<code>aliceClient.readMessages();</code></p>
<h2 id="licensing">Licensing</h2>
<p>Copyright 2016 Jigar Joshi</p>
<p>Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at</p>
<p><a href="http://www.apache.org/licenses/LICENSE-2.0">http://www.apache.org/licenses/LICENSE-2.0</a></p>
<p>Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p><a href="https://github.com/JigarJoshi/otr">Source Code</a></p>
<p><a href="https://github.com/JigarJoshi/otr/blob/master/README.md">Documentation</a></p>
<p><a href="https://www.owasp.org/index.php/OWASP_Off_the_record_4_Java_Project">Wiki Home Page</a></p>
<p><a href="https://github.com/JigarJoshi/otr/issues">Issue Tracker</a></p>
<h2 id="project_leader">Project Leader</h2>
<p>Project Leader - <a href="https://www.owasp.org/index.php/User:Jigarjm">Jigar Joshi</a> ( <a href="mailto:jigar.joshi@owasp.org">jigar.joshi@owasp.org</a> )</p>
<h2 id="related_projects">Related Projects</h2>
<p><a href="https://www.owasp.org/index.php/OWASP_Java_Encoder_Project">JavaEncoderProject</a></p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
</tr>
</tbody>
</table></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="news_and_events">News and Events</h2>
<ul>
<li>[22 Dec 2016] 1.0-SNAPSHOT is available</li>
</ul>
<p><strong>API</strong></p>
<p>APIs for basic functionality is available</p>
<p>Basic client with in-memory storage is provided for reference</p>
<p><strong>Functionality</strong></p>
<p>Privacy in transit is available</p>
<p>Message authentication and out of the band verification</p>
<p>User authentication for REST</p>
<p>MySQL based message store for server</p>
<p>Configurable toggles are available for various knobs of encryption</p></td>
</tr>
</tbody>
</table>

# FAQs

## How can I participate in your project?

You can participate in project by multiple ways.

**Feature Request** Raise your feature request
[here](https://github.com/JigarJoshi/otr/issues/new) with detailed
information

**Contribute code** Pick an open issue, forkoff the github repository
and create PR

**Help in awareness** One of the quarter goal is to spread awareness.
you can help here by mentioning this project in your blog, tweets and
through any other media.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for researchers and software developers to help.

## I have nothing to hide why should I care for privacy?

Some users have thinking that they have got nothing to hide and they are
ok with sharing content. This is too local and narrow perspective to
privacy concerns.

# Acknowledgements

## Volunteers

The OWASP Security Principles project is developed by a worldwide team
of volunteers. A live update of project [contributors is found
here](https://github.com/JigarJoshi/otr/graphs/contributors). Your name
will be recognized here for your help and volunteer work for this
project

The first contributors to the project were:

  - [Jigar Joshi](mailto:jigar.joshi@owasp.org)
  - Want to see your name here ? Contribute please

# Road Map and Getting Involved

## Broader Goal

<strong>Provide ability to strengthen privacy by providing stronger
end-to-end encryption in transit and stronger encryption at rest to
application developers by simpler API for most of the popular
languages</strong>

## Roadmap

As of <strong>March, 2017</strong>, the highest priorities for the next
3 months are:

*This section will keep on updating*

  - Get other people to review the Code Project Template and provide
    feedback

<!-- end list -->

  - **Better API**: Simplify APIs and document them for Java

<!-- end list -->

  - **Privacy at Rest**: APIs for privacy at rest

<!-- end list -->

  - **Awareness**: Get 3 clients using this framework in real life
    \[please let us know by email if you already use it. to keep track
    of the goal's progress\]

## Getting Involved

Involvement in the development and promotion of <strong>OTR4J</strong>
is actively encouraged\! You do not have to be a security expert or a
programmer to contribute.

Some of the ways you can help are as follows:

### Security Researcher

Are you a security researcher, privacy advocate ? help review & audit
protocol design and implementation, suggest functional requirement,

### Coding

Are you a Software Developer ? you can help contributing code to solve
some of the [open issues](https://github.com/JigarJoshi/otr/issues), We
are actively seeking client framework building in Python, Javascript,
Objective C

### Fan of privacy and OTR

Are you a privacy advocate on internet ? liked the project ? Help
spreading awareness of this project

### Feedback

Please create the [issues](https://github.com/JigarJoshi/otr/issues) for
feedback about

  - What do like?
  - What don't you like?
  - What features would you like to see prioritized on the roadmap?

# Minimum Viable Product

Minimum viable product for this project is a simpler Java API that
provides stronger end-to-end encryption in transit and stronger
encryption at rest

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Code](Category:OWASP_Code "wikilink")