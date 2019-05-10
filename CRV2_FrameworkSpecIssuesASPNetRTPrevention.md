# Preventing Round Tripping Engineering

## The importance of Obfuscation

As mentioned before , Round Tripping is indeed a technique used to
reverse engineer assemblies. Therefore, if you want to avoid your
assemblies being reversed engineered or even worse, that the code is
victim of malicious manipulation using the ildasm and Ilasm tools, then
its is advisable to apply it. There are different kinds of products that
can be used for this purpose such as DeepSea, Crypto or Dotfuscator

## Using Obfuscation

The most effective technique used to avoid reverse engineering and
tampering of assemblies is the use of Obfuscation. Visual Studio
contains a version of Dotfuscator. This program is accessible by
choosing on the VS menu, Tools → Dotfuscator(Community Edition menu
command). Note: This tools is not available in Express versions

To obfuscate your assemblies :

  - Build the project in VS Studio
  - Tools--\> Dotfuscator Community Edition
  - A screen prompts asking for which project type, choose 'Creat New
    Project' and click OK
  - On the Input tab of the Dotfuscator interface, click 'Browse and Add
    assembly to list'

Browse for the compiled application