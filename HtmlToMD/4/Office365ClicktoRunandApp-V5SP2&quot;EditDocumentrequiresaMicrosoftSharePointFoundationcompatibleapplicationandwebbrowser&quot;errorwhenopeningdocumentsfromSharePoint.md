<div id="page">

# Office 365 Click to Run and App-V 5 SP2 "Edit Document requires a Microsoft SharePoint Foundation compatible application and web browser" error when opening documents from SharePoint

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
10/15/2014 8:14:45 AM

-----

<div id="content">

**Issue:  (Updated 2/17/2016)**

Office 365 Click to Run and App-V 5 SP2 are installed on same computer.

Users try to pick document menu item "Edit in Microsoft XXX" where XXX
is an Office application name.

Users get error "Edit Document requires a Microsoft SharePoint
Foundation compatible application and web browser"

Repair install of Office does not resolve the problem.

 

**Cause:**

The Office IE add-ons and App-V 5 SP2 are do not work together at the
moment.

 

**Workaround:**

****If iexplore.exe is removed from the registry key value
<span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">ProcessesUsingVirtualComponents</span> 
under
key:

<span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">HKLM\\Software\\Microsoft\\AppV\\Client\\Virtualization</span><span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">
</span>

<span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;">The
issue goes away, the side effects of this action are listed
below:</span>

The registry value that toggles this on or off is
EnableDynamicVirtualization. In addition, those processes that are
specified for this feature are listed in the
ProcessesUsingVirtualComponents registry value located in the same key.
By default, Explorer.exe and Internet Explorer are listed there.

Dynamic Virtualization has a limited scope of interaction designed for
features introduced in App-V Service Pack 2.

This leads to an important statement: Just because the application is
hooked, doesn’t always mean it is running virtualized if it appears as a
process under the ProcessesUsingVirtualComponents registry value. This
will be done at the thread level. When an ActiveX OCX or a DLL that
implements a shell extension is loaded from a native process or a
process from another virtual application, App-V generates an additional
virtual environment on demand linking the package containing the OCX or
DLL with the process. Then dynamic virtualization is turned on for that
particular thread. Once the thread exits, dynamic virtualization is
turned off. If the said thread with dynamic virtualization spawns
another thread, that thread too will be virtualized.

**\*\*\*\*When you turn off the Dynamic Virtualization and remove the
Executable paths from the above configuration you will lose the
functionality described above.\*\*\*\***

Most of the above details came from the below blogs and App-V
documentation:

1.  [http://blogs.technet.com/b/gladiatormsft/archive/2014/02/05/app-v-5-on-run-virtual-rds-run-virtual-virtualizable-extensions-and-dynamic-virtualization.aspx](/b/gladiatormsft/archive/2014/02/05/app-v-5-on-run-virtual-rds-run-virtual-virtualizable-extensions-and-dynamic-virtualization.aspx)
2.  [http://blogs.technet.com/b/gladiatormsft/archive/2014/02/11/app-v-5-the-case-of-the-runvirtual-collision.aspx](/b/gladiatormsft/archive/2014/02/11/app-v-5-the-case-of-the-runvirtual-collision.aspx)
3.  About App-V 5.0 SP2:
    <http://technet.microsoft.com/en-us/library/dn508408.aspx>
4.  About Client Configuration Settings:
    <http://technet.microsoft.com/en-us/library/jj687745.aspx>

**Current Status:**

Use the workaround if at all possible.

If you run into the situation where you need App-V to function inside of
Internet Explorer, say for your own custom IE add-ins that require
App-V, in this case please contact Microsoft technical support and get
help from the Office support
team.

<span style="font-family:&#39;Calibri&#39;,sans-serif;font-size:11pt;"></span> 

</div>

</div>
