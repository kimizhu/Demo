<div id="page">

# Excel 2016 Default save location gives error

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
2/22/2017 4:49:59 PM

-----

<div id="content">

**Overview:**

You have Excel 2016 and try to change the default save location to a
SharePoint location and get error:

"Cannot access directory 'http://myserver/mydoclib'

The setting is on the Excel Options Window, Save section, "Default local
file location:"  (see picture below)

[![error](media/2017/02/error-300x187.jpg)](media/2017/02/error.jpg)

**Cause:**

For some unknown reason, some Office 2016 installs fail to create a
needed directory.

 

**Workaround:**

<span style="color: #000000;font-family: Calibri">Add this directory to
the systems experiencing the
problem:</span>

<span style="color: #000000;font-family: Calibri">C:\\Users\\\<userid\>\\AppData\\Roaming\\Microsoft\\Excel\\URL\\</span>

<span style="color: #000000;font-family: Calibri">For
example:</span>

<span style="color: #000000;font-family: Calibri">C:\\Users\\warren\\AppData\\Roaming\\Microsoft\\Excel\\URL\\</span>

 

</div>

</div>
