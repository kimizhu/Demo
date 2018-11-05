<div id="page">

# Remove Office Add-in references from "Recently Used Add-ins" area of Office 2016

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/18/2017 6:52:20 PM

-----

<div id="content">

**Overview:**

Currently there is no way to remove an App for Office add-in reference
from Office 2016 (see
below).

[![recentaddins](https://msdnshared.blob.core.windows.net/media/2017/04/RecentAddins-300x134.jpg)](https://msdnshared.blob.core.windows.net/media/2017/04/RecentAddins.jpg)

These add-in references are stored in the registry under a combination
value that includes the add-in's ID GUID.  This ID can be seen in both
the add-in manifest and in the SharePoint Online application catalog
(see
below).

[![appcat](https://msdnshared.blob.core.windows.net/media/2017/04/AppCat-300x107.jpg)](https://msdnshared.blob.core.windows.net/media/2017/04/AppCat.jpg)

**Workaround:**

\*\*\*Computer systems can be broken if registry edits are not performed
properly, use this workaround at your own risk.  There are no guarantees
or warrantees of any kind \*\*

There are a list of Item(1,2,3,etc) values  under a key like this one:

HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Office\\16.0\\Excel\\Web
Extension User
MRU\\ADAL\_z139970C84C528DEE9B3F50D634024065AABC863258DFEC9DB277DB4808974A9\\File
MRU

The entry looks like this value name = "Item1"

value =
"\[F00000000\]\[T01D2B8497B0ABB70\]\[O00000000\]\*51c8c010-87f6-4b2a-b105-e6128bc8b66z SPCatalog https://hempele3.sharepoint.com/sites/apps   1.0.0.0"

Since the add-in reference you want to remove could be anywhere in this
list, it could be complicated to find and removed.

I have created a sample program that will remove these add-in
references:

usage: RemoveAddinRef \<app excel word powerpoint\> \<GUID of addin\>

example: RemoveAddinRef excel 51c8c010-87f6-4b2a-b105-e6128bc8b66f

The GUID can be obtained from the "Apps for Office" catalog that can be
found in the SharePoint admin tools for Office 365.

The .exe and Visual Studio source code is attached to this blog post.
 [Project Download
zip](https://msdnshared.blob.core.windows.net/media/2017/04/RemoveAddinRef.zip)

 

</div>

</div>
