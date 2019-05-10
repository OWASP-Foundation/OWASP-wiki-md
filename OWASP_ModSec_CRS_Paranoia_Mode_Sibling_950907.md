*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 950907 : OS Command Injection Attacks

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 950907`
`| 932100`
`| 932101-932104`
`| Rule now triggers on it's own`
`| none`

|}

` #`
` # OS Command Injection Attacks`
` #`
` # This is a paranoid sibling to 2.2.x Rule 950907.`
` # The rule is no longer chained in order to trigger anomaly scoring.`
` # For 3.0.0-rc1 rule, see 932100. `
` #`
` SecRule REQUEST_COOKIES|!REQUEST_COOKIES:/__utm/|REQUEST_COOKIES_NAMES|ARGS_NAMES|ARGS|XML:/* "@pmf os-commands.data" \`
`       "msg:'Remote Command Execution (RCE) Attempt',\`
`       phase:request,\`
`       rev:'2',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       maturity:'9',\`
`       accuracy:'8',\`
`       t:none,t:normalisePath,\`
`       ctl:auditLogParts=+E,\`
`       block,\`
`       id:'XXXXXX',\`
`       `<tag:'application-multi>`',\`
`       `<tag:'language-multi>`',\`
`       `<tag:'platform-multi>`',\`
`       `<tag:'attack-remote>` code execution',\`
`       `<tag:'OWASP_CRS/WEB_ATTACK/COMMAND_INJECTION>`',\`
`       `<tag:'WASCTC/WASC-31>`',\`
`       `<tag:'OWASP_TOP_10/A1>`',\`
`       `<tag:'PCI/6.5.2>`',\`
`       logdata:'Matched Data: %{TX.0} found within %{MATCHED_VAR_NAME}: %{MATCHED_VAR}',\`
`       severity:'CRITICAL',\`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.rce_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.%{rule.id}-OWASP_CRS/WEB_ATTACK/RCE-%{matched_var_name}=%{tx.0}"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")