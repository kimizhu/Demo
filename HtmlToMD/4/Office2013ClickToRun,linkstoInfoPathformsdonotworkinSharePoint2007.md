<div id="page">

# Office 2013 Click To Run, links to InfoPath forms do not work in SharePoint 2007

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
12/8/2014 8:20:42 AM

-----

<div id="content">

**Issue:**

You have Office 2013 Click To Run installed on a client computer, you
have SharePoint 2007 lists that contain links to InfoPath forms.  When
users click on the link to the InfoPath form, instead of InfoPath being
started IE shows the document as XML in an IE window (see screen shot
below).

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/xml.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/xml.png)

**Cause:**

****The Office IE add-on that ships with the Click to Run version of
Office are different and currently do not fully work with SharePoint
2007. 

\*\*But InfoPath forms opened from a document library work fine.

**Workaround:**

****You can change IE's behavior on how it opens XML documents to point
to InfoPath instead.

Open Regedit.exe and navigate to key:

HKEY\_CLASSES\_ROOT\\MIME\\Database\\Content Type\\text/xml

Change the value for the CLSID member to be
{807583E6-5146-11D5-A672-00B0D022E945}

The above class ID is for InfoPath.

 

</div>

</div>
