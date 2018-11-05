<div id="page">

# Office 2013 clients do not properly utilize a multi-cookie authentication

[Al - MSFT](https://social.msdn.microsoft.com/profile/Al%20-%20MSFT)
9/28/2015 4:41:00 PM

-----

<div id="content">

  
  
<span style="font-size:small;">**Symptom:**</span>

Consider the following scenario...

  
In a custom,  cookie authentication environment using a multiple cookie
(persistent & session) scheme - whereas the first cookie (a persistent
one) is set to allow the creation of the session cookie(s) to be used
for continued authentication -  Office 2013 client users are
unexpectedly prompted for credentials after already authenticating.

Office 2010 clients were found to not exhibit this behavior.

  
**Cause:**  
  
Investigations showed Office 2013 was not accepting the second
authenticating session cookies after initial persistent cookie expires.
Office 2010 clients were able to retain the other cookie(s) for use. 
This was determined to be a code defect in the Office 2013 product.  

  
**Resolution:**

*Solution 1:*  
  
See the following knowledge base (KB) article for the fix:  
  
  
<https://support.microsoft.com/en-us/kb/3054925>  
  
*Note: * Although the above article mentions several fixes in it, the
one in this blog is not mentioned at the time of writing - thus the need
for the blog.  
  

Solution 2:

  
(workaround)

Set the initial (persistent) cookie to a longer life (expiration) so
users can complete their work before being prompted again.

</div>

</div>
