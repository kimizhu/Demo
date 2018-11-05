<div id="page">

# Office 2016 O365, Get Visio and Project MSI to work via Citrix

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
10/6/2016 9:09:03 PM

-----

<div id="content">

**Summary:**

Office 2016 O365 uses click to run (C2R) deployment technology.  It is
not possible to have Office 2016 C2R installed on a computer that also
has 2016 MSI products on it, like Visio and Project.  Some customer want
to be able to leverage an existing investment they have in 2016 MSI
products by making them available via Citrix.  With Citrix the MSI
application are not actually installed on the client system.

Office / SharePoint use protocol handers to open files since Visio and
Project are not actually installed there is no handler present for them
to use and the SharePoint web UI does nothing or gives an error when
trying to open these file types from the SharePoint web UI.  Details
about the protocol handler format can be found
here:

https://msdn.microsoft.com/en-us/library/office/Dn906146.aspx?f=255\&MSPPError=-2147217396

The advantage of the protocol handers is that they do not require any
browser add-ins so they work with all modern browsers.

**Solution:**

The "right" solution would be to give users licenses to the O365 version
of Visio and Project, your account manager can often make this
financially equivalent.

If for some reason you must have the MSI version of Visio and Project
available to some of your users you can use Azure RemoteApp or Citrix to
provide access to the MSI applications with out actually having to
install them on the users local computer.

https://www.remoteapp.windowsazure.com/Default.aspx

The solution presented in this blog post creates a custom protocol
hander that can point to any executable you want.  It basically routes
the request from the web browser to whatever local exe can start the
remote application.

\*\*Warning, this blog post contains sample code, there are no
warrantees, use at your own risk.

How to deploy and use this solution:

First download this zip file [VisioHandler Visual Studio
Solution](media/2016/10/VisioHandler.zip)

Unzip the file

Go to the VisioHandler\\VisioHandler\\bin\\Debug folder and copy the
VisioHandler.exe and VisioHandler.exe.config file to a location on users
hard disk, record this location.

I am assuming that the exe that connects to the remote application
is under the users AppData folder, like C:\\Users\\warren\\AppData

The VisioHandler.exe needs to know where the exe that connects to the
remote application is located, you can edit the VisioHandler.exe.config
file and replace the value "\\Citrix\\SelfService\\Visio2016.exe" with
whatever subdirectory and exe under AppData where your exe that connects
to the remote application lives.

You then need to build a registry file (.reg) to configure the protocol
handler, here is a sample registry text:

\*\*PATH\_TO\_HANDLER needs to be wherever you put the VisioHandler.exe

Windows Registry Editor Version 5.00

\[HKEY\_CLASSES\_ROOT\\ms-visio\]

@="Url:Visio Protocol"

"URL
Protocol"=""

"UseOriginalUrlEncoding"=dword:00000001

\[HKEY\_CLASSES\_ROOT\\ms-visio\\DefaultIcon\]

@="C:\\\\Users\\\\warren\\\\AppData\\\\Roaming\\\\Citrix\\\\SelfService\\\\Visio2016.exe,0"

\[HKEY\_CLASSES\_ROOT\\ms-visio\\shell\]

\[HKEY\_CLASSES\_ROOT\\ms-visio\\shell\\open\]

\[HKEY\_CLASSES\_ROOT\\ms-visio\\shell\\open\\command\]

@="C:\\\\PATH\_TO\_HANDLER\\\\VisioHandler.exe \\"%1\\""

Once you save the .reg file, just double click it to have the data put
into the registry.

**What about project?**

Download this Visual Studio project
[ProjectHelper](media/2016/10/ProjectHelper.zip)

Then follow the same steps as the Visio protocol handler listed above,
except in the .reg file you need to use ms-project instead of ms-visio
in all places that it is used.

 

</div>

</div>
