---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Event Message Request Payload with Common Properties
====================================================

The **Event Message Request Payload with Common Properties** API enables you to send event notifications with arrays of common audience member properties through Push, SMS, Email, and Pass channels. For each event message request, the **Event Message Request Payload with Common Properties** API generates a response ID.

URL
---

The HTTP URL for Event Message Request Payload with Common Properties API is:

{% highlight voltMx %}            
            http://<host or ip>:<port>/api/v1/events/push
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

POST

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameters | Level – Two | Level – Three | Level - Four | Required | Type | Description |
| --- | --- | --- | --- | --- | --- | --- |
| event |   |   |   |   |   | An array of event objects |
|   | eventNamePairs |   |   |   |   | An array of eventNamePairs for push message, email, SMS and passes |
|   |   | message |   |   |   | An array of message objects |
|   |   |   | Email | Yes | string | An array of audience member property-value pairs for email message |
|   |   |   | Mobile Number | Yes | string | An array of audience member property-value pairs for mobile number |
|   |   | content |   |   |   | An array of content objects |
|   |   |   | mimeType | Yes | string |   |
|   |   |   | priorityService | Yes | string |   |
|   |   | email |   |   |   | An array of email objects |
|   |   |   | from | Yes | string | An array of from objects |
|   |   |   | audienceMembers | Yes | string | An array of audienceMembers properties and value pairs |
|   |   | sms |   |   |   | An array of audience member property-value pairs for SMS message |
|   |   |   | Email | Yes | string | An array of audience member property-value pairs for email message |
|   |   |   | Mobile Number | Yes | string | An array of audience member property-value pairs for mobile number |
|   |   | pass |   |   |   | An array of audience member property-value pairs for passes |
|   |   |   | Email | Yes | string | An array of audience member property-value pairs for email message |
|   |   |   | Mobile Number | Yes | string | An array of audience member property-value pairs for mobile number |
|   |   |   | passTemplateValues | Optional |   | An array of passTemplateValues objects |

Sample Request Payload
----------------------

Sample request payloads are sent in the following formats:

*   [JSON](#json)
*   [XML](#xml)

### JSON

{% highlight voltMx %}{
	"event": {
		"eventNamePairs": {

		},
		"eventid": "4931534310398459652",
		"message": {
			"audienceMembers": {
				"property": "Email",
				"audienceMember": [{
					"value":"aron.hale@voltmx.com"
				}, {
					"value":"aron.hale@voltmx.com"
				}]
			},
			"content": {
				"mimeType": "text/plain",
				"priorityService": "false"
			}
		},
		"email": {
			"from": {
				"emailId": "admin@voltmx.com"
			},
			"audienceMembers": {
				"property": "Email",
				"audienceMember": [{
					"value": "aron.hale@voltmx.com"
				}]
			},
			"content": {
				"priorityService": "false"
			}
		},
		"sms": {
			"audienceMembers": {
				"property": "Mobile Number",
				"audienceMember": [{
					"value": "+1214322412312"
				}, {
					"value": "+1214322412312"
				}]
			},
			"content": {
				"mimeType": "text/plain",
				"priorityService": "false"
			}
		},
		"pass": {
			"audienceMembers": {
				"property": "Email",
				"audienceMember": [{
					"value": "+1214322412312"
				}, {
					"value":"aron.hale@voltmx.com"
				}]
			},
			"passTemplateValues": {
				"key": [{
					"name": "gate",
					"label": "GATE",
					"data": "23"
				}, {
					"name": "depart",
					"label": "SAN FRANCISCO",
					"data": "SFO"
				}, {
					"name": "arrive",
					"label": "NEW YORK",
					"data": "JFK"
				}, {
					"name": "passenger",
					"label": "PASSENGER",
					"data": "John Appleseed"
				}, {
					"name": "boardingTime",
					"label": "DEPART",
					"data": "2:25 PM"
				}, {
					"name": "flightNewkey",
					"label": "FLIGHT",
					"data": "815"
				}, {
					"name": "class",
					"label": "DESIG",
					"data": "Coach"
				}, {
					"name": "date",
					"label": "DATE",
					"data": "7/21"
				}, {
					"name": "passport",
					"label": "PASSPORT",
					"data": "Canadian/Canadien"
				}]
			}
		}
	}
}
{% endhighlight %}

### XML

{% highlight voltMx %}<?xml version="1.0" encoding="UTF-8"?>  
<event>  
<eventid>4931534310398459652</eventid>  
<eventNamePairs />  
<message>  
<audienceMembers property="Email">  
<audienceMember value="aron.hale@voltmx.com" />  
<audienceMember value="aron.hale@voltmx.com" />  
</audienceMembers>  
<content>  
<mimeType>text/plain</mimeType>  
<priorityService>false</priorityService>  
</content>  
</message>  
<email>  
<from emailId="test@test.com" />  
<audienceMembers property="Email">  

<audienceMember value="aron.hale@voltmx.com" />

<audienceMember value="aron.hale@voltmx.com" />  
</audienceMembers>  
<content>  
<priorityService>false</priorityService>  
</content>  
</email>  
<sms>  
<audienceMembers property="Mobile Number">  
<audienceMember value="+1214322412312" />  
<audienceMember value="+1214322412312" />  
</audienceMembers>  
<content>  
<mimeType>text/plain</mimeType>  
<priorityService>false</priorityService>  
</content>  
</sms>  
<pass>  
<audienceMembers property="Email">  
<audienceMember value="+1214322412312" />  
<audienceMember value="aron.hale@voltmx.com" />  
</audienceMembers>  
<passTemplateValues>  
<key name="gate" label="GATE" data="23" />  
<key name="depart" label="SAN FRANCISCO" data="SFO" />  
<key name="arrive" label="NEW YORK" data="JFK" />  
<key name="passenger" label="PASSENGER" data="John Appleseed" />  
<key name="boardingTime" label="DEPART" data="2:25 PM" />  
<key name="flightNewkey" label="FLIGHT" data="815" />  
<key name="class" label="DESIG" data="Coach" />  
<key name="date" label="DATE" data="7/21" />  
<key name="passport" label="PASSPORT" data="Canadian/Canadien" />  
</passTemplateValues>  
</pass>  
</event>  

{% endhighlight %}

Output Parameters
-----------------

Following fields are the output parameters:

  
| Output Parameter | Level-Two | Level-Three | Level - Four | Type | Description |
| --- | --- | --- | --- | --- | --- |
| event |   |   |   |   | An array of event objects |
|   | messageResponse |   |   |   | An array of messageResponse objects |
|   |   | response |   |   | An array of response objects |
|   |   |   | id | long | The unique id assigned to an event |
|   |   |   | message | string | Response status message |
|   |   | status |   | long | Response status code |

> **_Note:_** The sample response includes similar arrays for smsResponse, emailResponse and passResponse respectively.

Sample Response
---------------

### JSON

The following sample response payload returns request IDs for each request.

{% highlight voltMx %}{
  "event": {
    "smsResponse": {
      "response": {
        "message": "Request Queued. ",
        "id": "5769244567376011206"
      },
      "status": 200
    },
    "emailResponse": {
      "response": {
        "message": "Request Queued. ",
        "id": 2365011587565306649
      },
      "status": 200
    },
    "messageResponse": {
      "response": {
        "message": "Request Queued. ",
        "id": 7599706893432389638
      },
      "status": 200
    },
    "passResponse": {
      "response": {
        "message": "Request Queued. ",
        "id": 3402221074572385797
      },
      "status": 200
    }
  }
}
{% endhighlight %}

### XML

{% highlight voltMx %}<?xml version="1.0" encoding="UTF-8"?>  
<event>  
<messageResponse>  
<code>200</code>  
<description>Request Queued.</description>  
<requestId>7599706892396396547</requestId>  
<messages>  
<message msgId="7599706892396396548" description="Queued" />  
</messages>  
</messageResponse>  
<emailResponse>  
<code>200</code>  
<description>Request Queued.</description>  
<requestId>2365628586553189762</requestId>  
</emailResponse>  
<smsResponse>  
<code>200</code>  
<description>Request Queued.</description>  
<requestId>1227058458646255055</requestId>  
</smsResponse>  
<passResponse>  
<code>200</code>  
<description>Request Queued.</description>  

{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Request queued |
| Status 400 | Invalid request format |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
