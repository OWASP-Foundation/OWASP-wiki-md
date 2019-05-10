## Overview

This article’s focus is to define, where practical, nomenclature and
definitions of the differing security **Assessment Levels**. These
levels rely on the **Assessment Techniques** defined elsewhere within
this project.

## Levels

**Note this is a working draft for discussion purposes and should not be
relied upon. There is no guarantee that these levels will be used or
will be stable for any purpose**

The goal is to advance the levels in two dimensions, breadth and depth.
Breadth is the coverage of the review across the space of security
mechanisms and security vulnerabilities. Depth is the level of rigor
applied to the analysis of the application.

The following assessment levels are proposed:

  - AL1: Partial Application Security Check
  - AL2: Basic Application Security Check
  - AL3: Standard Application Security Verification
  - AL4: Enhanced Application Security Verification
  - AL5: Comprehensive Application Security Verification

## AL1: Partial Application Security Check

Automated scans (either external vulnerability scan or code scan or
both) with minimal interpretation and verification.

## AL2: Basic Application Security Check

AL1 + verification of scan results using manual penetration testing and
code review. Security areas not scanned (encryption, access control,
etc...) must be lightly tested or code reviewed.

## AL3: Standard Application Security Verification

AL2 + verification of common security mechanisms and common
vulnerabilities using either manual pentesting or code review or both.
Not all instances of problems found. Sampling allowed.

## AL4: Enhanced Application Security Verification

AL3 + verification of all security mechanisms and vulnerabilities based
on high level threat model (part of assessment if not provided) using
either manual pentest or code review or both.

## AL5: Comprehensive Application Security Verification

AL4 + search for malicious code. All code must be manually reviewed
against a standard and all security mechanisms tested.

[Category:OWASP Application Security Assessment Standards
Project](Category:OWASP_Application_Security_Assessment_Standards_Project "wikilink")