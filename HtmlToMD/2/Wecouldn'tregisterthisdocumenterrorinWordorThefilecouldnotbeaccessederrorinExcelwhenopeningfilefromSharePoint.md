<div id="page">

# "We couldn't register this document" error in Word or "The file could not be accessed" error in Excel when opening file from SharePoint

[Zakir H -
MSFT](https://social.msdn.microsoft.com/profile/Zakir%20H%20-%20MSFT)
1/9/2018 1:32:50 AM

-----

<div id="content">

You may receive the following error when opening a Word document from
SharePoint:

 

<https://msdnshared.blob.core.windows.net/media/2018/01/LongnameWord2.png>

 

**We couldn't register this document. You won't be able to create links
from other documents to this one.**

 

Or you may receive the following error when opening an Excel workbook
from
SharePoint:

 

<https://msdnshared.blob.core.windows.net/media/2018/01/LongnameExcel.png>

 

**The file could not be accessed.**

 

These two errors can happen if the file has a long file path.

Per the following document, Office (Word/PowerPoint) has a 260 character
limitation in the full file path, which includes the path and the file
name, when used with SharePoint:

<https://technet.microsoft.com/en-sg/library/ff919564(v=office.14).aspx>

There is a different limitation in Excel for the file path, which is 218
characters:

[](https://support.microsoft.com/en-us/help/213983/error-message-when-you-open-or-save-a-file-in-microsoft-excel-filename)<https://support.microsoft.com/en-us/help/213983/error-message-when-you-open-or-save-a-file-in-microsoft-excel-filename>

These limits apply to both SharePoint on-premise and SharePoint Online
as the limitation is in Office.

To fix the error, reduce length of the file name so that the full file
path is below the character limit.

</div>

</div>
