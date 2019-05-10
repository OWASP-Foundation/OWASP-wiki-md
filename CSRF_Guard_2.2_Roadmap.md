## Overview

The purpose of this article is to maintain the desired change requests
for the upcoming CSRFGuard releases. If there is a particular feature
that you would like to see implemented, please feel free to add it to
the appropriate sections below.

## Completed Changes

The following is a list of changes that have been implemented for the
development version of J2EE CSRFGuard 2.2:

:\# JavaScriptHandler now iterates over all DOM elements and puts the
token in if the element is a form or has a 'src' or 'href' attribute.

:\# Allow the user to define "entry point pages" whose token is never
validated but a token always gets inserted

:\# Allow the user to define "unprotected pages" that we will simply
ignore. By default, all pages are "protected"

:\# Update the response handlers to support the various locations that
an "href" and "src" attribute can be placed in the HTML 5 spec

:\# Visiting the page and clicking "refresh" is caught as a CSRF attack.
Only verify the token if parameters exist in the request (optional).

:\# Allow the developer to specify where to send the user on the initial
request (i.e. when the token is being created). Prevents initial CSRF
attacks against unauthenticated users.

:\# Add a "CSRF Token" JSP Tag library that developers can call in their
JSP to dynamically add the token.

## Planned Changes

The following is a list of changes that are tentatively scheduled for
the J2EE CSRFGuard 2.2 release:

:\# Modify the response handlers to only place the token in links/forms
that point to our origin

:\# Add basic JavaScript support for invocations such as
"document.location" or "window.location"

:\# Optionally randomize the CSRF token parameter name.

## Deferred Changes

The following is a list of changes that were suggested but not
implemented:

:\# Port the existing configuration file to an XML based config file

:\# Allow the user to define a list of "known safe extensions" that do
not require CSRF checks

## Changes Under Consideration

The following is a list of change requests that are still under
consideration:

TBD