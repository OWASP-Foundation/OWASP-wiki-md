# OWASP Installer Guidelines

This is a *proposed* set of guidelines for the installers of OWASP
projects.

Please update this page with any suggestions for improvements you may
have.

## Windows

OWASP projects should be installed into a project specific directory
underneath:

    C:\Program Files (x86)\OWASP\

or for older Windows versions:

    C:\Program Files\OWASP\

On uninstallation the 'OWASP' directory should be deleted if there are
no other files or directories left underneath it.

Installers should add programs to the 'All programs'/'Start Menu' list
in a directory underneath an 'OWASP' directory.

If necessary the 'OWASP' directory should be created and a link to the
OWASP home page added.

On uninstallation the OWASP 'Start Menu' directory should be deleted if
there are no other files or directories left underneath it.

Project known to conform to these recommendations:

  - [OWASP Zed Attack Proxy
    Project](OWASP_Zed_Attack_Proxy_Project "wikilink")

## Linux

OWASP projects should be installed into a project specific directory
underneath:

    /opt/owasp/

On uninstallation the 'owasp' directory should be deleted if there are
no other files or directories left underneath it.

See [OWASP Linux packaging](OWASP_Linux_packaging "wikilink") for
details of how to create and distribute Linux packages of OWASP
projects.

## Mac OS

TBA - please add suggestions

## iPhone

TBA - please add suggestions

## Android

package name :

    com.owasp.<name>

Where <name> will be package name. also on sdcard

    /sdcard/owasp/<name>