During development of the [OWASP ModSec CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink"), there have been
discussions about various individual CRS rules, but they are mostly
unstructured.

This framework can be used to guide those discussions, and might provide
a checklist for a thorough evaluation of a CRS rule, and possible
actions to improve the rule.

## Contribution of a rule to user security

1.  **Is the rule or pattern useful for detecting attacks?** Can we find
    good example of attack requests?
2.  **Is the rule or pattern *essential* for detecting the attack?**
    That is, is there no other way to detect the attack class? If we
    have multiple mechanisms in our toolbox (e.g. `@detectSQLi` to
    detect SQLi in addition to regexps), a singular rule may become less
    important. If this rule is the only way to detect the attack
    however, the rule becomes more important.
3.  **Is the rule or pattern *complete* in detecting the attack?** For
    instance, we can completely rule out path traversal attacks by
    blocking \`../\` and its encoded forms, which makes it an important
    pattern. At the other hand, the data file `php-variables.data`
    indicates PHP code, but it's possible to inject PHP variables while
    bypassing this data file, so it contributes less.
4.  **How common is the attack?** Are the attacks seen in the wild? Do
    we have examples of mass scans or use in vulnerability scanners?
    Grep error- and audit-logs.
5.  **How severe would it be for a user if we would remove this rule?**
    If the attack is 'omitting an Accept header', the user loses only a
    signal for unusual activity. If the attack is a reliable remote code
    injection, the user loses a lot of security.

## Contribution of a rule to false positives

1.  **How big do we judge the chance of false positives?** Can we come
    up with reasonable examples of bona fide traffic that triggers the
    pattern?
2.  **Can we find false-positive matches in the logs?** Grep error- and
    audit-logs for a rule ID.
3.  **Do people often write exceptions for the rule?** Grep
    configurations for whitelistings and exceptions. Mailinglist posts
    and forum posts can be found in Google too.
4.  **How high is the rule severity?** Moat rules are written with
    severity "critical". But "notice" and "anomaly" can be used
    alternatively. If you are running in scoring mode, this makes a
    substantial difference. A false positive of a rule with 'critical'
    severity will cause downtime quickly.

## Strategies for resolution of false negatives

1.  **Improve completeness by adding alternative patterns.** For a rule
    detecting shell command injection, compile a list of possible other
    shell commands. For a rule detecting LFI injection, compile a list
    of high-value local files such as web application configuration
    files.
2.  **Create additional rule(s) to detect evasion techniques.** For
    example, attackers often hide PHP code by encoding it, but in this
    case they need a decoding function like `gzdecode` or
    `base64_decode` which we may be able to detect. Many more evasion
    methods exist and it takes a lot of experience to detect them as
    "WAF evasion" is an attack discpline on its own.
3.  **Make the rule more sensitive.** Some rules may count a number of
    characters. We might have the rule trigger at a lower number of
    characters. Or we can add more character to the list.
4.  **Increase potential total score.** If a rule does fire, but the
    total score remains low, consider partitioning patterns/data file
    entries into multiple rules. Each separate rule hit would increase
    the total attack score.

## Strategies for resolution of false positives

1.  **Keep the rule, but document.** If the rule is extremely important,
    and the level of false positives is not too high, we can consider to
    accept a false positive. We can possibly add a documentation example
    about whitelisting.
2.  **Make rule or pattern more specific.** For instance, instead of
    matching `sh` (which causes false positives in text) we can reason
    that an attacker likely wants to access `/bin/sh` or puts `sh` at
    the beginning of a string, so we can look for such patterns instead.
    This may allow us to keep the modified rule at original paranoia
    level so it protects as many users as possible.
3.  **Exclude some variables from checking.** For instance, if a rule
    checks cookies as well as parameters, and we find many false
    positives in cookies, we might consider excluding cookies from this
    rule, or splitting the cookie check into another rule.
4.  **Make the rule less sensitive, but create a more sensitive sibling
    at higher paranoia level.** If the rule or pattern is useful, and we
    can devise a less-sensitive version with less FP that would still
    contribute positively, we may adjust the rule in-place, and move the
    original rule to a higher paranoia level, so power users still can
    enjoy the full security offered by the original rule.
5.  **Move the whole rule to a higher paranoia level.** If we find the
    rule or pattern has a medium (but not high) contribution, and a high
    false positive rate, and we cannot separate or split the rule, we
    can consider moving the rule to a higher paranoia level. We will
    have to accept that novice users won't be protected.
6.  **Remove the rule completely.** If the rule's contribution is too
    low to justify the cost, even at high paranoia level, consider
    removing it.

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")