*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 981173 : SQL Injection Character Anomaly Usage

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 981173`
`| 942430`
`| 942431-942434`
`| Regex counter decreased from 4 to 1.`
`Anomaly scoring increased to critical.`
`| Regex for UUIDs in chained Rule`

|}

` #`
` # -=[ SQL Injection Character Anomaly Usage ]=-`
` #`
` # This is a paranoid sibling to 2.2.x Rule 981173.`
` # The regex limit is set to '1' and the anomaly scoring is increased to 'critical'.`
` # For dealing with false positives, UUID format is whitelisted with a chained rule.`
` # For 3.0.0-rc1 rule, see FIXME.`
` #`
` SecRule ARGS_NAMES|ARGS|XML:/* "([\~\!\@\#\$\%\^\&\*`\(\)`\-\+\=\{\}`\[\]``\|\:\;\"\'\´\’\‘\`\<\>].*?){1,}"\``
`       "chain,\`
`       phase:request,\`
`       rev:'2',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       maturity:'X',\`
`       accuracy:'Y',\`
`       t:none,t:urlDecodeUni,\`
`       block,\`
`       msg:'Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded',\`
`       id:'XXXXXX',\`
`       `<tag:'OWASP_CRS/WEB_ATTACK/SQL_INJECTION>`',\`
`       `<tag:'Paranoia>` rule on level Z',\`
`       logdata:'Matched Data: %{TX.1} found within %{MATCHED_VAR_NAME}: %{MATCHED_VAR}',\`
`       severity:'CRITICAL',\`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.%{rule.id}-OWASP_CRS/WEB_ATTACK/RESTRICTED_SQLI_CHARS-%{matched_var_name}=%{tx.0}"`
`       SecRule MATCHED_VARS "!@rx ^[a-f0-9-]{36}$"\`
`               "t:lowercase,\`
`               setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`               setvar:tx.sql_injection_score=+1"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")