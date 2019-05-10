<center>

[Back To The Mobile Top Ten Main
Page](https://www.owasp.org/index.php/Projects/OWASP_Mobile_Security_Project_-_Top_Ten_Mobile_Risks)

</center>

`    <td ``>Threats agents include the following: an adversary that has attained a lost/stolen mobile device; malware or a other repackaged app acting on the adversary's behalf that executes on the mobile device.`

</td>

`    <td ``>In the event that an adversary physically attains the mobile device, the adversary hooks up the mobile device to a computer with freely available software. These tools allow the adversary to see all third party application directories that often contain stored personally identifiable information (PII) or other sensitive information assets. An adversary may construct malware or modify a legitimate app to steal such information assets.`

</td>

`    <td colspan=2  ``>Insecure data storage vulnerabilities occur when development teams assume that users or malware will not have access to a mobile device's filesystem and subsequent sensitive information in data-stores on the device.  Filesystems are easily accessible.  Organizations should expect a malicious user or malware to inspect sensitive data stores.`

Rooting or jailbreaking a mobile device circumvents any encryption
protections. When data is not protected properly, specialized tools are
all that is needed to view application data.

</td>

`    <td ``>Insecure data storage can result in data loss, in the best case, for one user. In the worst case, for many users. Common valuable pieces of data seen stored include: `

  - Usernames
  - Authentication tokens
  - Passwords
  - Cookies
  - Location data
  - UDID/EMEI, Device Name, Network Connection Name
  - Personal Information: DoB, Address, Social, Credit Card Data
  - Application Data:
      - Stored application logs e.g For an android Apps ADB logcat
      - Debug information
      - Cached application messages
      - Transaction histories
        </td>

`    <td ``>Insecure data storage vulnerabilities typically lead to the following business risks for the organization that owns the risk app:`

  - Identity Theft
  - Fraud
  - Reputation Damage
  - External Policy Violation (PCI)
  - or Material Loss.
    </td>

It is important to threat-model your mobile app to understand the
information assets it processes and how the underlying APIs handle those
assets. These APIs should store sensitive information securely. Places
OWASP most often sees data being stored insecurely include the
following:

  - SQLite databases
  - Log Files
  - Plist Files
  - XML Data Stores or Manifest Files
  - Binary data stores
  - Cookie stores
  - SD Card
  - Cloud synced

When applying encryption and decryption to sensitive information assets,
malware may perform a binary attack on the app in order to steal
encryption or decryption keys. Once it steals the keys, it will decrypt
the local data and steal sensitive information. See OWASP Mobile Top Ten
2014 Category M10 for more information on this topic.

The cardinal rule of mobile apps is to not store data unless absolutely
necessary. As a developer you have to assume that the data is forfeited
as soon as it touches the phone. You also have to consider the
implications of losing mobile users' data to a silent jailbreak or root
exploit. If the usability versus security trade-off is too much for you,
OWASP recommends scrutinizing your platforms data security APIs and
making sure you’re calling them appropriately. The lesson here is to
know what data is being stored and protect it appropriately.

**iOS Specific Best Practices:**

  - Never store credentials on the phone file system. Force the user to
    authenticate using a standard web or API login scheme (over HTTPS)
    to the application upon each opening and ensure session timeouts are
    set at the bare minimum to meet the user experience requirements.
  - Where storage or caching of information is necessary consider using
    a standard iOS encryption library such as CommonCrypto. However, for
    particularly sensitive apps, consider using whitebox cryptography
    solutions that avoid the leakage of binary signatures found within
    common encryption libraries.
  - If the data is small, using the provided apple keychain API is
    recommended but, once a phone is jailbroken or exploited the
    keychain can be easily read. This is in addition to the threat of a
    bruteforce on the devices PIN, which as stated above is trivial in
    some cases.
  - For databases consider using SQLcipher for Sqlite data encryption
  - For items stored in the keychain leverage the most secure API
    designation, kSecAttrAccessibleWhenUnlocked (now the default in iOS
    5) and for enterprise managed mobile devices ensure a strong PIN is
    forced, alphanumeric, larger than 4 characters.
  - For larger or more general types of consumer-grade data, Apple’s
    File Protection mechanism can safely be used (see NSData Class
    Reference for protection options).
  - Avoid using NSUserDefaults to store sensitive pieces of information
    as it stores data in plist files.
  - Be aware that all data/entities using NSManagedObects will be stored
    in an unencrypted database file.
  - Avoid exclusively relying upon hardcoded encryption or decryption
    keys when storing sensitive information assets.
  - Consider providing an additional layer of encryption beyond any
    default encryption mechanisms provided by the operating system.

**Android Specific Best Practices:**

  - For local storage the enterprise android device administration API
    can be used to force encryption to local file-stores using
    “setStorageEncryption”
  - For SD Card Storage some security can be achieved via the
    ‘javax.crypto’ library. You have a few options, but an easy one is
    simply to encrypt any plain text data with a master password and AES
    128.
  - Ensure any shared preferences properties are
    **NOT** MODE_WORLD_READABLE unless explicitly required for
    information sharing between apps.
  - Avoid exclusively relying upon hardcoded encryption or decryption
    keys when storing sensitive information assets.
  - Consider providing an additional layer of encryption beyond any
    default encryption mechanisms provided by the operating system.

**A Visual Example:**

iGoat is a purposefully vulnerable mobile app for the security community
to explore these types of vulnerabilities first hand. In the exercise
below, we enter our credentials and log in to the fake bank app. Then,
we navigate to the file system. Within the applications directory, we
can see a database called “credentials.sqlite”. Exploring this database
reveals that the application is storing our username and credentials
(Jason:pleasedontstoremebro\!) in plain text.

![Image:Screen%20Shot%202012-12-19%20at%206.34.23%20AM.png](Screen%20Shot%202012-12-19%20at%206.34.23%20AM.png
"Image:Screen%20Shot%202012-12-19%20at%206.34.23%20AM.png")
![Image:Screen%20Shot%202012-12-19%20at%206.44.51%20AM.png](Screen%20Shot%202012-12-19%20at%206.44.51%20AM.png
"Image:Screen%20Shot%202012-12-19%20at%206.44.51%20AM.png")
![Image:Screen%20Shot%202012-12-19%20at%2010.11.15%20AM.png](Screen%20Shot%202012-12-19%20at%2010.11.15%20AM.png
"Image:Screen%20Shot%202012-12-19%20at%2010.11.15%20AM.png")

  - [OWASP](https://www.owasp.org/index.php/IOS_Developer_Cheat_Sheet)[IOS
    Developer Cheat
    Sheet](https://www.owasp.org/index.php/IOS_Developer_Cheat_Sheet)
  - [Google Androids Developer Security
    Topics 1](http://source.android.com/tech/security/)
  - [Google Androids Developer Security
    Topics 2](http://developer.android.com/training/articles/security-tips.html)
  - [Apple's Introduction to Secure
    Coding](https://developer.apple.com/library/mac/)
  - [Fortify On Demand Blog - Exploring The OWASP Mobile Top 10:
    Insecure Data
    Storage](http://h30499.www3.hp.com/t5/Application-Security-Fortify-on/Exploring-The-OWASP-Mobile-Top-10-M1-Insecure-Data-Storage/ba-p/5904609)