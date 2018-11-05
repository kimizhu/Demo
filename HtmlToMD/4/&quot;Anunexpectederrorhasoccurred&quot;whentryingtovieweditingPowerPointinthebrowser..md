<div id="page">

# "An unexpected error has occurred" when trying to view/editing PowerPoint in the browser.

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
12/15/2014 9:01:13 PM

-----

<div id="content">

**<span style="font-family:Calibri;font-size:medium;">SYMPTON:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Receive error
message "An unexpected error has occurred" when trying to view/editing
PowerPoint in the browser using Office Web Apps 2010.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">\*  Word and Excel
files are displayed without an error.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">CAUSE:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">\* The installation
procedure for Office Web Apps did not complete successfully or an update
was applied to the web app.  (The Configuration Wizard had not been
executed on all servers in the farm).</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Or</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">\*  There are
missing lines in web.config file for the Web Application under the
\<appSettings\> section.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">If you take a
**ULS** trace, you may see something like
this:</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;"><span style="font-size:medium;">Office
Web Apps PowerPoint Front End f9zy Assert **Unexpected exception on**
</span></span><span style="font-family:Calibri;"><span style="font-size:medium;">**PptWebControl.OnInit**:
System.TypeInitializationException: The type initializer for
'Microsoft.Office.Server.Powerpoint.**Pipe.Interface.PipeManager' threw
an exception**. ---\> System.NotSupportedException: **Specified method
is not
supported**.</span></span>

<span style="font-family:Calibri;font-size:medium;"><span style="font-family:Times New Roman;font-size:medium;"> </span></span><span style="font-family:Calibri;font-size:medium;"> </span><span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">RESOLUTION:</span>**

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Run PSConfig on all
servers in the
farm.</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Or</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;"><span style="font-size:medium;">Update
any missing lines in the web.config file.  </span></span>

<span style="font-family:Calibri;font-size:medium;"> </span>

<span style="font-family:Calibri;font-size:medium;">Example
\<appSettings\>
section:</span>

<span style="font-family:Calibri;font-size:medium;"> </span>

**<span style="font-family:Calibri;font-size:medium;">\<appSettings\></span>**

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="PptServer\_Pipe"
value="Microsoft.Office.Server.Powerpoint.Pipe.Web.WacPipe,
Microsoft.Office.Server.Powerpoint.Pipe.Web, Version=14.0.0.0,
</span></span>

<span style="font-family:Calibri;font-size:medium;">Culture=neutral,
PublicKeyToken=71e9bce111e9429c" /\></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="PptServer\_BroadcastManager"
value="Microsoft.Office.Server.Powerpoint.Web.MossHost.MossBroadcastManager,
</span></span>

<span style="font-family:Calibri;font-size:medium;">Microsoft.Office.Server.Powerpoint.Web.MossHost,
Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
/\></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="FeedCacheTime" value="300" /\></span></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="FeedPageUrl" value="/\_layouts/feed.aspx?" /\></span></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="FeedXsl1" value="/Style Library/Xsl Style Sheets/Rss.xsl"
/\></span></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="ReportViewerMessages"
value="Microsoft.SharePoint.Portal.Analytics.UI.ReportViewerMessages,
Microsoft.SharePoint.Portal, Version=14.0.0.0, </span></span>

<span style="font-family:Calibri;font-size:medium;">Culture=neutral,
PublicKeyToken=71e9bce111e9429c" /\></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="aspnet:AllowAnonymousImpersonation" value="true"
/\></span></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="aspnet:UseStrictParserRegex" value="true" /\></span></span>

<span style="font-family:Calibri;"><span style="font-size:medium;">   
\<add key="ChartImageHandler" value="storage=session;timeout=20;"
/\></span></span>

**<span style="font-family:Calibri;font-size:medium;">\</appSettings\></span>**

</div>

</div>
