*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 960901 : Invalid character in request

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 960901`
`| 920270`
`| 920271-920274`
`| Character byte range limited to 32-126.`
`| none`

|}

` #`
` # [ Invalid character in request ]`
` #`
` # This is a paranoid sibling to 2.2.x Rule 960901.`
` # Byte range restrictions are now set to 32-126.`
` # For 3.0.0-rc1 rule, see 920270. `
` #`
` SecRule ARGS|ARGS_NAMES|REQUEST_HEADERS|!REQUEST_HEADERS:Referer "@validateByteRange 32-126" \`
`       "phase:request,\`
`       rev:'2',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       maturity:'9',\`
`       accuracy:'9',\`
`       block,\`
`       msg:'Invalid character in request',\`
`       id:'XXXXXX',\`
`       severity:'ERROR',\`
`       t:none,t:urlDecodeUni,\`
`       `<tag:'application-multi>`',\`
`       `<tag:'language-multi>`',\`
`       `<tag:'platform-multi>`',\`
`       `<tag:'attack-protocol>`',\`
`       `<tag:'OWASP_CRS/PROTOCOL_VIOLATION/EVASION>`',\`
`       setvar:'tx.msg=%{rule.msg}',\`
`       setvar:tx.anomaly_score=+%{tx.error_anomaly_score},\`
`       setvar:tx.%{rule.id}-OWASP_CRS/PROTOCOL_VIOLATION/EVASION-%{matched_var_name}=%{matched_var}"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")