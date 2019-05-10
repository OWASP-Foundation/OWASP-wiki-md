__TOC__

# Database objects

## Tables

### List table names

### List columns for a specific table

### View table permissions

### Change table permissions

### Create a table

## Stored procedures or functions

### List stored procedures or functions

### Parameters for a stored procedure or function

### Source code of a stored procedure or function

### Create a stored procedure or function

# System data

## Users

### Identify current user

### List of database users

### List of database administrators

### Database user permissions

### Create a new user

### Change a user password

### Delete a user

## Database server

### View database server settings

### Change database server settings

### View database server processes

### Kill database server process

## Host Operating System

### Operating System version

### OS environment variables

### Execute OS shell command

### Read file contents

### Arbitrary file writes

### File uploads

# Queries

## Strings

### Valid string delimiters

### String concatenation

### String-based queries with no quote characters

## Query syntax

### Result row count limiters

### Acceptable whitespace

### Tableless queries

### Query comments

### Command delimiters

### Set operators

Set operators are used to combine the results from two different
queries. The number of columns and order of column types must be
identical for both queries. The general syntax is

` SELECT`
`    fname, lname`
` FROM`
`    employees`
` `***`SET_OPERATOR`***
` SELECT`
`    fname, lname`
` FROM`
`    customers`

## Special queries

### Single column queries

### Single row queries

## Functions, etc.

### Data type casting

### Query output to file

# Attacks

## Breaking out of a query

### WHERE clauses

### FROM clauses

### Other parts of a SELECT

### INSERT statements

### UPDATE statements

## Inference and timing attacks

## SQL Tautologies

A tautology is something that is inherently true. SQL tautologies are
used when you want to force a query to return all results, basically
ignoring any WHERE conditionals. Simple tautologies like " OR 1=1" are
useful, but may be filtered out by some security tools. The table below
offers a number of tautologies that filter writers (even on well known
commercial tools) may not have considered.

| width="55%"       | Statement      | width="15%" | Numeric (1 = 1) | width="15%" | String ('a' = 'a') | width="15%" | Binary (0x1 = 0x1) |
| ----------------- | -------------- | ----------- | --------------- | ----------- | ------------------ | ----------- | ------------------ |
| ***a*** = ***a*** | align="center" | X           | align="center"  | X           | align="center"     | X           |                    |

# Data exfiltration

## E-mail

## Web

## General network

# Platform specific

## Unique database platform features

## Authoritative documentation resources

## Links