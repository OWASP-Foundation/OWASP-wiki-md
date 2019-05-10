The plan for this page is to document how OWASP projects should go about
creating and distributing Linux packages.

But right now it just documents where we are right now, initially based
on this
[thread](http://lists.owasp.org/pipermail/owasp-leaders/2012-September/007793.html)
in the Leaders list.

## Existing repos

### OWASP WTE

The [OWASP Web Testing Environment
Project](OWASP_Web_Testing_Environment_Project "wikilink") has its own
repo: <http://appseclive.org/apt/stable/> which contains various OWASP
projects.

To update projects from this repo use commands like:

    $ sudo echo "deb OWASP Mantra OS / #OWASP WTE Stable Repository" >> /etc/apt/sources.list

    $ sudo apt-get update

    $ sudo apt-get install owasp-wte-zap

### Backtrack

[BackTrack](http://www.backtrack-linux.org/) has its own repository
which includes various OWASP projects.

Note that you really need to download and install BackTrack and download
the projects from within it.

### Mantra OS

[OWASP Mantra OS](OWASP_Mantra_OS "wikilink") is planning its own
repository, which will include various OWASP projects.

## Work in progress - ZAP repos

Work is ongoing to add the [OWASP Zed Attack Proxy
Project](OWASP_Zed_Attack_Proxy_Project "wikilink") into key upstream
distros. The progress will be documented here and will hopefully become
a template that other projects can reuse.

### Open SUSE

It turns out someone had already started a ZAP project:
<https://build.opensuse.org/package/show?package=owasp-zap&project=home%3Athomas-worm-datev%3Aowasp>

This has now been cloned and work is ongoing to make this official:
<https://build.opensuse.org/package/show?package=owasp-zap&project=home%3Acanislycan%3Adraconic>

### Debian

Not started.

### Fedora

Not started.