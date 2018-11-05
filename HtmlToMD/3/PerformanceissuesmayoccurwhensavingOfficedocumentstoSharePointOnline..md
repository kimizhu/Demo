<div id="page">

# Performance issues may occur when saving Office documents to SharePoint Online.

[Al - MSFT](https://social.msdn.microsoft.com/profile/Al%20-%20MSFT)
9/11/2015 4:48:11 PM

-----

<div id="content">

<span style="text-decoration:underline;">**Symptoms**</span>  
  
Imagine a scenario where users on a corporate network are editing their
Office (Word, PowerPoint, etc) documents and click to save them.  They
wait and noticed it takes an unusually long wait (thirty seconds or
longer) that it takes to save the data.  If they take their laptop off
of their corporate network, the save time to SPO is decreased
dramatically.  
  
Taking a network trace of the clients attempting to save their data
shows unusually high TCP and/or UDP traffic across ports such as 139.  
  

<span style="text-decoration:underline;">**Workaround**</span>  
  
In scenarios like this, it was noted that removing the local bindings of
NetBIOS over TCP/IP seems to allow the saving of Office documents to
complete at a quicker rate.

One can troubleshoot what device or network issues is causing this
behavior, or simply disable (as indicated below).  
  
**NOTE:** Ensure network printers do not require these settings in order
for users to utilize them.  
  
  
*Steps to disable TCP/IP over NetBIOS*  
  
1)      Go to the client machine's Control Panel  
2)      If the control panel view is setup by Category, there should be
a section entitled “Network and Internet”.  
3)      Under that section, we need to select “View network status and
tasks”.  
4)      In the next window (which should be “View your basic network
information and set up connections”) there should be a setting toe
“Change adapter settings” on the left window pane. We need to select
that option.  
5)      This will open the “Network Connections” window.  
6)      We need to right mouse click on the network connection we are
using (for example “Ethernet” or “Wi-Fi”) and select “Properties”.  
7)      In the Network connection properties windows, we should be on
the “Networking” tab and a box in the middle of the window “This
connection uses the following items:”  
8)      We want to scroll down in that box until can see and highlight
“Internet Protocol Version 4 (TCP/IPv4)”.  
9)      With that option highlighted, we should be able to select the
Properties button just underneath that window.  
10)   In the “Internet Protocol Version 4 (TCP/IPv4)” window, there
should be an “Advanced” button near the bottom right of the window.
Select that button.  
11)   In the “Advanced TCP/IP Settings” window we need to select the
“WINS” tab.  
12)   At the bottom of this tab, we need to select the option to
“Disable NetBIOS over TCP/IP” and select the “OK” button

</div>

</div>
