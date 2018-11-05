<div id="page">

# Sorry, but to open this workbook, your computer must be running a supported version of Microsoft \<application\> and a browser that supports opening files directly from Office Online.

[Taylor H -
MSFT](https://social.msdn.microsoft.com/profile/Taylor%20H%20-%20MSFT)
6/17/2015 12:43:13 PM

-----

<div id="content">

**ISSUE:**

Users are receiving an error message
\[<span style="background-color: #ffff99">Sorry, but to open this
workbook, your computer must be running a supported version of Microsoft
\<application\> and a browser that supports opening files directly from
Office Online.</span>\] when opening documents from SharePoint 2013
sites into Office Pro Plus 2013.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Error.jpg)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Error.jpg)

**CAUSE:**

Webroot AV seems to be blocking Internet Explorer's access to
Interceptor.dll, which is an Office component that allows Internet
Explorer to open documents in the local Office applications.

**FIX:**

As Webroot AV seems to be blocking access, Microsoft has no direct fixes
for this issue. There are several workarounds available below.

**WORKAROUNDS:**

The best workaround we've found is to add an exception for
Interceptor.dll in Webroot AV. This dll is typically found at
\[<span style="background-color: #ffff99">C:\\Program Files\\Microsoft
Office 15\\root\\office15</span>\].

**NOTE:**

\-Although it's not limited to Windows 7, the vast majority of support
cases we've encountered, users have been running Windows 7.

\-This issue should only effect Internet Explorer due to the unique way
it reaches out to the local machine to engage the Office apps. In our
troubleshooting, the latest versions of Firefox and Chrome should not
reproduce this issue.

\-If the workaround stops the issue from reproducing, we highly
recommend you reach out to Webroot support to report the issue.

</div>

</div>
