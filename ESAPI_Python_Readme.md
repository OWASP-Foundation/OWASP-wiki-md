-----

**OWASP ESAPI - Python Edition**


**Python Edition of OWASP ESAPI v1 BETA Has Been Released**

I'm pleased to announce that a beta of version 1 has been released. To
get a copy, go to our [Google
Code](http://code.google.com/p/owasp-esapi-python/) site to [clone the
Mercurial
repository](http://code.google.com/p/owasp-esapi-python/source/checkout)
or [download an
archive](http://code.google.com/p/owasp-esapi-python/downloads/list).
Documentation for the API is available
[here](http://owasp-esapi-python.googlecode.com/hg/doc/index.html).

This beta has been tested on Python 2.6 on Windows and Linux, but other
versions have not been tested. If you take a look, I would appreciate it
if you would send me an [email](mailto:craig.younkins@owasp.org) about
your experience.


**README**

Requirements:

*If you have setuptools installed, you should be able to install all
except KeyCzar and Visual C++ 2008 by doing 'easy_install
<packagename>' in a shell or command prompt.*

  - PyCrypto 2.01 - <http://www.amk.ca/python/code/crypto>
      - PyCrypto requires a C Compiler. Windows users can us Visual C++
        2008 Express Edition -
        <http://www.microsoft.com/express/vc/#webInstall>
  - KeyCzar 0.6b - <http://www.keyczar.org/>
      - KeyCzar requires PyASN1 - <http://pypi.python.org/pypi/pyasn1>
      - and simplejson, which is standard in 2.6 -
        <http://pypi.python.org/pypi/simplejson>
  - PyLint 0.18.1 - Only needed for static analysis. -
    <http://pypi.python.org/pypi/pylint>
  - Coverage module by Ned Batchelder v3.0.1 - Only needed if you want
    coverage analysis - <http://pypi.python.org/pypi/coverage/3.0.1>
  - Nose 0.11.1 - Only needed if you want to run unit tests together and
    combine it with coverage analysis -
    <http://pypi.python.org/pypi/nose/0.11.1>

Installation:

  - Install any of the missing dependencies listed above.
  - Extract the ESAPI on Python package.
  - Add the extracted folder to your Python path. One way to do this is
    to create a text file, such as 'esapi.pth', in your Python
    installation's Lib\\site-packages folder. Copy the path of the
    folder you extracted into this text file. The path should have the
    'esapi' folder inside.
  - Start a new interactive Python console and enter 'import esapi'. If
    you get no output, it ran successfully. If you got "ImportError: No
    module named esapi", double check the step above.
  - By default, ESAPI is set up for Linux. If you are running ESAPI on
    Windows, you will need to modify the Encryptor_KeysLocation and
    Executor_WorkingDirectory settings in esapi/conf/settings.py. You
    should use forward slashes in the paths.
  - See "To set up a crypto keyring" to generate the keys necessary for
    crypto.
  - Run the unit tests by opening a shell or command prompt in
    esapi/test and running runTests.bat or runTests.sh, depending on
    your platform. If you get around 7 errors relating to crypto, please
    ensure you have followed the steps under "To set up a crypto
    keyring".
  - **Note**: Running all tests may appear to block or pause,
    particularly on Windows. This may be be due to exhaustion of the
    entropy pool. If it blocks, try moving the mouse, typing, or
    generating some disk activity.

To adapt and integrate with your project:

  - You can use as much or as little of ESAPI as you would like. You'll
    want to do a 'from esapi.core import ESAPI' and use the methods that
    class provides.

To set up a crypto keyring:

  - Select a root directory for your keyring, like /esapi/keyring/, and
    set Encryptor_KeysLocation in settings.py to this string if you
    have not already.
  - Open a python interactive shell and execute:
      - from esapi.core import ESAPI
      - ESAPI.encryptor().gen_keys()
  - Modify esapi/conf/settings.py according to the output by replacing
    the Encryptor_MasterSalt line with the one given.

To enable internationalization:

  - Set the 'LANGUAGE' environment variable with your locale
  - On \*nix: export LANGUAGE=en_US
  - On Windows: set LANGUAGE=en_US

<!-- end list -->

  - Please note that as of this writing, no translation files are
    available. A GNU gettext .po file is available in esapi/conf/locale
    .

[Category: OWASP Enterprise Security
API](Category:_OWASP_Enterprise_Security_API "wikilink")