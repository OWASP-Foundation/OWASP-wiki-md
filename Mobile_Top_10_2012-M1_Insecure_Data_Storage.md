`    <td ``>Threats agents include lost/stolen phones and the possibility of in-the-wild exploit/malware gaining access to the device. `

</td>

`    <td ``> A malicious agent hooks up an unprotected device to a computer with commonly available software. They are able to see all third party application directories that often contain stored personal information. `

</td>

`    <td colspan=2  ``>M1, insecure data storage, occurs when development teams assume that users will not have access to the phones file system and store sensitive pieces of information in data-stores on the phone. Devices file systems are often easily accessible and you should expect a malicious user to be inspecting your data stores. Rooting or jailbreaking a device usually circumvents any encryption protections and in some cases, where data is not protected properly, all that is needed to view application data is to hook the phone up to a computer and use some specialized tools. `

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
      - Stored application logs
      - Debug information
      - Cached application messages
      - Transaction histories
        </td>

`    <td ``> Insert text here `

</td>

It is important to threat model applications to see what data they
handle, as well as know the API's that handle it and if they store
sensitive information securely. Although annecdotal, places we most
often see data being stored insecurely are:

  - SQLite databases
  - Log Files
  - Plist Files
  - XML Data Stores or Manifest Files
  - Binary data stores
  - Cookie stores
  - SD Card
  - Cloud synced

The cardinal rule of mobile apps is: don’t store data unless absolutely
necessary. As a developer you have to assume that the data is forfeit as
soon as it touches the phone. You also have to consider the implications
of losing every single mobile users data to a silent jailbreak or root
exploit. If the usability versus security tradeoff is too much for you,
we recommend scrutinizing your platforms data security API’s and making
sure you’re calling them appropriately. The lesson here is to know what
data is being stored and protect it appropriately.

**iOS Specific Best Practices:**

** **

  - Never store credentials on the phone file system. Force the user to
    authenticate using a standard web or API login scheme (over HTTPS)
    to the application upon each opening and ensure session timeouts are
    set at the bare minimum to meet the user experience requirements.
  - Where storage or caching of information is necessary consider using
    a standard iOS encryption library such as CommonCrypto
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
  - Avoid using NSUserDefaults to store senstitve pieces of information
    as it stores data in plist files.
  - Be aware that all data/entities using NSManagedObects will be stored
    in an unencrypted database file.

**Android Specific Best Practices:**

** **

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

**A Visual Example:**

Here we have iGoat, a purposefully vulnerable mobile app for security
conscious folk to see these types of vulnerabilities first hand. In the
exercise we enter our credentials, and log in to the fake bank app. We
can then navigate to the file system and in our applications directory
we can see a database called “credentials.sqlite”. Exploring this
database reveals our username and credentials
(Jason:pleasedontstoremebro\!) being stored in plain text.

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
    Topics 2](http://developer.android.com/guide/topics/security)
  - [Apple's Introduction to Secure
    Coding](https://developer.apple.com/library/mac/)
  - [Fortify On Demand Blog - Exploring The OWASP Mobile Top 10: M1
    Insecure Data
    Storage](http://h30499.www3.hp.com/t5/Application-Security-Fortify-on/Exploring-The-OWASP-Mobile-Top-10-M1-Insecure-Data-Storage/ba-p/5904609)