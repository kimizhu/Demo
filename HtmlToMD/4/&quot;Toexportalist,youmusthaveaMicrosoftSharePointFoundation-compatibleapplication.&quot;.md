<div id="page">

# "To export a list, you must have a Microsoft SharePoint Foundation-compatible application."

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
2/24/2014 5:11:23 AM

-----

<div id="content">

**ISSUE:**

You receive message "To export a list, <span id="#h10">you</span>
<span id="#h11">must</span> <span id="#h12">have</span> a
<span id="#h13">Microsoft</span> <span id="#h14">SharePoint</span>
<span id="#h15">Foundation</span>-compatible application"  when trying
to export a list from SharePoint.

**CAUSE:**

You have multiple versions of Office installed on your workstation
(Office 2013 and Office 2010  or Office 2007).

  
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
    ](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Controls_disable.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Controls_disable.JPG)  
      
      
  - Once the change process is complete, click the Office 2007 or
    Office 2010 instance and choose “Change”
  - In the “Change your installation of …” window, select the “Repair”
    option and click Continue.
  - Once Repair complete, Restart your computer

**NOTE: ** This solution doesn't apply to scenarios when the following
2013 applications are installed:  **SharePoint Designer, OneNote or
InfoPath**

To  export a list from SharePoint when SharePoint Designer, OneNote or
InfoPath is installed, go into the registry by typing **regedit** from
the Run line and rename the **SharePoint.OpenDocuments.5** key (ex.
SharePoint.OpenDocuments.5.old) under **HKEY\_CLASSES\_ROOT**.

**\*\*** This key will be added back to the registry anytime you run a
**Repair/Update** of the Office 2013 program and will be have to
**renamed/deleted again**.

** **

</div>

</div>
