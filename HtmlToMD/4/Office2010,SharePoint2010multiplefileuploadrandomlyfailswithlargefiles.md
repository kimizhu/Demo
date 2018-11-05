<div id="page">

# Office 2010, SharePoint 2010 multiple file upload randomly fails with large files

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/8/2014 7:47:00 AM

-----

<div id="content">

**Issue:**

Office 2010 / SharePoint 2010 when uploading multiple documents, large
files will sometimes randomly fail. (114012011114004)

**Cause:**

****This is a design limitation of the feature and limitations with 32
bit processes.  As memory get allocated by the .NET runtime if a large
enough block is not found an out of memory exception is generated and
the file upload fails.  The level of memory fragmentation at any given
time is random.

**Workaround:**

Use single file upload or upgrade to both Office 2013 and SharePoint
2013 and use the new "Drag and Drop Upload".

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/error.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/error.png)

</div>

</div>
