<div id="page">

# Office 2010 - Error during check in of password protected files to SharePoint

[Zakir H -
MSFT](https://social.msdn.microsoft.com/profile/Zakir%20H%20-%20MSFT)
2/6/2014 9:26:00 AM

-----

<div id="content">

When you check in a file to SharePoint using Office 2010 that is
encrypted with password protection, you may receive the following error:

 

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/checkin.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/checkin.png)

 

**Cannot perform this operation. The file is no longer checked out or
has been deleted.**

By default, when you encrypt a file using password protection, the file
properties, or metadata, are also encrypted. When the file properties
are encrypted,
<span id="#h39" class="KeywordHighlight">SharePoint</span> cannot read
the existing properties, and therefore cannot write new property values
to the document in SharePoint.**  
**

To fix this error, try the following steps to disable metadata
encryption:

1.  Open the **Registry Editor** by going **Start \> Run** and typing
    **regedit**, or run it from the **Command Prompt** by going
    to** Start \> Programs \> Accessories \> Command Prompt**
2.  Navigate to
    **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\14.0\\Common\\Security**
3.  If you get to **Common** and the **Security** key does not exist,
    create it by right-clicking on **Common** and selecting **New \>
    Key** and name it **Security**
4.  Inside the **Security** key, create a new DWORD value by
    right-clicking and selecting **New \> DWORD (32-bit) value** and
    name it **OpenXMLEncryptProperty**
5.  Right-click **OpenXMLEncryptProperty,** select **Modify,** and in
    **Value Data,** enter the number **0,** and click **OK.  
    **
6.  Close all Office applications and then test to see if the issue is
    resolved

</div>

</div>
