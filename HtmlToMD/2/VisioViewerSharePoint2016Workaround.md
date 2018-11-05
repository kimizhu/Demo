<div id="page">

# Visio Viewer / SharePoint 2016 Workaround

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
7/14/2017 2:56:14 PM

-----

<div id="content">

**Issue:**

In SharePoint 2016 for document libraries that are set to "Open in the
client application" Visio documents will do nothing when clicked on or
show the Windows Store popup window, if the Visio rich client is not
installed.

 

**Details:**

The Visio Viewer is installed with Microsoft Office, ideally the Visio
Viewer would show the file or the web Visio Viewer would show the file. 
If the web viewer were to be used, it would require a change to the
SharePoint code.  SharePoint JavaScript code has no way of telling if
Visio is installed or not due to web browser security, so their only
option would be to open all Visio files in the web viewer, not honoring
the document library setting for users that do have the Visio rich
client installed who want Visio to start when the files are clicked on
in the SharePoint UI.

 

**This use to work, what happened? **

Office, SharePoint and Internet Explorer have been evolving, they are
moving away from using the Office IE add-ins to using a protocol handler
technology.  Modern browsers do not support old style add-ins, but
protocol handlers will work in all modern browsers and IE.  The
SharePoint code now uses protocol handlers instead of browser add-ins to
open files, see links below for more
information:

https://developer.mozilla.org/en-US/docs/Web-based\_protocol\_handlers

https://msdn.microsoft.com/en-us/library/office/Dn906146.aspx?f=255\&MSPPError=-2147217396

 

**Workaround:**

\*\*Warning, this is sample code, use at your own risk, there are no
guarantees or warranties of any kind\*\*

This blog post contains a sample program that will create a protocol
handler for the Visio Viewer that ships with Microsoft Office.

The Visual Studio solution can be found here:
[VisioHandlerSolution](https://msdnshared.blob.core.windows.net/media/2017/07/VisioHandlerSolution.zip).

You can find the VisioHandler.exe program under the
VisioHandler\\VisioHandler\\bin\\Debug folder.

VisioHandler.exe needs to be deployed to this exact folder: C:\\Program
Files\\VisioViewerHandler

One time setup is needed to configure the registry to hookup the
protocol handler, this command needs to be ran with administrator
privileges:

VisioHandler.exe install

The above command will check to see if the protocol handler already
exists, if it does exist the command will do nothing.  This insures that
if the Visio rich client is installed, none of its settings will be
overwritten.

After the file has been deployed and the "install" command ran, all
should be working.  Go to a SharePoint 2016 document library and try to
open a Visio document, IE will download the file and open it using the
Visio viewer.

The code could be modified to use the Visio web viewer, simply change
the call to ShellExecute to call VisioWebAccess.aspx instead, see sample
below:

http://sp2016ocsi/\_layouts/15/VisioWebAccess/VisioWebAccess.aspx?id=/Shared%20Documents/warrenr/Drawing1.vsdx

</div>

</div>
