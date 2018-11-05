<div id="page">

# Office 2013 opens .ppsx files in PowerPoint instead of slide show mode

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
8/14/2015 7:06:01 AM

-----

<div id="content">

**Issue:**

****User opens a .ppsx file from SharePoint or other network location
and the file opens in PowerPoint full application.  Users want the file
to open in Slide show mode.

 

**Workaround:**

This behavior can be modified by making a registry change.

\*\*Registry changes can be dangerous if not done correctly, you assume
all risks for editing the registry.

 

Open Regedit.exe

Navigate to Key "HKEY\_CLASSES\_ROOT\\PowerPoint.Show.12"

edit value BrowserFlags

Set the value to be 8

 

The possible values are

a = open in edit mode

8 = open in show mode in new window

0 = open in show mode   - this opens in the browser, I would not
recommend this, the power point process could possibly get stuck and
stay running even after the slide show ended.

</div>

</div>
