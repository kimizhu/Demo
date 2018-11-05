<div id="page">

# Shredded Storage in SharePoint 2013 and Office client opening some files as "Read-Only"

[Adam R -
MSFT](https://social.msdn.microsoft.com/profile/Adam%20R%20-%20MSFT)
4/26/2016 11:36:43 AM

-----

<div id="content">

<span style="font-size: medium">**Issue:**</span>

<span style="font-size: medium">You are seeing many of your Office
documents opening up from SharePoint 2013 in a "Read-Only" state, but
other files are opening in an "Online" state. This is sometimes shown as
a hard limit in the size of the document being opened.</span>

<span style="font-size: medium">Example: Documents over 6MB in size are
opening as "Read-Only", but documents smaller than that are opening
normally.</span>

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/2477.1.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/2477.1.png)

<span style="font-size: medium">**Cause:**</span>

<span style="font-size: medium">It is possible the FileWriteChunkSize
property has been changed in the SharePoint 2013 Farm</span>

<span style="font-size: medium">**Resolution:**</span>

<span style="font-size: medium">1. Check the property size in SharePoint
Management shell(Specify your own Web Application URL):</span>

<span style="font-size: medium">$webapp = Get-SPWebApplication
http://sp2013</span>

<span style="font-size: medium">$webapp.WebService.FileWriteChunkSize |
Write-Host</span>

<span style="font-size: medium"> 2. If the value shown is not equal to
64320 then proceed to step 3.</span>

<span style="font-size: medium"> 3. Reset to default value of 64320 in
SharePoint Management shell:</span>

<span style="font-size: medium">$webapp.WebService.FileWriteChunkSize =
64320</span>

<span style="font-size: medium">$webapp.WebService.update()</span>

<span style="font-size: medium">**NOTE:**</span>

<span style="font-size: medium">SPWebApplication.WebService.FileWriteChunkSize
shouldn't be modified from the original value. The value is used in the
chunking algorithm and doesn't act as one would think, for example
setting that value to be 1 GB doesn't cause the chunks to be 1 GB each
and also doesn't cause SharePoint to start chunking at that 1 GB. The
value should be left at its original state and not modified.</span>

</div>

</div>
