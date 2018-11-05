<div id="page">

# Word / SharePoint - locked for editing by 'another user'

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
5/28/2015 6:54:00
AM

-----

<div id="content">

**<span style="font-size:small;">Issue:</span>**

**<span style="font-size:small;"></span>**<span><span style="font-size:small;">Sometimes
when opening Word documents from SharePoint you see message:  my.docx is
locked for editing by 'another user'.</span></span>

**<span style="font-size:small;">[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/anotheruser.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/anotheruser.png)</span>**

<span><span style="font-size:small;">Or with PowerPoint or Excel you see
similar message, but instead of the users name, like "John Smith", you
see their network ID, like "I:0\#w|mydom\\smithj"</span></span>

<span><span style="font-size:small;">You would like to accurately see
the users name in the message so they can more easily be contacted to
release the lock on the document.</span></span>

<span><span style="font-size:small;">This issue will only happen when IE
tries to open a real hyperlink to the document, most SharePoint document
opens happen via JavaScript code or a protocol handler.  But SharePoint
search preview "Edit" link will open document like a direct URL, which
can cause this issue.  For example, if you paste a document URL into IE
address bar and hit enter you may encounter this issue: 
Like:</span></span>

<span><span style="font-size:small;"><http://sp2013ocsi/WRBI/ForceCheckoutLib/Test2-Ben.docx></span></span>

**<span style="font-size:small;"></span>** 

**<span style="font-size:small;">Workarounds:</span>**

<span><span style="font-size:small;">If you have Office Web Apps
configured, you can first open in the web app, then pick to edit in the
rich client from there.  This will by pass the issue.</span></span>

<span><span style="font-size:small;">Or you can modify these registry
keys, they will change how the Office application is started and bypass
this issue.  The screen below will be showed instead:</span></span>

<span><span style="font-size:small;">[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/working.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/working.png)</span></span>

**\*\*You assume all risks for modifying the registry, invalid changes
to the registry could cause your computer to stop working**

These registry changes can work around the
issue:

HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Classes\\Word.Document.12\\shell\\OpenAsReadOnly\\command  
Remove the /h from the default value, you would end up with something
like this:  
"C:\\Program Files (x86)\\Microsoft Office\\Office14\\WINWORD.EXE" /n
"%1"

 

HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Classes\\Excel.Sheet.12\\shell\\OpenAsReadOnly\\command  
Remove the /h from the default value, you would end up with something
like this:  
"C:\\Program Files (x86)\\Microsoft Office\\Office14\\EXCEL.EXE"
/dde

 

HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Classes\\PowerPoint.Slide.12\\shell\\OpenAsReadOnly\\command  
Remove the /h from the default value, you would end up with something
like this:  
C:\\PROGRA\~2\\MICROS\~4\\Office14\\POWERPNT.EXE "%1"

 

 

 

 

 

</div>

</div>
