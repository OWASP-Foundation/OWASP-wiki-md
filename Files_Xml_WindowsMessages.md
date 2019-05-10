**NOTE THIS IS DRAFT CODE :)**

`#region namespaces`
` using System;`
` using System.Collections;`
` using System.Collections.Specialized;`
` using System.Windows.Forms;  `
` using System.Xml.Serialization;`
` `
` using System.IO;`
` using System.Text;`
` using System.Threading;`
` using System.Runtime.InteropServices;`
`#endregion`

`namespace Owasp`
`{`
`   class Files_Xml_WindowsMessages`
`   {    `
`       [DllImport("user32", CharSet = CharSet.Auto)] public extern static IntPtr SendMessage(IntPtr hWnd, int msg, int wParam, IntPtr lParam);            `

`       private const int WM_SETREDRAW      = 0x000B;`
`       private const int WM_USER           = 0x400;`
`       private const int EM_GETEVENTMASK   = (WM_USER + 59);`
`       private const int EM_SETEVENTMASK   = (WM_USER + 69);`
`       private const int EM_SETSCROLLPOS   = (WM_USER + 222);        `

`       public static IntPtr DisableRichTextBoxReDraw(IntPtr ipHandle)`
`       {        `
`           IntPtr eventMask;                    `
`           SendMessage(ipHandle, WM_SETREDRAW, 0, IntPtr.Zero);        // Stop redrawing:             `
`           eventMask = SendMessage(ipHandle, EM_GETEVENTMASK, 0, IntPtr.Zero); // Stop sending of events:`
`           return eventMask;`
`       }`

`       public static void EnableRichTextBoxReDraw(IntPtr ipHandle,IntPtr eventMask)`
`       {                        `
`           SendMessage(ipHandle, EM_SETEVENTMASK, 0, eventMask);        // turn on events            `
`           SendMessage(ipHandle, WM_SETREDRAW, 1, IntPtr.Zero);            // turn on redrawing`
`       }`

`       public static string GetFileContent(string strFile)`
`       {`
`           try`
`           {`
`               FileStream fs = File.OpenRead(strFile);`
`               if(fs == null)`
`                   return string.Empty;`
`               StreamReader sr = new StreamReader(fs);`
`               if(sr == null)`
`                   return string.Empty;`
`               string strContent = sr.ReadToEnd();            `
`               sr.Close();`
`               fs.Close();`
`               return strContent;`
`           }`
`           catch`
`           {`
`               return "";`
`           }`
`       }`

`       public static void WriteFileContent(string strFile,string strFileContent)`
`       {`
`           if (File.Exists(strFile))`
`           {                `
`               File.Delete(strFile);`
`           }`
`           using (FileStream fs = File.Create(strFile))`
`           {`
`               Byte[] info =`
`                   new UTF8Encoding(true).GetBytes(strFileContent);`
`               // Add some information to the file.`
`               fs.Write(info, 0, info.Length);`
`           }`
`       }`

`       public static string returnStringOfSerializedObject(object objToSerialize,Type[] tExtraTypes)`
`       {`
`           XmlSerializer xsObjectSerializer;`
`           if (null ==  tExtraTypes)`
`               xsObjectSerializer = new XmlSerializer(objToSerialize.GetType());`
`           else`
`               xsObjectSerializer = new XmlSerializer(objToSerialize.GetType(),tExtraTypes);`
`           MemoryStream mstemp = new MemoryStream();`
`           xsObjectSerializer.Serialize(mstemp,objToSerialize);`
`           mstemp.Flush();`
`           mstemp.Position=0;`
`           byte[] bContents = new byte[(int)mstemp.Length];`
`           mstemp.Read(bContents,0,(int)mstemp.Length);`
`           string strSerializedObject =  Encoding.UTF8.GetString(bContents);`
`           return strSerializedObject;`
`       }`

`       public static object returnDeSerializedObjectOfSerializedString(string strObjectToDeSerialize, Type tTypeOfObjectToDeSerialize,Type[] tExtraTypes)`
`       {`
`           XmlSerializer xsObjectSerializer = new XmlSerializer(tTypeOfObjectToDeSerialize,tExtraTypes);`
`           return xsObjectSerializer.Deserialize(new MemoryStream(Encoding.UTF8.GetBytes(strObjectToDeSerialize)));        `
`       }`

`       public static void GetFilesFromDirectory(string FolderLocation,string strDirectorySearchFilter, ref StringCollection strcol)`
`       {`
`           string[] strFiles = Directory.GetFiles(FolderLocation,strDirectorySearchFilter);`
`           if(strFiles.Length != 0)`
`               strcol.AddRange(strFiles);`
`           string[] Folders = Directory.GetDirectories(FolderLocation);`
`           foreach(string strFolder in Folders)`
`           {`
`               GetFilesFromDirectory(strFolder,strDirectorySearchFilter,ref strcol);`
`           }`
`       }`

`       public static string GetTempFileName(string strExtension)`
`       {`
`           string strTempFileName = Path.Combine(AppDomain.CurrentDomain.BaseDirectory,ProgramSettings.strProjectsTempXmlFiles);`
`           strTempFileName  = Path.Combine(strTempFileName,Path.GetFileNameWithoutExtension(Path.GetTempFileName())+ strExtension);             `
`           return     strTempFileName;`
`       }`
`   }`
`}`