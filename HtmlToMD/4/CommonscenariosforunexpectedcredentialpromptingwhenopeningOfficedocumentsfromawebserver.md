<div id="page">

# Common scenarios for unexpected credential prompting when opening Office documents from a web server

[Al - MSFT](https://social.msdn.microsoft.com/profile/Al%20-%20MSFT)
9/24/2015 9:33:00 PM

-----

<div id="content">

<span style="font-size:small;">**Symptom:**</span>  
  
Consider the following scenario....  
  
A user browses to a WebDav or other website site, clicks into a document
library and chooses to open (let's say) a Word document.  A challenge
for credentials occurs.  Since the user was already prompted for
credentials when browsing to the site, he/she was not expected to be
prompted again every time they open a new document in the rich client.

  
**<span style="font-size:small;">Causes:</span>**  
  
*Some general info first: * When switching from a browser's session (IE,
etc) to an Office application, the two cannot (directly) share
authentication.  All access to a web server, like SharePoint, requires
some form of authentication.  A user will always be challenged, even if
said user never sees the challenge for credentials (it may be occurring
automatically behind the scenes).     
  
Here are some common causes....

  
  
1\. Some authentication types like Basic Authentication will always
prompt.  Get used to it, it's by-design.  
  
2\. If a cookie-based authentication is using session cookies, there
will always be a challenge.    
  
3\. Non-IE browsers will not pass the persistent cookie to Office.  
  
4\. Zone settings in IE may not be set optimally for passing credentials
such as NTLM or persistent cookies.  
  
5\. In older versions of Office, the WebClient Service was used for
WebDav calls.  Since this service uses WinHTTP - instead of WinInet like
IE - the IE zones are not checked/adhered to.  If the URL is not a local
address and no proxy is configured, WinHTTP will not pass the
credentials.  
  
6\. NTLM authentication is used, but users log into their client
machines with one account, while browsing with another.  Since NTLM, by
it's nature, automatically grabs the logged-in user account; it
initially sends the wrong credentials in this scenario.  
  
  
  
  
  
<span style="font-size:small;">**Workarounds:**</span>  
  
1\. For older authentication types that are designed to always challenge
a user, the only workaround is to use another authentication type.  
  
2\. If an organization allows it, consider using a persistent cookie
authentication.  
  
3.  Office ends up getting the cookie from IE's cookie jar.  Either use
IE or ensure, at some point, IE was also browsed to the same site and
stored the cookie first..  
  
4\. If the zone isn't set to automatically pass credentials, Windows
authentication will not be passed.  Also, Protected mode - if set on the
zone -  will segregate a persistent cookie from other applications, like
Office.  
  
\*\*See the following blog for more info around \#s 3 &
4:  
  
http://blogs.technet.com/b/office\_integration\_\_sharepoint/archive/2015/04/14/additional-credential-prompts-opening-office-documents-from-a-web-server-using-persistent-cookies.aspx  
  
5\. Since the WebClient Service does not use IE's security zones to
determine if it should pass credentials automatically, the following
registry key will need to be set.

  
*NOTE:  Always back up your registry before making changes\!*  
  
  Open regedit and find the following
key:  
**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\WebClient\\Parameters**  
  
  Create a new multi-string value called:  **AuthForwardServerList**  
  
  Add site URLs to this key that are considered safe to forward creds
to.  
  
*See the following KB for more details:*  
<https://support.microsoft.com/en-us/kb/943280>

  
6.  For Windows authentication, try setting 'remember my password'
check-box after the first time credentials are entered.  This should
cache the account to the Windows Credential Manager for later use.  Not
all organizations allow using stored credentials from this location, so
this may or may not work.

**NOTE**: It's considered a *security risk* for multiple users to share
a machine that logs in as one (shared) account, browse as their corpnet
account and cache those credentials on the shared machine.

</div>

</div>
