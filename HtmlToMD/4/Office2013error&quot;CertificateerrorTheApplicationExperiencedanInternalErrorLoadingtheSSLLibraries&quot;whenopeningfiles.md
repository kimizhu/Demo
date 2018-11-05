<div id="page">

# Office 2013 error "Certificate error: The Application Experienced an Internal Error Loading the SSL Libraries" when opening files

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/20/2015 7:28:42 AM

-----

<div id="content">

**Overview:   (Updated as of 4/20/2016)**

Microsoft Office 2013 applications give error when opening a file from a
SSL website or SSL SharePoint server.  Error:  "Certificate error:  The
Application Experienced an Internal Error Loading the SSL Libraries"

**Issue:**

There are actually four different aspects to this issue, out of the box
Office 2013 only supports the default SSL settings for whatever OS
Office is running on.  So for Windows 7 Office 2013 requires TLS 1.0 or
SSL3 to be supported on the server.  Windows 8.1 and Office 2013 SSL3,
TLS 1.0, TLS 1.1 and TLS 1.2 are supported but the RC4 cipher suite is
not supported.

So some users will see this error because they are on Windows 8.1 and
their servers hosting the SSL site do not support the newer protocols
and some users will get this error because the servers only support
newer protocols and the client is Windows 7 which only supports SSL3 and
TLS 1.0 by default.

Also Office 2013 attempted to work around this limitation by overriding
the network API defaults and this patch was released in September 2015
for Office 2013, this patched the csi.dll (15.0.4753.1000 or greater). 
Unfortunately this patch did not fully resolve the issue, there was a
needed change to Windows 7, that Windows 7 change will not be coming. 
For some yet to be identified reason this csi.dll patch can cause this
same error message to show, there is a registry key that can be set to
change Office to behave like it did prior to version 15.0.4753.1000 of
csi.dll.

Finally, Windows 8 and Office 2013 have stricter SSL security
requirements, they no longer accept
the <span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">RC4
cipher
suite.</span>

<span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">[http://blogs.technet.com/b/srd/archive/2013/11/12/security-advisory-2868725-recommendation-to-disable-rc4.aspx](/b/srd/archive/2013/11/12/security-advisory-2868725-recommendation-to-disable-rc4.aspx)</span>

**\*\*To be clear Office on Windows 7 does not support servers that only
support TLS 1.1 and TLS 1.2, this is known to be a large issue for some
customers.**

**Workaround:**

**For issue where Windows 8.1 does not support RC4** **cipher suite:**

****The server hosting the SSL site needs to support newer ciphers

<https://support.microsoft.com/en-us/kb/245030>

 You want to enable the TLS 1.2 support **on the server**. Snippet from
the blog

\<Snippet\> 

SCHANNEL Key 

Start Registry Editor (Regedt32.exe), and locate the following key in
the
registry. 

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL 

SCHANNEL\\Protocols SubKey 

To enable the use of the protocols that will not be negotiated by
default (such as TLS 1.1 or TLS 1.2), change the DWORD value data of the
DisabledByDefault value to 0x0 in each of the following registry keys
under the Protocols key:

•SCHANNEL\\Protocols\\TLS 1.1\\Client 

•SCHANNEL\\Protocols\\TLS 1.1\\Server 

•SCHANNEL\\Protocols\\TLS 1.2\\Client 

•SCHANNEL\\Protocols\\TLS 1.2\\Server 

\<Snippet\>

**** 

**For users that have Windows 7 and do not want to support the older SSL
3 and TLS 1.0 protocols on their servers**

<span style="text-decoration:line-through;">There is no workaround to
this issue other than upgrading your operating system or having your
server support SSL3 or TLS 1.0.  There will not be a hotfix for this
issue.</span>

<span style="text-decoration:line-through;"></span>\*\*Update, Windows 7
now has a hotfix and a registry key to allow for TLS 1.1 and TLS 1.2
support for its web service API, this allows Office to be able to access
SharePoint on Windows 7 now if the server only supports TLS 1.2.

See this KB for more information:

<https://support.microsoft.com/en-us/kb/3140245>

 

**For users that have patched Office 2013 running on Windows 7 to a
csi.dll equal to or greater than 15.0.4753.1000**  
We have be unable to reproduce this issue, but for some customers this
csi.dll version or greater causes this error, this registry key will
revert Office to the pre-patched behavior.

1.  Add a new dword registry value

<!-- end list -->

1.  under
    HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Common\\Internet
2.  New value called WinHttpSecureProtocols
3.  Set the value to hex value A8
4.  The above value sets the network API to Windows 7 defaults of SSL3
    and TLS 1.0

**** 

</div>

</div>
