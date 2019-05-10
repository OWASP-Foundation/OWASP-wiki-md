### Development Issues

## Objective

This document will describe different areas of program vulnerabilities
that can be found in the source code of Enterprise Business applications
and ERP systems.

## Purpose

The purpose of this document is to increase awareness of the developers
of Enterprise Business software. Here, we will collect top software
vulnerabilities in server side and frontend side that can exist in
Business Applications.

## Intro

There are many different languages and technologies that can be used to
develop business applications and write custom code such as ABAP for
SAP, PeopleCode for PeopleSoft, X++ for Microsoft Dynamics, PL/SQL for
Oracle EBS, LotusScript for Lotus and much, much more. Here, we will try
to categorize them into 9 main areas filtered by criticality.

## Main

Crosslinks to CWE, SANS, OWASP and risks with descriptions will be added
soon.

## 9 most critical types of issues in source code \[EASSEC-ASDI-9-2013\]


1 Injections (code, SQL, OS)
2 Critical calls (to DB, to OS)
3 Missing or bad access control checks (missing auth checks)
4 Directory / path traversal (write, read, SMBRelay)
5 Modification of displayed content (XSS stored, XSS linked, JS/HTML
injections)
6 Backdoors (hardcoded credentials)
7 Covert channels (sockets, HTTP calls, SSRFs)
8 Information disclosure (hardcoded users, passwords, debug
information)
9 Obsolete statements (READ TABLE, kernel methods)

## Links

coming soon



## Authors

Alexander Polyakov

Alexander Minozhenko

Pavel Kuzmin