---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Segment by ID
=================

The **Get Segment by ID** API accepts a segment ID as an input parameter and responds with a segment details matching the Segment ID.

URL
---

The HTTP URL for **Get Segment by ID** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/segments/<id>
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

GET

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| id | long | Unique ID assigned to a segment |
| name | string | Segment name |
| owner | string | User who created the segment |
| segmentDefinition | string | Segment definition |
| conditionType | string | Condition type |
| lastModifiedBy | string | User name showing who last modified the segment |
| lastModifiedDateStr | string | Date and time on which the segment was last modified |
| createdBy | string | User name showing who created the application |
| createdDateStr | string | Date on which the segment was created |
| segmentAudienceList |   | An array of segment audience parameters. It includes: attributeName attributeValue attributeOperator conditionNo |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : 5,
  "name" : "Flipkart Segment",
  "owner" : "admin",
  "segmentDefinition" : "",
  "conditionType" : "all",
  "lastModifiedBy" : "admin",
  "lastModifiedDateStr" : "06/21/2016 03:25:01 PM IST",
  "createdBy" : "admin",
  "createdDateStr" : "06/21/2016 03:25:01 PM IST",
  "segmentAudienceList" : [ {
    "attributeOperator" : "Contains",
    "attributeValue" : "yahoo",
    "attributeName" : "email",
    "conditionNo" : 1
  }, {
    "attributeOperator" : "Contains",
    "attributeValue" : "9",
    "attributeName" : "mobileNumber",
    "conditionNo" : 2
  } ]
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Segment details |
| Status 400 | Invalid request format |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
