<div id="page">

# Office 2016 does not render custom login page correctly

[Warren\_R\_Msft](https://social.msdn.microsoft.com/profile/Warren_R_Msft)
2/9/2016 6:08:26 AM

-----

<div id="content">

**Summary:**

You have a custom HTML login page (like ADFS) that shows in the Office
client applications when Office wants to authenticate a user for online
resources.

This custom HTML login page fails to render correctly, either the UI
does not fit right or you get JScript errors.

 

**Cause:**

Currently Office 2016 uses IE document mode 7 (aka IE7 mode) by default
when rendering the HTML login page in the Office client, much HTML and
JScript does not work or works differently when viewed with IE7.

 

**Workaround:**

You can force Office to use a different document mode for you page, you
can work around this issue by putting this directive in your custom
login HTML page.

\<meta http-equiv="x-ua-compatible" content="IE=9" \>

If your web page is bigger than what can fit into the Office sign-in
screen, you can use code similar to this to force the HTML page to stay
the correct size and have scroll bars.

\<DIV STYLE="width: 460px; height: 530px; overflow: scroll"\>

If you need to dynamically change the style, Office will use this token
in the user agent string that you can switch off of,  "MSIE 7.0".

 

</div>

</div>
