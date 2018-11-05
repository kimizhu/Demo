<div id="page">

# Office 2010 - SharePoint online (SPO) corrupt document open / Save fails as read-only or fails silently

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
12/27/2013 12:04:00 PM

-----

<div id="content">

**Office 2010 - SPO read only error / data loss**

Doing an IE reset causes the office document cache handler add-on to be
disabled.  This add-on could also be disabled for many other reasons.

The office document cache handler add-on and the SharePoint OpenDocument
Class add-on need to either be both disabled or both enabled.  Otherwise
we get the corrupt open and failed saves.

What I am calling a corrupt open is: 

Doc looks to open fine, but when you save you get read-only error below,
or if you close Excel (or other office app) via the X in upper right
hand corner, Excel will ask if you want to save, you say yes, you get no
error, but no save happens (data loss). 

This behavior does not seem to impact SharePoint 2013 on premises
servers.  Enabling the office document cache handler add-on seems to
make the issue go away.

Error:

"FullDocPath is read-only.  To save a copy, click OK, then give the
workbook a new name in the Save As dialog box."

 

</div>

</div>
