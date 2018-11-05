<div id="page">

# The document information panel does not open automatically for Office files opened via SharePoint Workflow hyperlink.

[Susie Martin
\[MSFT\]](https://social.msdn.microsoft.com/profile/Susie%20Martin%20%5BMSFT%5D)
7/8/2015 9:03:00 AM

-----

<div id="content">

**Overview:** 

By default Microsoft Word opens hyperlinks to documents as read only
when the hyperlink is part of an emails contents.  Many issues can arise
when the document is opened read only. 

One issue that we have noticed in testing is that anytime files are
opened in Read only the Document Information Panel will not
automatically open even if the SharePoint site is set to open it
automatically.

**Environment:**

SharePoint Online

Office 2013

Here are the steps we used in our testing to reproduce the behavior:

**Repro Steps:**

 

1.  While in a SPO library, in Site Settings \> Site Content Types \>
    Document \> Document Information Panel Settings
      -  Select "Always show Document Information Panel on document open
        and initial save for this content type".
2.  Create an OOB approval workflow on the SPO library.  To do this:
      -  From the library Ribbon \> Workflow Settings \> Add a Workflow
      -  Be sure that “\*Approval – SharePoint 2010” is selected
      -  Enter anything you’d like for the Name
      -  Uncheck “Allow this workflow to be manually started by an
        authenticated user with Edit Item permissions” and check
        “Creating a new item will start this workflow”
      - Click “Next”
      - Choose an approver to receive the workflow notification emails
      - Click “Save” – This should create the workflow
3.  Create a new Word document in the SPO library where you created the
    workflow.  Once you save the document this should kick off the
    workflow and generate an email to the approvers titled something
    like “Tasks – Please approve…”
4.  Within the email, you will see “To complete this task:” along with a
    link to the Word document.
5.  Click on that link and the document opens in your local Word client,
    but does not display the document information panel.  However, when
    you open the document directly from the SPO library and it opens in
    my local Word client, the Document Information Panel does display
    properly.

Currently there are no workarounds for modifying this behavior when
using out of the box SharePoint Workflows.   If you are using customized
workflows you may be able to use the workaround noted in the following
blog:

http://blogs.technet.com/b/office\_integration\_\_sharepoint/archive/2014/12/04/force-microsoft-word-to-open-in-edit-mode-from-hyperlink-in-an-email.aspx

 

 

</div>

</div>
