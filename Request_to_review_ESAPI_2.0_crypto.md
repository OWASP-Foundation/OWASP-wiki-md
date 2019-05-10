# Call for Review

OWASP is looking for some professional cryptographers and security
professionals with expertise in cryptography to donate a small amount of
time to review the code and/or documentation handling symmetric
encryption in [Enterprise Security
API (ESAPI)](http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API)
2.0 before this software package is considered generally available.

The latest release candidate of OWASP's ESAPI for Java (ESAPI-2.0_rc10)
has recently been released. This is the fifth complete release candidate
that contains the completely revamped symmetric encryption and the first
release candidate with completed user documentation describing it.

Many of these changes to ESAPI's symmetric encryption came about as a
result of the suggestions of many of you and your fellow cryptographers
made on the Metzdowd cryptography mailing list. (See thread "[Detecting
attempts to decrypt with incorrect secret key in OWASP
ESAP](http://www.mail-archive.com/cryptography@metzdowd.com/msg10889.html)I"
back in mid-Sept, 2009.) Specifically advice from David A. Wagner and
Ian Griggs directly affected several of the detailed design decisions.

The OWASP ESAPI team has only limited experience in applied
cryptography, and realizing several of the mistakes in implementing this
for ESAPI 1.4, we are interested in getting feedback on the reworked
symmetric encryption portion of ESAPI to ensure it is correct and secure
this time. Therefore, we are seeking experienced cryptographers as well
as anyone else with an interest to comment on the ESAPI implementation
and documentation.

In particular, OWASP would like to get feedback on the method used to
compute derived keys and to portably serialize the **'CipherText**'
objects as getting these correct is imperative before people start
actually using ESAPI symmetric encryption to store encrypted data. If
changes to this method are required later to make it secure, it will
almost certainly cause backward compatibility issues with data encrypted
with older versions.

Ideally, we would like a few of you with expertise in cryptography to
inspect the Java code for correctness and secure implementation. (We
remember all too well what happened with the IEEE and WEP when
cryptographers were not invited to participate and we would like to
avoid any similar issues.)

The links for the ESAPI-2.0_rc10.zip file as well as separate source
code are provided below. As you review things, please keep in mind that
ESAPI was meant to be a general API. In particular, this means that not
all enterprises have the same security policies so flexibility was
required with respect to algorithms allowed, allowed cipher modes,
permitted padding schemes, etc. Also allowing compatibility with legacy
applications was considered important as well. However, we hope to have
chosen reasonable defaults for things such that application developers
who do not have issues with compatibility with legacy systems can use
the ESAPI crypto configuration as-is without the need for tweaking
anything other than the master key and master salt properties (which are
left unset by default).

To comment on issues to this source code, email comments to [Kevin
Wall](mailto:kevin.w.wall@gmail.com) or post an issue on the ESAPI
Issues List (see below).
Thanks to those of you have already help provided back in September and
any future contribution you are able to make. If you would care to be
acknowledged in some future ESAPI documentation for your contribution,
please let OWASP know that as well, and if so, whether you only wish
your name to be mentioned, or your name and email address.

-----

<table>
<tbody>
<tr class="odd">
<td><p><strong>Download ESAPI</strong><br />
</p></td>
<td><p><a href="http://code.google.com/p/owasp-esapi-java/downloads/detail?name=esapi-2.0_rc10.zip">Download ESAPI-2.0_rc10 zip</a></p>
<p>The source code is located is under 'project/src/main/java'. Note that the source code uses Maven 2.0 to build it, via the pom.xml file.<br />
</p></td>
</tr>
<tr class="even">
<td><p><strong>Code</strong></p>
<p>(Approximately 3900 LOC or 1700 NCSL)</p></td>
<td><p>Relevant configuration properties (ESAPI.properties file): <a href="http://owasp-esapi-java.googlecode.com/svn/trunk/src/main/resources/.esapi/ESAPI.properties">ESAPI.properties file</a></p>
<hr />
<p>Interface (Encryptor): <a href="http://owasp-esapi-java.googlecode.com/svn/trunk/src/main/java/org/owasp/esapi/Encryptor.java">Encryptor interface</a></p>
<hr />
<p>Helper implementation classes (CipherSpec, CipherText, CipherTextSerializer, CryptoHelper, PlainText, SecurityProviderLoader): <a href="http://owasp-esapi-java.googlecode.com/svn/trunk/src/main/java/org/owasp/esapi/crypto/">Crypto helper classes</a><br />
</p>
<ul>
<li>CipherSpec: All relevant data for using Cipher, except the SecretKey</li>
<li>CipherText: All the CipherSpec data, plus the ciphertext from encrypting</li>
<li>CipherTextSerializer: Helper class to assist with portable serialization of CipherText objects.</li>
<li>CryptoHelper: Static helper methods.</li>
</ul>
<p>Of these, the method I want to see inspected above all others is<br />
<em>     public static SecretKey computeDerivedKey(SecretKey keyDerivationKey, int keySize, String purpose)</em><br />
Implementation (JavaEncryptor):</p>
<hr />
<p><a href="http://owasp-esapi-java.googlecode.com/svn/trunk/src/main/java/org/owasp/esapi/reference/crypto/JavaEncryptor.java">JavaEncryptor class</a><br />
We welcome feedback on all methods, but please focus on the *symmetric*<br />
encryption / decryption methods (all named encrypt() / decrypt()) in this class.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Javadoc</strong><br />
</p></td>
<td><p><a href="http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/index.html">ESAPI Javadoc</a><br />
</p></td>
</tr>
<tr class="even">
<td><p><strong>General documentation</strong><br />
</p></td>
<td><p>Describes reasons of <a href="http://owasp-esapi-java.googlecode.com/svn/trunk/documentation/esapi4java-core-2.0-readme-crypto-changes.html">why we are changing the ESAPI symmetric crypto for ESAPI 2.0</a><br />
Description of the <a href="http://owasp-esapi-java.googlecode.com/svn/trunk/documentation/esapi4java-core-2.0-ciphertext-serialization.pdf">portable serialization of CipherText objects</a><br />
<a href="http://owasp-esapi-java.googlecode.com/svn/trunk/documentation/esapi4java-core-2.0-symmetric-crypto-user-guide.html">User Guide for Symmetric Encryption in ESAPI 2.0</a><br />
</p></td>
</tr>
<tr class="odd">
<td><p><strong>ESAPI Issues List</strong><br />
</p></td>
<td><p><a href="http://code.google.com/p/owasp-esapi-java/issues/list">Google Issues List</a><br />
Requires Google account to submit new issues.<br />
Note that issue # 81 is a request to review the <em>computeDerivedKey()</em> method in CryptoHelper. You may comment on this issue or add your own if you find defects by first logging in using your Google account.<br />
</p></td>
</tr>
</tbody>
</table>



__NOTOC__



\== Known Relevant Issues
\==

The crypto in ESAPI 2.0-rc6 is known to be vulnerable to a "padded
oracle attack" which is a type of chosen ciphertext attack designed to
reveal plaintext. We believe this is fixed in ESAPI 2.0_rc10 but it
would be nice if someone who is a professional cryptographer could
confirm this.

The details are provided at [ESAPI Google Issues list, issue
\#120](http://code.google.com/p/owasp-esapi-java/issues/detail?id=120).



[Category:OWASP_Enterprise_Security_API](Category:OWASP_Enterprise_Security_API "wikilink")