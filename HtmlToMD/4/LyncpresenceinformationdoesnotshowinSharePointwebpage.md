<div id="page">

# Lync presence information does not show in SharePoint web page

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
4/16/2015 9:08:00 AM

-----

<div id="content">

**Issue:**

You have Lync running and open a SharePoint web page with IE (internet
explorer) and the user presence information does not show.

 

**Workaround:**

Find the IE security zone the SharePoint site is in, and turn off
"protected mode" for the IE security zone.

Or run IE as administrator

 

**Issue Details:**

The Office IE add-on loops though all the processes on the computer
looking for Lync, so it can use a handle to the process to communicate
with it.  When IE is enforcing protected mode Windows security restricts
the process list that is sent back to the Office IE add-on and the Lync
handle is inaccessible.

 

</div>

</div>
