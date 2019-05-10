## Abstract

This is a page about the development of a paranoia mode aka bringing
back the rules that used to yield a high number of false positives. This
little project is aimed at inclusion into the 3.0.0 release of the OWASP
ModSecurity Core Rules, where some rules have been removed in order to
reduce the number of false positives with vanilla installations.

FIXME: Detailed description

*Back to the [OWASP ModSecurity Core Rules
Set](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink").*

## Sub-Project Infos

  - **Status**: active (January 2016)
  - **Schedule**: **DONE** (we're all done and Paranoia Mode made it
    into the CRS3 release.
  - **Who**: Christian Folini (dune73), Noël Zindel (zino), Franziska
    Bühler (franziskabuehler), Manuel Leos (Spartan), Walter Hop
    (lifeforms)
  - **Documentation**: Here on the [OWASP
    Wiki](https://www.owasp.org/index.php/OWASP_ModSec_CRS_Paranoia_Mode)
    / [Mechanics
    Proposal](https://www.netnea.com/cms/2016/02/04/owasp-modsecurity-core-rules-paranoia-mode-mechanics-proposal/)
  - **Discussion / Archive**:
    `owasp-modsecurity-core-rule-set@lists.owasp.org` / archive:
    <http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/>
  - **Github Link v3.0.0-rc1 (our base)**:
    <https://github.com/SpiderLabs/owasp-modsecurity-crs/tree/v3.0.0-rc1>
  - **Github Link paranoia-mode**:
    <https://github.com/dune73/owasp-modsecurity-crs/tree/paranoia-mode>
  - **Final Pull Request \#1: Add paranoia mode mechanics**:
    <https://github.com/SpiderLabs/owasp-modsecurity-crs/pull/292>
    MERGED
  - **Final Pull Request \#2: Move first rules to paranoia mode**:
    <https://github.com/SpiderLabs/owasp-modsecurity-crs/pull/300>
    MERGED
  - **Final Pull Request \#3: Add 2.2.X rules to paranoia mode**:
    <https://github.com/SpiderLabs/owasp-modsecurity-crs/pull/308>
    MERGED
  - **Final Pull Request \#4: Add stricter siblings**: FIXME

## Tasks

### Open Tasks

Please define state as follows: *new*, *assigned*, *waiting*, *closed*.
When a task is closed, it is moved to the seperate closed tasks table
below.

`class="wikitable"`

| class="wikitable"

` |`**`Task`**
` |         `**`Who`**`       `
` |    `**`Status`**`   `

|-

` | Write pull request number 4`
` | n.n.`
` | new`

|-

` | Submit pull request number 4`
` | n.n.`
` | new`

|-

` | Draw flowchart`
` | n.n.`
` | new`

|-

` | Write documentation`
` | Christian`
` | new`

|}

### Closed Tasks

`class="wikitable"`

| class="wikitable"

` |`**`Task`**
` |         `**`Who`**`       `
` |    `**`Status`**`   `

|-

` | Assemble list of rules, which triggered false positives in 2.2.X frequently`
` | Christian`
` | closed`

|-

` | Assemble list of 2.2.x rules, which have disappeared from 3.0.0-rc1`
` | Spartan`
` | closed`

|-

` | Assemble list of 3.0.0-rc1 rules, which could be accompanied with`
`stricter siblings in paranoia mode`
`(same idea of the rule, but harder limit etc.)`
` | Christian`
` | closed`

|-

` | Assemble list of 3.0.0-rc1 rules, which could be moved to the paranoia mode`
` | Franziska`
` | closed`

|-

` | Assemble list of disappeared / missing 2.2.X base_rules, which should be brought back`
` | group`
` | closed`

|-

` | Assemble list of 2.2.X optional and experimental rules, which should be brought back`
` | group`
` | closed (could be repeated more throughly)`

|-

` | Nail down final list of rules which should be moved / recreated into the paranoia mode`
` | group`
` | closed`

|-

` | Sort out mechanics of the paranoia mode`
` | Christian`
` | closed`

|-

` | Write new stricter siblings for existing rules`
` | Noël`
` | closed`

|-

` | Define ID-space for strict siblings`
` | Fraziska, group`
` | closed`

|-

` | Define exact syntax of paranoia mode setup`
` | Christian, group`
` | closed`

|-

` | Sort out name: Is "Paranoia Mode" really the right term?`
` | Christian, group`
` | closed`

|}

## Rules

### Paranoia Mode Candidates

The 3.0.0-rc1 has all rules renumbered. Existing numbering was fairly
crazy and the new numbering follows the numbering scheme of the rules
files (-\> 9\<2-digit-rulefile\>\<3-digit-id\>) A mapping table exists
[IdNumbering.csv](https://github.com/SpiderLabs/owasp-modsecurity-crs/blob/v3.0.0-rc1/id_renumbering/IdNumbering.csv)
We need to make sure, we do not mess things up, so let's add both IDs to
the table, the old one and the new one.

Please set status as follows : *confirmed*,*candidate*,
*cloning-confirmed*,*cloning-candidate*, *unsure*, *dropped*.

  - 'cloning-confirmed', 'cloning-candidates' are rules, that could be
    cloned into an even stricter variant with a stricter limit in a
    higher paranoia setting.
  - If dropped, please provide reasoning in the remarks.

`class="wikitable"`

| class="wikitable"

` |`**`RuleID``   ``2.2.x`**
` |`**`RuleID``   ``3.0.0-rc1`**
` |         `**`msg`**`       `
` |    `**`Status`**`   `
` |    `**`Remarks`**`   `

|-

` | 950001`
` | 942150`
` | SQL Injection Attack`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Also Franziska's candidate: @pmf file with very short function names, could match frequently.`

|-

` | 950109`
` | 920230`
` | Multiple URL Encoding Detected`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives`

|-

` | 950120`
` | 931130`
` | Possible Remote File Inclusion (RFI) Attack: Off-Domain Reference/Link`
` | confirmed`
` | Walter's 2.2.X candidate: many FP; Chrstian: hardly any FPs; `
`discussion concluded, that rule should end up in paranoia mode, possibly with additional conditions to reduce FPs (scope outside of this paranoia mode project)`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001885.html)

|-

` | 960335`
` | 920380`
` | Too many arguments in request`
` | confirmed`
` | Walter's 2.2.X candidate: some FP (phpMyAdmin, large forms), alternatively would recommend raising tx.max_num_args to 1000`

|-

` | 950901`
` | 942130`
` | SQL Injection Attack: SQL Tautology Detected.`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Also Franziska's candidate: legitimate sentences could match. Walter's 2.2.x experience: many FP in natural text however the rule seems to have merit`

|-

` | 950916`
` | 921170`
` | HTTP Header Injection Attack via payload (CR/LF detected)`
` | confirmed`
` | Franziska's candidate: change action from pass to block and move to paranoia mode.`

|-

` | 959070`
` | gone -> 942380  `
` | SQL Injection Attack`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives`

|-

` | 959071`
` | gone -> 942390 `
` | SQL Injection Attack`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives`

|-

` | 959072`
` | gone -> 942400  `
` | SQL Injection Attack`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives`

|-

` | 959073`
` | gone -> 942410  `
` | SQL Injection Attack`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives`

|-

` | 960015`
` | 920300`
` | Request Missing an Accept Header`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Also Franziska's candidate: Not every legitimate client behaves correctly. Walter's experience: many FP (PHP SoapClient)`
`Discussion concluded it's moved to paranoia mode.`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001888.html)
`Spartan: Many mobile devices do not send this header, very high FP.`

|-

` | 960024`
` | gone -> 942460 `
` | Meta-Character Anomaly Detection Alert - Repetative Non-Word Characters`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives`

|-

` | 960035`
` | 920440`
` | URL file extension is restricted by policy`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives`

|-

` | 970901`
` | 950100`
` | The Application Returned a 500-Level Status Code`
` | confirmed`
` | Franziska's candidate: too strict, too generic, no data leakage happened so far. Walter: it's useful however to prevent attacker from distinguishing between a failed SQLi attempt (403 blocked by ModSec) or a query error due to vulnerable app (500 from application); `
`Discussion resolved with move to paranoia mode. 403 will cloak a backend error, which is hard for an inexperienced admin and thus complicates things in standard installations`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001889.html)

|-

` | 973300`
` | gone -> 941320 `
` | Possible XSS Attack Detected - HTML Tag Handler`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP`

|-

` | 973332`
` | gone -> 941330 `
` | IE XSS Filters - Attack Detected.`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP`

|-

` | 973333`
` | gone -> 941340 `
` | IE XSS Filters - Attack Detected.`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP`

|-

` | 981172`
` | gone -> 942420 `
` | Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: very high FP`

|-

` | 981173`
` | gone -> 942430 `
` | Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: very high FP`

|-

` | 981231`
` | gone -> 942440 `
` | SQL Comment Sequence Detected.`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: high FP but rule seems useful`

|-

` | 981240`
` | 942300`
` | Detects MySQL comments, conditions and ch(a)r injections`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP`

|-

` | 981242`
` | 942330`
` | Detects classic SQL injection probings 1/2`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Also Franziska's candidate: one quote character already matches?? Walter: low FP, but seen in cookies injected by some US ISPs; `

|-

` | 981243`
` | 942370`
` | Detects classic SQL injection probings 2/2`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: medium FP`

|-

` | 981244`
` | 942180`
` | Detects basic SQL authentication bypass attempts 1/3`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP; `
` discussion did not bring up additional arguments. Moving to paranoia mode`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001890.html)

|-

` | 981245`
` | 942260`
` | Detects basic SQL authentication bypass attempts 2/3`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: medium FP`

|-

` | 981246`
` | 942340`
` | Detects basic SQL authentication bypass attempts 3/3`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: medium FP`

|-

` | 981248`
` | 942210`
` | Detects chained SQL injection attempts 1/2`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: low FP, `
` discussion did not bring up any additional arguments. Moving to paranoia mode`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001890.html)

|-

` | 981249`
` | 942310`
` | Detects chained SQL injection attempts 2/2`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: low FP but seen in very specific situations`

|-

` | 981257`
` | 942200`
` | Detects MySQL comment-/space-obfuscated injections and backtick termination`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Walter: medium FP`

|-

` | 981260`
` | gone -> 942450 `
` | SQL Hex Encoding Identified`
` | confirmed`
` | Christian's 2.2.X experience: very frequently false positives. Walter: high FP in long random strings`

|-

` | 981318`
` | 942110`
` | SQL Injection Attack: Common Injection Testing Detected`
` | confirmed`
` | Franziska's candidate: one quote character at the beginning/end really not legitimate? Walter 2.2.X candidate: frequent FP`

|-

` | 981319`
` | 942120`
` | SQL Injection Attack: SQL Operator Detected`
` | confirmed`
` | Christian's 2.2.X experience: frequently false positives. Also Franziska's candidate: very short operators or strings already match. Walter: some FP (WooCommerce)`

|-

` | 981049`
` | 912100`
` | Potential Denial of Service (DoS) Attack from ... - # of Request Bursts: ...       `
` | cloning-confirmed   `
` | limit currently at 2; could be set to 1; now, the attacker has to exceed dos_counter_threshold twice. With full reset of counter after first hit. Source: 2.2.X->experimental rules`

|-

` | 960901          `
` | 920270          `
` | Invalid character in request`
` | cloning-confirmed   `
` | @validateByteRange 1-255; there was a conditional rule with stricter byterange 32-126 in 2.2.X as well`

|-

` | 970003          `
` | 951100          `
` | none                                           `
` | cloning-confirmed   `
` | rule is only setting tx.sql_error_match. Could also trigger score directly`

|-

` | 950907          `
` | 932100          `
` | Remote Command Execution (RCE) Attempt                         `
` | cloning-confirmed   `
` | rule is only triggering in combination with chained rule. Could trigger on its on`

|-

` | 958977          `
` | 933110          `
` | PHP Injection Attack: Function Name Found                       `
` | cloning-confirmed`
` | rule is only triggering in combination with chained rule. Could trigger on its on`

|-

` | 958979          `
` | 933120          `
` | PHP Injection Attack: Configuration Directive Found                 `
` | cloning-candidate`
` | rule is only triggering in combination with chained rule. Could trigger on its on`

|-

` | 950001          `
` | 942150          `
` | SQL Injection Attack                                    `
` | cloning-confirmed`
` | rule is only triggering in combination with chained rule. Could trigger on its on`

|-

` | 950907`
` | 932100`
` | System Command Injection`
` | dropped`
` | Christian's 2.2.X experience: frequently false positives. Also Franziska's candidate: false positives possible because of @pmf, file with short cmds. Discussion evolved about splitting the file, which everybody thinks is a good idea. But that would be outside the scope of the introduction of the paranoia mode. So the rule stays in the standard set of rules for the time being and will be split in the future `[`Link``
 ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001886.html)

|-

` | 900050`
` | 910100`
` | Client IP is from a HIGH Risk Country Location.`
` | dropped`
` | Franziska's candidate: Do we want to exlude countries? But then easy to configure. Discussion pointed out this as an effective rule. We leave it in the standard rules, but provide an empty country list by default `[`Link``
 ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001951.html)`. `[`Separate``
 ``pull``
 ``request`](https://github.com/SpiderLabs/owasp-modsecurity-crs/pull/284)

|-

` | 960017`
` | 920350`
` | Host header is a numeric IP address`
` | dropped`
` | Christian's 2.2.X experience: very frequently false positives. Also Franziska's candidate: Not every legitimate client behaves correctly. Walter's experience: low FP (almost all are mass scans); `
` Discussion concluded that legitimate use of numeric IP addresses is rare. This is really mostly mass scanners. Rule will be kept in standard set of rules`
[`Link``   ``to``
 ``discussion`](http://lists.owasp.org/pipermail/owasp-modsecurity-core-rule-set/2016-February/001888.html)

|-

` | 958977`
` | 933110`
` | PHP Injection Attack: Function Name Found`
` | dropped`
` | Franziska's candidate: false positives possible because of @pmf, file with short function names. Maybe we should split the data file. The discussion revealed that splitting the data file in a clean way is very difficult. Walter Hop volunteered to rework the php rules completely. Chaim might join that effort.`

|-

` | 958979`
` | 933120`
` | PHP Injection Attack: Configuration Directive Found`
` | dropped`
` | Franziska's candidate: false positives possible because of @pmf, file with short configuration directives. Splitting file?  The discussion revealed that splitting the data file in a clean way is very difficult. Walter Hop volunteered to rework the php rules completely. Chaim might join that effort.`

|}

### Rules from 2.2.X, missing in 3.0.0-rc1

It looks as if only the base_rules made it into 3.0.0. In fact there
are a few rule ids know from the optional and experimental rule folders
in 2.2.X, but it is more likely, these are new 3.0.0 rules reusing old
rule ids as the rules (regexes and msg) do not match at all.

When trying to generate the list below, be aware that the rule ids have
been renumbered between 3.0.0-dev and 3.0.0-rc1. IdNumbering.csv in your
friend.

#### Base rules

`class="wikitable"`

| class="wikitable"

` |`**`2.2.X``   ``rule``   ``id`**
` |         `**`msg`**`       `
` |    `**`remarks`**`   `

|-

` | 950002`
` | System Command Access`
` | `

|-

` | 950006`
` | System Command Injection`
` | `

|-

` | 950007`
` | Blind SQL Injection Attack`
` | `

|-

` | 950008`
` | Injection of Undocumented ColdFusion Tags`
` | `

|-

` | 950010`
` | LDAP Injection Attack`
` | `

|-

` | 950011`
` | SSI injection Attack`
` | `

|-

` | 950018`
` | Universal PDF XSS URL Detected.`
` | Walter: medium FP (foo.pdf#javascript)`

|-

` | 950019`
` | Email Injection Attack`
` | `

|-

` | 950908`
` | SQL Injection Attack.`
` | `

|-

` | 950921`
` | Backdoor access`
` | `

|-

` | 950922`
` | Backdoor access`
` | `

|-

` | 958000`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958001`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958002`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958003`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958004`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958005`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958006`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958007`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958008`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958009`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958010`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958011`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958012`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958013`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958016`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958017`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958018`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958019`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958020`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958022`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958023`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958024`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958025`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958026`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958027`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958028`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958030`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958031`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958032`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958033`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958034`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958036`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958037`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958038`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958039`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958040`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958041`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958045`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958046`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958047`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958049`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958051`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958052`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958054`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958056`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958057`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958059`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958291`
` | Range: field exists and begins with 0.`
` | Walter: high FP (Chrome PDF viewer) and not useful.`

|-

` | 958404`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958405`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958406`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958407`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958408`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958409`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958410`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958411`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958412`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958413`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958414`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958415`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958416`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958417`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958418`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958419`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958420`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958421`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958422`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958423`
` | Cross-site Scripting (XSS) Attack`
` | `

|-

` | 958976`
` | PHP Injection Attack`
` | `

|-

` | 959070`
` | SQL Injection Attack`
` | `

|-

` | 959071`
` | SQL Injection Attack`
` | `

|-

` | 959072`
` | SQL Injection Attack`
` | `

|-

` | 959073`
` | SQL Injection Attack`
` | `

|-

` | 960014`
` | Proxy access attempt`
` | `

|-

` | 960018`
` | Invalid character in request`
` | `

|-

` | 960020`
` | Pragma Header requires Cache-Control Header for HTTP/1.1 requests.`
` | Walter: some FP`

|-

` | 960022`
` | UNKNOWN`
` | `

|-

` | 960024`
` | Meta-Character Anomaly Detection Alert - Repetative Non-Word Characters`
` | Walter: many FP`

|-

` | 960902`
` | UNKNOWN`
` | `

|-

` | 960913`
` | Invalid request`
` | `

|-

` | 970007`
` | Zope Information Leakage`
` | `

|-

` | 970008`
` | Cold Fusion Information Leakage`
` | `

|-

` | 970010`
` | ISA server existence revealed`
` | `

|-

` | 970011`
` | File or Directory Names Leakage`
` | `

|-

` | 970012`
` | Microsoft Office document properties leakage`
` | `

|-

` | 970016`
` | Cold Fusion source code leakage`
` | Walter: some FP but not using this language`

|-

` | 970018`
` | IIS installed in default location`
` | `

|-

` | 970021`
` | WebLogic information disclosure`
` | `

|-

` | 970903`
` | ASP/JSP source code leakage`
` | Walter: some FP but not using this language`

|-

` | 973300`
` | Possible XSS Attack Detected - HTML Tag Handler`
` | `

|-

` | 973301`
` | XSS Attack Detected`
` | `

|-

` | 973302`
` | XSS Attack Detected`
` | `

|-

` | 973303`
` | XSS Attack Detected`
` | `

|-

` | 973304`
` | XSS Attack Detected`
` | `

|-

` | 973305`
` | XSS Attack Detected`
` | `

|-

` | 973306`
` | XSS Attack Detected`
` | `

|-

` | 973307`
` | XSS Attack Detected`
` | `

|-

` | 973308`
` | XSS Attack Detected`
` | `

|-

` | 973309`
` | XSS Attack Detected`
` | `

|-

` | 973310`
` | XSS Attack Detected`
` | `

|-

` | 973311`
` | XSS Attack Detected`
` | `

|-

` | 973312`
` | XSS Attack Detected`
` | `

|-

` | 973313`
` | XSS Attack Detected`
` | `

|-

` | 973314`
` | XSS Attack Detected`
` | `

|-

` | 973316`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973325`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973327`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973328`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973329`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973330`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973331`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973332`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973333`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 973334`
` | IE XSS Filters - Attack Detected.`
` | Walter: many FP in text`

|-

` | 973335`
` | IE XSS Filters - Attack Detected.`
` | Walter: many FP in text`

|-

` | 973347`
` | IE XSS Filters - Attack Detected.`
` | `

|-

` | 981000`
` | Possibly malicious iframe tag in output`
` | Walter: medium FP`

|-

` | 981001`
` | Possibly malicious iframe tag in output`
` | Walter: medium FP (iframes with display:none)`

|-

` | 981003`
` | Malicious iframe+javascript tag in output`
` | `

|-

` | 981004`
` | Potential Obfuscated Javascript in Output - Excessive fromCharCode`
` | Walter: many FP (Wordpress 4.4 inlined emoji javascripts); folinic: Problem solved in WP: `<https://core.trac.wordpress.org/ticket/35412>

|-

` | 981005`
` | Potential Obfuscated Javascript in Output - Eval+Unescape`
` | `

|-

` | 981006`
` | Potential Obfuscated Javascript in Output - Unescape`
` | `

|-

` | 981007`
` | Potential Obfuscated Javascript in Output - Heap Spray`
` | `

|-

` | 981018`
` | UNKNOWN`
` | `

|-

` | 981022`
` | UNKNOWN`
` | `

|-

` | 981133`
` | UNKNOWN`
` | `

|-

` | 981134`
` | UNKNOWN`
` | `

|-

` | 981136`
` | UNKNOWN`
` | `

|-

` | 981172`
` | Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded`
` | Walter: many FP`

|-

` | 981173`
` | Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded`
` | Walter: many FP`

|-

` | 981177`
` | UNKNOWN`
` | `

|-

` | 981178`
` | UNKNOWN`
` | `

|-

` | 981231`
` | SQL Comment Sequence Detected.`
` | `

|-

` | 981260`
` | SQL Hex Encoding Identified`
` | `

|-

` | 981300`
` | UNKNOWN`
` | `

|-

` | 981301`
` | UNKNOWN`
` | `

|-

` | 981302`
` | UNKNOWN`
` | `

|-

` | 981303`
` | UNKNOWN`
` | `

|-

` | 981304`
` | UNKNOWN`
` | `

|-

` | 981305`
` | UNKNOWN`
` | `

|-

` | 981306`
` | UNKNOWN`
` | `

|-

` | 981307`
` | UNKNOWN`
` | `

|-

` | 981308`
` | UNKNOWN`
` | `

|-

` | 981309`
` | UNKNOWN`
` | `

|-

` | 981310`
` | UNKNOWN`
` | `

|-

` | 981311`
` | UNKNOWN`
` | `

|-

` | 981312`
` | UNKNOWN`
` | `

|-

` | 981313`
` | UNKNOWN`
` | `

|-

` | 981314`
` | UNKNOWN`
` | `

|-

` | 981315`
` | UNKNOWN`
` | `

|-

` | 981316`
` | SQL SELECT Statement Anomaly Detection Alert`
` | `

|-

` | 981317`
` | SQL SELECT Statement Anomaly Detection Alert`
` | `

|-

` | 990012`
` | Rogue web site crawler`
` | `

|}

#### Optional, experimental, slr rules

`class="wikitable"`

| class="wikitable"

`| 900048`
`| Identifies Reflected XSS (optional_rules)`
`| Walter: could be very interesting candidate but have not used it in production`

|-

`| 920021, 920022, 920023`
`| Possible Credit Card Track 1 Data Leakage. (experimental_rules)`
`| Walter: could be interesting candidates but have not used it in production`

|-

`| 981080, 920020, 920006`
`| Detect CC# in output and block transaction (optional_rules)`
`| Walter: could be interesting candidate but have not used it in production`

|-

`| 900047, 900048, 981180, 981182`
`| Identifies Stored XSS (optional_rules)`
`| Walter: could be somewhat interesting candidate but have not used it in production`

|}

### Stricter siblings for existing rules

Stricter Siblings are rules that are present in the CRS but could be
accompanied by a stricter clone in Paranoia Mode. Adjustments can differ
from rule to rule but include higher anomaly ratings or stricter
triggers (e.g. regex counters). To prevent masses of false positives,
rules can come with additional filters (chained rules) for common
use-cases. These can either be included into Paranoia Mode or simply
serve as a recommendation.

Note: To avoid a cluttered project main-page, rule proposals are
documented in their respective sub-page. When adding new proposals, make
sure adding the rules original (2.2.x) ID, a quick description of what
changes were made, and, if applicable, which additional filters were
added. For every proposed rule change, we will create a [Github
issue](https://github.com/SpiderLabs/owasp-modsecurity-crs/issues);
after discussion a pull request will be created. For brainstorming about
CRS rules, see our [OWASP ModSecurity rule evaluation
framework](OWASP_ModSecurity_rule_evaluation_framework "wikilink").

**Possible siblings:**

[981173 : SQL Injection Character Anomaly
Usage](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_981173 "wikilink")
[981172 : SQL Injection Character Anomaly
Usage](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_981172 "wikilink")
[981049 : Potential Denial of Service
(DoS)](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_981049 "wikilink")
[970003 : SQL Error
Leakage](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_970003 "wikilink")
[960901 : Invalid character in
request](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_960901 "wikilink")
[958980 : PHP Injection Attack: Variables
Found](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_958980 "wikilink")
[958979 : PHP Injection Attack: Configuration Directive
Found](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_958979 "wikilink")
[958977 : PHP Injection Attack: Function Name
Found](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_958977 "wikilink")
[950907 : Remote Command Execution (RCE)
Attempt](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_950907 "wikilink")
[950001 : SQL Injection
Attack](OWASP_ModSec_CRS_Paranoia_Mode_Sibling_950001 "wikilink")

## Project Status

### Project Status January 30, 2016

<code> Hello everybody,

It's time to do a status report of our little core rules project.

I am including Franziska Bühler and Walter Hop in this status mail. Both
are experienced ModSec sysadmins. Franziska contributed to this first
stage, Walter told me he does not have much time, but he was interested
in participating at least in the discussions about the rules.

All in all, this is taking more time than anticipated. But we have also
done things very throughly than I thought. Which is generally a good
thing.

Done so far:

  - Manuel has provided us with a list of rules removed between 2.2.x
    and 3.0.0rc1
  - I have assembled a list of rules known to trigger false positives
    frequently in the 2.2.x ruleset, they are thus candidates for the
    paranoia mode
  - Franziska has looked through the 3.0.0rc1 rules and identified a set
    of rules which look like good candidates.
  - Noël has sharpened his skills by re-writing 981173 in a way that
    ignores innocent UUIDs. In my eyes, he found a very elegant
    solution.
  - With the development of 3.0.0-dev, Chaim unfortunately reused rule
    ids formerly used with optional and experimental rules. Now this has
    all been renumbered. I have pointed this out in the mailinglist and
    had private contact with Chaim where he confirmed the fact - and
    promised to resolve the issue.

We have not really looked at the disappeared rules and identified those
who should be brought back and have not been picked so far. This
includes the 2.2.X base_rules, but also the optional, experimental, and
huge stock of slr rules. Of these three groups, only the anti-ddos rules
have made it into 3.0.0. There are probably more interesting candidates.

If somebody among you wants to look into these, then that would be
welcome, but I do not want to have these tasks delay us any further.
After all, Old rules can also be brought back in subsequent releases if
we see a benefit.

So the next real tasks are:

  - Looking through the list of candidates and cloning-candidates (the
    latter are those rules we might accompany with a clone with stricter
    limits in paranoia mode).
  - Defining the exact working of the paranoia mode.

Please sit down and look through the rule lists in the wiki and add
remarks with regards to the candidate rules. If you think a rule should
be included, if you think an individual rule should not be included etc.

I am also going to invite the people on the mailinglist to take look at
the rules as well and add their remarks in the wiki (or respond via
mail). This should allow us to nail down the list of rules which will
actually be included in the paranoia mode.

As for defining the exact working of the paranoia mode, I guess I need
to write down the idea I have in mind and see if it makes sense to you.

Thank you for contributing so far\! It is a lot of fun to work in a
team\!

Christian

</code>

## Git help

#### How to Perform Pull Request to CRS v3.0.0-rc1

**By Walter Hop**

This example assumes that the Github username is 'lifeforms', replace
with your own username.

**Step 1. Create a Github fork of the original repository**

  - a. Browse to CRS:
    <https://github.com/SpiderLabs/owasp-modsecurity-crs>
  - b. Click "Fork" button in the top right

'''Step 2. Download your Github fork, and checkout the correct branch
'''
`git clone git@github.com:lifeforms/owasp-modsecurity-crs.git`
`cd owasp-modsecurity-crs`
`git checkout v3.0.0-rc1`

**Step 3. Add the original repository as upstream, to integrate new
changes easily**
<code>

`   git remote add upstream git@github.com:SpiderLabs/owasp-modsecurity-crs.git`

</code>

**Step 4. Make sure your forked repo is up to date with changes in the
original repository**
You need to re-do these steps if somebody else made changes to upstream
in the meantime\!

`git checkout v3.0.0-rc1`
`git fetch upstream`
`git merge --ff upstream/v3.0.0-rc1`
`git push`

**Step 5. Create a branch for every separate issue you'd like to
fix.**
`git checkout -b myfeature v3.0.0-rc1`
`git push --set-upstream origin myfeature`

**Step 6. Make local changes and commit them**
`git add ...`
`git commit`

**Step 7. Push your local changes to your fork at Github**
`git push`

**Step 8. Create the pull request**

  - a. Browse to your own fork:
    <https://github.com/lifeforms/owasp-modsecurity-crs>
  - b. Click "New pull request" button
  - c. In the "base fork", ensure that the correct branch is selected:
    v3.0.0-rc1
  - d. In the "head fork", pick "myfeature" (if you used branches) or
    v3.0.0-rc1 (if you didn't)
  - e. Review the content of the pull request (should only contain your
    commits)
  - f. Press "Create pull request" button

**Optional: Updating your pull request**

After opening the pull request, people will review it, and probably will
make some suggestions for changes before the PR can be accepted. You can
keep pushing to your branch, and it will be reflected in the PR.

If in the meantime the code in upstream has drifted, you should re-do
step 4 above.

Then, just change some files, commit and push.

`git add ...`
`git commit`
`git push`

See also:

  - <https://help.github.com/articles/fork-a-repo/>
  - <https://help.github.com/articles/syncing-a-fork/>
  - <https://help.github.com/articles/using-pull-requests/>

#### Testing someone else's pull request

To test a PR locally, use the following commands to create a branch for
it.

In this example we check out PR \#427, creating a branch `chaim-headers`
locally (you can use any name):

    git fetch upstream pull/427/head:chaim-headers
    git checkout chaim-headers

#### Pushing to someone else's pull request

In an editable PR, the PR will say something like:

    Add more commits by pushing to the ExceptionSupport branch on csanders-git/owasp-modsecurity-crs.

To add to branch `ExceptionSupport` of user `csanders-git`, do:

    git remote add chaim git@github.com:csanders-git/owasp-modsecurity-crs.git
    git fetch chaim
    git co ExceptionSupport
    git add ...
    git push

#### Purging a file completely from Git

Delete the file from the repo:

    git rm file
    git commit
    git push

Download [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)

Make a NEW mirror:

    git clone --mirror git@github.com:SpiderLabs/owasp-modsecurity-crs.git
    cd owasp-modsecurity-crs.git

Purge the file:

    java -jar ~/Downloads/bfg-*.jar --delete-files example.png
    git reflog expire --expire=now --all && git gc --prune=now --aggressive
    git push -f

E-mail all users to REMOVE their copies of the repositories, and do a
FRESH CLONE of the repo. If a user pulls again, the divergent histories
will be merged, and there is a big risk that the dirty history
(containing the purged file) will return again when they push later.

See also: [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")