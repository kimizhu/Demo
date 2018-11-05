<div id="page">

# "Couldn't open https://\<path\>/\_vti\_history/Shared Documents/filename"

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
12/9/2014 3:46:00 PM

-----

<div id="content">

**<span style="font-family:Calibri;font-size:medium;">SYMPTION:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">When opening Office
files from the version history in SharePoint, users receive a message
**“Couldn't open
[https](https://%3Cpath%3E/_vti_history/Shared)**<span>://\<path\>/**\_vti\_history**/Shared</span>
Documents/filename.</span>

<span style="font-family:Calibri;font-size:medium;"> </span><span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">CAUSE:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span><span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">The **"Do not save
encrypted pages to disk**" was enabled in IE under the **Tools, Internet
Options**, **Advanced** tab or via Group Policy.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/2211.DoNotSaveEncryption2.bmp)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/2211.DoNotSaveEncryption2.bmp)</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">RESOLUTION:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Uncheck the "Do not
save encrypted pages to disk" setting.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">NOTE:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">By default, the "Do
not save encrypted pages to disk" option is **unchecked** (except for
Windows Server systems).</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;"><span style="font-size:medium;">The
**purpose** of **"Do not save encrypted pages to disk":**</span></span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">In **IE9**, this
option does exactly what it says it does—resources received from HTTPS
URLs are not placed in the Temporary Internet Files Cache and temporary
files are not created for these resources. This option is universal for
HTTPS responses.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">In **IE10** **or
above**, the option behaves differently. Instead of trying to prevent
HTTPS resources from being saved to disk, the option will delete
cached-from-HTTPS resources from the cache when the browser is closed.
This helps ensure that the browser works correctly even when this
setting is enabled. </span>

</div>

</div>
