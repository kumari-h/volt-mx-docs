---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Pass Template by ID
=======================

The **Get Pass Template by ID** API accepts the template ID as an input parameter and returns all the pass template details.

URL
---

The HTTP URL for Get Pass Template by ID API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/templates/passbook/{id}
{% endhighlight %}

Method
------

GET

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Level – Two | Level – Three | Type | Description |
| --- | --- | --- | --- | --- |
| id |   |   | long | Unique pass ID assigned to a pass template |
| name |   |   | string | The unique name assigned to a pass template |
| passIntegrationConfig |   |   |   | An array of passIntegrationConfig objects |
|   | passIssueNotificationDetails |   |   | An array of passIssueNotificationDetails objects |
|   |   | channel | string | Channel type as push , SMS or email |
|   |   | enabled | boolean | If channel type is enabled or not |
|   |   | messageContent | string | Message description |
|   |   | subject | string | Subject of the pass template. The subject convey the essence of the pass template |
|   |   | senderName | string | Name of the sender |
|   |   | senderEmail | string | Email ID of the sender |
|   | createdBy |   | string | A user name that shows who created the pass template |
|   | createdDate |   | string | Date on which the pass template is created |
|   | lastModifiedBy |   | string | User name showing who last modified the pass template |
|   | lastModifiedDate |   | string | Date the pass template was last modified |
|   | passContent |   |   | An array of passContent objects |
|   |   | basicDetails |   | An array of basicDetails objects. For more details, [see](Pass_Template.html#passtemplates) |
|   |   | appearance |   | An array of appearance objects. For more details, [see](Pass_Template.html#appearance) |
|   |   | frontLayout |   | An array of frontLayout objects. For more details, [see](Pass_Template.html#frontLayout) |
|   |   | backLayout |   | An array of backLayout objects. For more details, [see](Pass_Template.html#backLayout) |
|   |   | passRelevance |   | An array of passRelevance objects. For more details, [see](Pass_Template.html#passRelevance) |
|   |   | passRules |   | An array of passRules objects. For more details, [see](Pass_Template.html#passRules) |
|   |   | languageDetails |   | An array of languageDetails objects. For more details, [see](Pass_Template.html#languageDetails) |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : 1,
  "name" : "eBay membership pass",
  "passIntegrationConfig" : {
    "passIssueNotificationDetails" : [ {
      "channel" : "SMS",
      "enabled" : true,
      "messageContent" : "##First Name####Last Name##",
      "subject" : "",
      "senderName" : "",
      "senderEmail" : ""
    } ]
  },
  "createdBy" : "admin",
  "createdDate" : "06/30/2016 05:19:58 AM GMT",
  "lastModifiedBy" : "admin",
  "lastModifiedDate" : "08/29/2016 01:00:15 PM GMT",
  "passContent" : {
    "basicDetails" : {
      "passTypeIdentifier" : "pass.com.vms.passbook2",
      "passSerialNumber" : "",
      "groupIdentifier" : "",
      "appLaunchURL" : "",
      "ituneIdentifiers" : "",
      "webServiceUrl" : "",
      "timezone" : "(GMT-05:00) Eastern Time (US & Canada)",
      "passType" : "GENERIC",
      "organizationName" : "eBay",
      "description" : "eBay membership pass",
      "passSerialNumberType" : "AUTO_GEN",
      "eventTicketType" : "",
      "customJsonData" : { }
    },
    "appearance" : {
      "bgColor" : "#64798c",
      "labelColor" : "#ccdae9",
      "valueColor" : "#ffffff",
      "suppressStripShine" : false,
      "images" : [ {
        "url" : "https://upload.wikimedia.org/wikipedia/commons/4/48/EBay_logo.png",
        "blob" : false,
        "size" : 9633,
        "extension" : "png",
        "imageType" : "ICON",
        "imageId" : ""
      } ]
    },
    "frontLayout" : {
      "logoText" : "eBay",
      "headerFields" : [ {
        "label" : "SummerSale ",
        "data" : "2016",
        "changeMessage" : "",
        "displayRelatively" : false,
        "ignoreTimezone" : false,
        "key" : "Membership Card",
        "dataType" : "TEXT",
        "numberFormat" : "",
        "currency" : "",
        "dateTimeFormat" : "",
        "alignment" : "LEFT",
        "autolink" : [ ]
      } ],
      "primaryFields" : [ ],
      "auxiliaryFields" : [ ],
      "secondaryFields" : [ ],
      "barcodeDetails" : {
        "message" : "",
        "alternateText" : "",
        "barcodeType" : "PDF417",
        "embeddedMessageType" : "PASS_SERIAL_NO",
        "alternativeTextType" : "BARCODE_CONTENTS",
        "embeddedFormat" : "UTF_8"
      },
      "transitType" : ""
    },
    "backLayout" : {
      "fields" : [ ],
      "enableAutoUpdates" : false
    },
    "passRelevance" : {
      "relevantDate" : "",
      "ignoreTimezone" : false,
      "relevantLocations" : [ ],
      "relevantBeacons" : [ ],
      "maxDistance" : ""
    },
    "passRules" : {
      "stopAfter" : "",
      "expiryDate" : "",
      "voided" : false,
      "dateRestriction" : "PERMANENTLY_AVAILABLE"
    },
    "languageDetails" : {
      "originalFields" : [ "eBay passes for shopping" ],
      "languageEntries" : [ {
        "data" : [ {
          "localText" : "eBay geht zum Einkaufen"
        } ],
        "images" : [ ],
        "language" : "DE"
      } ],
      "passLanguage" : "EN"
    }
  }
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Array of pass template details |
| Status 400 | Bad request |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
