---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Delete Inbound Number
=====================

The **Delete Inbound Number** API deletes an inbound number from Engagement Services. All the communication from this number stops immediately.

URL
---

The HTTP URL for the Delete Inbound Number API is:

{% highlight voltMx %}http://<host>>:<<port>>/api/v1/twowaysms/number/<number-id>/delete
{% endhighlight %}

> **_Note:_** <number-id>: Here, number ID refers to an ID that is used to map inbound number with internal data record.

This service implements ‘Gateway Filter for Authentication’ to authenticate access of the service by a user.

Method
------

POST

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| number-id | Yes | long | Unique number ID assigned to an inbound number |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "5",
  "message" : "Inbound SMS Number deleted successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Inbound SMS number deleted successfully |
| Status 400 | Invalid Inbound number ID provided or no valid Inbound Number found with given IDNumbers with commands cannot be deleted |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
