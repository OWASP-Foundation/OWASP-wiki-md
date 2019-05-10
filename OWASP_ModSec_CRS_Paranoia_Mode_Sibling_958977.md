*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 958977 : PHP Injection Attack: Function Name Found

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 958977`
`| 933110`
`| 933111-933114`
`| Rule now triggers on it's own`
`| none`

|}

` #`
` # [ PHP Function Names ]`
` # `
` # This is a paranoid sibling to 2.2.x Rule 958977.`
` # The rule is no longer chained in order to trigger anomaly scoring.`
` # For 3.0.0-rc1 rule, see 933110. `
` #`
` SecRule REQUEST_COOKIES|!REQUEST_COOKIES:/__utm/|REQUEST_COOKIES_NAMES|ARGS_NAMES|ARGS|XML:/* "@pmf php-function-names.data" \`
`       "msg:'PHP Injection Attack: Function Name Found',\`
`       phase:request,\`
`       rev:'2',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       maturity:'1',\`
`       accuracy:'8',\`
`       t:none,t:normalisePath,t:urldecode,\`
`       ctl:auditLogParts=+E,\`
`       block,\`
`       id:'XXXXXX',\`
`       `<tag:'application-multi>`',\`
`       `<tag:'language-PHP>`',\`
`       `<tag:'platform-multi>`',\`
`       `<tag:'attack-PHP>` injection',\`
`       `<tag:'OWASP_CRS/WEB_ATTACK/PHP_INJECTION>`',\`
`       `<tag:'OWASP_TOP_10/A1>`',\`
`       logdata:'Matched Data: %{TX.0} found within %{MATCHED_VAR_NAME}: %{MATCHED_VAR}',\`
`       severity:'CRITICAL',\`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.php_injection_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.%{rule.id}-OWASP_CRS/WEB_ATTACK/PHP_INJECTION-%{matched_var_name}=%{tx.0}"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")