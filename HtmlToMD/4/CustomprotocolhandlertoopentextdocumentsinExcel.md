<div id="page">

# Custom protocol handler to open text documents in Excel

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
1/4/2017 3:41:23 PM

-----

<div id="content">

**Summary:**

You want to be able to open select text files in Excel instead of the
configured text editor for the system.

**Solution:**

This blog post contains a custom protocol handler that will open any
file type in Excel.

For example once the custom protocol handler has been deployed (see
below for more info) you can use this URL format to open text files in
Excel

ExcelText:http://sp2013ocsi/Shared%20Documents/warrenr/test.txt

The above format can be used as a link in a web page or email, pasted
into a web browser tab, or pasted into Windows explorer and will open
the text file with Excel.

 

**Setup:**

\*\*Warning, this blog post contains sample code and registry changes,
there are no warrantees, use at your own risk.

A version of Office must be installed on the client computer.

The ExcelTextHandler.exe from the attached Visual Studio solution needs
to be placed somewhere on the client computer.

Here is the zip file containing the Visual Studio solution
[exceltexthandler](media/2017/01/ExcelTextHandler.zip).

path to the exe in the zip file is:
ExcelTextHandler\\ExcelTextHandler\\bin\\Debug\\ExcelTextHandler.exe

Once the ExcelTextHandler.exe has been placed on the client computer,
you can update the registry to use it.

Below is text that can be used to build a registry file (.reg) to
configure the protocol handler:

\*\*PATH\_TO\_HANDLER needs to be wherever you put the
ExcelTextHandler.exe

Windows Registry Editor Version 5.00

\[HKEY\_CLASSES\_ROOT\\ExcelText\]

@="Url:ExcelText Protocol"

"URL Protocol"=""

"UseOriginalUrlEncoding"=dword:00000001

\[HKEY\_CLASSES\_ROOT\\ExcelText\\shell\]

\[HKEY\_CLASSES\_ROOT\\ExcelText\\shell\\open\]

\[HKEY\_CLASSES\_ROOT\\ExcelText\\shell\\open\\command\]

@="C:\\\\PATH\_TO\_HANDLER \\\\ExcelTextHandler.exe \\"%1\\""

Once you save the .reg file, just double click it to have the data put
into the registry.  Pushing out registry changes and files to many
client computers is a straight forward process, just talk to whoever
manages your  enterprises computers.

</div>

</div>
