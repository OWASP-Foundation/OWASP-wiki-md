While testing what was the best function to hook in HttpListenerRequest
(see [Hooking HttpApi.dll's
HttpReceiveHttpRequest](Hooking_HttpApi.dll's_HttpReceiveHttpRequest "wikilink"))
I found what I think is a bug in the 2.0 method
System.Net.HttpListenerRequest which belongs to the Platform SDK: HTTP
API\]:

  - open *System.Net.HttpListenerRequest* in reflector
  - in the internal *unsafe HttpListenerRequest(HttpListenerContext
    httpContext, RequestContextBase memoryBlob)* method look for this:

`'' if ((memoryBlob.RequestBlob.CookedUrl.pFullUrl != null) && (memoryBlob.RequestBlob.CookedUrl.FullUrlLength > 0))`
`   {`
`     this.m_CookedUrl = Marshal.PtrToStringAnsi((IntPtr) memoryBlob.RequestBlob.CookedUrl.pFullUrl, memoryBlob.RequestBlob.CookedUrl.FullUrlLength);`
`   }''`

  - *this.m_CookedUrl* is an private string m_CookedUrl;
  - and memoryBlob.RequestBlob.CookedUrl.pFullUrl is an internal unsafe
    ushort\* pFullUrl; (i.e. a pointer).
  - If we look at the unmanaged definitions ( see [Hooking HttpApi.dll's
    HttpReceiveHttpRequest](Hooking_HttpApi.dll's_HttpReceiveHttpRequest "wikilink"))
    we have:
      - HttpReceiveHttpRequest -\>
          - _HTTP_REQUEST pRequestBuffer -\>
              - HTTP_COOKED_URL CookedUrl -\>
                  - PCWSTR pFullUrl

<!-- end list -->

  - The problem is that unManaged version of pFullUrl is in Unicode
    format, where the BCL version handles it as it was ASCII

<!-- end list -->

  - I noticed this problem because
    System.Net.HttpListenerRequest.m_cookedUrl, had a value of
    "h\\0t\\0t\\0p\\0:\\0/\\0/\\0l\\0o\\0c\\0a\\0l\\0h\\0o\\0s\\0t\\0:\\08\\00\\09\\00\\0/"
    which if you remove the \\0 is "<http://localhost:8090/>"

<!-- end list -->

  - Looking at the definition of
    [Marshal.PtrToStringAnsi](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfsystemruntimeinteropservicesmarshalclassptrtostringansitopic.asp)
    in MSDN we see that there are two definitions of
    Marshal.PtrToStringAnsi Method (HttpReceiveHttpRequest uses the
    second one)
      - [public static string
        PtrToStringAnsi(IntPtr);](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemruntimeinteropservicesmarshalclassptrtostringansitopic1.asp)
        Copies all characters up to the first null from an unmanaged
        ANSI string to a managed String. Widens each ANSI character to
        Unicode.
      - [public static string PtrToStringAnsi(IntPtr,
        int);](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemruntimeinteropservicesmarshalclassptrtostringansitopic2.asp)
        Allocates a [managed
        String](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemstringclasstopic.asp),
        copies a specified number of characters from an unmanaged ANSI
        string into it, and widens each ANSI character to Unicode.

<!-- end list -->

  - The source code of [public static string
    PtrToStringAnsi(IntPtr);](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemruntimeinteropservicesmarshalclassptrtostringansitopic1.asp)
    is (using reflector):

`[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.UnmanagedCode)]`
`public static string PtrToStringAnsi(IntPtr ptr)`
`{`
`  if (Win32Native.NULL == ptr)`
`  {`
`     return null;`
`  }`
`  if (Marshal.IsWin32Atom(ptr))`
`  {`
`     return null;`
`  }`
`  int num1 = Win32Native.lstrlenA(ptr);`
`  if (num1 == 0)`
`  {`
`     return string.Empty;`
`  }`
`  StringBuilder builder1 = new StringBuilder(num1);`
`  Win32Native.CopyMemoryAnsi(builder1, ptr, new IntPtr(1 + num1));`
`  return builder1.ToString();`
`}`

  - The source code of [public static string PtrToStringAnsi(IntPtr,
    int);](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemruntimeinteropservicesmarshalclassptrtostringansitopic2.asp)
    (using reflector) is:

`[MethodImpl(MethodImplOptions.InternalCall), SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.UnmanagedCode)]`
`public static extern string PtrToStringAnsi(IntPtr ptr, int len);`

  - we see that it is an internalCall method
    ("MethodImplOptions.InternalCall" is used to declare a method in
    managed code that has no managed implementation. The implementation
    (unmanaged) is supplied by the runtime itself (CLR)):

<!-- end list -->

  - Since we don't have the source code of the CLR and the 2.0 version
    of Rotor, I had to look at Rotor's version 1.1 where I found (using
    CodeScoping's cool feature for searching text in files:) ) inside
    (\\sscli\\clr\\src\\vm\\comndirect.cpp) this:

<i>

`* PInvoke.PtrToStringAnsi()`
`*/`
`FCIMPL2(Object*, PtrToStringAnsi, LPVOID ptr, INT32 len)`
`{`
`               STRINGREF pString = NULL;`
`               HELPER_METHOD_FRAME_BEGIN_RET_ATTRIB_1(Frame::FRAME_ATTR_RETURNOBJ, pString);`
`               //-[autocvtpro]-------------------------------------------------------`
`               THROWSCOMPLUSEXCEPTION();`
`               if (ptr == NULL)`
`                   COMPlusThrowArgumentNull(L"ptr");`
`               if (len < 0)`
`                   COMPlusThrowNonLocalized(kArgumentException, L"len");`
`               int nwc = 0;`
`               if (len != 0) {`

`                   nwc = MultiByteToWideChar(CP_ACP,MB_PRECOMPOSED,(LPCSTR)(ptr),len,NULL,0);`
`                   if (nwc == 0)COMPlusThrow(kArgumentException, IDS_UNI2ANSI_FAILURE);`

`               }`
`               pString = COMString::NewString(nwc);`
`               MultiByteToWideChar(CP_ACP,MB_PRECOMPOSED,(LPCSTR)(ptr),len,pString->GetBuffer(),nwc);`
`               //-[autocvtepi]-------------------------------------------------------`
`               HELPER_METHOD_FRAME_END();`
`               return OBJECTREFToObject(pString);`
`}`
`FCIMPLEND`

</i>

  - In summary:
      - The problem is in here:

`internal unsafe HttpListenerRequest(HttpListenerContext httpContext, RequestContextBase memoryBlob)`
`{`
`   ....`
`       if ((memoryBlob.RequestBlob.CookedUrl.pFullUrl != null) && (memoryBlob.RequestBlob.CookedUrl.FullUrlLength > 0))`
`       {`
`           this.m_CookedUrl = Marshal.PtrToStringAnsi((IntPtr) memoryBlob.RequestBlob.CookedUrl.pFullUrl, memoryBlob.RequestBlob.CookedUrl.FullUrlLength)  `
`       }`
`   ....`
`}`

  -   - since it should be Marshal.PtrToStringUni and not
        Marshal.PtrToStringAnsi

**Note1:** as far as I can tell m_CookedUrl is only used here:

`private System.Net.HttpListenerRequest.Uri get_RequestUri()`

<i>`{`
`       ....`
`       if (!string.IsNullOrEmpty(this.m_CookedUrl))`
`       {`
`           flag1 = Uri.TryCreate(this.m_CookedUrl, UriKind.Absolute, out this.m_RequestUri);`
`       }`
`       ....`
`}`</i>

Which probably explains why this was not picked up by the MS .Net team
(i.e. No aparent side effects)

**Note2:** using the detoured HttpReceiveHttpRequest I changed the
contents of (\*pRequestBuffer).CookedUrl.pFullUrl to

`StringCbPrintfA((STRSAFE_LPSTR)(*pRequestBuffer).CookedUrl.pFullUrl,30,"`<http://localhost:8090/Test.aspx>`");`

and I got “http://localhost:8090/Test.aspx\*&(&(^(^(\*&(\*&(\*&” (i.e.
The original ANSI string + strlen(original ANSI string) chars) in
System.Net.HttpListenerRequest.m_CookedUrl (which shows that the
original assumption was that (\*pRequestBuffer).CookedUrl.pFullUrl
should have an ANSI string.

[link not working](Category:FIXME "wikilink") [link not
working](Category:FIXME "wikilink") [link not
working](Category:FIXME "wikilink") [link not
working](Category:FIXME "wikilink") [link not
working](Category:FIXME "wikilink") [link not
working](Category:FIXME "wikilink")