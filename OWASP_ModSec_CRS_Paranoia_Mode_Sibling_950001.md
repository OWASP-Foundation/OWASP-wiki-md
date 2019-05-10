*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 950001 : SQL Injection Attack

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 950001`
`| 942150`
`| 942151-942154`
`| Rule now triggers on it's own`
`| none`

|}

` #`
` # -=[ SQL Function Names ]=-`
` #`
` # This is a paranoid sibling to 2.2.x Rule 950001.`
` # The rule is no longer chained in order to trigger anomaly scoring.`
` # For 3.0.0-rc1 rule, see 942150.`
` #`
` SecRule REQUEST_COOKIES|!REQUEST_COOKIES:/__utm/|REQUEST_COOKIES_NAMES|ARGS_NAMES|ARGS|XML:/* "@pmf sql-function-names.data" \`
`       "msg:'SQL Injection Attack',\`
`       phase:request,\`
`       rev:'2',\`
`       ver:'OWASP_CRS/2.2.6',\`
`       maturity:'9',\`
`       accuracy:'8',\`
`       capture,\`
`       t:none,t:urlDecodeUni,\`
`       ctl:auditLogParts=+E,\`
`       block,\`
`       id:'XXXXXX',\`
`       `<tag:'application-multi>`',\`
`       `<tag:'language-mutli>`',\`
`       `<tag:'platform-multi>`',\`
`       `<tag:'attack-sqli>`',\`
`       `<tag:'OWASP_CRS/WEB_ATTACK/SQL_INJECTION>`',\`
`       `<tag:'WASCTC/WASC-19>`',\`
`       `<tag:'OWASP_TOP_10/A1>`',\`
`       `<tag:'OWASP_AppSensor/CIE1>`',\`
`       `<tag:'PCI/6.5.2>`',\`
`       logdata:'Matched Data: %{TX.0} found within %{MATCHED_VAR_NAME}: %{MATCHED_VAR}',\`
`       severity:'CRITICAL'`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.sql_injection_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.%{rule.id}-OWASP_CRS/WEB_ATTACK/SQL_INJECTION-%{matched_var_name}=%{tx.0}"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")