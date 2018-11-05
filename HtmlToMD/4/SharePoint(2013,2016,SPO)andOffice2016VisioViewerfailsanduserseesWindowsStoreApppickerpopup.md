<div id="page">

# SharePoint (2013,2016,SPO) and Office 2016 Visio Viewer fails and user sees Windows Store App picker popup

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
7/26/2016 1:37:46 PM

-----

<div id="content">

**Summary:**

You have Office 2016 installed (but not Visio), you attempt to open a
Visio file from SharePoint (2013,2016,SPO).  The file should open in the
Visio Viewer that comes with Office 2016, but instead the file does not
open and the user is prompted with popup:

"You'll need a new app to open this ms-visio"  and the button to "Look
for an app in the Store" is shown.

 

**Cause:**

This is a known software defect on the SharePoint web pages.

 

**Workaround:**

For SharePoint Online (SPO) if you switch the document library "List
Experience" to be "New experience" instead of "Classic experience" the
issue will go away.

This link describes how to
turn New experince on.

<https://support.office.com/en-us/article/Switch-the-default-for-document-libraries-from-new-or-classic-66dac24b-4177-4775-bf50-3d267318caa9>

 

This link describes what the new experience is and how it differs from
classic
mode.

<https://support.office.com/en-us/article/Differences-between-the-new-document-library-experience-and-classic-mode-30e1aab0-a5cc-4363-b7f2-09e2ae07d4dc>

 

Or if you change the document library to "Open in browser" instead of
"Open in client application" the issue will go away.

This is a limitation with the Visio Viewer.

</div>

</div>
