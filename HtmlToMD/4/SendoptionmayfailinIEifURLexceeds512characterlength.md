<div id="page">

# Send option may fail in IE if URL exceeds 512 character length

[Al - MSFT](https://social.msdn.microsoft.com/profile/Al%20-%20MSFT)
4/6/2015 4:49:00 PM

-----

<div id="content">

**SYMPTOM:**

Consider a scenario where a user browses to a SharePoint 2013 site using
Internet Explorer (IE), searches for an Office document and hits the
'Send' option (in order to send the URL via Email).

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5327.Send.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/5327.Send.JPG)

One of the following occurs:

  - IE hangs and nothing ever occurs.
  - IE opens a blank tab, hangs and does nothing further.

During this same scenario, the following is also true:

  - Other non-IE browsers seem to work fine with the same document URL.
  - The URL is at least 512 characters in length.

**CAUSE:**

This is a known limitation involving current versions of Internet
Explorer, the *mailto:* protocol, and URLs that exceed 512 characters.

**SOLUTION:**

Some suggestions to avoid this include (choose
<span style="text-decoration:underline;">one</span> of the following).

  - Enable Protected Mode for the IE zone that the site URLs are set
    to.  *Note that this workaround may cause other limitations.*

*[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Protected%20Mode.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Protected%20Mode.JPG)*

* *

  - Ensure the size of the URL does not exceed 512 characters in length.

<!-- end list -->

  - Use a registry setting to configure the *mailto* protocol for the IE
    zone that Sharepoint sites are set to.  If, for example, the site
    URL is in the Trusted Sites zone, set the mailto protocol to 2, and
    so
on.

**HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet
Settings\\ZoneMap\\ProtocolDefaults**

or 

**HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet
Settings\\ZoneMap\\ProtocolDefaults **    

Name: mailto  
Type: REG\_DWORD  
Data: 0

*The value for the zones are:*

   Value    Setting  
   ------------------------------  
   0        Local Machine Zone  
   1        Local Intranet Zone  
   2        Trusted sites Zone  
   3        Internet Zone  
   4        Restricted Sites Zone

</div>

</div>
