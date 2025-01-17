---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Delete Selected Geolocations
============================

The **Delete Selected Geolocations** API deletes the specified geolocations from the Engagement server. The API accepts an array of geolocation IDs as an input parameter and deletes the specified geolocations. Only locations that are not associated with any segments will be deleted. If there are locations in the engagement server that are associated with segments, they will not be deleted.

URL
---

The HTTP URL for Delete Selected Geolocations API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/geolocations/delete
{% endhighlight %}

This API is protected and implements Gateway Filter for Authentication to authenticate access of the API by a user.

Method
------

POST

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| locationids | Yes | array | An array of IDs of geolocations to delete. |

Sample Request
--------------

{% highlight voltMx %}{ 
   "locationIds":[56,62,31]
}
{% endhighlight %}

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| message | string | Message associated with response status code |
| id | long | Unique transaction ID |

Sample Response
---------------

{% highlight voltMx %}{
    "message" : "Location(s) which are not assigned to Segments are deleted successfully",
    "id" : "2"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Location(s) which are not assigned to Segments are deleted successfully. |
| Status 400 | Only Locations(s) which are not assigned to Segments are allowed to be deleted. |
| Status 401 | Unauthorized request. |
| Status 500 | Failed to delete Location(s). |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.3</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">SS</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">SS</td></tr></tbody></table>
