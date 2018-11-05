<div id="page">

# Unable to open Office files from SharePoint site

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
2/24/2014 5:10:00 AM

-----

<div id="content">

**ISSUE**:

When trying to open an Office file within the client application from a
SharePoint site, nothing happens.

The file does not open and no error message is presented.

**CAUSE**:

  
This issue is seen when an Office 2013 product such as Lync, Project,
Visio is installed and Office 2010 is install on the same machine and
the SharePoint Foundation Support enabled on both

**SOLUTION 1:** 

  - Install **Service Pack 2** for Office 2010  - 
    [<span style="color:#0563c1;">http://support.microsoft.com/kb/2687455</span>](http://support.microsoft.com/kb/2687455)<span style="font-family:Times New Roman;font-size:medium;"> </span>

**SOLUTION 2:**

  - Using Control Panel, Programs and Features window, locate existing
    instance of Office 2013 application, select it and click on  Change
    button.
  - In the “Change your installation of …” window, select the “Add or
    Remove Features” option and click Continue.
  - Expand the “Office Tools”, select “Microsoft SharePoint Foundation
    Support” and then select the “Not Available” option, Click
     Continue.  
      
    [![
    ](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5187.Controls_disable.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5187.Controls_disable.JPG)  
      
      
  - Once the change process is complete, click the Office 2010 instance
    and choose “Change”
  - In the “Change your installation of …” window, select the “Repair”
    option and click Continue.
  - Once Repair complete, Restart your computer

**NOTE: ** This solution doesn't apply to scenarios when the following
applications are installed:  **SharePoint Designer, OneNote or InfoPath
2013, or InfoPath 2010 with SP-2.**

To  open an Office file in the client when SharePoint Designer, OneNote
or InfoPath is installed, go into the registry by typing **regedit**
from the Run line and rename the **SharePoint.OpenDocuments.5** key (ex.
SharePoint.OpenDocuments.5.x) under **HKEY\_CLASSES\_ROOT**.

**\*\*** This key will be added back to the registry anytime you run a
**Repair/Update** of the Office 2013 program and will be have to
**renamed/deleted again**.

</div>

</div>
