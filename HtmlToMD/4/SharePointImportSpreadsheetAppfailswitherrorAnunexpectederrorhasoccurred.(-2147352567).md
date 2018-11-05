<div id="page">

# SharePoint "Import Spreadsheet" App fails with error "An unexpected error has occurred. (-2147352567)"

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
8/9/2016 2:22:22 PM

-----

<div id="content">

**Summary:**

You are using the SharePoint "Import Spreadsheet" App and when the
"Import" button on the web page is clicked this error is shown in the
web browser:

"An unexpected error has occurred.  (-2147352567)"

 

**Cause:**

Security restrictions are preventing the web page from starting and
using Excel.exe.

 

**Workaround:**

Delete or modify this registry value:

\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Common\\Security\]

"automationsecurity"=dword:00000003

This policy setting controls whether macros can run in an
Office application that is opened programmatically by another
application.

If you enable this policy setting, you can choose from three options for
controlling macro behavior in Excel, PowerPoint, and Word when the
application is opened programmatically:

\- Disable macros by default \[3\] - All macros are disabled in the
programmatically opened application.

\- Macros enabled (default) \[1\] - Macros can run in the
programmatically opened application. This option enforces the default
configuration in Excel, PowerPoint, and Word.

\- User application macro security level \[2\] - Macro functionality is
determined by the setting in the "Macro Settings" section of the Trust
Center.

If you disable or do not configure this policy setting, when a separate
program is used to launch Microsoft Excel, PowerPoint, or Word
programmatically, any macros can run in the programmatically opened
application without being blocked.

</div>

</div>
