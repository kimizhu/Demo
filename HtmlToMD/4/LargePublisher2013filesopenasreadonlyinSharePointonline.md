<div id="page">

# Large Publisher 2013 files open as read only in SharePoint online

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
10/10/2014 9:16:50 AM

-----

<div id="content">

**Issue:**

Large (50MB+) Publisher 2013 files only open as read only from
SharePoint online or SharePoint 2013, user must save locally, then
upload the file by hand.

 

**Cause:**

Publisher relies on the "Web Client" local service, this service has a
default limit of 50MB.

 

**Workaround:**

Set the registry key value FileSizeLimitInBytes to a larger value, so
for 200MB put a decimal value of
200000000:

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\WebClient\\Parameters\\FileSizeLimitInBytes

</div>

</div>
