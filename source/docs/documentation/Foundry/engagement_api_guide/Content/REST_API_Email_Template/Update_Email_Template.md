---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Update Email Template
=====================

The **Update Email Template** API modifies the details of a template based on a requirement.

URL
---

The HTTP URL for Update Email Template API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/templates/emails/<id>
{% endhighlight %}

This service implements ‘Gateway Filter for Authentication’ to authenticate access of the service by a user.

Method
------

PUT

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| templatename | Yes | string | The unique name assigned to a template |
| mailSubject | Yes | string | The subject of the email |
| mailContent | Yes | string | The content of the email |

Sample Request
--------------

{% highlight voltMx %}{
	"templateName": "Electronic Gadgets Sale on Amazon 2016",
	"mailSubject":"Low Prices on Popular Products",
	"mailContent": " Electronic Dictionary,Black TimeR MJ02 Smart Multifunctional Ring"
}
{% endhighlight %}

Sample Response
---------------

{% highlight voltMx %}{  
  "message" : "Details updated successfully",  
  "id" : "templateid"  
}  

{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Details updated successfully |
| Status 400 | Template name is requiredTemplate subject is requiredMail content cannot be blank for code a template |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
