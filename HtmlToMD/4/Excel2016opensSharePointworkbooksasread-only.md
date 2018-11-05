<div id="page">

# Excel 2016 opens SharePoint workbooks as read-only

[Zakir H -
MSFT](https://social.msdn.microsoft.com/profile/Zakir%20H%20-%20MSFT)
11/12/2015 12:12:00 PM

-----

<div id="content">

UPDATE - 9/6/17: See solution below

When opening a workbook in SharePoint using Excel 2016, it opens as
read-only with the following message:

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/excel2016.PNG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/excel2016.PNG)

**We opened this workbook read-only from the server.**

To edit the workbook, click on the button **Edit Workbook**

This is a design change from Excel 2013, which opened workbooks directly
into edit mode by default. The reason for the change in Excel 2016 is to
prevent locking out users from editing the file.

When you open a file in edit mode, you get exclusive editing capability
in the file, and no other person can then open the file to edit. They
can only view the spreadsheet in read-only mode. Even if you are the
only person that uses the workbook, this can happen when you open a file
in edit mode and leave it open on your work machine, for example, which
means you are locked out of the file for editing on another computer at
home or elsewhere.

Changing the behavior to open workbooks by default in read-only mode
helps prevent these scenarios. Many users read information but never
make edits to the spreadsheet. For these users, opening the file as
read-only works just fine for them, and it leaves the file unlocked for
editing for someone else. So this change in behavior helps keep the
workbook available for those people who need to edit.

**Solution**

The behavior has changed back to workbooks opening directly into edit
mode with Office 2016 Click-to-Run Monthly Channel (Current Channel)
Version 1707 (Build 8326.2058) and later. This build was released on
July 27, 2017 with a new co-authoring feature, allowing multiple users
to edit the workbook simultaneously. Because of this feature, workbooks
no longer open in read-only mode by default. If you are on Monthly
Channel, make sure it is updated to Version 1707 (Build 8326.2058) to
take advantage of co-authoring and to allow workbooks to open in edit
mode. If you are on Semi-Annual Channel Targeted (First Release for
Deferred Channel) or on Semi-Annual Channel (Deferred Channel), this
feature will be released in the future per the update channels
deployment
process:

<https://support.office.com/en-us/article/Overview-of-update-channels-for-Office-365-ProPlus-9ccf0f13-28ff-4975-9bd2-7e4ea2fefef4?ui=en-US&rs=en-US&ad=US>

 

</div>

</div>
