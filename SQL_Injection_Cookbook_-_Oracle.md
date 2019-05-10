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

String concatenation is performed by a double pipe (*' | |*').

` SELECT`
`    FirstName `

| | ' ' | | LastName

` FROM`
`    People`

## Query syntax

### Result row count limiters

### Acceptable whitespace

### Tableless queries

Tableless queries aren’t supported in Oracle per se. However, a special
table named "Dual" allows for similar functionality. This doesn't help
much for filter evasion since it still matches the standard SELECT
syntax.

` SELECT`
`    'This is a string'`
` FROM`
`    Dual`

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

**UNION**
Returns the rows from both queries, removing duplicates

**UNION ALL**
Returns the rows from both queries, duplicates are not removed.

**INTERSECT**
Returns the rows that are found in the results of both queries.

**MINUS**
Returns only the rows in the first query that are not found in the
second query.

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

| width="55%"                                                                                                                                                                                                                                        | Statement      | width="15%"    | Numeric (1 = 1) | width="15%" | String ('a' = 'a') | width="15%" | Binary (0x1 = 0x1) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | -------------- | --------------- | ----------- | ------------------ | ----------- | ------------------ |
| ***a*** = ***a***                                                                                                                                                                                                                                  | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** ^= ***b***                                                                                                                                                                                                                                 | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** \< ***b***                                                                                                                                                                                                                                 | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***b*** \> ***a***                                                                                                                                                                                                                                 | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** \<= ***b***                                                                                                                                                                                                                                | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***b*** \>= ***a***                                                                                                                                                                                                                                | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** \<\! ***b***                                                                                                                                                                                                                               | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***b*** \>\! ***a***                                                                                                                                                                                                                               | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a**'' *operator* ANY (***a**'', ***b***, ***c***, ***d***) where ''operator ''is any of the first 9 listed comparison operators; for the statement to be true, the operator must return true for ***a*** and least one of the items in the list | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a**'' *operator* SOME (***a**'', ***b***, ***c***, ***d***) SOME is a synonym of ANY                                                                                                                                                            | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a**'' ''operator *ALL (***a***, ***b***, ***c***, ***d***) similar to ANY, except that the operator must return true for ***a*** and all of the items in the list                                                                               | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a**'' IN (***c**'', ***b***, ***a***)                                                                                                                                                                                                           | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a**'' NOT IN (***d**'', ***c***, ***b***)                                                                                                                                                                                                       | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***b*** BETWEEN ***a*** AND ***c***                                                                                                                                                                                                                | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** NOT BETWEEN ***c*** AND ***d***                                                                                                                                                                                                            | align="center" | X              | align="center"  | X           | align="center"     | X           |                    |
| ***a*** LIKE ***a***                                                                                                                                                                                                                               |                | align="center" | X               |             |                    |             |                    |
| ***a*** NOT LIKE ***b***                                                                                                                                                                                                                           |                | align="center" | X               |             |                    |             |                    |

# Data exfiltration

## E-mail

## Web

## General network

# Platform specific

## Unique database platform features

## Authoritative documentation resources

## Links