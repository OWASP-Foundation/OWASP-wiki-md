I did some tests and found that the .Net Framework is also affected by
the [Vulnerability in Graphics Rendering Engine Could Allow Remote Code
Execution](http://www.owasp.net/blogs/dinis_cruz/archive/2006/01/03/406.aspx)
(these tests were done in 2.0)

My research is not complete, but here are some pointers:

  - If you have access to an wmf file containg an exploit you can use
    the
    [System.Windows.Forms.PictureBox](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfsystemwindowsformspictureboxclasstopic.asp)
    class to open it (pictureBox1.Load("wmf_exploit_II.wmf");).
      - You can get a benign wmf file from the Wmf Vulnerability Checker
        available here
        [<http://www.hexblog.com>](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfsystemwindowsformspictureboxclasstopic.asp)
      - This exploit is good to use in tests since it will display a
        MessageBox upon succesful exploitation
  - The exploit will work in both Full Trust and Partial Trust.
      - I need to look more into this, but (using the PictureBox) you
        will need a partial trust Sandbox with:
          - Internet PermissionSet
          - FileIO to Unrestricted (altough this seems to be caused by
            either a grand PictureBox demand for it, or by my lack of
            time in doing it right :))
          - UserInterface to 'All windows and Events' (this is an
            interresting one, since using the default Internet Policy
            UserInterface setting, the exploit doesn't work and we get
            array out of bounds error, this again might be a side effect
            of PictureBox and I'm pretty sure that this will be
            exploitable from an Internet PermissionSet SandBox).
  - This exploit (at least my version) will not work in windows 2003 Web
    Edition, but will work in a fully patched Windows XP SP2
      - Note that disabling shimgvw (via regsvr32 /u
        %windir%\\system32\\shimgvw.dll) doesn't stop this attack vector
        since the .Net Framework hooks the GDI32.dll direcly (via
        GdiPlus.dll)
  - The .Net Framework supports Metafiles via the
    [System.Drawing.Imaging.Metafile](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfsystemdrawingimagingmetafileclasstopic.asp)
    class and a quick look in reflector shows a large number of methods
    in there

The Full Trust attack vector is not the bad one (since if you are in
full trust you already own the process), but the Partial Trust is quite
problematic since it would allow malcious code to jump outside the
Sandbox.

[Dinis.cruz](User:Dinis.cruz "wikilink")

[link not working](Category:FIXME "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink")