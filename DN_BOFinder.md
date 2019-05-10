DN_BOFinder v0.2 - Feb 2007

The DN_BOFinder (DotNet Buffer Overflow Finder) is a semi-intelligent
tool designed to find Buffer Overflows type vulnerabilities in COM
objects used by .NET Assemblies (and mistakes in unsafe .Net code
blocks).

This project was created by Dinis Cruz.

## Download

The latest version (0.2) can be downloaded from SourceForge:
[1](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=105632&release_id=519695)

#### Features

Here are some of its features:

  - Supports fuzzing of individual methods, \*.dll files and entire
    directories
  - Works by using Reflection to create 'live instances' of classes and
    then fuzzing each of the exposed methods
  - there are currently 16 different payloads for basic types (int,
    unint, char) and strings
  - Fully automated use of cdb to find issues (i.e. you can start the
    fuzzer and go for lunch)
  - use of an 'FuzzedMethods' list for each fuzzed dll to avoid
    re-fuzzing the same methods
  - stored of exception information in an 'ExceptionData' file (per dll)
  - use of an 'ExcludeList'to list the classes/methods that should be
    further analyzed
  - auto detection of methods that consume large amounts of memory
    (currently set to 20M) and auto-detection of methods that 'hang'
    (some callbacks or windows pop-ups have this behaviour).The methods
    identified are automatically added to the 'ExcludeList'
  - The results are current quite conservative (i.e. only the really bad
    exceptions are shown). this means that there might be several
    exploitable vulnerabilities that are currently reported as 'Normal
    CLR exception'
  - A big blind spot at the moment is that the current version does not
    fuzz certain static methods (which can be invoked without need of a
    constructor (i.e. a live instance))
  - When it finds an interface it tries to find who implements that
    interface and tries to create an instance of them (supports caching
    of objects for performance reasons). The problem here is that the
    class created is not documented, and ideally we should be fuzzing
    each of those implementations (especially in the cases where that
    Interface is used as a parameter)
  - When in auto mode, it auto-restarts fuzzing session after a
    predefined number of seconds (this also helps in long fuzzing
    sessions since the process is refreshed regularly, which of course
    might also introduce some blind spots)

<!-- end list -->

  - Files:
      - The binary (DN_BOFinder.exe) can be found on the
        DN_BOFinder_V0.2\\binary folder
      - The results will inside the
        DN_BOFinder_V0.2\\binary\\_fuzz_results folder (created on
        first run)
      - The source code is in DN_BOFinder_V0.2\\Source Code

#### fuzzing modes

There are 5 operational fuzzing modes:

  - File ::: to Fuzz a file (in this mode a CLR crash will also crash
    the fuzzer)
  - File Auto ::: to Fuzz a file automatically (in this mode new
    processes of DN_BOFinder are started in the 'File' Mode under cdb
    (Microsoft's Command Line Debugger). The cdb output is analyzed for
    unhandled exception data which when discovered is appended to the
    'ExepctionData'
  - Dir ::: to fuzz directories (basically invoking 'File Auto' for each
    \*.dll in the target directory
  - Method ::: to fuzz a method directly
  - Method Auto ::: to fuzz a method automatically (this will invoke the
    method using the number of payloads specified)

#### Current limitations

  - when one of the create parameters value is null, the method is not
    invoked (since it was throwing a lot of errors). This is a legacy
    from the first version of this fuzzer (before cdb automation) so it
    should be possible to remove this now
  - Need to add support for call stack information (and sequence of
    methods invoked) since sometimes the exception is not thrown by the
    method we fuzzed (and we need those details to replicate the state
    of that issue)
  - the fact that we don't fuzz the same method twice creates some blind
    spots (since some errors occur by state changes in previous methods)
  - the payloads are still quite basic, in a future version the fuzzing
    of live objects (i.e. variation of it) will be implemented
  - the creation of live instances is still not very cleaver and has
    problem with more complex types (like the ones that require a file
    to be loaded before some of its methods make sense). The plan is to
    implement a new fuzzing mode where we are able to use real objects
    created during an execution of an real application (for example an
    win32 gui app or an ASP.NET website) and fuzz them.

#### Bugs and to-do-list

  - we should delete the 'ExcludeList'and 'ExceptionData' when nothing
    is found
  - list the methods/classes that we couldn't fuzz
  - Add a Gui
  - Add code coverage
  - export results in XML format
  - add directory recursive capabilities to the 'Dir' fuzzing mode

## HOW-TO use instructions

**'Fuzzing MsCorLib**'

`> binary\DN_BOFinder.exe file mscorlib.dll`

by default if no path is included, DN_BOFinder will try to find the
file in the current directory or in the main .Net 2.0 directory

If all goes well you will see a large number of entries that look like
these:

`[INFO]: Fuzzing mscorlib.dll (18372 methods, 1264 types): 0 type processed`
`...`
`>>> Fuzzing System.Object [0]<<<:`
`...`
`***************************************************`
`*********`
`*********   System.Object[] - FuzzIndex: 0`
`*********`
`***************************************************`
`...`
`[6:03 AM] > Executing System.Int32.System.IConvertible.ToBoolean(System.IFormatProvider) [0]:`
`[6:03 AM] > Executing System.Int32.System.IConvertible.ToChar(System.IFormatProvider) [0]:`
`[6:03 AM] > Executing System.Int32.System.IConvertible.ToSByte(System.IFormatProvider) [0]:`

while this is running, open the
\\DN_BOFinder_V0.2\\binary\\_fuzz_results folder and you will see
three files in there:

`* mscorlib.dll_ExceptionData.txt     - Will contain details about exeptions discovered (only in auto or dir modes)`
`* mscorlib.dll_ExcludeList.txt       - Will contain a list of methods to exclude (only in auto or dir modes)`
`* mscorlib.dll_FuzzedMethods.txt     - will contain a list of methods and classes that have been fuzzed`

now try

`> DN_BOFinder file system.dll`

and you should get a crash (of the CLR) in the method:

`>>> Fuzzing System.Text.RegularExpressions.MatchEvaluator [0]<<<:`

run it under a debugger:

`> cdb DN_BOFinder file system.dll `
`(press g)`

and you should get this exception data:

`(d64.bb0): CLR exception - code e0434f4d (first chance)`
`(d64.bb0): CLR exception - code e0434f4d (first chance)`
`(d64.bb0): Access violation - code c0000005 (first chance)`
`First chance exceptions are reported before any exception handling.`
`This exception may be expected and handled.`
`eax=00000000 ebx=00000000 ecx=00000000 edx=00000001 esi=0014d3d0 edi=00000000`
`eip=79eea7c3 esp=0012e944 ebp=0012e9b4 iopl=0         nv up ei pl nz na po nc`
`cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010202`
`*** ERROR: Symbol file could not be found.  Defaulted to export symbols for   C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\mscorwks.dll -`
`mscorwks!IEE+0x13277:`
`79eea7c3 0fb708          movzx   ecx,word ptr [eax]       ds:0023:00000000=????`
`0:000>`

Which is an error that occurred inside the mscorwks.dll and was the
reason the .NET assembly crashed. The exeption mscorwks\!IEE+0x13277 is
actually quite common, and I think it is a false positive since it looks
like part of a method that checks for bad points (which is weird method
to check it, but it seems to be quite common on the CLR). I need to load
the symbols in my dev laptop (which is always offline btw :) ) to see
where mscorwks\!IEE+0x13277 resolves to.

Now that we have an issue you have two choices:

1\) add manually the signature of the offending class
System.Text.RegularExpressions.MatchEvaluator to the
_fuzz_results\\system.dll_ExcludeList.txt file or

2\) run

`> DN_BOFinder file auto system.dll`

which will do that for you :)

the output of "DN_BOFinder file auto system.dll" should be something
like:

`*********************************************`
`*******`
`*******    DotNet BOFinder v0.2 (12 Mar 2007)`
`*******`
`*********************************************`
`....`
`Populating ByPassList`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 3 type processed`
`Normal CLR Exception in System.Text.RegularExpressions.MatchEvaluator [0]`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 4 type processed`
`System.Collections.CollectionBase.set_Capacity(Int32) Forced Exception - iPageMemorySize64 Grew by 1048MB`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 23 type processed`
`Normal CLR Exception in System.CodeDom.CodeMemberMethod.add_PopulateParameters(System.EventHandler) [0]`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 41 type processed`
`Normal CLR Exception in System.CodeDom.CodeMemberMethod.remove_PopulateParameters(System.EventHandler) [0]`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 42 type processed`
`Normal CLR Exception in System.CodeDom.CodeMemberMethod.add_PopulateStatements(System.EventHandler) [0]`
`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 43 type processed`
`Normal CLR Exception in System.CodeDom.CodeMemberMethod.remove_PopulateStatements(System.EventHandler) [0]`

so what is happening here is, you get an \[INFO\] every time a fuzzing
session starts (i.e. new process) and we have a bunch of 'Normal CLR
Exception' entries (which crash the CLR but I think are false positives
(I would actually put money that some of these might be exploitable
(most are null pointers)). Note for example that the case I shown above
(System.Text.RegularExpressions.MatchEvaluator) is here shown as a
'Normal CLR Exception'

Every time a 'CLR Exception' occurs, its signature is added to the
MethodsFuzzed list and the process restarts (only in the cases where the
error doesn't match one of my hard-coded signatures the methods are
added to the ExcludeList and its data added to the ExceptionData.

...

Eventually you start to get some more interesting issues like for
example:

`[INFO]: Fuzzing system.dll (12676 methods, 889 types): 167 type processed`
`System.Resources.ResourceManager.GetStream(System.String) [0]  - via CDB`
`       eax=00000000 ebx=0126853c ecx=00000000 edx=0126853c esi=0127ef20 edi=00000000`
`       eip=039827df esp=0012ec74 ebp=0012ecc0 iopl=0         nv up ei pl zr na pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246`
`       039827df 8b01            mov     eax,dword ptr [ecx]  ds:0023:00000000=????????`
`       0:000`

which you can go to reflector and see its code:

`class: System.Resources.ResourceManager`
`method: public UnmanagedMemoryStream GetStream(string name)`

At this stage (after a bit of fuzzing) the system.dll_ExcludeList.txt
should look like this:

`System.Collections.CollectionBase.set_Capacity(Int32) Forced Exception - iPageMemorySize64 Grew by 1048MB`
`System.ComponentModel.ComponentResourceManager.ApplyResources(System.Object, System.String) [0]  - via CDB`
`System.Resources.ResourceManager.ReleaseAllResources() [0]  - via CDB`
`System.Resources.ResourceManager.GetString(System.String) [0]  - via CDB`
`System.Resources.ResourceManager.GetObject(System.String) [0]  - via CDB`
`System.Resources.ResourceManager.GetStream(System.String) [0]  - via CDB`
`System.ComponentModel.TypeConverter.ConvertFromInvariantString(System.String) [0]  - via CDB`

Note: For non .NET Framework Assemblies (that are not placed on the v2
folder), you will need to pass the full path to the dll to fuzz.

Here for example is fuzzing a dll that is part of the .NET 2.0 SDK

`> dn_boFinder file "c:\Program Files\Microsoft Visual Studio 8\SDK\v2.0\Bin\RequiredPermissions.dll"`

This actually an interresting case since if you run it normally, you
will not see a lot of exceptions, but if you run it under the cdb

`> cdb dn_boFinder file "c:\Program Files\Microsoft Visual Studio 8\SDK\v2.0\Bin\RequiredPermissions.dll"`

you will see a lot exceptions that look like these

`[8:11 PM] > Executing ManagedMD.Utils.SafePointer.op_Implicit(ManagedMD.Utils.SafePointer) [0]: (1ac.634): Access violation `
`- code c0000005 (first chance)`
`First chance exceptions are reported before any exception handling.`
`This exception may be expected and handled.`
`eax=00000000 ebx=0012ed2c ecx=0012ed00 edx=00000000 esi=00181028 edi=00000000`
`eip=03684f95 esp=0012ecf4 ebp=0012ed10 iopl=0         nv up ei pl nz ac pe nc`
`cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010216`
`03684f95 3b4204          cmp     eax,dword ptr [edx+4] ds:0023:00000004=????????`

so run it in auto mode to document them

`> dn_boFinder file auto "c:\Program Files\Microsoft Visual Studio 8\SDK\v2.0\Bin\RequiredPermissions.dll"`

(these type of cmp are another type of exceptions that I think are false
positives)

## fuzzing methods

lets go back to the system.dll
System.ComponentModel.ComponentResourceManager.ApplyResources(System.Object,System.String)
discovered before

the final piece of the puzzle is to see if this method is exploitable
(i.e. can we contol the CPU Registers from a variable that we control).
So to do that, the easier way is to run just that method with all fuzzed
combinations.

And that is what we can do with the method option. (you can also write a
simple c\# code to do that)

the format is

`DN_BOFinder {full Path to Dll}!{full method signature (with no spaces)}!0 {number of fuzzed items to try (optional)}`

so execute:

`> DN_BOFinder.exe method auto c:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\system.dll!System.ComponentModel.ComponentResourceManager.ApplyResources(System.Object,System.String)!0`

which should give you something like:

`*********************************************`
`*******`
`*******    DotNet BOFinder v0.2 (12 Mar 2007)`
`******* `
`*********************************************`
`...`
`strDllToLoad: c:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\system.dll`
`strTypeToCreate: System.ComponentModel.ComponentResourceManager`
`strMethodToFuzz_FullName: System.ComponentModel.ComponentResourceManager.ApplyResources`
`strMethodToFuzz_Name: ApplyResources`
`strMethodToFuzz_Params: (System.Object,System.String)`
` Populating ByPassList`
`System.ComponentModel.ComponentResourceManager.ApplyResources [0]  - via CDB`
`       eax=00000000 ebx=012696b8 ecx=00000000 edx=012696b8 esi=01275460 edi=012696b8`
`       eip=032d009f esp=0012eb74 ebp=0012ebc0 iopl=0         nv up ei pl zr na pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246`
`       032d009f 8b01            mov     eax,dword ptr [ecx]  ds:0023:00000000=????????`
`       0:000`
`...`
`System.ComponentModel.ComponentResourceManager.ApplyResources [1]  - via CDB`
`       eax=00000000 ebx=012696b8 ecx=00000000 edx=012696b8 esi=01275460 edi=012696b8`
`       eip=032d009f esp=0012eb74 ebp=0012ebc0 iopl=0         nv up ei pl zr na pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246`
`       032d009f 8b01            mov     eax,dword ptr [ecx]  ds:0023:00000000=????????`
`       0:000 `
`...`
`(other results omited)`

so here one can see that the value of the CPU registers don't really
change, which might mean that this is a false positive

#### interop.MediaPlayer

To see a better example of this, create a wrapper for the MediaPlayer
control in a default xp sp2 installation in Visual Studio (i.e. the file
Interop.MediaPlayer.dll) and fuzz it.

After a while you will get these two exceptions:

`MediaPlayer.RadioPlayerClass.BindRadioMemory() [0]  - via CDB`
`       eax=7ffdf000 ebx=1d3063a8 ecx=1d363167 edx=00000000 esi=0039b6e4 edi=00000000`
`       eip=1d363175 esp=0012ed4c ebp=0012ed74 iopl=0         nv up ei pl nz na po nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=        `
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx - `
`       msdxm!RunDll+0x2f6e5:`
`       1d363175 66c7076c00      mov     word ptr [edi],6Ch       ds:0023:00000000=????`
`       0:000`
`...`
`MediaPlayer.RadioServerClass.Unregister(Int32) [0]  - via CDB`
`       eax=00000000 ebx=1d308fc0 ecx=03a40004 edx=001eeaca esi=003978f0 edi=f0000001`
`       eip=1d3639f6 esp=0012ece0 ebp=0012ed04 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx - `
`       msdxm!RunDll+0x2ff66:`
`       1d3639f6 8b07            mov     eax,dword ptr [edi]  ds:0023:f0000001=????????`
`       0:000`

the first one, MediaPlayer.RadioPlayerClass.BindRadioMemory(), seems to
be one that is caused by some change of state on a previous fuzzed
method, but the 2nd one looks much more interresting:
MediaPlayer.RadioServerClass.Unregister(Int32)

Let's fuzz it using the auto method system:

DN_BOFinder.exe method auto
d:\\...\\...\\...\\...\\Interop.MediaPlayer.dll\!MediaPlayer.RadioServerClass.Unregister(Int32)\!0
15

`*********************************************`
`*******`
`*******    DotNet BOFinder v0.2 (12 Mar 2007)`
`*******`
`*********************************************`
`... `
`strDllToLoad: d:\...\...\...\...\Interop.MediaPlayer.dll`
`strTypeToCreate: MediaPlayer.RadioServerClass`
`strMethodToFuzz_FullName: MediaPlayer.RadioServerClass.Unregister`
`strMethodToFuzz_Name: Unregister`
`strMethodToFuzz_Params: (Int32)`
`Populating ByPassList`
`Fuzzing 15 objects`
`MediaPlayer.RadioServerClass.Unregister [0]  - via CDB`
`       eax=00000000 ebx=1d308fc0 ecx=034a0004 edx=001c7d3a esi=00397030 edi=f0000001`
`       eip=1d3639f6 esp=0012ed40 ebp=0012ed64 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx -`
`       msdxm!RunDll+0x2ff66:`
`       1d3639f6 8b07            mov     eax,dword ptr [edi]  ds:0023:f0000001=????????`
`       0:000`
`....`
`MediaPlayer.RadioServerClass.Unregister [1]  - via CDB`
`       eax=00000000 ebx=1d308fc0 ecx=034a0004 edx=001a4c32 esi=00397030 edi=fff00001`
`       eip=1d3639f6 esp=0012ed40 ebp=0012ed64 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx -`
`       msdxm!RunDll+0x2ff66:`
`       1d3639f6 8b07            mov     eax,dword ptr [edi]  ds:0023:fff00001=????????`
`       0:000`
`....`
`MediaPlayer.RadioServerClass.Unregister [6]  - via CDB`
`       eax=00000000 ebx=1d308fc0 ecx=034a0004 edx=001a4bca esi=00397030 edi=0fffffff`
`       eip=1d3639f6 esp=0012ed40 ebp=0012ed64 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx -`
`       msdxm!RunDll+0x2ff66:`
`       1d3639f6 8b07            mov     eax,dword ptr [edi]  ds:0023:0fffffff=????????`
`       0:000`
`...`
`MediaPlayer.RadioServerClass.Unregister [7]  - via CDB`
`       eax=72006300 ebx=1d308fc0 ecx=034a0004 edx=001c7d3a esi=00397030 edi=00ffffff`
`       eip=1d3639f8 esp=0012ed40 ebp=0012ed64 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx -`
`       msdxm!RunDll+0x2ff68:`
`       1d3639f8 8b5808          mov     ebx,dword ptr [eax+8] ds:0023:72006308=????????`
`       0:000`
`...`
`MediaPlayer.RadioServerClass.Unregister [9]  - via CDB`
`       eax=00000000 ebx=1d308fc0 ecx=034a0004 edx=001c2392 esi=00397030 edi=0000ffff`
`       eip=1d3639f6 esp=0012ed40 ebp=0012ed64 iopl=0         nv up ei pl zr ac pe nc`
`       cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010256`
`       *** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\WINDOWS\System32\msdxm.ocx -`
`       msdxm!RunDll+0x2ff66:`
`       1d3639f6 8b07            mov     eax,dword ptr [edi]  ds:0023:0000ffff=????????`
`       0:000`

and notice that we have direct control of EAX.

Now since you can only invoke this Interop.MediaPlayer.dll from Full
Trust, this is not technically a vulnerability :)

## Development notes

1\) to create and invoke private methods change in the
utils/reflection.cs file

`   public static BindingFlags bfPublicNonPublicFlag = BindingFlags.Public;`
`   `
`   with`

`   public static BindingFlags bfBindingFlags_InsSta = bfPublicNonPublicFlag `

| BindingFlags.Instance | BindingFlags.Static;

`{add more}`