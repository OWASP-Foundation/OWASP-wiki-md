*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 970003 : SQL Error Leakage

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 970003`
`| 951100`
`| 951101-951104`
`| Triggers anomaly score directly now`
`| none`

|}

` #`
` # -=[ SQL Error Leakage ]=-`
` #`
` # This is a paranoid sibling to 2.2.9 Rule 970003.`
` # The rule now triggers the anomaly scoring instantly`
` # instead of just setting tx.sql_error_match.`
` # For 3.0.0-rc1 rule, see 951100.`
` #`
` SecRule RESPONSE_BODY "@pmFromFile sql-errors.data" \`
`       "phase:response,\`
`       id:XXXXXX,\`
`       rev:'5',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       pass,\`
`       nolog,\`
`       `<tag:'application-multi>`',\`
`       `<tag:'language-multi>`',\`
`       `<tag:'platform-multi>`',\`
`       `<tag:'attack-information>` disclosure',\`
`       setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},\`
`       t:none"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")