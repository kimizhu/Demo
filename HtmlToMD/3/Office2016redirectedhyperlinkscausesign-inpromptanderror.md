<div id="page">

# Office 2016 redirected hyperlinks cause sign-in prompt and error

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
3/7/2017 2:36:27 PM

-----

<div id="content">

**Overview:**

You have migrated your on premise SharePoint content to the cloud, on
your old on premise SharePoint server you added a redirector that routes
request to the corresponding location on the cloud.

User opens an Office document that contains hyperlinks to locations on
your old on premise SharePoint server.  When user CTRL + clicks on the
hyperlink the Office sign-in window will appear, once filled out, the
user will get an error that the link can not be opened.

"Unable to open http://.... Cannot download the information you
requested."

 

**Workaround:**

Modify the redirector on your old SharePoint server to use smart links
per this blog
post:

http://blog.enowsoftware.com/solutions-engine/using-smart-links-to-improve-the-login-process-to-office-365-applications

A product change to address this issue is estimated to be in the July
current channel release of Office 365.

 

</div>

</div>
