<div id="page">

# Office 365 Cannot open files from recent documents list (MRU) with RoamingSettingsDisabled policy set

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
10/8/2018 2:49:29 PM

-----

<div id="content">

**Issue:**

You have Office 365 client application (Word, Excel, PowerPoint) trying
to open a document from SharePoint or OneDrive via the Office recently
used document list and receive error:

"Sorry, something went wrong"

**Cause:**

Office 365 no longer support the registry
key:

\[HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Office\\16.0\\Common\\Roaming\]
"RoamingSettingsDisabled"

\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\16.0\\Common\\Roaming\]
"RoamingSettingsDisabled"

**Workaround:**

The workaround is to delete the above registry keys or set it to 0.

If you need to reduce the traffic that Office is sending to the internet
you can use these registry
    keys:

  - HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*16*.0\\Common\\Internet
    
    Name: UseOnlineContent
    
    Type: DWORD
    
    Value: 0 -<span>Do not allow Office to connect to the Internet.
    Office applications do not connect to the Internet to access online
    services or to download the latest online content from Office.com.
    Connected features of Office are
    disabled.</span>

  - HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Office\\*16*.0\\Common\\Internet
    
    Name: UseOnlineContent
    
    Type: DWORD
    
    Value: 0 - <span>Do not allow Office to connect to the Internet.
    Office applications do not connect to the Internet to access online
    services or to download the latest online content from Office.com.
    Connected features of Office are disabled.</span>

</div>

</div>
