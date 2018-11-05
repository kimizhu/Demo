<div id="page">

# Minor latency when saving to OneDrive for Business from Office 2013

[Taylor H -
MSFT](https://social.msdn.microsoft.com/profile/Taylor%20H%20-%20MSFT)
12/29/2014 1:48:34 PM

-----

<div id="content">

**Scenario**

You experience a small amount of latency (usually 3-5 seconds) when
saving to a local OneDrive for Business directory, but not other local
directories.

**Cause**

In Office 2013, when saving to the local directory tied to your OneDrive
for Business 2013 application (typically located at
C:\\users\\%username%\\\<Example Folder Name\>) Office will actually
make two simultaneous saves.  One save to the local directory, and
another to the server location tied to your OneDrive for Business 2013
application.  An example of a server location would be your Office 365
OneDrive site which you are syncing with OneDrive for Business 2013.

The reasoning behind this behavior is to give you a "server copy" of the
file right away so you have server copy functionality immediately. 
Server copy functionality includes, but is not limited to, co-authoring,
sharing, versioning, etc.

To provide context, here is how you would have to get "server copy"
functionality in Office 2010.

\-Save the file to local OneDrive for Business directory.  
\-Close the document in Office to release the lock on the document.  
\-Wait for OneDrive for Business to sync the document up to OneDrive.
Syncs usually happen every 10 minutes.  
\-Reopen the document in Office from your OneDrive site, now it’s a
server copy.  
\-Server copy functionality available in Office (co-authoring, sharing,
versioning, etc.).

**Resolution**

Since this functionality is very engrained into the design of Office
2013, there are no means to disable the simultaneous save.

As far as workarounds are concerned, the following situations would be
viable, however server copy functionality would be sacrificed.

\-Do not save directly to the OneDrive for Business folder, but rather
save to another local directory.  Then manually move documents to the
OneDrive for Business directory.

</div>

</div>
