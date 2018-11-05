<div id="page">

# SharePoint 2010 site shortcuts for "Connect to Office" or File | Save As or File | Open dialog box are not available

[Scotland\_MSFT](https://social.msdn.microsoft.com/profile/Scotland_MSFT)
4/23/2014 1:05:00 PM

-----

<div id="content">

<span style="font-family: Century;font-size: medium"></span>

<span style="font-size: x-large">***Issue:***</span>

<span style="font-size: medium">Within Word, Excel, PowerPoint or
OneNote, select within each of the products, select File, Save As or
File, Open dialog box in Office 2010, the SharePoint site shortcuts
within the SharePoint sites folder are not present.  Or you have
selected a SharePoint document library, on the Library Tools tab,
Library, choose on the Connect & Export area of the ribbon, Connect to
Office choice.  When you select this, it will write a shortcut to the
document library into the Office 2010 area under Favorites folder name,
SharePoint Sites.</span>

\*\*\*\*\*This will ONLY work with pure 2010 environment, client and
server.  If you have anything 2013 installed on client, this feature can
behave unpredictably as this feature was deprecated in
2013.\*\*\*\*\*

<span style="font-family: Century Gothic;font-size: medium"><span style="font-family: Segoe UI;font-size: x-large">***Resolution:***</span></span>

<span style="font-size: medium">1. Launch Regedit (if you have
permissions to launch Regedit) </span>

<span style="font-size: medium">2. Within the registry key:
</span>

<span style="font-size: small">**HKEY\_CURRENT\_USER\\Software\\AppDataLow\\Microsoft\\Office\\14.0\\Common\\Portal**
</span>

<span style="font-size: medium">Check the registry key value of
PersonalSiteURL, if you have MySite listed in the value, then copy the
URL and see if the URL resolves in the browser. </span>

<span style="font-size: medium">3. There is another registry key
to check to see if it is already present and if it is set to the Mysite
- <http://my> equal to your MySite
URL:</span>

<span style="font-size: medium"><span style="font-size: x-small">\[<span style="font-size: small">HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\14.0\\common\\Portal\\Link
Providers\\MySiteHost\]</span></span> </span>

<span style="font-size: medium">"URL"=http://my</span>

<span style="font-size: medium"> </span>

NOTE:  URL = <http://my> is your MySite URL - this is a String value.

<span style="font-size: medium">4. If the registry key is not present in
step \#3, then you will need to implement this key as a policy:
</span>

<span style="font-size: x-small"><span>\[<span style="font-size: small">HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Office\\14.0\\common\\Portal\\Link
Providers\\MySiteHost\]</span></span> </span>

<span style="font-size: medium">“URL"=http://my </span>

<span style="font-size: medium"><span style="font-size: medium">NOTE: 
URL = [http://my](http://my/) is your MySite URL - this is a String
value.</span></span>

<span style="font-size: medium">5. 
</span><span style="font-size: medium">If the MySite is an **FQDN** site
(URL contains periods), then you will need to add the following registry
key(s) under:
</span>

<span style="font-size: small">HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\WebClient\\Parameters
</span>

<span style="font-size: medium">1. Click **Start**, type **regedit** in
the **Start Search** box, and then press **ENTER**. </span>

<span style="font-size: medium">2. Locate and then click the following
registry subkey:
</span>

<span style="font-size: small">HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\WebClient\\Parameters
</span>

<span style="font-size: medium">3. On the **Edit** menu, point to
**New**, and then click **Multi-String Value**. </span>

<span style="font-size: medium">4. Type **AuthForwardServerList**, and
then press **ENTER**. </span>

<span style="font-size: medium">5. On the **Edit** menu, click
**Modify**. </span>

<span style="font-size: medium">6. In the **Value data** box, type the
MySite URL, i.e. <http://my.microsoft.com> or
<https://mysite.microsoft.com>, and then click **OK**. </span>

<span style="font-size: medium">7. Also check the **BasicAuthLevel** key
to make it shows a value of **2** (if your MySite is https) </span>

<span style="font-size: medium">8. Restart the Webclient service
</span>

<span style="font-size: medium"></span>

<span style="font-size: medium">***<span style="font-size: large">Troubleshooting:</span>***
</span>

<span style="font-size: medium">For testing purposes, you can add a
value to the registry so that it bypasses the default time which is 24
hours. You will need to add the value of DWORD:
**LinkPublishingFrequency** and set the value for decimal to **60
seconds**:
</span>

<span style="font-size: medium">**\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\14.0\\Common\\Portal\]**
</span>

<span style="font-size: medium">"LinkPublishingFrequency"=Dword:0x0000c3
</span>

<span style="font-size: medium">(Hexidecimal value = 60 seconds decimal)
</span>

<span style="font-size: medium">Once the value is set, launch Word or
Excel, and File | open or File | Save, and check the registry key in
step \#1. </span>

</div>

</div>
