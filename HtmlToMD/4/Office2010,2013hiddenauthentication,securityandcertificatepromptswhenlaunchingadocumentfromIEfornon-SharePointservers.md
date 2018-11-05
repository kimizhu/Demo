<div id="page">

# Office 2010, 2013 hidden authentication, security and certificate prompts when launching a document from IE for non-SharePoint servers

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
2/18/2014 7:11:30 AM

-----

<div id="content">

**Issue:**

When users try to launch Microsoft Office documents that reside on a
non-SharePoint server an authentication or security or certificate
prompt could popup behind the IE window, giving the appearance that IE
has hung.

This issue affects both Office 2010 and 2013 on Windows 7.

 

**Workaround:**

**Important** This section, method, or task contains steps that tell you
how to modify the registry. However, serious problems might occur if you
modify the registry incorrectly. Therefore, make sure that you follow
these steps carefully. For added protection, back up the registry before
you modify it. Then, you can restore the registry if a problem occurs.
For more information about how to back up and restore the registry, the
following article number to view the article in the Microsoft Knowledge
Base:  (http://support.microsoft.com/kb/322756)    

The user can minimize the IE window to see the prompt.

In some cases setting the HKEY\_CURRENT\_USER\\Control
Panel\\Desktop\\ForegroundLockTimeout registry key to a value of 0 can
cause this issue to go away.  A possible side effect could be windows
coming to the foreground that may not have jumped to the foreground
before.

 

**Current Status:**

The product group has been informed of this issue.  This blog will be
updated when more information is known.

</div>

</div>
