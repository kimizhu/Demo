::: {#page}
\"Sorry, you can\'t edit this document with other people\" error {#sorry-you-cant-edit-this-document-with-other-people-error .entry-title}
================================================================

[Zakir H -
MSFT](https://social.msdn.microsoft.com/profile/Zakir%20H%20-%20MSFT){.url
.fn .n .profile-usercard-hover} 10/11/2017 1:55:50 AM

------------------------------------------------------------------------

::: {#content}
You may receive the following error when trying to open a Microsoft
Office file in the browser stored in SharePoint on-premise using Office
Web Apps or Office Online Server, or in SharePoint Online using Office
Online:
[](https://msdnshared.blob.core.windows.net/media/2017/10/WordWebAppError.png)
 

[![](https://msdnshared.blob.core.windows.net/media/2017/10/WordWebAppError.png){.alignnone
.wp-image-1095 width="418"
height="196"}](https://msdnshared.blob.core.windows.net/media/2017/10/WordWebAppError.png)

[![](https://msdnshared.blob.core.windows.net/media/2017/10/WordOnlineError.png){.alignnone
.size-full .wp-image-1085 width="414"
height="197"}](https://msdnshared.blob.core.windows.net/media/2017/10/WordOnlineError.png)

**Sorry, you can\'t edit this document with other people.**

  This error can occur if another user has the file open in a Microsoft
Office 2016 client application, such as Word, when they have one of the
following registry keys set to 1:
HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Office\\16.0\\Common\\Internet\\FSSHTTPOffWord
HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Office\\16.0\\Common\\Internet\\FSSHTTPOffExcel
HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Office\\16.0\\Common\\Internet\\FSSHTTPOffPowerPoint
  For a user with Microsoft Office 2013, the following registry key may
be set to 1:
HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Office\\15.0\\Common\\Internet\\FSSHTTPOff
  When the value is set to 1, it disables the Cell Storage Service. When
this is disabled, it in turn disables the co-authoring feature of
Office. So when a user opens the file, instead of allowing multiple
users to edit the file, it puts the lock on the file and prevents others
from editing the file in the browser or client. To resolve the issue,
make sure the registry key value is set to 0 on user machines.
:::
:::
