<div id="page">

# "The Webpage cannot be displayed" when trying to open/edit an Office file from a SharePoint 2013 site

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
2/24/2014 5:12:00 AM

-----

<div id="content">

** **

**ISSUE:**

 

When opening an Office file from a SharePoint 2013 site, you receive a
message “The Webpage cannot be displayed” also in the address bar you
will see the following:

Excel  -  ms-excel:ofv|u|https://abc.sharepoint.com/Shared
Documents/Excelfile.xlsx

Word  -   ms-word:ofe|u|https://abc.sharepoint.com/Shared
Documents/Wordfile.docx

 

**CAUSE:**

 

This issue is seen when multiple versions of Office are installed on the
same system and the SharePoint Foundation Support is enabled on both:

 Office 2013 including products such as Lync, Project, Visio and Office
2010 or Office 2007

**SOLUTION 1:** (When Office 2007 is present)

  - Using Control Panel, Programs and Features window, locate existing
    instance of Office 2013 application, select it and click on  Change
    button.
  - In the “Change your installation of …” window, select the “Add or
    Remove Features” option and click Continue.
  - Expand the “Office Tools”, select “Microsoft SharePoint Foundation
    Support” and then select the “Not Available” option, Click
     Continue.  
      
    [![
    ](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/8540.Controls_disable.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/8540.Controls_disable.JPG)  
      
      
  - Once the change process is complete, click the Office 2007 instance
    and choose “Change”
  - In the “Change your installation of …” window, select the “Repair”
    option and click Continue.
  - Once Repair complete, Restart your computer

**NOTE: ** This solution doesn't apply to scenarios when the following
2013 applications are installed:  **SharePoint Designer, OneNote or
InfoPath**

To open the Office 2007 files in this scenario, go into the registry by
typing regedit from the Run line and rename the
**SharePoint.OpenDocuments.5** key (ex. SharePoint.OpenDocuments.5.old)
under **HKEY\_CLASSES\_ROOT**.

**\*\*** This key will be added back to the registry anytime you run a
**Repair/Update** of the Office 2013 program and will be have to
**renamed/deleted again**.

**  
  
SOLUTION 2:**  (When 2010 is present)

  - Install **Service Pack 2** for Office 2010  - 
    [<span style="color:#0563c1;">http://support.microsoft.com/kb/2687455</span>](http://support.microsoft.com/kb/2687455)<span style="font-family:Times New Roman;font-size:medium;"> </span>

<span style="font-family:Times New Roman;font-size:medium;"> </span>

**NOTE: ** This solution doesn't apply to scenarios when SP-2 is
installed on **InfoPath 2010.**

To open the InfoPath 2010 files in this scenario, go into the registry
by typing regedit from the Run line and rename the
**SharePoint.OpenDocuments.5** key (ex. SharePoint.OpenDocuments.5.old)
under **HKEY\_CLASSES\_ROOT**.

**\*\*** This key will be added back to the registry anytime you run a
**Repair/Update** of the Office 2013 program and will be have to
**renamed/deleted again**.

</div>

</div>
