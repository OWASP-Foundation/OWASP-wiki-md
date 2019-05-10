*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 981172 : SQL Injection Character Anomaly Usage

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 981172`
`| 942420`
`| 942421-942424`
`| Regex counter decreased from 8 to 2.`
`Anomaly scoring increased to critical.`
`| None`

|}

` #`
` # -=[ SQL Injection Character Anomaly Usage  ]=-`
` #`
` # This is a paranoid sibling to 2.2.9 Rule 981172.`
` # The regex limit is set to '2' and the anomaly scoring is increased to 'critical'.`
` #`
` SecRule REQUEST_COOKIES|!REQUEST_COOKIES:/__utm/|!REQUEST_COOKIES:/__utm/|REQUEST_COOKIES_NAMES "([\~\!\@\#\$\%\^\&\*`\(\)`\-\+\=\{\}`\[\]``\|\:\;\"\'\´\’\‘\`\<\>].*?){2,}"``
`       "capture,\`
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
`       setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`       setvar:tx.sql_injection_score=+1,\`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.%{rule.id}-OWASP_CRS/WEB_ATTACK/RESTRICTED_SQLI_CHARS-%{matched_var_name}=%{tx.0}"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")