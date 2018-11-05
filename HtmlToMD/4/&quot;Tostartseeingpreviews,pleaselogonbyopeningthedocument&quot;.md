<div id="page">

# "To start seeing previews, please log on by opening the document"

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
3/27/2015 10:23:00 AM

-----

<div id="content">

**ISSUE:**

Document preview for SharePoint 2013 search results randomly
give an error "To start seeing previews, please log on by opening the
document".

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/0624.Start%20Previews.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/0624.Start%20Previews.JPG)

**CAUSE:**

The behavior occurs because the page that we use to show the preview
(\_layouts/15/wopiframe.aspx) is set up for anonymous access.  Since the
user did not browse the site collections from where the documents to be
displayed reside, there is no access token which can be presented in
order to retrieve the file. If the browser does not supply the
authentication token with the request for the page, the user will be
authenticated anonymously, which will not have access to the document
that is supposed to be shown in the preview. 
<span style="color:black;">Now in the case where the user is
authenticated, the browser sometimes drops the authentication token so
that even though the user is authenticated on the outer page, the
wopiframe request does not contain the auth token and we end up with the
“to start seeing previews…” message.</span>

RESOLUTION:

For Windows **NTLM authentication only**, a fix to target this scenario
is included **May 2014 CU** or later.

  
For other authentication providers including Kerberos, use one of the
following workarounds:

**1**.  Use the Wopiframe2.aspx logic in place of Wopiframe.aspx:

     1.        Open the file location C:\\Program Files\\Common
Files\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\LAYOUTS  
     2.        Locate wopiframe.aspx.  Rename it to wopiframe.aspx.bak. 
– This will be our backup copy.  
     3.        Locate Wopiframe2.aspx.  Make a copy of it and paste it
in the same directory.  Rename it to Wopiframe.aspx.  
     4.        Open the file location: C:\\Program Files\\Common
Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS  
     5.        Repeat steps 2 and 3 within the 15\\Template\\Layouts
folder.  
     6.        Reset IIS on the box.

               - **Possible issues** with the above workaround:

                     -Anonymous users may get prompted when looking at
document previews.

                     -Wopiframe.aspx could be overwritten and set back
to default by a
CU.

                  <span style="color:black;font-family:&#39;Arial&#39;,sans-serif;font-size:9pt;">   -<span>P<span>reviews
of Excel files may return message "We can't show a preview of this
item". </span></span></span>

**2**.  Switch to NTLM

**3**.  Disable the preview functionality

**4**.  Refresh the browser

</div>

</div>
