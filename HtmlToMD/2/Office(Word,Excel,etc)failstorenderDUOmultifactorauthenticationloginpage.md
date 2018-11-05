<div id="page">

# Office(Word, Excel, etc) fails to render DUO multifactor authentication login page

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
2/26/2018 2:24:21 PM

-----

<div id="content">

**Issue:**

You have a custom multifactor authentication login pages that leverage
DUI API, and all works fine from web browsers but the Office client
(Word, Excel, etc) fails to render all of the HTML property, you may see
a flicker of the login page but in the end Office shows this error:

"Your organization's policies are preventing us from completing this
action for you.  For more info, please contact your help desk."

**Cause:**

When the DUO iframe is loaded from the ‘duo.form.login.template.html’
file, the code is \<iframe id="duo\_iframe" width="100%" height="350px"
frameborder="0"\>

Note that the SRC attribute of the Iframe element is missing, causing
the iFrame to load the URL about:blank (The Iframe SRC attribute is set
at a later point in the Duo-Web-v2.js file).  For security reasons
Office does not allow navigation to any non-https end point within the
webview which is shown to capture user credentials. The lack of a SRC
attribute causes the embedded browser to load "about:blank" in the
IFRAME which is not based on HTTPS and Office cannot allow such
navigation to take place.

**Workaround:**

Specifying a SRC attribute for the Iframe element resolves the issue :
\<iframe id="duo\_iframe" src="images/TempImage.gif” width="100%"
height="350px" frameborder="0"\> (Since we have a SRC, about:blank no
longer loads, and hence the issue does not occur)

 

</div>

</div>
