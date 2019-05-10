# Round Tripping

Round Tripping is a revese engineering technique that allow us to
decompile an assembly from a certain application. Ildasm.exe can be used
for this purpose, and ILAsm is used to recompiled the assembly . The
MSIL Disassembler( Ildasm.exe) is a companion tool to the MSIL Assembler
(Ilasm.exe). Ildasm.exe takes a portable executable (PE) file that
contains Microsoft intermediate language (MSIL) code and creates a text
file suitable as input to Ilasm.exe. This tool is automatically
installed with Visual Studio and with the Windows SDK.

## The importance of Obfuscation

As mentioned before , Round Tripping is indeed a technique used to
reverse engineer assemblies. Therefore, if you want to avoid your
assemblies being reversed engineered or even worse, that the code is
victim of malicious manipulation using the Ildasm and Ilasm tools, then
its is advisable to apply it. There are different kinds of products that
can be used for this purpose such as DeepSea, Crypto or Dotfuscator.