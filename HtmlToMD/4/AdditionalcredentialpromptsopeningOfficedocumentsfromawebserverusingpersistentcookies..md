<div id="page">

# Additional credential prompts opening Office documents from a web server using persistent cookies.

[Al - MSFT](https://social.msdn.microsoft.com/profile/Al%20-%20MSFT)
4/13/2015 4:37:53 PM

-----

<div id="content">

**Symptom:**

Consider the following scenarios:

*Scenario 1.*

A user browses to a SharePoint or other web site using a non-IE browser,
enters their forms-based authentication (FBA) credentials and checks the
box to remember their account info, which creates a persistent cookie.  
They proceed to click on a link to open an Office document, which
produces a prompt again for their credentials.

If the user switches to an IE browser, they do not receive the
additional prompt.

*Scenario 2.*

A user browses to a SharePoint or other web site using IE to browse.  
This user enters their credentials in the form and proceeds to click on
a link to open an Office document.   They receive another FBA challenge
for credentials.

If they then place the URL of the site into either the Local Intranet
zone or the Trusted Site zone, they do not receive the additional
challenge for credentials.

**Cause:**

For *Scenario 1*, the reason for the challenge in the non-IE browser is
that when Office requests the persistent, it is retrieved from IE's
cookie jar.   Other browsers do not write their cookies the same way or
to the same location; therefore Office cannot retrieve those cookies.

For *Scenario 2*, the reason for the challenge is due to IE's Protected
Mode.   If the URL is resolved to an IE zone that has Protected Mode
set, IE will not share the cookie with other applications, like
Office.  

**Solutions:**

For *Scenario 1*, the workaround is either to use IE to take advantage
that Office can retrieve the persistent cookie, or (for non-IE browsers)
the user will need to log in again when opening Office documents. 

For *Scenario 2*, the workaround is to ether remove the checkbox for
Protected Mode or move the URL of the site to a zone that does not have
it set.

</div>

</div>
