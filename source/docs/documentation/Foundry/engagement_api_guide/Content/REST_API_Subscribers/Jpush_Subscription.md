---
layout: "documentation"
category: "engagement_api_guide"
---
                            


JPush Subscription
==================

The **JPush Subscription** API subscribes applications to send push notifications in China where Google is disabled.

URL
---

The HTTP URL for the **JPush Subscription** API is:

{% highlight voltMx %}<host>:<port>/api/v1/subscribers
{% endhighlight %}

The JPush Subscription API applies the Gateway Filter for Authentication to authenticate a user's credentials and allow access to the service.

Method
------

POST

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Level – Two | Level – Three | Type | Description |
| --- | --- | --- | --- | --- |
| subscriptionService |   |   |   | An array of subscriptionService objects |
|   | subscribe |   |   | An array of subscribe objects |
|   |   | sid | long | The subscription identification serial number |
|   |   | appId | long | Application ID |
|   |   | ufid | string | The User Friendly Identifier or UFID is used when you subscribe to Volt MX Foundry Engagement Services. Based on your requirement, you can provide an UFID. It is alphanumeric, for example xxx@voltmx.com or 2890XZCY. It can be used to map devices to the user using the value as a reconciliation key |
|   |   | osType | string | Operating system |
|   |   | deviceId | string | A unique ID assigned to the device |
|   |   | isJpush | boolean | Is JPush connectivity true or false |

Header
------

Based on the content format, the payload's request header includes Content-Type for:

*   XML as text/xml;charset=UTF-8
*   JSON as application/json;charset=UTF-8

Sample Request
--------------

### XML

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
    <subscribe>
        <appId>20096-6548262167</appId>
        <deviceId>92345600XY</deviceId>
        <ufid>aron.hale@voltmx.com</ufid>
        <sid>923456XQYN</sid>
        <osType>android</osType>
        <isJpush>true</isJpush>
    </subscribe>
</subscriptionService>
{% endhighlight %}

### JSON

{% highlight voltMx %}{
 "subscriptionService": {
  "subscribe": {
   "sid": "0a043dda850",
   "appId": "20096-6548262167",
   "ufid": "aron.hale@voltmx.com",
   "osType": "androidjpush",
   "deviceId": "09XCUYT909",
   "isJpush": true
  }
 }
}
{% endhighlight %}

Sample Response
---------------

### XML

{% highlight voltMx %}<subscriptionResponse>
    <statusCode>200</statusCode>
    <ksid>xxxx</ksid>
    <message>Subscription successful. </message>
</subscriptionResponse>
{% endhighlight %}

### JSON

{% highlight voltMx %}{
  "id" : "4927821427136428978",
  "message" : "Subscription successful. "
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Subscription successful |
| Status 400 | Invalid request format |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
