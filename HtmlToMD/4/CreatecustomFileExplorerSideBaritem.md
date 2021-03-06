<div id="page">

# Create custom File Explorer Side Bar item

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/24/2017 7:46:06 PM

-----

<div id="content">

**Overview:**

Some users opt to not have the Office Client installed at all and just
to use the Office web applications.  In this scenario there is no
OneDrive sync client installed and no shortcuts appear in the File
Explorer navigation.   This blog post will provide a tool and
instructions for a custom OneDrive like link to be made in the File
Explorer Side Bar area (see picture below):

[![Custom Side
Bar](media/2017/04/mycustod-300x164.jpg)](media/2017/04/mycustod.jpg)

**Workaround:**

This blog has a Visual Studio sample project and an sample .exe that
will create a Side Bar item from passed in parameters.

First you will need to know the location of the OneDrive or SharePoint
URL, a good way to do this is to open your OneDrive location and pick
"Return to classic OneDrive", this will get a more direct URL, something
like:

https://somecompany-my.sharepoint.com/personal/warren\_somecompany\_com/Documents/Forms/All.aspx

Turn the above into a WebDAV URL like
below:

\\\\somecompany-my.sharepoint.com@SSL\\DavWWWRoot\\personal\\warren\_somecompany\_com\\Documents

Once you have the title you want to use (can be anything) and the WebDAV
URL you can call the sample program:

CreateSidebarItem.exe "My Title"
"\\\\somecompany-my.sharepoint.com@SSL\\DavWWWRoot\\personal\\warren\_somecompany\_com\\Documents"

Use this sample code at your own risk, there are no warranties or
guarantees of any kind.

The solution and exe can be found
here [solution](media/2017/04/CreateSidebarItem.zip)

</div>

</div>
