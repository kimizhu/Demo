<div id="page">

# Office 365 Click to Run install has issues with opening InfoPath Forms and Office documents from in house SharePoint 2007 and 2010 servers

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
8/20/2014 8:02:00 AM

-----

<div id="content">

**Issue:**

When opening an InfoPath form from SharePoint 2007 or 2010 with Office
365 (2013) click to run installed the form opens in IE as XML not in the
InfoPath client as it should.

When opening Office documents from SharePoint 2007 or 2010 with Office
365 (2013) click to run installed the open click in IE results in error:

"The document could not be opened for editing. A Microsoft SharePoint
Foundation compatible application could not be found to edit the
document"

The cause is that all the files and settings for the Office IE add-ons
are not present.

 

**Workaround:**

If you install the "Microsoft SharePoint Foundation Support" feature
then the issues go away.

**Detailed Workaround steps:**

First, download SharePoint Designer 2013 from here:

<http://www.microsoft.com/en-us/download/details.aspx?id=35491>

 Extract the SharePointdesigner\_32bit.EXE to access the source files:

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p1.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p1.png)

 

Access the Office Customization Tool (OCT) by running the /admin switch:

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p2.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p2.png)

Once inside the OCT, navigate to the “Set Feature Installation states”
on the left, and set all features to 1) Not available, 2) Hidden, 3)
Locked as such:

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p3.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p3.png)[](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p3.png)

File \> Save the MSP file that gets created by the OCT and place it into
the “Updates” folder that is included with your previously extracted
source.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p4.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/p4.png)

 Now you can simply double click Setup.exe, push out a batch file that
calls setup from a network location, or use a software distribution tool
like SCCM to push out the fix.

 

</div>

</div>
