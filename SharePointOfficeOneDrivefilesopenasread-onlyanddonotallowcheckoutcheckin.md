::: {#page}
SharePoint / Office / OneDrive files open as read-only and do not allow check out / check in {#sharepoint-office-onedrive-files-open-as-read-only-and-do-not-allow-check-out-check-in .entry-title}
============================================================================================

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft){.url
.fn .n .profile-usercard-hover} 3/7/2018 2:37:53 PM

------------------------------------------------------------------------

::: {#content}
**Issue:** You have a SharePoint Online document library that requires
checkout and you have it synced locally via OneDrive for business. 
Files opened from either online or from the local synced folder open
documents read only with no way to check in or check out files from the
Office client.   **Cause: ** This is a current design limitation with
OneDrive, \"L[ibraries with
]{style="float: none;background-color: #f2f2f2;color: #000000;font-family: 'Segoe UI',SegoeUI,'Helvetica Neue',Helvetica,Arial,sans-serif;font-size: 15px;font-style: normal;font-variant: normal;font-weight: 400;letter-spacing: normal;text-align: left;text-decoration: none;text-indent: 0px"}**Checkout**[,
]{style="float: none;background-color: #f2f2f2;color: #000000;font-family: 'Segoe UI',SegoeUI,'Helvetica Neue',Helvetica,Arial,sans-serif;font-size: 15px;font-style: normal;font-variant: normal;font-weight: 400;letter-spacing: normal;text-align: left;text-decoration: none;text-indent: 0px"}**Required**
[columns or
metadata, ]{style="float: none;background-color: #f2f2f2;color: #000000;font-family: 'Segoe UI',SegoeUI,'Helvetica Neue',Helvetica,Arial,sans-serif;font-size: 15px;font-style: normal;font-variant: normal;font-weight: 400;letter-spacing: normal;text-align: left;text-decoration: none;text-indent: 0px"}or
when **Draft Item Security** is set to either **Only users who can edit
**or **Only users who can approve items** in Version Settings of the
library.\"
https://support.microsoft.com/en-us/help/3125202/restrictions-and-limitations-when-you-sync-files-and-folders
  **Workarounds:**

1.  Do not sync SharePoint document libraries that require checkout
2.  Uncheck the OneDrive setting: Office\[tab\] \\ \"Use Office 2016 to
    sync Office files that I open\";  If you uncheck this global
    setting, co-authoring will not work for any file opened from a local
    synced folder.  But co-authoring will work for any files opened from
    online.  GPO for controlling this setting is
    [EnableAllOcsiClients]{style="float: none;background-color: transparent;color: #2f2f2f;font-family: 'Segoe UI','Segoe UI Web','Segoe UI Symbol','Helvetica Neue','BBAlpha Sans','S60 Sans',Arial,sans-serif;font-size: 16px;font-style: normal;font-variant: normal;font-weight: 400;letter-spacing: normal;line-height: 24px;text-align: left;text-decoration: none;text-indent: 0px"}
    defined at:  
    https://support.office.com/en-us/article/Use-Group-Policy-to-control-OneDrive-sync-client-settings-0ecb2cf5-8882-42b3-a6e9-be6bda30899c\#enableallocsiclients

  **Status:** Supporting libraries that require checkout is on the
product groups backlog and maybe fully supported at some point in the
future.  
:::
:::
