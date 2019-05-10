# Introduction

This section serves as the installation guide for JBroFuzz on different
operating systems. Generally, the platforms listed herein tend to be the
more exotic non-standard win32 type Operating Systems (O/S).

With each of the sections below, there is a common trend: Java 1.6 must
be installed in the guest operating system in order for JBroFuzz to be
able to run correctly.

# Installing JBroFuzz in Solaris 10

By default, Solaris 10, ships with java 1.5. Earlier flavours are also
present, with packages like SUNWj3dmo SUNWj3man SUNWj3dev SUNWj3rt in
existence. In order to run JBroFuzz, you will need to install a 1.6
java.

## Prerequisites

A Java Development Kit (JDK) or a Java Runtime Environment (JRE) version
1.6 or later installed

You can obtain the latest version from:

<http://java.sun.com/>

Under Downloads -\> Java SE (Standard Edition)

In this particular case, the Java SE Development Kit 6u17 for Solaris
x86. You can choose to skip the registration popup window that appears
and proceed to download either of the two:

  - Java SE Development Kit 6u17 (jdk-6u17-solaris-i586.tar.Z) {130.51
    MB}
  - Java SE Development Kit 6u17 (jdk-6u17-solaris-i586.sh) {76.90 MB}

Naturally, these files will be obsolete in due course, but they were the
latest files available from Sun at the time of writting this brief
guide.

## Java 1.6 Install

For the Java SE Development Kit 6u17 (jdk-6u17-solaris-i586.tar.Z)
downloaded above, we need to uncompress and untar the file. At the
prompt enter:

    uncompress jdk-6u17-solaris-i586.tar.Z
    | tar xvf -

You can also use zcat instead of uncompress. From the
\[<http://java.sun.com/javase/6/webnotes/install/jdk/install-solaris.html>|
Solaris Java 1.6 Installation Notes\], come the following steps:

The above command creates several directories (SUNWj6rt, SUNWj6dev,
SUNWj6cfg, SUNWj6man, SUNWj6dmo, and SUNWj6jmp) plus a few files in the
current directory.

Become root by running su and entering the super-user password.

```
su
```

Uninstall any earlier installation of JDK packages.

If your machine has an earlier installation of this version of the JDK
in the default location (/usr/jdk/jdk1.6.0), you must remove it before
installing this version at the same location.

You can skip this step if you intend to install the JDK in a non-default
location. For more details, see Selecting the Default Java Platform.

As an example, to uninstall the Solaris packages for this version of the
JDK, remove them by running:

On all processors, if you wanted to remove java 1.6:

    pkgrm SUNWj6rt SUNWj6dev SUNWj6cfg SUNWj6man SUNWj6dmo

Run the pkgadd command to install the packages. On all processors:

    pkgadd -d . SUNWj6rt SUNWj6dev SUNWj6cfg SUNWj6man SUNWj6dmo

This command installs the JDK into /usr/jdk/jdk1.6.0.

## Obtain the latest version of JBroFuzz

You will need the latest version of JBroFuzz. In this case, we will use
JBroFuzz 1.8; you can obtain it from sourceforge:

  - JBroFuzz 1.8 (jbrofuzz-jar-18.zip) {3.6 MB}

Unzipping the contents, yields:

    unzip jbrofuzz-jar-18.zip

The important file is the JBroFuzz.jar file. There will also be a
subversion examples directory, plus a JBroFuzz.sh.

## Running JBroFuzz

At the command prompt:

    java -jar JBroFuzz.jar

Or, with more memory:

    java -Xmx256m -jar JBroFuzz.jar

Optionally, you can move the contents to the /opt folder and get a
listing similar to the one below:

    bash-3.00# ls -l /opt/jbrofuzz
    total 7460
    -rw-r--r--   1 yiannis  other    3807964 Dec  6 20:16 JBroFuzz.jar
    drwxr-xr-x   3 yiannis  other        512 Nov 19 03:00 examples
    -rwxr--r--   1 yiannis  other        339 Dec  6 19:59 jbrofuzz.sh
    bash-3.00# java -Xmx128m -jar JBroFuzz.jar

A screenshot of JBroFuzz, running in Solaris 10 is depicted below:

![JBroFuzz, running in Solaris 10](001-JBroFuzz-Install.jpg
"JBroFuzz, running in Solaris 10")

## Note for Solaris 8 & 9

The version of java 1.6 detailed above, does not automatically become
the default Java platform on Solaris 9 or earlier (unless there was no
default), but does become the default on Solaris 10. If you want 6.0 to
be the default on Solaris 8 or 9, then dig out and follow Sun's
instructions at Default Installations of Java Platform.

See the pkgadd(1) and admin(4) man pages for information on installing
the JDK in a non-default location.

# Installing JBroFuzz in Mac OS X

In order to run JBroFuzz, you will need to install a 1.6 java. To
determine what version of Java you are currently running you can type
the following at the command line

    java -version

## Prerequisites

A Java Development Kit (JDK) or a Java Runtime Environment (JRE) version
1.6 or later installed.

You can obtain the latest version for Mac OS X 10.5 from:

<http://support.apple.com/downloads/Java_for_Mac_OS_X_10_5_Update_4>

Java 6 is also available for earlier instances of OS X. It's important
to note Java 1.6 on Mac OS X 10.5 is currently only available for 64 bit
platforms. Java 1.6 for Mac OS X 10.4 supports both 32 bit and 64 bit
platforms.

## Java 1.6 Install

The JDK or JRE downloaded will be packaged as either a pkg and dmg
archive. If the package does not automatically run at download
completion, simply double click on the downloaded file to begin the
install. Follow the steps of the installer guide to complete the
installation. Once the install has completed you are not required to
uninstall any earlier instances of Java, but you will need to update
your Java preferences to use the new version of Java that has just been
installed.

Found Under Go -\> Utilities -\> Java Preferences

Under the Java Applications section, drag the Java SE 6 version to the
top of the list and close the Java Preferences window. If you rerun java
-version you should see that the system is now using the 1.6 version.

## Obtain the latest version of JBroFuzz

You will need the latest version of JBroFuzz. In this case, we will use
JBroFuzz 1.8; you can obtain it from sourceforge:

  - JBroFuzz 1.8 (jbrofuzz-jar-18.zip) {3.6 MB}

Unzipping the contents, yields:

    unzip jbrofuzz-jar-18.zip

The important file is the JBroFuzz.jar file. There will also be a
subversion examples directory, plus a JBroFuzz.sh.

## Running JBroFuzz

At the command prompt:

    java -jar JBroFuzz.jar

Or, with more memory:

    java -Xmx256m -jar JBroFuzz.jar

A screenshot of JBroFuzz, running on Mac OS X is depicted below:

![JBroFuzz, running in Mac OS X 10.5](002-JBroFuzz-Install.jpg
"JBroFuzz, running in Mac OS X 10.5")

## Note for Mac OS X

It is important to remember that while the Java Runtime Environment for
most operating systems is provided by Sun Microsystems, the Java Runtime
Environment for Mac comes from Apple. Subsequently, the reliability is
not as sound and you may find Mac OS specific bugs that the JBroFuzz
development team has no control over.

### Double-click does not Work

JBroFuzz needs Java 1.6 installed. If you don't have a 1.6 VM present,
here is what happens when you double click on the file:

After double clicking on the .jar file, a small window appeared which
said basically that the application didn't launch and to look at the
"Console" app to see the actual error message. Here's what the console
had to say:

    11/25/09 4:56:23 PM [0x0-0x2c02c].com.apple.JarLauncher[300]  at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:374)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306] SystemFlippers: didn't consume all data for long ID 0 (pBase = 0x100f2e0c0, p = 0x100f2e0c4, pEnd = 0x100f2e0c8)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306] SystemFlippers: didn't consume all data for long ID 0 (pBase = 0x100f2c4c0, p = 0x100f2c4c4, pEnd = 0x100f2c4c8)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306] SystemFlippers: didn't consume all data for long ID 0 (pBase = 0x100f2c4c0, p = 0x100f2c4c4, pEnd = 0x100f2c4c8)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306] Exception in thread "main"
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306] java.lang.UnsupportedClassVersionError: Bad version number in .class file
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.lang.ClassLoader.defineClass1(Native Method)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.lang.ClassLoader.defineClass(ClassLoader.java:675)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.security.AccessController.doPrivileged(Native Method)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.lang.ClassLoader.loadClass(ClassLoader.java:316)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:280)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    11/25/09 4:57:09 PM [0x0-0x2e02e].com.apple.JarLauncher[306]  at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:374)

You need to install Java 1.6. See the section above on how to install
Java 1.6

### Running JBroFuzz from the Command Line does not Work

If you try to run JBroFuzz from a "Terminal" app, with the wrong version
of Java installed (i.e. Java 1.5 or earlier), you will get the following
error message:

    Macintosh-3:jbrofuzz-jar-17 cougar$ java -Xmx512 -jar JBroFuzz.jar
    Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad
    version number in .class file
           at java.lang.ClassLoader.defineClass1(Native Method)
           at java.lang.ClassLoader.defineClass(ClassLoader.java:675)
           at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
           at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
           at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
           at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
           at java.security.AccessController.doPrivileged(Native Method)
           at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
           at java.lang.ClassLoader.loadClass(ClassLoader.java:316)
           at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:280)
           at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
           at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:374)

The UnsupportedClassVersionError implies that you have the wrong version
of java installed, let's verify:

    Last login: Wed Nov 25 17:18:54 on console
    Macintosh-3:~ cougar$ which java
    /usr/bin/java
    Macintosh-3:~ cougar$ java -version
    java version "1.5.0_20"
    Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_20-b02-315)
    Java HotSpot(TM) Client VM (build 1.5.0_20-141, mixed mode, sharing)

You need to install Java 1.6. See the section above on how to install
Java 1.6