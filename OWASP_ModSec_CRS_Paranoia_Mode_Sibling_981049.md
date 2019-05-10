*This page contains a proposal for a stricter rule-clone for
[ModSecurity CRS Paranoia
Mode](OWASP_ModSec_CRS_Paranoia_Mode "wikilink").*

## 981049 : Potential Denial of Service (DoS)

`class="wikitable"`

| class="wikitable"

`| `**`RuleID``   ``2.2.x`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(original``   ``Rule)`**
`| `**`RuleID``   ``3.0.0-rc1``   ``(paranoid``   ``Rule)`**
`| `**`Change`**
`| `**`Whitelisting`**

|-

`| 981049`
`| 912100`
`| 912101-912104`
`| Operator match decreased form 2 to 1.`
*`Optional:``   ``change``   ``tx.dos_burst_time_slice,``
 ``tx.dos_counter_threshold``   ``and/or``   ``tx.dos_block_timeout`*
`| None`

|}

` #`
` # -=[ Potential Denial of Service (DoS)  ]=-`
` #`
` # This is a paranoid sibling to 2.2.9 Experimental Rule 981049.`
` # The rule now triggers after the first burst instead of the second.`
` # For 3.0.0-rc1 rule, see 912100.`
` #`
` SecRule IP:DOS_BURST_COUNTER "@ge 1"`
`       "phase:logging,\`
`       rev:'1',\`
`       ver:'OWASP_CRS/3.0.0',\`
`       maturity:'X',\`
`       accuracy:'Y',\`
`       t:none,\`
`       log,\`
`       msg:'Potential Denial of Service (DoS) Attack from %{tx.real_ip} - # of Request Bursts:%{ip.dos_burst_counter}',\`
`       id:'XXXXXX',\`
`       `<tag:'FIXME>` Filler for attacktype',\`
`       `<tag:'Paranoia>` rule on level Z',\`
`       setvar:ip.dos_block=1,\`
`       expirevar:ip.dos_block=%{tx.dos_block_timeout},\`
`       pass"`

### Notes

This rule can not be implemented as is. Rules 981044 - 981048 from
*owasp-modsecurity-crs/experimental_rules/modsecurity_crs_11_dos_protection.conf*
need to be integrated to allow proper blocking. There should be no need
to adjust these rules for desired effects.

Also note that more Paranoia tuning can be done by adjusting the DoS
Protection variable values in your main configuration (e.g.
modsecurity_crs_10_setup.conf).

` #`
` # -- [[DoS_Protection|DoS Protection]] ----------------------------------------------------------------`
` #`
` # This is a Paranoia Mode Clone.`
` # Adjust the following variables to fine tune paranoia level.`
` #`
` # - Burst Time Slice Interval: time interval window to monitor for bursts`
` # - Request Threshold: request # threshold to trigger a burst`
` # - Block Period: temporary block timeout`
` #`
` SecAction \`
`       "id:XXXXXX',\`
`       phase:request,\`
`       t:none,\`
`       setvar:'tx.dos_burst_time_slice=90',\`
`       setvar:'tx.dos_counter_threshold=50',\`
`       setvar:'tx.dos_block_timeout=600',\`
`       nolog,\`
`       pass"`

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")