<div id="page">

# Excel 2013 / 2016 does not open XML files from SharePoint

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/4/2017 3:28:18 PM

-----

<div id="content">

**Overview:**

You have Excel files in .XML format (XML Spreadsheet 2003) and you get
error

"<span style="margin: 0px;font-family: &#39;Segoe UI&#39;,sans-serif;font-size: 10pt"><span style="color: #000000">This
action couldn't be performed because Office doesn't recognize the
command it was given."</span></span>

When you try to open the file from a SharePoint document library.

There will likely not be a product change to address this issue, it is
recommended that the issue is worked around.

**Workaround:**

Deploy a registry key based fix, depending on the version and bitness of
Office Installed the registry changes will vary.

\*\*Warning, editing the registry can have harmful side effects if not
done property, use this workaround at your own risk.

Registry file content will be in-between the ---- markers

\----Office 2013 MSI 32 bit ---

<div>

Windows Registry Editor Version 5.00

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\.xml\\OpenWithList\\excel.exe\]

@=""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files (x86)\\\\Microsoft
Office\\\\Office15\\\\EXCEL.EXE\\" /n \\"%1\\""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\SupportedTypes\]

".xml"=""

</div>

\---End Office 2013 MSI 32 bit ---

<div>

\----Office 2016 MSI 32 bit ---

</div>

<div>

Windows Registry Editor Version 5.00

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\.xml\\OpenWithList\\excel.exe\]

@=""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\Office16\\\\EXCEL.EXE\\" /n \\"%1\\""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\SupportedTypes\]

".xml"=""

</div>

\----End Office 2016 MSI 32 bit ---

\----Office 2016 MSI 64 bit ---

<div>

Windows Registry Editor Version 5.00

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\.xml\\OpenWithList\\excel.exe\]

@=""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\Office16\\\\EXCEL.EXE\\" /n \\"%1\\""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\excel.exe\\SupportedTypes\]

".xml"=""

</div>

\----End Office 2016 MSI 64 bit ---

<div>

\----Office 2016 C2R 32 bit ---

</div>

<div>

Windows Registry Editor Version 5.00

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\]

"FriendlyAppName"="@C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\VFS\\\\ProgramFilesCommonX86\\\\Microsoft
Shared\\\\Office16\\\\oregres.dll,-206"

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\]

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\\edit\]

@="@C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\VFS\\\\ProgramFilesCommonX86\\\\Microsoft
Shared\\\\Office16\\\\oregres.dll,-1"

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\Office16\\\\EXCEL.EXE\\" /n
\\"%1\\""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\SupportedTypes\]

".xml"=""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\Applications\\excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\Root\\\\Office16\\\\EXCEL.EXE\\" /n
\\"%1\\""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\Applications\\excel.exe\\SupportedTypes\]

".xml"=""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\.xml\\OpenWithList\\Excel.exe\]

@=""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\.xml\\OpenWithList\\excel.exe\]

@=""

</div>

<div>

\----End Office 2016 C2R 32 bit ---

</div>

<div>

</div>

<div>

<div>

\----Office 2016 C2R 64 bit ---

</div>

<div>

Windows Registry Editor Version
5.00

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\.xml\\OpenWithList\\Excel.exe\]

@=""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\.xml\\OpenWithList\\excel.exe\]

@=""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\]

"FriendlyAppName"="@C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\VFS\\\\ProgramFilesCommonX64\\\\Microsoft
Shared\\\\Office16\\\\oregres.dll,-206"

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\]

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\\edit\]

@="@C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\VFS\\\\ProgramFilesCommonX64\\\\Microsoft
Shared\\\\Office16\\\\oregres.dll,-1"

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\root\\\\Office16\\\\EXCEL.EXE\\" /n
\\"%1\\""

</div>

<div>

\[HKEY\_CLASSES\_ROOT\\Applications\\Excel.exe\\SupportedTypes\]

".xml"=""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\Applications\\excel.exe\\shell\\edit\\command\]

@="\\"C:\\\\Program Files\\\\Microsoft
Office\\\\Root\\\\Office16\\\\EXCEL.EXE\\" /n
\\"%1\\""

</div>

<div>

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\ClickToRun\\REGISTRY\\MACHINE\\Software\\Classes\\Applications\\excel.exe\\SupportedTypes\]

".xml"=""

</div>

<div>

<div>

\----End Office 2016 C2R 64 bit ---

</div>

</div>

</div>

</div>

</div>
