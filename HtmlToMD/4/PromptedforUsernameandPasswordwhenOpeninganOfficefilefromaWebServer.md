<div id="page">

# Prompted for Username and Password when Opening an Office file from a Web Server

[Kim P -
MSFT](https://social.msdn.microsoft.com/profile/Kim%20P%20-%20MSFT)
2/24/2014 10:28:14 AM

-----

<div id="content">

**ISSUE:**

** **

When opening Office files from a web server (i.e SharePoint), users are
**prompted** for **credentials**, even if credentials have already been
entered.

**CAUSE:**

  
The Office application is trying to access the document directly from
the server which has to communicate with the server to determine what
type of server that's accessing the file and what web authoring protocol
is available.

\*  Anytime a new process tries to access the server, the Office
application will require renegoiation.

  
**RESOLUTION:**

  
There are different resolutions depending on if users are within the
network and if direct editing is needed.  This blog is not all-inclusive
of every prompting scenario, however, just a highlight of some of the
most common resolutions.

**Intranet users that want direct editing:**

If you are in the intranet, you can configure the server to use
**Integrated Windows Authentication** and then configure the client to
**enable automatic logon**.  The Local Intranet zone has a default
configuration of automatic logon with the current user name and
password.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Intranet%20Zone.JPG)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Intranet%20Zone.JPG)

  
**NOTE**:  If the intranet user is accessing a site where they **have
not configured a proxy** in Windows Internet Explorer and are using Web
Distributed Authoring and Versioning (**WebDav**) to access a fully
qualified domain names (**FQDN**) site, they will also be **prompted for
credentials** (On Windows **Vista** or **Later**).

  
If the URL contains **periods**, the server is assumed to be on the
**Internet**. The periods indicate that you use an FQDN address.
Therefore, no credentials are automatically sent to this server unless a
proxy is configured and unless this server is indicated for proxy
bypass.

In this scenario, you will need add the following registy key:

  
1.Click Start, type regedit in the Start Search box, and then press
ENTER.  
2.Locate and then click the following registry
subkey:

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\WebClient\\Parameters

3.On the Edit menu, point to New, and then click Multi-String Value.  
4.Type **AuthForwardServerList**, and then press ENTER.  
5.On the Edit menu, click Modify.  
6.In the Value data box, type the URL of the server that hosts the Web
share (ex. <https://*.abc.sharepoint.com>), and then click OK.

7.Exit Registry Editor.

\* You have to **restart** the **Webclient **service after you modify
the registry.

  
**Related article**  -  http://support.microsoft.com/kb/943280

\--

**Extranet users that want direct editing**:

Use Forms Based Authentication (**FBA**) with **persistent** **cookies**
– The **only way** to maintain direct-edit functionality and also **not
be prompted** by the Office application is to implement a proxy/firewall
server by using Forms Based Authentication with persistent cookies such
as an Internet Security and Acceleration (ISA) server or a Forefront
Threat Management Gateway.

**Extranet users and direct editing is not needed**:

**Disable Client Integration** or the **OPTIONS/PROPFIND** Verbs  -  If
the site provides WebDAV functionality through another extension, the
provider of that extension should be engaged. For example, to do this
with Windows SharePoint Services (WSS), the site should be configured to
**disable Client Integration**, or the **OPTIONS** and **PROPFIND** verb
should be **inhibited**. (To inhibit the OPTIONS and PROPFIND verbs on
Internet Information Services (IIS) version 6, remove the verbs from the
\<httpHandlers\> registration line in the web.config file. On IIS 7.0,
use the HTTP Verbs tab of the Request Filtering feature to deny the
verbs.) Be aware that this approach will open the content in read-only
mode because this approach disables direct-edit functionality.

  
**NOTE**:  Using Web servers that respond to a **PROPFIND** with a
**200** response can also result in an authentication prompt if
**cookies are present**.

Example of what is seen in the network trace:

**PROPFIND** http://abc.sharepoint.com/Shared Documents/ HTTP/1.1  
**Cookie**: JSESSIONID=01234/3iasdueaioeujf390qm30239jf02\[3mk3099  
User-Agent: Microsoft-WebDAV-MiniRedir/6.1.7601  
Depth: 0  
translate: f  
Connection: Keep-Alive  
Content-Length: 0  
Host: abc.sharepoint.com

**HTTP/1.1 200 OK**  
Date: Mon, 24 Feb 2014 20:57:03 GMT  
Server: Application Server/7.0  
Content-Length: 1386  
Keep-Alive: timeout=300, max=96  
Connection: Keep-Alive  
Content-Type: text/html; charset=ISO-8859-1  
Content-Language: en-US

\--

**\*\* For risk of using FBA with persistent cookies, client side
approaches to reduce prompting, and other options when direct editing is
not needed, see article**  -  **Authentication** **requests when you
open Office documents**  -  http://support.microsoft.com/kb/2019105

</div>

</div>
