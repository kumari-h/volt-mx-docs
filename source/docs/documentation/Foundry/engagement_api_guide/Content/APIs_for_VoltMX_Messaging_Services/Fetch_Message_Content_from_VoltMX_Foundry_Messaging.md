---
layout: "documentation"
category: "engagement_api_guide"
---
                           


Fetch Message Content from Volt MX Foundry Engagement Services
=============================================================

The **Fetch Message Content from Volt MX Foundry Engagement Services** API is used to get message content from the Volt MX Foundry Engagement server.

For example, Apple delivers messages that are limited to 256 characters only. In order to view detailed messages, user has to send a request included pushId to Volt MX Foundry Engagement Services.

> **_Important:_** The Fetch Message Content from Volt MX Foundry Engagement Services API is maintained here to preserve backward compatibility.  
We encourage you to use [Fetch Message Content from Volt MX Foundry Engagement Services](../Push_Message_APIs/Fetch_Message_Content_from_VoltMX_Foundry_Messaging.html)

**URL**
-------

The HTTP URL for Fetch Message Content from Volt MX Foundry Engagement Services API is:

{% highlight voltMx %}http://<host or ip>:<port>/service/entrydata/content/$pushId  

{% endhighlight %}

Method
------

POST

Input Parameters
----------------

PushID is appended at the end of the URL.

Response Code
-------------

Success response code is _200._

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
