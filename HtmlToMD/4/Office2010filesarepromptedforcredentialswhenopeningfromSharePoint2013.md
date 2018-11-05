<div id="page">

# Office 2010 files are prompted for credentials when opening from SharePoint 2013

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
10/28/2014 9:21:00 AM

-----

<div id="content">

**<span style="font-family:Calibri;font-size:medium;">ISSUE:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">When opening an
**Office 2010** file from a **SharePoint 2013** site, users are prompted
for credentials even though **client integration** is disabled in
SharePoint Central
Administration.</span>

<span style="font-family:Calibri;font-size:medium;"> </span><span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">CAUSE:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">There is an
additional HEAD request which returns a 403 Forbidden response. 
</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;"><span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:12pt;">For
example, if you take a network trace, you may see something like
this</span>:</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**HEAD** https://int-www.sharepointportal.test.com/Documents/test.docx
HTTP/1.1

Connection: Keep-Alive

Cookie:
BIGipServer\~seccp\~int-www.sharepointportal.test.com-ssl=rd2861o00000dfdsfddsfdd0ffff0ab33040o5000;
ASP.NET\_SessionId=whcr4m0unufc483493jf4f0hn;
s\_vi=\[CS\]v1|2A0851ED051D1A84-4000013540001FFC\[CE\];
s\_fid=241D25D30F5546C1-15779EB616A64E07; s\_nr=1411663880736-Repeat;
s\_vnum=1411704000263%26vn%3D4; s\_invisit=true;
gpv\_pageName=Login%20to%20SharePoint%20Portal; s\_cc=true;
SC\_LINKS=%5B%5BB%5D%5D; s\_sq=%5B%5BB%5D%5D

User-Agent: Microsoft Office Word 2013 (15.0.4615) Windows NT 6.1

X-IDCRL\_ACCEPTED: t

Host: int-www.sharepointportal.test.com

  

**HTTP/1.1 403 FORBIDDEN**

Content-Length: 13

Content-Type: text/plain; charset=utf-8

Server: Microsoft-IIS/7.5

X-SharePointHealthScore: 0

SPRequestGuid: 64febb9c-f42f-90b8-4c8d-a753439264e3

request-id: 64febb9c-f42f-90b8-4c8d- a753439264e3

X-Forms\_Based\_Auth\_Required:
https://int-www.sharepointportal.test.com/\_login/default.aspx?ReturnUrl=/\_layouts/15/error.aspx\&Source=%2fDocuments%2ftest.docx

X-Forms\_Based\_Auth\_Return\_Url:
https://int-www.sharepointlportal.test.com/\_layouts/15/error.aspx

**X-MSDAVEXT\_Error: 917656; Access denied. Before opening files in this
location, you must first browse to the web site and select the option to
login
automatically.**

<span style="font-family:Calibri;font-size:medium;"> </span><span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">**RESOLUTION**:</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">-  For **IE 8** and
**9** block the verbs **OPTIONS**, **PROPFIND** and if necessary
**HEAD** in the Request Filtering section in IIS.</span>

If you are using Windows Server 2008 or Windows Server 2008 R2:

            On the taskbar, click **Start**, point to **Administrative
Tools**, and then click **Internet Information Services (IIS) Manager**

    If you are using Windows Vista or Windows 7:

          On the taskbar, click **Start**, and then click **Control
Panel** Double-click **Administrative Tools**, and then double-click
**Internet Information Services (IIS) Manager**.

    In the **Connections** pane,

         Go to the connection, site, application, or directory for which
you want to modify your request filtering settings.

         **Home** pane, double-click **Request Filtering**.In the
**Request Filtering** pane, click the **HTTP verbs** tab, and then click
**Deny Verb...** in the **Actions**
pane.<span style="font-family:Times New Roman;font-size:medium;"> </span><span style="font-family:Times New Roman;font-size:medium;"> </span><span style="font-family:Times New Roman;font-size:medium;">
</span>

<span style="font-family:Calibri;font-size:medium;">**NOTE**:  Office
2010 may issue a HEAD request in addition to the OPTIONS request. It is
not recommended to suppress the HEAD request because it may be used by
other applications for other purposes.  
</span>

<span style="font-family:Calibri;font-size:medium;"> --</span>

<span style="font-family:Calibri;font-size:medium;">-  For **IE 10+**
remove the **X-MS-InvokeApp** header from each web application.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

</div>

</div>
