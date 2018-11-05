<div id="page">

# Office 2013 / ADFS / SharePoint online / Office will not Authenticate users

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
1/7/2014 7:31:55 AM

-----

<div id="content">

**Issue:**

1.  Office 2013 / ADFS SharePoint online, users unable to authenticate
    to SharePoint online from Office applications.

2.  The credentials work fine from IE to access SharePoint online.

3.  Office 2010 works fine.

4.  If the logged in Windows user does not match the ADFS user account,
    used to access SharePoint online, Office 2013 will work.

 

**Cause:**

Office 2013 has a design change from Office 2010 concerning
authentication.  It now uses the ADFS Windows transport endpoint.  If
this endpoint is disabled end users will be prompted for credentials
each time they access SharePoint online.  If the Windows transport
endpoint in ADFS is enabled but unreachable for some reason then Office
will be unable to authenticate.

 

**Possible Solutions:**

Ensure your ADFS server is configured according to:

<http://support.microsoft.com/kb/2712957>

Possible solution for this type of issue

<http://support.microsoft.com/kb/2839539>

 

If the above fails turn on IDCRL tracing on the client with this
registry file:

Windows Registry Editor Version 5.00  
\[HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\MSOIdentityCRL\\Trace\]  
"Folder"="C:\\\\MSOTrace"  
"Flags"=dword:00000001  
"level" =dword:00000099

\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSOIdentityCRL\\Trace\]  
"Folder"="C:\\\\MSOTrace"  
"Flags"=dword:00000001  
"level" =dword:00000099

Reproduce the issue and open the file found at c:\\msotrace

Look for "WinHttpQueryHeaders returns 401" string in the log after the
first "\#\# SOAP Request:" occurrence.

If you find this is possible that a proxy server between the client and
the ADFS server is stripping out needed Windows authentication packet
contents.

 

If you still have not found the issue look for a "\#\# SOAP Response:"
string, this should start like this:

\#\# SOAP Response:  
\<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
xmlns:a="ht  …..continues…

If you have a non SOAP response, like the contents of an HTML page, it
is possible that your proxy server is terminating the request at the
proxy and sending back content of its own instead of forwarding the
request to the ADFS server.

 

**Other links of interest:**

How to diagnose SSO issues, analyzer tool  
<http://support.microsoft.com/kb/2650717/en-us>

Office 365 and ADFS…Active Directory Federation Service
Installation  
<http://social.technet.microsoft.com/wiki/contents/articles/9082.office-365-adfs-active-directory-federation-service-installation.aspx>

SSO authentication to Office 365 fails after you change AD FS 2.0
service endpoint settings in the AD FS 2.0 Management Console  
<http://support.microsoft.com/kb/2712957>   
   
A federated user is repeatedly prompted for credentials during sign-in
to Office 365  
<http://support.microsoft.com/kb/2461628>

Overview of identity, authentication, and authorization in Office 2013  
<http://technet.microsoft.com/en-us/library/jj683102.aspx>  
             

A federated user is repeatedly prompted for credentials during sign-in
to Office 365  
<http://support.microsoft.com/kb/2461628>

Troubleshoot single sign-on setup in Office 365  
<http://support.microsoft.com/kb/2530569>

ADFS single signon  
Checklist: Use AD FS to implement and manage single sign-on  
<http://technet.microsoft.com/en-us/library/jj205462.aspx>

Geek of All Trades: Office 365 SSO: A Simplified Installation Guide  
<http://technet.microsoft.com/en-us/magazine/jj631606.aspx>

SSO authentication to Office 365 fails after you change AD FS 2.0
service endpoint settings in the AD FS 2.0 Management Console \*\*ADFS
END POINT LISTING  
<http://support.microsoft.com/kb/2712957>

401 errors from ADFS Windows Transport  
<http://support.microsoft.com/kb/2839539>

 

****

****

 

</div>

</div>
