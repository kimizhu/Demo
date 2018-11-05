<div id="page">

# Office 2013 can not check in files when LAN does not have internet access or over some VPN's

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
3/11/2014 7:16:00 AM

-----

<div id="content">

**Update (4/21/2017):**

In cases where the VPN causes this issue, we have found an issue in
Windows code (113100710844135), the fix is out
<http://support.microsoft.com/kb/2964643>  we have verified
that <span style="font-family: &#39;Calibri&#39;,&#39;sans-serif&#39;;font-size: 11pt">Palo
Alto Networks Global Protect Client, and Juniper VPN work with this
fix.</span>

<span style="font-family: &#39;Calibri&#39;,&#39;sans-serif&#39;;font-size: 11pt">Office
now does not require internet connection to check out files, this update
resolves the issue <https://support.microsoft.com/en-us/kb/3101360> for
Office
2013</span>

<span style="font-family: &#39;Calibri&#39;,&#39;sans-serif&#39;;font-size: 11pt">Office
2016 Click To Run should work without internet connectivity now, and
Office 2016 MSI has a hotfix
</span>

<span style="font-family: &#39;Calibri&#39;,&#39;sans-serif&#39;;font-size: 11pt">https://support.microsoft.com/en-us/help/3141508/february-7-2017-update-for-office-2016-kb3141508 </span>

 

<span style="font-family: &#39;Calibri&#39;,&#39;sans-serif&#39;;font-size: 11pt"></span>Customers
are using third party VPN solutions on Windows 7.  If customers migrate
to Office 2013 from an older version of Office, they may experience
functionality loss in Office when connected via VPN.  Office 2013 took a
dependency on NLA (Network Location Awareness), and some VPN solutions
do not work properly with NLA.  Specifically, if the VPN software does
not define a default gateway.  In this case,  NLA will always report
that the client is not connected to the internet.  This impacts
Office2013 since it depends on internet connectivity for some
functions.  For example, there is no help file on the machine,and all
help is on the internet.  If a customer presses F1 in an Office 2013
application, they will always get an error that says they are not
connected to the internet while connected via VPN.

\*\*I will update this blog post as more information becomes available.

 

**Issue:**

Users without full internet access may not be able to check in files
from the Office 2013 client, even though there is good connection
between the Office client and the SharePoint server.

 

**Cause:**

There was a design change between Office 2010 and 2013, where 2013 now
requires an internet connection for some activities.  Some customers
have already complained about this issue and the product group has been
informed of the design limitations.  (but no hotfix is currently in the
works, a hotfix may not be possible this looks to be a big change)

The root of the issue seems to be that Office 2013 has a dependency on
NLA (Network Location Awareness).  NLA uses probes to determine if the
network connection has “Internet Access”.  The way that is does this is
2 ways.

1.  It does a DNS probe for dns.msftncsi.com.  It expects a specific
response.  The response must be 131.107.255.255.  If it is, then that is
the correct DNS probe.

2.  It attempts to connect to <http://www.msftncsi.com> and attempts to
retrieve the file ncsi.txt.  Inside the file the text must be “Microsoft
NCSI”.

If both of the above conditions are met, then the connection is marked
as having internet connectivity, if not the connection is marked has
having no internet connectivity and some Office features will not work.

 

**Possible Workaround:**

It is possible to setup a local NCIS server (Network Connection Status
Indicator) on your LAN that will respond to the Office Clients requests
and allow the Office feature to work.

See posts below for related information and
directions:

[http://blogs.technet.com/b/networking/archive/2012/12/20/the-network-connection-status-icon.aspx](/b/networking/archive/2012/12/20/the-network-connection-status-icon.aspx)

<http://www.techrepublic.com/blog/data-center/what-do-microsoft-and-ncsi-have-in-common/>

 

</div>

</div>
