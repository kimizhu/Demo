<div id="page">

# “A problem occurred when accessing Office Document Cache"

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
1/12/2015 8:40:37 AM

-----

<div id="content">

**ISSUE**:

Receive a message **“A problem occurred when accessing Office Document
Cache.  Do you want to repair the problem?”** when trying to open any
Office file from **SharePoint** or **OneDrive**.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/OfficeDocCache.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/OfficeDocCache.png)

Clicking **Yes**, shows message **"The Microsoft Office Upload Center
found a problem while accessing the Microsoft Office Document Cache."**

** **

** **

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Upload%20Message.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Upload%20Message.PNG)

  
**CAUSE**:

**Office 2013** and a **Click-2-Run** version of OneDrive for
Business was installed on same system.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/OnedriveEnUs.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/OnedriveEnUs.PNG)

\* To verify if you have installed the Click-2-Run version of OneDrive
for Business, go to Control Panel, Programs and Features, and "en-us"
will be next to the name.

  
**RESOLUTION:**

Remove the **Click-2-Run** version of OneDrive for Business.

\* **.msi and Click-2-Run** versions of Office are **not recommended**
on the same system  -  **http://support.microsoft.com/kb/2753630**.

</div>

</div>
