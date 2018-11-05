<div id="page">

# Prompted for Username/Password when Opening Excel files from PeopleSoft or SAP

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
2/24/2014 5:47:02 AM

-----

<div id="content">

**ISSUE:**

When opening Excel files from PeopleSoft or SAP, users are prompted to
enter username/password. 

It is not possible to enter correct credentials because user does not
have access to those folders

If the Cancel button is selected then file is opened as read-only.

**CAUSE:**

Office cannot determine if the file can be authored on the webserver or
not due to invalid responses to the OPTIONS and PROPFIND WebDAV calls
made by the Office application and/or the webclient service.

This does not occur when using Mozilla Firefox, nor did it occur with
computers running Office 2003 on Windows XP.

    
**RESOLUTION**:

Configure the server to respond to the OPTIONS and PROPFINDS WebDAV call
with a **405** (**Not allowed**).  
 

**NOTE**: Another solution is to disable the WebClient service in its
entirety. However, this will be problematic if you use both PeopleSoft
and Sharepoint are in the same environment. For Sharepoint, you want the
webserver to process the WebDAV HTTP methods issued by Excel. For
PeopleSoft, you do not.  
   
Another solution recommended by Microsoft is to disable the OPTIONS and
PROPFIND methods on your webserver if WebDAV is not applicable.

This is fairly straightforward for IIS. However, it is not so simple
when dealing with PeopleSoft (Weblogic or Websphere).

For these PeopleTools releases, the OPTIONS and PROPFIND requests return
a 200 and/or 302 code rather than 405. Despite a valid return code of
200, the response content isn't what Excel is expecting. Thus, it
continues to throw an authentication dialog.  

</div>

</div>
