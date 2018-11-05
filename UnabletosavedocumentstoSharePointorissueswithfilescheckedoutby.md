::: {#page}
Unable to save documents to SharePoint or issues with files checked out by \" \" {#unable-to-save-documents-to-sharepoint-or-issues-with-files-checked-out-by .entry-title}
================================================================================

[dustinyonker](https://social.msdn.microsoft.com/profile/dustinyonker){.url
.fn .n .profile-usercard-hover} 5/4/2017 2:43:16 PM

------------------------------------------------------------------------

::: {#content}
**Scenario**: We have recently recognized an influx of issues regarding
Office 2013/Office 2016 and saving/checking out Office files to
SharePoint Online. This issue can be ambiguous and have many causes but
we want to raise awareness that WAN accelerators, such as RiverBed, have
been involved in multiple of our recent cases. WAN accelerators are
intended to optimize traffic but if misconfiguration or errors are
occurring, this can cause delays and/or the inability to save and check
out Office files to SharePoint. Due to the design of acceleration and
modification of TCP packets, if not done properly it cause expected
errors for Office.   **Errors**: Error messages we have seen connect
directly to this issue have been:

-   The  file \"http://domain\....\" is checked out for editing by user
    \' \'
-   The file \"filename.xlsx\" has been locked for editing by \' \'
-   \" Upload failed\" - You may notice you are locked out of the file
    for extended durations (minutes to hours while you know no other
    user is in the file)

  **What to do**: Testing the removal/bypassing of WAN accelerators
(such as modifying the hosts file) is critical to early troubleshooting.
If a change in behavior is found after removing these acceleration
services, engage your WAN acceleration team to investigate further. If
the issue is still present after removal of WAN acceleration services,
continue with normal troubleshooting which typically involves
simplification of environment (both local machine and network), review
of networking logs (Fiddler/Netmon), and review of ULS logs on the
SharePoint side (ULS would be available to SharePoint On-Premise users
but not available to the public for SharePoint Online).   As noted,
there can be many causes for this issue but wanted to let you know of a
topic hitting our radar a bit more frequently and then ideas for further
troubleshooting in chance WAN acceleration is not the cause.   Dustin
:::
:::
