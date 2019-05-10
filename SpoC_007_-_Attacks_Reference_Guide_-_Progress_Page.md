[Back to Attacks Reference Guide Main
Page](http://www.owasp.org/index.php/SpoC_007_-_Attacks_Reference_Guide)

[Back to Refresh Attacks List Main
Page](http://www.owasp.org/index.php/SpoC_007_-_Refresh_Attacks_list)

The Attack reference guide is being developed by [NSRAV Security
R\&D](SpoC_007_-_Attacks_Reference_Guide "wikilink") and [Przemyslaw
'Rezos' Skowron](SpoC_007_-_Refresh_Attacks_list "wikilink"). In order
to avoid work superposition, the project was divided in 3 phases
comprising the following activities:

1.  Attack list revision and description (60% of the project)
2.  Attacks categorization (20% of the project)
3.  Research and describe new attacks (20% of the project)

Total project status: **100% Done\!**

## CheckPoints and Decision

### Phase 1 - 100% DONE

  - Attack List Revision: **Done\!**

Total number of items on the Attack Guide: **91**\!

We noticed that Attack reference guide was previously defined based on
[CWE - Common Weakness Enumeration](http://cwe.mitre.org/), which
defines global software weakness and threats. In order to develop the
Attack reference guide focused on Web application attacks, we reviewed
the list and marked some items to be removed from the list. The contents
of generic or redundant items were used in descriptions of some items
and marked to be removed too.

Items considered to removal from the attack list: **30 items**, as
follows:

  -   - [API_Abuse](API_Abuse "wikilink")
      - [Cross_Site_Scripting](Cross_Site_Scripting "wikilink")
      - [Cross-Site_Scripting](Cross-Site_Scripting "wikilink")
      - [CSRF](CSRF "wikilink")
      - [Internal_software_developer](Internal_software_developer "wikilink")
      - [Interpreter_Injection](Interpreter_Injection "wikilink")
      - [Link_Following](Link_Following "wikilink")
      - [Log_forging](Log_forging "wikilink")
      - [Logic/time_bomb](Logic/time_bomb "wikilink")
      - [Macro_symbol](Macro_symbol "wikilink")
      - [Network_amplification](Network_amplification "wikilink")
      - [One-Click_Attack](One-Click_Attack "wikilink")
      - [OS_Injection](OS_Injection "wikilink")
      - [OS_Command_Injection](OS_Command_Injection "wikilink")
      - [PRNG_permanent_compromise_attack](PRNG_permanent_compromise_attack "wikilink")
      - [Reviewing_Code_for_OS_Injection](Reviewing_Code_for_OS_Injection "wikilink")
      - [Script_in_IMG_tags](Script_in_IMG_tags "wikilink")
      - [Sniffing_application_traffic_attack](Sniffing_application_traffic_attack "wikilink")
      - [Template:Attack](Template:Attack "wikilink")
      - [Unquoted_Search_Path_or_Element](Unquoted_Search_Path_or_Element "wikilink")
      - [Web_problems](Web_problems "wikilink")
      - [Wildcard_or_Matching_Element](Wildcard_or_Matching_Element "wikilink")
      - [Windows_::DATA_alternate_data_stream](Windows_::DATA_alternate_data_stream "wikilink")
      - [Windows_hard_link](Windows_hard_link "wikilink")
      - [Windows_MS-DOS_device_names](Windows_MS-DOS_device_names "wikilink")
      - [Windows_Path_Link_problems](Windows_Path_Link_problems "wikilink")
      - [Windows_Shortcut_Following_%28.LNK%29](Windows_Shortcut_Following_%28.LNK%29 "wikilink")
      - [Windows_Virtual_File_problems](Windows_Virtual_File_problems "wikilink")
      - [XSS_Attacks](XSS_Attacks "wikilink")
      - [XSRF](XSRF "wikilink")

<!-- end list -->

  - Attacks Description: **61 of 61 items done**\!

### Phase 2 - DONE\!

The attacks categorization was based on [Common Attack Pattern
Enumeration and Classification - CAPEC](http://capec.mitre.org), since
it is maintained by a respected entity and wide enough to fit all web
application attacks.

The categories defined are:

  - [:Category:Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")
  - [:Category:Spoofing](:Category:Spoofing "wikilink")
  - [:Category:Probabilistic
    Techniques](:Category:Probabilistic_Techniques "wikilink")
  - [:Category:Exploitation of
    Authentication](:Category:Exploitation_of_Authentication "wikilink")
  - [:Category:Resource
    Depletion](:Category:Resource_Depletion "wikilink")
  - Exploitation of Privilege/Trust
  - [:Category:Injection](:Category:Injection "wikilink") (Injecting
    Control Plane content through the Data Plane)
  - [:Category:Data_Structure_Attacks](:Category:Data_Structure_Attacks "wikilink")
  - Data Leakage Attacks
  - [:Category:Resource
    Manipulation](:Category:Resource_Manipulation "wikilink")
  - [:Category:Protocol
    Manipulation](:Category:Protocol_Manipulation "wikilink")
  - Time and State Attacks

It was also defined the threats categorization based on [WASC Threat
Classification v2](http://wasc.ptsecurity.ru/wasc/index.php?title=TCv2),
under development.

### Phase 3 - 100% DONE

Research and Description of new attacks:

  -   - Block Access to Libraries - add as a example of
        [Setting_Manipulation](Setting_Manipulation "wikilink")
      - [Buffer_Overflow_via_Environment_Variables](Buffer_Overflow_via_Environment_Variables "wikilink")
      - [Cross_Frame_Scripting](Cross_Frame_Scripting "wikilink")
      - [Denial_of_Service](Denial_of_Service "wikilink") - The DoS
        items previously described were extracted from
        [Testing_for_Denial_of_Service](Testing_for_Denial_of_Service "wikilink")
        section of
        [OWASP_Testing_Guide](OWASP_Testing_Guide "wikilink").
      - [Embedding_Null_Code](Embedding_Null_Code "wikilink")
      - [Man-in-the-browser_attack](Man-in-the-browser_attack "wikilink")
      - [Manipulating_User_Permission_Identifier](Manipulating_User_Permission_Identifier "wikilink")
      - [Overflow_Binary_Resource_File](Overflow_Binary_Resource_File "wikilink")
      - [Session_Prediction](Session_Prediction "wikilink")

### Work Done

Note: this links were inserted here by Dinis Cruz from OWASP-NSRAV.zip
file

Note2: Other items inserted and sorted by name by Leonardo Cavallari
(NSRAV).

  - [Direct_Dynamic_Code_Evaluation_%28%27Eval_Injection%27%29](Direct_Dynamic_Code_Evaluation_%28%27Eval_Injection%27%29 "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Direct_Dynamic_Code_Evaluation_%28%27Eval_Injection%27%29&diff=23056&oldid=6053)
    ,
    [history](http://www.owasp.org/index.php?title=Direct_Dynamic_Code_Evaluation_%28%27Eval_Injection%27%29&action=history))

<!-- end list -->

  - [Direct_Static_Code_Injection](Direct_Static_Code_Injection "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Direct_Static_Code_Injection&diff=23057&oldid=5711)
    ,
    [history](http://www.owasp.org/index.php?title=Direct_Static_Code_Injection&action=history))

<!-- end list -->

  - [Double_Encoding](Double_Encoding "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Double_Encoding&diff=23058&oldid=5740)
    ,
    [history](http://www.owasp.org/index.php?title=Double_Encoding&action=history))

<!-- end list -->

  - [Forced_browsing](Forced_browsing "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Forced_browsing&diff=23060&oldid=19889)
    ,
    [history](http://www.owasp.org/index.php?title=Forced_browsing&action=history))

<!-- end list -->

  - [Format_string_attack](Format_string_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Format_string_attack&diff=23065&oldid=7393)
    ,
    [history](http://www.owasp.org/index.php?title=Format_string_attack&action=history))

<!-- end list -->

  - [HTTP_Response_Splitting](HTTP_Response_Splitting "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=HTTP_Response_Splitting&diff=23117&oldid=7948)
    ,
    [history](http://www.owasp.org/index.php?title=HTTP_Response_Splitting&action=history))

<!-- end list -->

  - [HTTP_Request_Smuggling](HTTP_Request_Smuggling "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=HTTP_Request_Smuggling&diff=23118&oldid=5802),
    [history](http://www.owasp.org/index.php?title=HTTP_Request_Smuggling&action=history))

<!-- end list -->

  - [LDAP_injection](LDAP_injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=LDAP_injection&diff=23067&oldid=10830)
    ,
    [history](http://www.owasp.org/index.php?title=LDAP_injection&action=history))

<!-- end list -->

  - [Man-in-the-middle_attack](Man-in-the-middle_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Man-in-the-middle_attack&diff=23075&oldid=18290)
    ,
    [history](http://www.owasp.org/index.php?title=Man-in-the-middle_attack&action=history))

<!-- end list -->

  - [Mobile_code:_invoking_untrusted_mobile_code](Mobile_code:_invoking_untrusted_mobile_code "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Mobile_code%3A_invoking_untrusted_mobile_code&diff=23077&oldid=6035)
    , [history
    history](http://www.owasp.org/index.php?title=Mobile_code:_invoking_untrusted_mobile_code&action=history))

<!-- end list -->

  - [Mobile_code:_non-final_public_field](Mobile_code:_non-final_public_field "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Mobile_code%3A_non-final_public_field&diff=23079&oldid=6036)
    ,
    [history](http://www.owasp.org/index.php?title=Mobile_code:_non-final_public_field&action=history))

<!-- end list -->

  - [Mobile_code:_object_hijack](Mobile_code:_object_hijack "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Mobile_code%3A_object_hijack&diff=23082&oldid=6040)
    ,
    [history](http://www.owasp.org/index.php?title=Mobile_code:_object_hijack&action=history))

<!-- end list -->

  - [Network_Eavesdropping](Network_Eavesdropping "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Network_Eavesdropping&diff=23146&oldid=7395)
    ,
    [history](http://www.owasp.org/index.php?title=Network_Eavesdropping&action=history))

<!-- end list -->

  - [Parameter_Delimiter](Parameter_Delimiter "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Parameter_Delimiter&diff=23084&oldid=6190)
    ,
    [history](http://www.owasp.org/index.php?title=Parameter_Delimiter&action=history))

<!-- end list -->

  - [Path_Manipulation](Path_Manipulation "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Path_Manipulation&diff=23059&oldid=7983)
    ,
    [history](http://www.owasp.org/index.php?title=Path_Manipulation&action=history))

<!-- end list -->

  - [Path_Traversal](Path_Traversal "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Path_Traversal&diff=23066&oldid=18282)
    ,
    [history](http://www.owasp.org/index.php?title=Path_Traversal&action=history))

<!-- end list -->

  - [Relative_Path_Traversal](Relative_Path_Traversal "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Relative_Path_Traversal&diff=23071&oldid=6423)
    ,
    [history](http://www.owasp.org/index.php?title=Relative_Path_Traversal&action=history))

<!-- end list -->

  - [Repudiation_Attack](Repudiation_Attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Repudiation_Attack&diff=23076&oldid=7397)
    ,
    [history](http://www.owasp.org/index.php?title=Repudiation_Attack&action=history))

<!-- end list -->

  - [Resource_Injection](Resource_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Resource_Injection&diff=23078&oldid=7980)
    ,
    [history](http://www.owasp.org/index.php/Resource_Injection&action=history))

<!-- end list -->

  - [Server-Side_Includes_%28SSI%29_Injection](Server-Side_Includes_%28SSI%29_Injection "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Server-Side_Includes_%28SSI%29_Injection&diff=23081&oldid=18278)
    ,
    [history](http://www.owasp.org/index.php?title=Server-Side_Includes_%28SSI%29_Injection&action=history))

<!-- end list -->

  - [Session_fixation](Session_fixation "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Session_fixation&diff=23144&oldid=7391)
    ,
    [history](http://www.owasp.org/index.php?title=Session_fixation&action=history))

<!-- end list -->

  - [Session_hijacking_attack](Session_hijacking_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Session_hijacking_attack&diff=23086&oldid=6467)
    ,
    [history](http://www.owasp.org/index.php?title=Session_hijacking_attack&action=history))

<!-- end list -->

  - [Setting_Manipulation](Setting_Manipulation "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Setting_Manipulation&diff=23088&oldid=7984)
    ,
    [history](http://www.owasp.org/index.php?title=Setting_Manipulation&action=history))

<!-- end list -->

  - [Special_Element_Injection](Special_Element_Injection "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Special_Element_Injection&diff=23089&oldid=6447)
    ,
    [history](http://www.owasp.org/index.php?title=Special_Element_Injection&action=history))

<!-- end list -->

  - [Spyware](Spyware "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Spyware&diff=23090&oldid=6448)
    ,
    [history](http://www.owasp.org/index.php?title=Spyware&action=history))

<!-- end list -->

  - [SQL_Injection](SQL_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=SQL_Injection&diff=23119&oldid=21964)
    ,
    [history](http://www.owasp.org/index.php?title=SQL_Injection&action=history))

<!-- end list -->

  - [Traffic_flood](Traffic_flood "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Traffic_flood&diff=23109&oldid=7392)
    ,
    [history](http://www.owasp.org/index.php?title=Traffic_flood&action=history))

<!-- end list -->

  - [Trojan_Horse](Trojan_Horse "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Trojan_Horse&diff=23093&oldid=7078)
    ,
    [history](http://www.owasp.org/index.php?title=Trojan_Horse&action=history))

<!-- end list -->

  - [Unicode_Encoding](Unicode_Encoding "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Unicode_Encoding&diff=23094&oldid=7943)
    ,
    [history](http://www.owasp.org/index.php?title=Unicode_Encoding&action=history))

<!-- end list -->

  - [Web_Parameter_Tampering](Web_Parameter_Tampering "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Web_Parameter_Tampering&diff=23104&oldid=6831)
    ,
    [history](http://www.owasp.org/index.php?title=Web_Parameter_Tampering&action=history))

**New items**

  -   - [Denial_of_Service](Denial_of_Service "wikilink")
      - [Embedding_Null_Code](Embedding_Null_Code "wikilink")
      - [Man-in-the-browser_attack](Man-in-the-browser_attack "wikilink")
      - [Manipulating_User_Permission_Identifier](Manipulating_User_Permission_Identifier "wikilink")
      - [Session_Prediction](Session_Prediction "wikilink")

by Przemyslaw 'rezos' Skowron (20071025 - part I - first 50%\])

  - [Absolute_Path_Traversal](Absolute_Path_Traversal "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Absolute_Path_Traversal&diff=22637&oldid=14001)
    ,
    [history](http://www.owasp.org/index.php?title=Absolute_Path_Traversal&action=history))

<!-- end list -->

  - [Argument_Injection_or_Modification](Argument_Injection_or_Modification "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Argument_Injection_or_Modification&diff=22638&oldid=5186)
    ,
    [history](http://www.owasp.org/index.php?title=Argument_Injection_or_Modification&action=history))

<!-- end list -->

  - [Brute_force_attack](Brute_force_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Brute_force_attack&diff=22641&oldid=13966)
    ,
    [history](http://www.owasp.org/index.php?title=Brute_force_attack&action=history))

<!-- end list -->

  - [Buffer_overflow_attack](Buffer_overflow_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Buffer_overflow_attack&diff=22642&oldid=7390)
    ,
    [history](http://www.owasp.org/index.php?title=Buffer_overflow_attack&action=history))

<!-- end list -->

  - [Cache_Poisoning](Cache_Poisoning "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Cache_Poisoning&diff=22647&oldid=13172)
    ,
    [history](http://www.owasp.org/index.php?title=Cache_Poisoning&action=history))

<!-- end list -->

  - [Code_Injection](Code_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Code_Injection&diff=22651&oldid=7913)
    ,
    [history](http://www.owasp.org/index.php?title=Code_Injection&action=history))

<!-- end list -->

  - [Command_Injection](Command_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Command_Injection&diff=22654&oldid=16438)
    ,
    [history](http://www.owasp.org/index.php?title=Command_Injection&action=history))

<!-- end list -->

  - [Cross-Site_Request_Forgery](Cross-Site_Request_Forgery "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Cross-Site_Request_Forgery&diff=22643&oldid=19627)
    ,
    [history](http://www.owasp.org/index.php?title=Cross-Site_Request_Forgery&action=history))

<!-- end list -->

  - [Cross-User_Defacement](Cross-User_Defacement "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Cross-User_Defacement&diff=22658&oldid=7949)
    ,
    [history](http://www.owasp.org/index.php?title=Cross-User_Defacement&action=history))

<!-- end list -->

  - [Cross-site-scripting](Cross-site-scripting "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Cross-site-scripting&diff=22660&oldid=21443)
    ,
    [history](http://www.owasp.org/index.php?title=Cross-site-scripting&action=history))

<!-- end list -->

  - [Integer_Overflows/Underflows](Integer_Overflows/Underflows "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Integer_Overflows%2FUnderflows&diff=22661&oldid=7380)
    ,
    [history](http://www.owasp.org/index.php?title=Integer_Overflows/Underflows&action=history))

<!-- end list -->

  - [XSS_in_error_pages](XSS_in_error_pages "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=XSS_in_error_pages&diff=22662&oldid=6850)
    ,
    [history](http://www.owasp.org/index.php?title=XSS_in_error_pages&action=history))

by Przemyslaw 'rezos' Skowron (20071104 - part II - second 50%\])

  - [Account_lockout_attack](Account_lockout_attack "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Account_lockout_attack&diff=22954&oldid=6117)
    ,
    [history](http://www.owasp.org/index.php?title=Account_lockout_attack&action=history))
  - [Alternate_XSS_Syntax](Alternate_XSS_Syntax "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Alternate_XSS_Syntax&diff=22956&oldid=16480),
    [history](http://www.owasp.org/index.php?title=Alternate_XSS_Syntax&action=history))
  - [Asymmetric_resource_consumption_%28amplification%29](Asymmetric_resource_consumption_%28amplification%29 "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Asymmetric_resource_consumption_%28amplification%29&diff=22957&oldid=5188),
    [history](http://www.owasp.org/index.php?title=Asymmetric_resource_consumption_%28amplification%29&action=history))
  - [Blind_SQL_Injection](Blind_SQL_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Blind_SQL_Injection&diff=22959&oldid=14497),
    [history](http://www.owasp.org/index.php?title=Blind_SQL_Injection&action=history))
  - [Blind_XPath_Injection](Blind_XPath_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Blind_XPath_Injection&diff=22960&oldid=9579),
    [history](http://www.owasp.org/index.php?title=Blind_XPath_Injection&action=history))
  - [Comment_Element](Comment_Element "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Comment_Element&diff=22961&oldid=5325),
    [history](http://www.owasp.org/index.php?title=Comment_Element&action=history))
  - [Cryptanalysis](Cryptanalysis "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=Cryptanalysis&diff=22962&oldid=7389),
    [history](http://www.owasp.org/index.php?title=Cryptanalysis&action=history))
  - [Custom_Special_Character_Injection](Custom_Special_Character_Injection "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=Custom_Special_Character_Injection&diff=22963&oldid=5357),
    [history](http://www.owasp.org/index.php?title=Custom_Special_Character_Injection&action=history))
  - [XPATH_Injection](XPATH_Injection "wikilink") -
    ([diff](http://www.owasp.org/index.php?title=XPATH_Injection&diff=22965&oldid=21461),
    [history](http://www.owasp.org/index.php?title=XPATH_Injection&action=history))
  - [XSS_using_Script_Via_Encoded_URI_Schemes](XSS_using_Script_Via_Encoded_URI_Schemes "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=XSS_using_Script_Via_Encoded_URI_Schemes&diff=22936&oldid=6851),
    [history](http://www.owasp.org/index.php?title=XSS_using_Script_Via_Encoded_URI_Schemes&action=history))
  - [XSS_using_Script_in_Attributes](XSS_using_Script_in_Attributes "wikilink")
    -
    ([diff](http://www.owasp.org/index.php?title=XSS_using_Script_in_Attributes&diff=22937&oldid=6852),
    [history](http://www.owasp.org/index.php?title=XSS_using_Script_in_Attributes&action=history))

NEW ITEMS - 20071104 (by Przemyslaw 'rezos' Skowron):

  - [Overflow_Binary_Resource_File](Overflow_Binary_Resource_File "wikilink")
    - (\[INITIAL VERSION diff\] ,
    [history](http://www.owasp.org/index.php?title=Overflow_Binary_Resource_File&action=history))
  - [Cross_Frame_Scripting](Cross_Frame_Scripting "wikilink") -
    (\[INITIAL VERSION diff\] ,
    [history](http://www.owasp.org/index.php?title=Cross_Frame_Scripting&action=history))
  - [Buffer_Overflow_via_Environment_Variables](Buffer_Overflow_via_Environment_Variables "wikilink")
    - (\[INITIAL VERSION diff\] ,
    [history](http://www.owasp.org/index.php?title=Buffer_Overflow_via_Environment_Variables&action=history))