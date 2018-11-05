<div id="page">

# Word (and other Office apps) freeze when opening documents from SharePoint online (SPO)

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
9/10/2014 8:43:09 AM

-----

<div id="content">

**Issue:**

Word and other Office apps appear to hang or freeze, just a blank
nonfunctional grey screen is shown when opening files from SharePoint
Online (SPO) in the rich client apps.

**Cause:**

The registry key:

HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Common\\SignIn

DWORD value signinoptions 

was set to a too restrictive option for your environment.

The value of 0 is the least restrictive and can be used if you are
having this problem.

0 - Don't block any sign in UI.

1 - Allow Live ID sign in UI only.

2 - Allow Org ID sign in UI. 

3 - Block all sign in UI. only.

4- Allow both Org and Live

 

**Workaround:**

****Set the "signinoptions" registry value to 0.

****

</div>

</div>
