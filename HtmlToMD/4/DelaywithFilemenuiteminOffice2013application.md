<div id="page">

# Delay with File menu item in Office 2013 application

[Zakir H -
MSFT](https://social.msdn.microsoft.com/profile/Zakir%20H%20-%20MSFT)
2/5/2015 4:58:00 PM

-----

<div id="content">

You may experience a long delay where an Office 2013 application seems
to hang for a number of seconds when you click on the File menu item,
for example when trying to access the Save options for a Word or Excel
file:

 

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage1.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage1.PNG)

 

Clicking on File should bring up the Backstage view, where you can
manage your files and related data by creating or saving files or
setting options:

 

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage2.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage2.PNG)

 

In cases where it takes a long time for the Backstage to appear, the
application may be trying to contact a network location such as
OneDrive, and network latency could cause the application to hang for a
number of seconds. If you are consistently experiencing this symptom,
and you are not using OneDrive, you can resolve the issue be enabling
the following option: **File \> Options \> Save \> Don't show the
Backstage when opening or saving files**

** **

**  
**[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5141.backstage3.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5141.backstage3.PNG)

 

With this setting enabled, the File menu should show up immediately.
Instead of getting a Backstage view when clicking Save or Open, you will
be presented with a classic Open or Save dialog box instead:

 

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage5.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage5.PNG) 

 

In order to implement this setting on all computers in your
organization, you can use a registry key to enable this option.
Configure the registry key below with a value of 1. Create the
SkipOpenAndSaveAsPlace key as a DWORD value if it does not already
exist.

   
   **HKEY\_CURRENT\_USER\\Software\\
Microsoft\\Office\\15.0\\Common\\General\\SkipOpenAndSaveAsPlace**

**   
**

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage4.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/backstage4.PNG)

</div>

</div>
