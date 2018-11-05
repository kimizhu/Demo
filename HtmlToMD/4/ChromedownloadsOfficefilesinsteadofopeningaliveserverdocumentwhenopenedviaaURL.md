<div id="page">

# Chrome downloads Office files instead of opening a live server document when opened via a URL

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
12/13/2016 5:13:49 PM

-----

<div id="content">

**Summary:**

You have a SharePoint generated email containing a hyperlink or you
paste a URL like http://sp2013ocsi/Shared%20Documents/DateTest.docx into
the Chrome browser.

When the above happens, Chrome downloads the document, instead of
opening the rich client Office application that opens a live server
document.

 

**Cause:**

This is how Chrome works.

**Workaround:**

If you add ?web=1 to the end of the URL, then Office Web Apps will
render the document and from the Web Apps, the user can pick to open in
the rich client.

For example:   http://sp2013ocsi/Shared%20Documents/DateTest.docx?web=1

</div>

</div>
