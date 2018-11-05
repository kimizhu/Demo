<div id="page">

# Force Microsoft Word to open in edit mode from hyperlink in an email

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
12/4/2014 8:08:00 AM

-----

<div id="content">

**Overview:**

By default Microsoft Word opens hyperlinks to documents as read only
when the hyperlink is part of an emails contents.

Many issues can arise when the document is opened read only.  This post
shows a way to have Word open the document as read-write when the
hyperlink to the document is in an email.

I am going to take this issue a step further by explaining how to edit a
SharePoint workflow email task to send an email where the hyperlink to
the document will open as read-write in Word without any security
warnings.

**Solution:**

You have a working SharePoint workflow that sends emails that contain
hyperlinks to Word documents.  When users click on the link in Outlook
the document opens as read only with Word, this behavior is causing you
problems.

1\. Open the "Define E-mail Message" task with SharePoint designer (see
screen shot below)

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/email.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/email.png)

2\. Select the hyperlink to the document and click the hyperlink edit
button [![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Link.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Link.png)

3\. Add ms-word:ofe|u| to the front of the hyperlink definition address
line.   For example:  ms-word:ofe|u|\[%Task Process:Web URL%\]/\[%Task
Process:Item URL%\]

4\. Save and publish your workflow

5\. Use the workflow to generate a new email and click on the link, the
user will get an Outlook security warning (see below)

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Security.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Security.png)

6.  You can make this warning go away by adding one of the two following
registry keys, 14 is for Office 2010 and 15 is for Office
2013

HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Office\\14.0\\common\\Security\\Trusted
Protocols\\All
Applications\\ms-word:

HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Office\\15.0\\common\\Security\\Trusted
Protocols\\All Applications\\ms-word:

This only prevents the security warning for Microsoft Word documents.

Of course you can use the technique for plain hyperlinks,  for example:

Instead of using: http://sp2010ocsi/WRWFLib/2My test document.docx

You could use:   ms-word:ofe|u|http://sp2010ocsi/WRWFLib/2My test
document.docx

 

</div>

</div>
