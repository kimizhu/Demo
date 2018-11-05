<div id="page">

# Unable to open SharePoint documents in local client (rich client) from Chrome due to NPAPI plug-in missing

[Ben W -
MSFT](https://social.msdn.microsoft.com/profile/Ben%20W%20-%20MSFT)
4/24/2015 1:20:00 PM

-----

<div id="content">

**\*\*UPDATE (8/10/2016)**  Opening Office documents with Chrome /
SharePoint 2013 stopped working around the May SharePoint 2013 update,
this issue has been resolved and the fix is in the August 2016 update
for SharePoint
2013.

https://support.microsoft.com/en-us/kb/3115454

https://blogs.technet.microsoft.com/stefan\_gossner/2016/08/09/august-2016-cu-for-sharepoint-2013-product-family-is-available-for-download/

\-- End Update --

Some may have noticed that recently Google has removed the NPAPI Plug-in
support from Chrome.  This change is discussed
here [http://blog.chromium.org/2014/05/update-on-npapi-deprecation.html.](http://blog.chromium.org/2014/05/update-on-npapi-deprecation.html "Chrome Blog")
What this means is that when opening a file from SharePoint on premise
or SharePoint online the browser will default to either downloading a
local copy or attempting to open the file in browser (regardless of your
library settings).

Many other SharePoint integration features will not work when the NPAPI
support is disabled, they include:

  - Documents will not open in rich client app when doc lib link is
    clicked
  - Lync Presence information will not show
  - Export to Excel from doc lib and SharePoint list will not work
  - "Edit Library" button will not work
  - "New Quick Step" will not work
  - "Workflow Settings" \\ "Create a workflow in SharePoint designer"
    will not work
  - "Open with Access" and "Open with Project
  - "Edit Lists"

As this can have an impact on how Office integrates with SharePoint and
Sharepoint Online we have found a temporary work around that allows you
to enable the NPAPI plug-ins while things are being figured out.

1\. Open Chrome

2\. Put "chrome://flags/\#enable-npapi" into the address bar

3\. Find the "Enable NPAPI" plug-in and enable it

4\. Select "relaunch now" at the bottom of the page

5\. Test, you should now have your old functionality back.

The above workaround will not work after September 2015, per Googles
blog post:

"In September 2015 we will remove the override and NPAPI support will be
permanently removed from Chrome. Installed extensions that require NPAPI
plugins will no longer be able to load those plugins."

<http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html>

Another workaround would be to open the file in the browser with Office
Web Apps, then click the button from the web editor to open in rich
client application, like "Edit in Word" button

<div class="WordSection1">

**Current Status:**

The fix for this issue has been rolled out in the 8/11/2015 SharePoint
2013 update and should be present starting in build 15.0.4745.1000 and
on.

Concerning Lync presence info in a SharePoint page, Chrome is
deprecating plugin technology that made this feature work.  We’re
working on a replacement.  In the meantime, if seeing presence inside
SharePoint is essential for you, use IE.

</div>

We unfortunately don’t have timelines to share on this yet. (the
presence replacement feature)

</div>

</div>
