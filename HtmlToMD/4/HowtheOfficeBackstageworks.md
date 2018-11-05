<div id="page">

# How the Office Backstage works

[Ben W -
MSFT](https://social.msdn.microsoft.com/profile/Ben%20W%20-%20MSFT)
5/12/2015 6:46:36 AM

-----

<div id="content">

This will just be a general overview of how the office backstage works.

There have recently been a number of requests asking how the office
backstage works with office 2013 or office 365. First I want to explain
the office backstage is different from the "connect to office" feature.
The backstage is the portion of office under file that resembles the
below image, where connect to office resembles explorer view/mapped
drive.

[![
](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Backstage%20image.png)](media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/00/97/Backstage%20image.png)

There are two types of locations in the backstage. There are the
account/service locations(also called Native Services) and the locations
you've manually added(sometimes referred to as Mounted Services).

Manually added locations are very straight forward as they just require
you to put in the orgid/Microsoft account and password tied to them and
they get added. These services get added to the registry and are saved.
It's the native service locations that can cause confusion.

Native Service locations are created by the Service Manager Cache
through Exchange's Autodiscover. Office uses that AutoDiscover to find
the On-Premises SharePoint settings (SPMySiteHostURL) as long as you
have Autodiscover setup (again usually via exchange) then the service
should find any sharepoint/onedrive accounts tied to the user account
currently accessing office.

In environments with both On-premise and SharePoint Online. If the
account is federated then both SharePoint Online and On-Premise should
show in the backstage by default. If not federated then only On-Premise
will show by default, but SharePoint Online can be added manually as a
Mounted service.

I hope this clears up any confusion with regards to the Office
Backstage.

</div>

</div>
