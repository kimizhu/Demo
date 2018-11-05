<div id="page">

# Office 2013 / 2016 continually prompt for credentials after Windows password reset

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
5/20/2016 3:33:54 PM

-----

<div id="content">

**Summary:**

You are trying to access files stored on SharePoint Online from a rich
client Office application (like Word, etc).  You are prompted to enter
you credentials, you do but they are not accepted, you are continually
prompted for credentials.  This may happen after you changed your
Windows password.

**Cause:**

This is a known software defect.

**Resolution:**

The click to run version of Office should already be patched to resolve
this issue.

The fix for Office 2013 MSI is:

<https://support.microsoft.com/en-us/kb/3085480>

The above fix only works if you have ADAL enabled in Office 2013, it is
turned off by default, the link below describes how to turn on ADAL in
Office
2013.

<https://support.office.com/en-us/article/Enable-Modern-Authentication-for-Office-2013-on-Windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910?ui=en-US&rs=en-US&ad=US>

The fix for Office 2016 MSI is in the July 2016 update for Office 2016,
see below:

<https://support.microsoft.com/en-us/kb/3115277>

 

 

</div>

</div>
