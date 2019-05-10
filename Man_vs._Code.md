**UPDATE: I have proposed a "Sticky" Marking When Smart Highlighting
enhancement to the Notepad++ team: when one is selecting a word
character-by-character, allow one to do this multiple times, without
clearing the previous selected (and now smart-highlighted) sets of
words. Then, clear all marks when double click on any other word.
Double-click smart-highlighting functionality remains the same as it was
before. This allows one to follow variable assignments through the code
more easily. This change allows one to select the original variable,
then select a new variable that the old variable is now assigned to, and
so on. If you're interested in the details contact
mike.boberski@owasp.org. If you'd like an already built version with the
changes to copy over after you've installed, you can find it
[here](http://www.owasp.org/index.php/File:Notepad%2B%2B.zip)**

![Man-v-code.gif](Man-v-code.gif "Man-v-code.gif") Tools such as source
code review tools are expensive. Let me rephrase. They cost as much as a
house\! Feeling like you just stepped into a survivalist reality show,
after being asked to perform a review using for example [OWASP
ASVS](http://www.owasp.org/index.php/ASVS)? You need tools, and you need
them now. You also need tools more useful than for example RATS (Rough
Auditing Tool for Security).

Tools such as RATS even if their rules are beefed up are still not a
fast way to do a code review. If you accept the premise that when
performing a code review, one should do at least a minimal check for
both false positives and false negatives, then regardless of tool, you
still need to go through each and every source file even if only for a
cursory inspection. This is where source code review tools shine, their
IDE-like GUIs allow you to jump through the code interactively in a very
efficient way. This is why tools such as RATS are pretty much useless.
You need to be able to easily jump through the code and follow data from
sources to sinks a lot more than you need an initial count of some huge
number of potential findings\!

With the above in mind, here's one way to fashion a basic, efficient
source code review tool (in this case, for PHP source) using a little
bit of research and some freely-available tools in perhaps unexpected
ways. The basic idea is to use Notepad++ and Its “User Defined Language”
Feature. It can be downloaded here:
<http://notepad-plus.sourceforge.net> So, go and do that. The ability to
define one’s language using Notepad++ configuration interfaces, its
syntax highlighting, and the ability to highlight variables throughout
by default after selecting them, provides the basis for a way to search
file-by-file for security-related flaws. E.g. create a new “PHP 4, 5
SCA” language. You'll also want to use a grep tool and also open up
the PHP web site so you can search for function/language definitions
<http://us2.php.net/manual/en/> Also, install the “Explorer” plugin
(copy to its plugins directory, download from
<http://sourceforge.net/project/showfiles.php?group_id=189927&package_id=223667>
then enable it using the “Plugins” menu

Then, based on looking for function and other keywords related to input,
SQL, sessions, URLs, files, etc. one can mine documents for relevant
keywords, e.g.:

  - <http://us2.php.net/manual/en/reserved.variables.php>
  - <http://us2.php.net/manual/en/book.mysql.php>
  - <http://us2.php.net/manual/en/book.hash.php>
  - <http://us2.php.net/manual/en/refs.fileprocess.file.php>
  - <http://us2.php.net/manual/en/book.mail.php>
  - <http://us2.php.net/manual/en/book.session.php>
  - <http://us2.php.net/manual/en/features.cookies.php>
  - <http://us2.php.net/manual/en/ref.url.php>
  - Chris Shiflett, Essential PHP Security (O’Reilly Media, Inc., 2005).
  - <http://www.fortify.com/vulncat/en/vulncat/index.html>

Next, configure Notepad++ to create a new PHP static analysis language:

Select “View” menu, then “User Define Dialog” menu item, then “Dock”
button

Ext:

  - Set to php (no period\!)

Folder & Default

  - Font name – Consolas

Keywords Lists - Use your research here\!

1st Group - Use this to find potential problems

  - Foreground color – red
  - Background color – white
  - Font style - bold
  - Prefix mode – make sure this is set (checked)

PHP Example:

  - $GLOBALS $_SERVER $_GET $_POST $_FILES $_REQUEST $_SESSION
    $_ENV $_COOKIE $php_errormsg $HTTP_RAW_POST_DATA
    $http_response_header $argc $argv mysql_ hash_ basename chgrp
    chmod chown clearstatcache copy delete dirname disk_free_space
    disk_total_space diskfreespace fclose feof fflush fgetc fgetcsv
    fgets fgetss file_exists file_get_contents file_put_contents
    file fileatime filectime filegroup fileinode filemtime fileowner
    fileperms filesize filetype flock fnmatch fopen fpassthru fputcsv
    fputs fread fscanf fseek fstat ftell ftruncate fwrite glob is_dir
    is_executable is_file is_link is_readable is_uploaded_file
    is_writable is_writeable lchgrp lchown link linkinfo lstat mkdir
    move_uploaded_file parse_ini_file parse_ini_string pathinfo
    pclose popen readfile readlink realpath rename rewind rmdir
    set_file_buffer stat symlink tempnam tmpfile touch umask unlink
    mail session_ setcookie setrawcookie header ob_ output_ base64_
    get_headers get_meta_tags http_build_query parse_url
    rawurlecode urldecode urlencode ini_set error_log
    allow_url_fopen disable_functions display_errors enable_dl
    error_reporting file_uploads log_errors magic_quotes_gpc
    memory_limit open_basedir register_globals safe_mode eval exec
    file file_get_contents fopen include passthru phpinfo popen
    preg_replace proc_open readfile require shell_exec system
    $password mcrypt_ return echo \<?php \<? md5 ldap_ @
    trigger_error print error_reporting display_errors \<form
    Ajax.Request preg_replace htmlspecialchars hidden \<input rand
    srand mt_srand mt_rand file extract href mysqli

NSS (v3.12.4) Example:

  - NSS_GetClientAuthData NSS_SetDomesticPolicy NSS_SetExportPolicy
    NSS_SetFrancePolicy NSSSSL_VersionCheck SSL_AuthCertificate
    SSL_AuthCertificateHook SSL_BadCertHook SSL_CertDBHandleSet
    SSL_CipherPolicyGet SSL_CipherPolicySet SSL_CipherPrefGet
    SSL_CipherPrefGetDefault SSL_CipherPrefSet
    SSL_CipherPrefSetDefault SSL_ClearSessionCache
    SSL_ConfigMPServerSIDCache SSL_ConfigSecureServer
    SSL_ConfigServerSessionIDCache SSL_DataPending SSL_ForceHandshake
    SSL_ForceHandshakeWithTimeout SSL_GetChannelInfo
    SSL_GetCipherSuiteInfo SSL_GetClientAuthDataHook
    SSL_GetMaxServerCacheLocks SSL_GetSessionID SSL_GetStatistics
    SSL_HandshakeCallback SSL_ImportFD SSL_InheritMPServerSIDCache
    SSL_InvalidateSession SSL_LocalCertificate SSL_OptionGet
    SSL_OptionGetDefault SSL_OptionSet SSL_OptionSetDefault
    SSL_PeerCertificate SSL_PreencryptedFileToStream
    SSL_PreencryptedStreamToFile SSL_ReHandshake
    SSL_ReHandshakeWithTimeout SSL_ResetHandshake
    SSL_RestartHandshakeAfterCertReq
    SSL_RestartHandshakeAfterServerCert SSL_RevealCert
    SSL_RevealPinArg SSL_RevealURL SSL_SecurityStatus
    SSL_SetMaxServerCacheLocks SSL_SetPKCS11PinArg SSL_SetSockPeerID
    SSL_SetURL SSL_ShutdownServerSessionIDCache SSL_Enable
    SSL_EnableCipher SSL_EnableDefault SSL_RedoHandshake
    SSL_SetPolicy CERT_AddCertToListTail CERT_AddExtension
    CERT_AddOCSPAcceptableResponses CERT_AddOKDomainName CERT_AddRDN
    CERT_AsciiToName CERT_CacheCRL CERT_CertChainFromCert
    CERT_CertListFromCert CERT_CertTimesValid CERT_ChangeCertTrust
    CERT_CheckCertValidTimes CERT_CheckCertUsage CERT_CompareName
    CERT_CompareValidityTimes CERT_CompleteCRLDecodeEntries
    CERT_ConvertAndDecodeCertificate CERT_CopyName CERT_CopyRDN
    CERT_CreateAVA CERT_CreateCertificate
    CERT_CreateCertificateRequest CERT_CreateName
    CERT_CreateOCSPCertID CERT_CreateOCSPRequest CERT_CreateRDN
    CERT_CreateSubjectCertList CERT_CreateValidity
    CERT_CRLCacheRefreshIssuer CERT_DecodeAltNameExtension
    CERT_DecodeAuthInfoAccessExtension CERT_DecodeAuthKeyID
    CERT_DecodeAVAValue CERT_DecodeBasicConstraintValue
    CERT_DecodeCertFromPackage CERT_DecodeCertificatePoliciesExtension
    CERT_DecodeCertPackage CERT_DecodeCRLDistributionPoints
    CERT_DecodeDERCrl CERT_DecodeDERCrlWithFlags
    CERT_DecodeGeneralName CERT_DecodeNameConstraintsExtension
    CERT_DecodeOCSPResponse CERT_DecodeOidSequence
    CERT_DecodePrivKeyUsagePeriodExtension CERT_DecodeTrustString
    CERT_DecodeUserNotice CERT_DerNameToAscii CERT_DestroyCertArray
    CERT_DestroyCertificate CERT_DestroyCertificateList
    CERT_DestroyCertificatePoliciesExtension
    CERT_DestroyCertificateRequest CERT_DestroyCertList
    CERT_DestroyName CERT_DestroyOCSPCertID CERT_DestroyOCSPRequest
    CERT_DestroyOCSPResponse CERT_DestroyOidSequence
    CERT_DestroyUserNotice CERT_DestroyValidity CERT_DupCertificate
    CERT_DupCertList CERT_EnableOCSPChecking
    CERT_EncodeAltNameExtension CERT_EncodeAndAddBitStrExtension
    CERT_EncodeAuthKeyID CERT_EncodeBasicConstraintValue
    CERT_EncodeCRLDistributionPoints CERT_EncodeGeneralName
    CERT_EncodeOCSPRequest CERT_ExtractPublicKey CERT_FindCertByName
    CERT_FilterCertListByCANames CERT_FilterCertListByUsage
    CERT_FilterCertListForUserCerts CERT_FindCertByDERCert
    CERT_FindCertByIssuerAndSN CERT_FindCertByNickname
    CERT_FindCertByNicknameOrEmailAddr CERT_FindCertBySubjectKeyID
    CERT_FindCertExtension CERT_FindCertIssuer
    CERT_FindKeyUsageExtension CERT_FindSMimeProfile
    CERT_FindSubjectKeyIDExtension CERT_FindUserCertByUsage
    CERT_FindUserCertsByUsage CERT_FinishCertificateRequestAttributes
    CERT_FinishExtensions CERT_FormatName CERT_FreeDistNames
    CERT_FreeNicknames CERT_GetAVATag CERT_GetCertChainFromCert
    CERT_GetCertEmailAddress CERT_GetCertificateNames
    CERT_GetCertificateRequestExtensions CERT_GetCertIssuerAndSN
    CERT_GetCertNicknames CERT_GetCertTrust CERT_GetCertUid
    CERT_GetCommonName CERT_GetCountryName CERT_GetDBContentVersion
    CERT_GetDefaultCertDB CERT_GetDomainComponentName
    CERT_GetFirstEmailAddress CERT_GetLocalityName
    CERT_GetNextEmailAddress CERT_GetNextGeneralName
    CERT_GetNextNameConstraint CERT_GetOCSPResponseStatus
    CERT_GetOCSPStatusForCertID CERT_GetOidString CERT_GetOrgName
    CERT_GetOrgUnitName CERT_GetOCSPAuthorityInfoAccessLocation
    CERT_GetPrevGeneralName CERT_GetPrevNameConstraint
    CERT_GetSlopTime CERT_GetSSLCACerts CERT_GetStateName
    CERT_GenTime2FormattedAscii CERT_Hexify CERT_ImportCAChain
    CERT_ImportCerts CERT_IsRootDERCert CERT_IsUserCert
    CERT_KeyFromDERCrl CERT_MakeCANickname CERT_MergeExtensions
    CERT_NameToAscii CERT_NewCertList
    CERT_NicknameStringsFromCertList CERT_OpenCertDBFilename
    CERT_RemoveCertListNode CERT_RFC1485_EscapeAndQuote
    CERT_SaveSMimeProfile CERT_SetSlopTime CERT_StartCertExtensions
    CERT_StartCertificateRequestAttributes
    CERT_StartCRLEntryExtensions CERT_StartCRLExtensions
    CERT_UncacheCRL CERT_VerifyCertName CERT_VerifyCACertForUsage
    CERT_VerifyCert CERT_VerifyCertificate CERT_VerifyCertificateNow
    CERT_VerifyCertNow CERT_VerifyOCSPResponseSignature
    CERT_VerifySignedData CERT_VerifySignedDataWithPublicKey
    CERT_VerifySignedDataWithPublicKeyInfo NSS_CmpCertChainWCANames
    NSS_FindCertKEAType PK11_AlgtagToMechanism PK11_Authenticate
    PK11_BlockData PK11_ChangePW PK11_CheckUserPassword
    PK11_CipherOp PK11_CloneContext PK11_ConfigurePKCS11
    PK11_ConvertSessionPrivKeyToTokenPrivKey
    PK11_ConvertSessionSymKeyToTokenSymKey
    PK11_CopyTokenPrivKeyToSessionPrivKey PK11_CreateContextBySymKey
    PK11_CreateDigestContext PK11_CreatePBEAlgorithmID
    PK11_DeleteTokenPrivateKey PK11_DeleteTokenPublicKey
    PK11_DeleteTokenSymKey PK11_Derive PK11_DeriveWithFlags
    PK11_DeriveWithFlagsPerm PK11_DestroyContext
    PK11_DestroyGenericObject PK11_DestroyGenericObjects
    PK11_DestroyObject PK11_DestroyTokenObject PK11_DigestBegin
    PK11_DigestKey PK11_DigestOp PK11_DigestFinal PK11_DoesMechanism
    PK11_ExportEncryptedPrivateKeyInfo PK11_ExportEncryptedPrivKeyInfo
    PK11_ExportPrivateKeyInfo PK11_Finalize PK11_FindBestKEAMatch
    PK11_FindCertAndKeyByRecipientList
    PK11_FindCertAndKeyByRecipientListNew PK11_FindCertByIssuerAndSN
    PK11_FindCertFromDERCert PK11_FindCertFromNickname
    PK11_FindCertInSlot PK11_FindGenericObjects PK11_FindFixedKey
    PK11_FindKeyByAnyCert PK11_FindKeyByDERCert
    PK11_FindPrivateKeyFromCert PK11_FindSlotByName
    PK11_FindSlotsByNames PK11_FortezzaHasKEA PK11_FortezzaMapSig
    PK11_FreeSlot PK11_FreeSlotList PK11_FreeSlotListElement
    PK11_FreeSymKey PK11_GenerateFortezzaIV PK11_GenerateKeyPair
    PK11_GenerateKeyPairWithFlags PK11_GenerateNewParam
    PK11_GenerateRandom PK11_GenerateRandomOnSlot PK11_GetAllTokens
    PK11_GetBestKeyLength PK11_GetBestSlot PK11_GetBestSlotMultiple
    PK11_GetBestWrapMechanism PK11_GetBlockSize
    PK11_GetCertFromPrivateKey PK11_GetCurrentWrapIndex
    PK11_GetDefaultArray PK11_GetDefaultFlags PK11_GetDisabledReason
    PK11_GetFirstSafe PK11_GetInternalKeySlot PK11_GetInternalSlot
    PK11_GetKeyGen PK11_GetKeyLength PK11_GetKeyStrength
    PK11_GetMechanism PK11_GetMinimumPwdLength PK11_GetModInfo
    PK11_GetModule PK11_GetModuleID PK11_GetNextGenericObject
    PK11_GetNextSafe PK11_GetNextSymKey PK11_GetPadMechanism
    PK11_GetPBEIV PK11_GetPQGParamsFromPrivateKey
    PK11_GetPrevGenericObject PK11_GetPrivateKeyNickname
    PK11_GetPrivateModulusLen PK11_GetPublicKeyNickname
    PK11_GetSlotFromKey PK11_GetSlotFromPrivateKey PK11_GetSlotID
    PK11_GetSlotInfo PK11_GetSlotName PK11_GetSlotSeries
    PK11_GetSymKeyNickname PK11_GetSymKeyType PK11_GetSymKeyUserData
    PK11_GetTokenInfo PK11_GetTokenName PK11_GetWindow
    PK11_GetWrapKey PK11_HashBuf PK11_HasRootCerts PK11_ImportCert
    PK11_ImportCertForKeyToSlot PK11_ImportCRL PK11_ImportDERCert
    PK11_ImportDERPrivateKeyInfoAndReturnKey
    PK11_ImportEncryptedPrivateKeyInfo PK11_ImportPrivateKeyInfo
    PK11_ImportPrivateKeyInfoAndReturnKey PK11_ImportPublicKey
    PK11_ImportSymKeyWithFlags PK11_InitPin PK11_IsFIPS
    PK11_IsDisabled PK11_IsFriendly PK11_IsHW PK11_IsInternal
    PK11_IsPresent PK11_IsReadOnly PK11_IVFromParam PK11_KeyGen
    PK11_LinkGenericObject PK11_ListCerts PK11_ListFixedKeysInSlot
    PK11_ListPrivKeysInSlot PK11_ListPublicKeysInSlot
    PK11_LoadPrivKey PK11_LogoutAll PK11_MakeKEAPubKey
    PK11_MapPBEMechanismToCryptoMechanism PK11_MapSignKeyType
    PK11_MechanismToAlgtag PK11_MoveSymKey PK11_NeedLogin
    PK11_NeedUserInit PK11_ParamFromIV PK11_ParamFromAlgid
    PK11_ParamToAlgid PK11_PBEKeyGen PK11_PrivDecryptPKCS1
    PK11_ProtectedAuthenticationPath PK11_PubDecryptRaw
    PK11_PubDerive PK11_PubDeriveWithKDF PK11_PubEncryptPKCS1
    PK11_PubEncryptRaw PK11_PubUnwrapSymKey
    PK11_PubUnwrapSymKeyWithFlags PK11_PubUnwrapSymKeyWithFlagsPerm
    PK11_PubWrapSymKey PK11_RandomUpdate PK11_ReadRawAttribute
    PK11_ReferenceSymKey PK11_ResetToken PK11_RestoreContext
    PK11_SaveContext PK11_SaveContextAlloc PK11_SetFortezzaHack
    PK11_SetPasswordFunc PK11_SetPrivateKeyNickname
    PK11_SetPublicKeyNickname PK11_SetSlotPWValues
    PK11_SetSymKeyNickname PK11_SetSymKeyUserData PK11_SetWrapKey
    PK11_Sign PK11_SignatureLen PK11_SymKeyFromHandle
    PK11_TokenExists PK11_TokenKeyGen PK11_TokenKeyGenWithFlags
    PK11_TokenRefresh PK11_TraverseCertsForNicknameInSlot
    PK11_TraverseCertsForSubjectInSlot PK11_TraverseSlotCerts
    PK11_UnlinkGenericObject PK11_UnwrapSymKey
    PK11_UnwrapSymKeyWithFlags PK11_UnwrapSymKeyWithFlagsPerm
    PK11_UpdateSlotAttribute PK11_UserEnableSlot PK11_UserDisableSlot
    PK11_Verify PK11_VerifyKeyOK PK11_WaitForTokenEvent
    PK11_WrapSymKey PK11SDR_Encrypt PK11SDR_Decrypt
    SEC_DeletePermCertificate SEC_DeletePermCRL SEC_DerSignData
    SEC_DestroyCrl SEC_FindCrlByDERCert SEC_FindCrlByName
    SEC_LookupCrls SEC_NewCrl SEC_QuickDERDecodeItem
    SECKEY_CacheStaticFlags SECKEY_ConvertToPublicKey
    SECKEY_CopyPrivateKey SECKEY_CopyPublicKey
    SECKEY_CopySubjectPublicKeyInfo SECKEY_CreateDHPrivateKey
    SECKEY_CreateECPrivateKey SECKEY_CreateSubjectPublicKeyInfo
    SECKEY_DecodeDERSubjectPublicKeyInfo SECKEY_DestroyPrivateKey
    SECKEY_DestroyPublicKeyList SECKEY_DestroySubjectPublicKeyInfo
    SECKEY_GetPublicKeyType SECKEY_PublicKeyStrengthInBits
    SECKEY_SignatureLen ATOB_AsciiToData ATOB_ConvertAsciiToItem
    BTOA_ConvertItemToAscii BTOA_DataToAscii DER_AsciiToTime
    DER_DecodeTimeChoice DER_Encode DER_EncodeTimeChoice
    DER_GeneralizedTimeToTime DER_GetInteger DER_Lengths
    DER_TimeToUTCTime DER_UTCDayToAscii DER_UTCTimeToAscii
    DER_UTCTimeToTime DSAU_DecodeDerSig DSAU_DecodeDerSigToLen
    DSAU_EncodeDerSig DSAU_EncodeDerSigWithLen HASH_Begin HASH_Clone
    HASH_Create HASH_Destroy HASH_End HASH_GetHashObject
    HASH_GetHashObjectByOidTag HASH_GetHashTypeByOidTag HASH_HashBuf
    HASH_ResultLen HASH_ResultLenByOidTag HASH_ResultLenContext
    HASH_Update NSS_Init NSS_Initialize NSS_InitReadWrite
    NSS_IsInitialized NSS_NoDBInit NSS_PutEnv NSS_RegisterShutdown
    NSS_Shutdown NSS_UnregisterShutdown NSS_VersionCheck
    NSSBase64_DecodeBuffer NSSBase64Decoder_Create
    NSSBase64Decoder_Destroy NSSBase64Decoder_Update
    NSSBase64_EncodeItem NSSBase64Encoder_Create
    NSSBase64Encoder_Destroy NSSBase64Encoder_Update
    NSSRWLock_Destroy NSSRWLock_HaveWriteLock NSSRWLock_LockRead
    NSSRWLock_LockWrite NSSRWLock_New NSSRWLock_UnlockRead
    NSSRWLock_UnlockWrite NSSSMIME_VersionCheck PORT_Alloc
    PORT_ArenaAlloc PORT_ArenaGrow PORT_ArenaMark PORT_ArenaRelease
    PORT_ArenaStrdup PORT_ArenaUnmark PORT_ArenaZAlloc PORT_Free
    PORT_FreeArena PORT_GetError PORT_NewArena PORT_Realloc
    PORT_SetError PORT_SetUCS2_ASCIIConversionFunction
    PORT_SetUCS2_UTF8ConversionFunction
    PORT_SetUCS4_UTF8ConversionFunction PORT_Strdup
    PORT_UCS2_ASCIIConversion PORT_UCS2_UTF8Conversion PORT_ZAlloc
    PORT_ZFree RSA_FormatBlock SEC_ASN1Decode SEC_ASN1DecodeInteger
    SEC_ASN1DecodeItem SEC_ASN1DecoderAbort
    SEC_ASN1DecoderClearFilterProc SEC_ASN1DecoderClearNotifyProc
    SEC_ASN1DecoderFinish SEC_ASN1DecoderSetFilterProc
    SEC_ASN1DecoderSetNotifyProc SEC_ASN1DecoderStart
    SEC_ASN1DecoderUpdate SEC_ASN1Encode SEC_ASN1EncodeInteger
    SEC_ASN1EncodeItem SEC_ASN1EncoderAbort
    SEC_ASN1EncoderClearNotifyProc SEC_ASN1EncoderClearStreaming
    SEC_ASN1EncoderClearTakeFromBuf SEC_ASN1EncoderFinish
    SEC_ASN1EncoderSetNotifyProc SEC_ASN1EncoderSetStreaming
    SEC_ASN1EncoderSetTakeFromBuf SEC_ASN1EncoderStart
    SEC_ASN1EncoderUpdate SEC_ASN1EncodeUnsignedInteger
    SEC_ASN1LengthLength SEC_DupCrl SEC_GetSignatureAlgorithmOidTag
    SEC_PKCS5GetCryptoAlgorithm SEC_PKCS5GetKeyLength
    SEC_PKCS5GetPBEAlgorithm SEC_PKCS5IsAlgorithmPBEAlg
    SEC_RegisterDefaultHttpClient SEC_SignData SECITEM_AllocItem
    SECITEM_ArenaDupItem SECITEM_CompareItem SECITEM_CopyItem
    SECITEM_DupItem SECITEM_FreeItem SECITEM_ItemsAreEqual
    SECITEM_ZfreeItem SECKEY_CopyEncryptedPrivateKeyInfo
    SECKEY_CopyPrivateKeyInfo SECKEY_CreateRSAPrivateKey
    SECKEY_DestroyEncryptedPrivateKeyInfo SECKEY_DestroyPrivateKeyInfo
    SECKEY_DestroyPublicKey SECKEY_PublicKeyStrength
    SECKEY_UpdateCertPQG SECMOD_AddNewModule SECMOD_AddNewModuleEx
    SECMOD_CancelWait SECMOD_CanDeleteInternalModule
    SECMOD_CreateModule SECMOD_DeleteModule SECMOD_FindModule
    SECMOD_FindSlot SECMOD_FreeModuleSpecList SECMOD_GetDBModuleList
    SECMOD_GetDeadModuleList SECMOD_GetModuleSpecList
    SECMOD_HasRemovableSlots SECMOD_IsModulePresent SECMOD_LoadModule
    SECMOD_LoadUserModule SECMOD_LookupSlot
    SECMOD_PubCipherFlagstoInternal SECMOD_PubMechFlagstoInternal
    SECMOD_UnloadUserModule SECMOD_UpdateModule SECMOD_UpdateSlotList
    SECMOD_WaitForAnyTokenEvent SECOID_AddEntry
    SECOID_CompareAlgorithmID SECOID_CopyAlgorithmID
    SECOID_DestroyAlgorithmID SECOID_FindOID SECOID_FindOIDByTag
    SECOID_FindOIDTag SECOID_FindOIDTagDescription
    SECOID_GetAlgorithmTag SECOID_SetAlgorithmID SGN_Begin
    SGN_CompareDigestInfo SGN_CopyDigestInfo SGN_CreateDigestInfo
    SGN_DestroyContext SGN_DestroyDigestInfo SGN_Digest SGN_End
    SGN_NewContext SGN_Update VFY_Begin VFY_CreateContext
    VFY_DestroyContext VFY_End VFY_Update VFY_VerifyData
    VFY_VerifyDigest NSS_CMSContentInfo_GetBulkKey
    NSS_CMSContentInfo_GetBulkKeySize NSS_CMSContentInfo_GetContent
    NSS_CMSContentInfo_GetContentEncAlgTag
    NSS_CMSContentInfo_GetContentTypeTag
    NSS_CMSContentInfo_SetBulkKey NSS_CMSContentInfo_SetContent
    NSS_CMSContentInfo_SetContent_Data
    NSS_CMSContentInfo_SetContentEncAlg
    NSS_CMSContentInfo_SetContent_DigestedData
    NSS_CMSContentInfo_SetContent_EncryptedData
    NSS_CMSContentInfo_SetContent_EnvelopedData
    NSS_CMSContentInfo_SetContent_SignedData NSS_CMSDecoder_Cancel
    NSS_CMSDecoder_Finish NSS_CMSDecoder_Start
    NSS_CMSDecoder_Update NSS_CMSDigestContext_Cancel
    NSS_CMSDigestContext_FinishMultiple
    NSS_CMSDigestContext_FinishSingle
    NSS_CMSDigestContext_StartMultiple
    NSS_CMSDigestContext_StartSingle NSS_CMSDigestContext_Update
    NSS_CMSDigestedData_Create NSS_CMSDigestedData_Destroy
    NSS_CMSDigestedData_GetContentInfo NSS_CMSDEREncode
    NSS_CMSEncoder_Cancel NSS_CMSEncoder_Finish
    NSS_CMSEncoder_Start NSS_CMSEncoder_Update
    NSS_CMSEncryptedData_Create NSS_CMSEncryptedData_Destroy
    NSS_CMSEncryptedData_GetContentInfo
    NSS_CMSEnvelopedData_AddRecipient NSS_CMSEnvelopedData_Create
    NSS_CMSEnvelopedData_Destroy NSS_CMSEnvelopedData_GetContentInfo
    NSS_CMSMessage_ContentLevel NSS_CMSMessage_ContentLevelCount
    NSS_CMSMessage_Copy NSS_CMSMessage_Create
    NSS_CMSMessage_CreateFromDER NSS_CMSMessage_Destroy
    NSS_CMSMessage_GetContent NSS_CMSMessage_GetContentInfo
    NSS_CMSMessage_IsEncrypted NSS_CMSMessage_IsSigned
    NSS_CMSRecipientInfo_Create NSS_CMSRecipientInfo_CreateFromDER
    NSS_CMSRecipientInfo_CreateNew
    NSS_CMSRecipientInfo_CreateWithSubjKeyID
    NSS_CMSRecipientInfo_CreateWithSubjKeyIDFromCert
    NSS_CMSRecipientInfo_Destroy NSS_CMSRecipientInfo_Encode
    NSS_CMSRecipientInfo_GetCertAndKey
    NSS_CMSRecipientInfo_UnwrapBulkKey
    NSS_CMSRecipientInfo_WrapBulkKey NSS_CMSSignedData_AddCertChain
    NSS_CMSSignedData_AddCertList NSS_CMSSignedData_AddCertificate
    NSS_CMSSignedData_AddDigest NSS_CMSSignedData_AddSignerInfo
    NSS_CMSSignedData_Create NSS_CMSSignedData_CreateCertsOnly
    NSS_CMSSignedData_Destroy NSS_CMSSignedData_GetContentInfo
    NSS_CMSSignedData_GetDigestAlgs NSS_CMSSignedData_GetSignerInfo
    NSS_CMSSignedData_HasDigests NSS_CMSSignedData_ImportCerts
    NSS_CMSSignedData_SetDigests NSS_CMSSignedData_SetDigestValue
    NSS_CMSSignedData_SignerInfoCount
    NSS_CMSSignedData_VerifyCertsOnly
    NSS_CMSSignedData_VerifySignerInfo
    NSS_CMSSignerInfo_AddMSSMIMEEncKeyPrefs
    NSS_CMSSignerInfo_AddSMIMECaps
    NSS_CMSSignerInfo_AddSMIMEEncKeyPrefs
    NSS_CMSSignerInfo_AddSigningTime NSS_CMSSignerInfo_Create
    NSS_CMSSignerInfo_CreateWithSubjKeyID NSS_CMSSignerInfo_Destroy
    NSS_CMSSignerInfo_GetCertList
    NSS_CMSSignerInfo_GetSignerCommonName
    NSS_CMSSignerInfo_GetSignerEmailAddress
    NSS_CMSSignerInfo_GetSigningCertificate
    NSS_CMSSignerInfo_GetSigningTime
    NSS_CMSSignerInfo_GetVerificationStatus
    NSS_CMSSignerInfo_GetVersion NSS_CMSSignerInfo_IncludeCerts
    NSS_CMSUtil_VerificationStatusToString
    NSS_SMIMESignerInfo_SaveSMIMEProfile
    NSS_SMIMEUtil_FindBulkAlgForRecipients SEC_PKCS7AddCertificate
    SEC_PKCS7AddRecipient SEC_PKCS7AddSigningTime
    SEC_PKCS7ContainsCertsOrCrls SEC_PKCS7ContentIsEncrypted
    SEC_PKCS7ContentIsSigned SEC_PKCS7ContentType
    SEC_PKCS7CopyContentInfo SEC_PKCS7CreateCertsOnly
    SEC_PKCS7CreateData SEC_PKCS7CreateEncryptedData
    SEC_PKCS7CreateEnvelopedData SEC_PKCS7CreateSignedData
    SEC_PKCS7DecodeItem SEC_PKCS7DecoderAbort SEC_PKCS7DecoderFinish
    SEC_PKCS7DecoderStart SEC_PKCS7DecoderUpdate
    SEC_PKCS7DecryptContents SEC_PKCS7DestroyContentInfo
    SEC_PKCS7Encode SEC_PKCS7EncodeItem SEC_PKCS7EncoderAbort
    SEC_PKCS7EncoderFinish SEC_PKCS7EncoderStart
    SEC_PKCS7EncoderUpdate SEC_PKCS7GetCertificateList
    SEC_PKCS7GetContent SEC_PKCS7GetEncryptionAlgorithm
    SEC_PKCS7GetSignerCommonName SEC_PKCS7GetSignerEmailAddress
    SEC_PKCS7GetSigningTime SEC_PKCS7IncludeCertChain
    SEC_PKCS7IsContentEmpty SEC_PKCS7SetContent
    SEC_PKCS7VerifyDetachedSignature SEC_PKCS7VerifySignature
    SECMIME_DecryptionAllowed SEC_PKCS12AddCertAndKey
    SEC_PKCS12AddPasswordIntegrity SEC_PKCS12CreateExportContext
    SEC_PKCS12CreatePasswordPrivSafe SEC_PKCS12CreateUnencryptedSafe
    SEC_PKCS12DecoderFinish SEC_PKCS12DecoderGetCerts
    SEC_PKCS12DecoderImportBags SEC_PKCS12DecoderIterateInit
    SEC_PKCS12DecoderIterateNext SEC_PKCS12DecoderSetTargetTokenCAs
    SEC_PKCS12DecoderStart SEC_PKCS12DecoderUpdate
    SEC_PKCS12DecoderValidateBags SEC_PKCS12DecoderVerify
    SEC_PKCS12DestroyExportContext SEC_PKCS12EnableCipher
    SEC_PKCS12Encode SEC_PKCS12IsEncryptionAllowed

2nd Group – Use this to highlight fixes

  - Foreground color – green
  - Font style - bold
  - Background color – white
  - Prefix mode – make sure this is set (checked)
  - mysql_real_escape_string

Comment & Number

  - Comment line
  - Foreground color – light grey
  - Treat keyword as symbol
  - // \#

Comment Block

  - Foreground color – light grey
  - Treat keyword as symbol
  - Comment open - /\*
  - Comment close - \*/

Save As

  - PHP4, 5 SCA

Then, when one opens a file using the new "language", starting from the
suspected highlighted finding, one can double click on the parameters
and return values of suspect functions, then keep selecting variables
and return values as you trace through the code, using the highlighting
all instances function and so on to expidite your review.

Here it is in action:

![Image:Npp-eg.JPG](Npp-eg.JPG "Image:Npp-eg.JPG")

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")