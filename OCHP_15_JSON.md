<!-- Generator: Widdershins v4.0.1 -->

<h1 id="ochp-1-5-json">OCHP 1.5 JSON v0.0.1</h1>

> Scroll down for example requests and responses.

OCHP 1.5 JSON API Prototype

Email: <a href="mailto:info@e-clearing.net">e-clearing.net</a> Web: <a href="https://ochp.eu">e-clearing.net</a> 
License: <a href="https://github.com/e-clearing-net/OCHP/blob/master/LICENSE">MIT License</a>

<h1 id="ochp-1-5-json-emsp-roaming-authorisation-data-exchange-api">EMSP: Roaming Authorisation Data Exchange API</h1>

Exchange of Roaming (EV-Charging) Informations between EMSP & eCHS

## put__RoamingAuthorisationInfos

> Code samples

`PUT /RoamingAuthorisationInfos`

Allows the EMSP to set Roaming Authorisation List or make updates on the Roaming Authorisation List to the CHS. PUT can also be used to update the tokens, but the request must contain all the tokens that the EMP wants to be in the eCHS system, as this request will replace all the old data in eCHS.

> Body parameter

```json
[
  {
    "roamingAuthorisationInfoArray": {
      "emtId": {
        "instance": 43,
        "representation": "plain",
        "type": "rfid",
        "subType": "mifareCls"
      },
      "contractId": null,
      "permissions": "AC",
      "printedNumber": 4424,
      "expiryDate": "2025-01-01T00:00:00Z"
    }
  }
]
```

<h3 id="put__roamingauthorisationinfos-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[object]|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="put__roamingauthorisationinfos-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successfully set/added roaming authorisation list by the EMSP into the CHS (SetRoamingAuthorisationList.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful addition/setting of roaming authorisation list by the EMSP into the CHS (SetRoamingAuthorisationList.conf).|[PartialSuccessResponseModel](#schemapartialsuccessresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="put__roamingauthorisationinfos-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## patch__RoamingAuthorisationInfos

> Code samples

`PATCH /RoamingAuthorisationInfos`

Allows the EMSP to make (partial) updates only on certain fields (that requires to be changed) of the Roaming Authorisation List in the CHS.

> Body parameter

```json
[
  {
    "roamingAuthorisationInfoArray": {
      "emtId": {
        "instance": 43,
        "representation": "plain",
        "type": "rfid",
        "subType": "mifareCls"
      },
      "contractId": null,
      "permissions": "AC",
      "printedNumber": 4424,
      "expiryDate": "2025-01-01T00:00:00Z"
    }
  }
]
```

<h3 id="patch__roamingauthorisationinfos-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[object]|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="patch__roamingauthorisationinfos-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successful update of roaming authorisation list by the EMSP into the CHS (UpdateRoamingAuthorisationList.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful (partial) update of roaming authorisation list by the EMSP into the CHS (UpdateRoamingAuthorisationList.conf).|[PartialSuccessResponseModel](#schemapartialsuccessresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="patch__roamingauthorisationinfos-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-cpo-roaming-authorisation-data-exchange-api">CPO: Roaming Authorisation Data Exchange API</h1>

Exchange of Roaming (EV-Charging) Informations between CPO & eCHS

## get__RoamingAuthorisationInfos

> Code samples

`GET /RoamingAuthorisationInfos`

Allows a CPO to download the Roaming Authorisation List from eCHS

<h3 id="get__roamingauthorisationinfos-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pagination|query|[Pagination](#schemapagination)|false|Filter the results updated, starting from the mentioned date and time.|
|CPO-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the CPO/CPOs requesting the data/Roaming Authorisation Information from the eCHS server. To retrieve the RoamingAuthorisations for selected CPOs.|
|EMP-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the EMSP/EMSPs whose data/Roaming Authorisation Information is requested by the CPO/CPOs from the eCHS server. To retrieve the RoamingAuthorisations from selected EMSPs.|

> Example responses

> 200 Response

```json
{
  "result": null,
  "roamingAuthorisationItemInfo": {
    "objectCount": 569,
    "objectSize": "20kB",
    "limit": 100
  },
  "roamingAuthorisationInfoArray": [
    {
      "emtId": {
        "instance": 43,
        "representation": "plain",
        "type": "rfid",
        "subType": "mifareCls"
      },
      "contractId": null,
      "permissions": "AC",
      "printedNumber": 4424,
      "expiryDate": "2025-01-01T00:00:00Z"
    }
  ]
}
```

<h3 id="get__roamingauthorisationinfos-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of the Roaming Authorisation Lists (GetRoamingAuthorisationList.conf).|[ResponseModel](#schemaresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__roamingauthorisationinfos-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## post__RoamingAuthorisationInfos_{instance}_{evseId}_authorise

> Code samples

`POST /RoamingAuthorisationInfos/{instance}/{evseId}/authorise`

Allows a single roaming authorisation of selected tokens. The Charge point management system may request the Clearing House to authorize one single token for a charging session. The Charge point management system sends the request to authorise selected tokens by the EMSP via the CHS.

> Body parameter

```json
{
  "emtId": {
    "instance": 43,
    "representation": "plain",
    "type": "rfid",
    "subType": "mifareCls"
  }
}
```

<h3 id="post__roamingauthorisationinfos_{instance}_{evseid}_authorise-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|instance|path|string|true|This contains the ID of the token which is to be validated.|
|evseId|path|object|true|This contains the ID of the EVSE where the charging has to take place. Unique identifier for every EVSE following a common scheme with a major id-unit reflecting the country and the market partner issuing it.|
|body|body|object|true|none|

> Example responses

> 200 Response

```json
{
  "result": null,
  "roamingAuthorisationInfo": {
    "emtId": {
      "instance": 43,
      "representation": "plain",
      "type": "rfid",
      "subType": "mifareCls"
    },
    "contractId": null,
    "permissions": "AC",
    "printedNumber": 4424,
    "expiryDate": "2025-01-01T00:00:00Z"
  }
}
```

<h3 id="post__roamingauthorisationinfos_{instance}_{evseid}_authorise-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successfully sends the roaming authorisation record for the requested token. (RequestSingleRoamingAuthorisationList.conf). This contains the roaming authorisation record for the requested token, if the request was valid.|[SingleRoamingResponseModel](#schemasingleroamingresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The response from EMSP via CHS. When the EMSP does not know the token for which the CPO is requesting an authorisation, CHS responds with a 404- Not found.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="post__roamingauthorisationinfos_{instance}_{evseid}_authorise-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-cpo-charge-detail-record-exchange-api">CPO: Charge Detail Record Exchange API</h1>

Exchange of Charge Data Informations between CPO and eCHS.

## post__CDRs

> Code samples

`POST /CDRs`

Allows a CPO to add the CDRs into CHS. May be used by a CPO to mark declined CDRs as finally rejected, by uploading them again under that status. (AddCDRs.req)

> Body parameter

```json
{
  "cdrInfoArray": []
}
```

<h3 id="post__cdrs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[AddCdrRequestModel](#schemaaddcdrrequestmodel)|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="post__cdrs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successful upload of Charge Detail Records into the CHS by the CPO. (AddCDRs.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful upload of charge detail records by the CPO into the CHS (AddCDRs.conf).|[ImplausibleCDRsResponseModel](#schemaimplausiblecdrsresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="post__cdrs-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__CDRs_CheckCDRs

> Code samples

`GET /CDRs/CheckCDRs`

Allows a CPO to check the CDR for EMSPs/EMSP (with which it has roaming connection) in the CHS. (CheckCDRs.req)

<h3 id="get__cdrs_checkcdrs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pagination|query|[Pagination](#schemapagination)|false|Filter the results updated, starting from the mentioned date and time.|
|EMP-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the EMSP/EMSPs, whose Charge Detail Records are to be checked by the requesting  CPO/CPOs in the CHS. To retrieve the CDRs from selected EMPs.|
|CPO-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the CPO/CPOs requesting to check the Charge Detail Record of EMSP/EMSPs in the CHS. To retrieve the CDRs for selected CPOs (own sister companies).|
|cdrStatus|query|undefined|false|Defines which status of CDRs to return. Valid options are- accepted, declined, revised, rejected, approved. If not set, will return declined CDRs.|

> Example responses

> 200 Response

```json
{
  "data": null
}
```

<h3 id="get__cdrs_checkcdrs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of the CDR from the CHS (CheckCDRs.conf)|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__cdrs_checkcdrs-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-emsp-charge-detail-record-exchange-api">EMSP: Charge Detail Record Exchange API</h1>

Exchange of Charge Data Informations between EMSP and eCHS.

## get__CDRs

> Code samples

`GET /CDRs`

Allows an EMSP to request for the Charge Detail Records from the CHS. The EMSP gets the CDRs from the CPOs endpoint through the CHS. (GetCDRs.req)

<h3 id="get__cdrs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pagination|query|[Pagination](#schemapagination)|false|Filter the results updated, starting from the mentioned date and time.|
|CPO-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the CPO/CPOs from where the Charge detail record is requested by an EMSP/EMSPs. To retrieve the CDRs from selected CPOs.|
|EMP-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the EMSP/EMSPs requesting the charge detail record from the respective CPO/CPOs with which it has a roaming connection. To retrieve the CDRs for selected EMPs|
|cdrStatus|query|undefined|false|Defines which status of CDRs to return. Valid options are:- accepted, declined, revised, rejected, approved. If not set, will return accepted and revised CDRs.|

> Example responses

> 200 Response

```json
{
  "data": null
}
```

<h3 id="get__cdrs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of the CDR from the CHS (GetCDRs.conf)|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__cdrs-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## patch__CDRs

> Code samples

`PATCH /CDRs`

The EMSP send the CHS the list of CDRs that it approves or declines.

> Body parameter

```json
{
  "approved": [
    {
      "cdrId": null,
      "EvseId": null
    }
  ],
  "declined": [
    {
      "cdrId": null,
      "EvseId": null
    }
  ]
}
```

<h3 id="patch__cdrs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[ConfirmCDRs](#schemaconfirmcdrs)|false|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="patch__cdrs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. This response is send to the confirmation of CDRs request from EMSP. (ConfirmCDRs.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful (partial) update of cdr status by the EMSP into the CHS (ConfirmCDRs.conf).|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="patch__cdrs-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

Status Code **206**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[refusedIDs](#schemarefusedids)]|false|none|[This response is sent by the CHS when the EMSP tries to send the list of Approved and/declined CDRs, however not all were  successful due to some reason. The CHS sends the Result value 'partly' and also sends the cdr Ids, whose status could not be uploaded in the CHS.]|
|» result|any|true|none|none|
|» refusedcdrIds|array|true|none|none|
|»» *anonymous*|any|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-cpo-live-status-interface-exchange-api">CPO: Live Status Interface Exchange API</h1>

Exchange of current Live Status of individual charging stations between CPO and eCHS.

## patch__Status

> Code samples

`PATCH /Status`

A CPO may update the current live status of individual charging stations in the Clearing House to allow   roaming partners to receive those statuses. Additionally, a PSO may update the current live status of individual parking spots, allowing the EVSE Operators roaming partners to receive these alongside the EVSE live status(UpdateStatus.req).

> Body parameter

```json
[
  {
    "evse": [
      {
        "evseId": null,
        "major": "available",
        "minor": "available",
        "ttl": "2025-01-01T00:00:00Z"
      }
    ],
    "parkingspot": [
      {
        "parkingId": "DELNDP12",
        "status": "available",
        "ttl": "2025-01-01T00:00:00Z"
      }
    ],
    "ttl": "2025-01-01T00:00:00Z"
  }
]
```

<h3 id="patch__status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|array[object]|false|none|

> Example responses

> 200 Response

```json
{
  "result": null
}
```

<h3 id="patch__status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. This response is send when the Status update is done by the CPO/PSO in the eCHs|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="patch__status-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-nsp-live-status-information-exchange-api">NSP: Live Status Information Exchange API</h1>

Exchange of current Live Status of individual charging stations and parking spot between eCHS and NSP.

## get__Status

> Code samples

`GET /Status`

Allows an NSP to download the global live status information from the eCHS.

<h3 id="get__status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|startDateTime|query|[DateTimeType](#schemadatetimetype)|false|If this value is set to a point in the past the response is limited to status information that is more actual than the given value.|
|statusType|query|[statusType](#schemastatustype)|false|This field can be set to determine which status values to return from the CHS. Valid entries:- evse, parking, combined. If not set, only EVSE status values will be returned.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|statusType|evse|
|statusType|parking|
|statusType|combined|

> Example responses

> 200 Response

```json
{
  "evse": [
    {
      "evseId": null,
      "major": "available",
      "minor": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "parking": [
    {
      "parkingId": "DELNDP12",
      "status": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "combined": [
    {
      "evseId": null,
      "major": "available",
      "minor": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ]
}
```

<h3 id="get__status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of global live status information from the CHS.|[StatusConfirmation](#schemastatusconfirmation)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__status-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-cpo-tariff-information-exchange-api">CPO: Tariff Information Exchange API</h1>

Exchange of Tariff Information between the CPO & eCHS.

## put__Tariff

> Code samples

`PUT /Tariff`

The CPO uploads and/updates their tariff information to the Clearing House.

> Body parameter

```json
{
  "tariffInfoArray": [
    {
      "tariffId": "YYABCT01",
      "individualTariff": [
        {
          "currency": null,
          "tariffElement": [
            {
              "priceComponent": {
                "billingItem": "parkingtime",
                "itemPrice": 0.1,
                "stepSize": 0.1
              },
              "tariffRestriction": {
                "regularHours": [
                  {
                    "weekday": 1,
                    "periodBegin": "18:15",
                    "periodEnd": "20:15"
                  }
                ],
                "startDate": "2025-01-01T00:00:00Z",
                "endDate": "2025-01-01T00:00:00Z",
                "minEnergy": 20,
                "maxEnergy": 50,
                "minPower": 0,
                "maxPower": 20,
                "minDuration": 10,
                "maxDuration": 600
              }
            }
          ],
          "recipient": [
            "^A$"
          ]
        }
      ]
    }
  ]
}
```

<h3 id="put__tariff-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[TariffRequestModel](#schematariffrequestmodel)|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="put__tariff-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successfully uploaded the tariff information  by the CPO into the CHS (UpdateTariffs.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful upload/update of tariff information by the CPO into the CHS (UpdateTariffs.conf).|[refusedTariffInfoModel](#schemarefusedtariffinfomodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="put__tariff-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-emsp-tariff-information-exchange-api">EMSP: Tariff Information Exchange API</h1>

Exchange of Tariff Information between eCHS & EMSP.

## get__Tariff

> Code samples

`GET /Tariff`

Download the Tariff Information from the CHS.

<h3 id="get__tariff-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pagination|query|[Pagination](#schemapagination)|false|Filter the results updated, starting from the mentioned date and time.|
|CPO-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the CPO/CPOs whose tariff information is requested by the EMSP/EMSPs from the eCHS server. To retrieve the Tariffs from selected CPOs|
|EMP-ID|query|[PartnerID](#schemapartnerid)|false|The ID of the EMSP/EMSPs requesting the Tariff information from the eCHS server. To retrieve the Tariffs for selected EMPs.|

> Example responses

> 200 Response

```json
{
  "result": null,
  "TariffInfoArray": [
    {
      "tariffId": "YYABCT01",
      "individualTariff": [
        {
          "currency": null,
          "tariffElement": [
            {
              "priceComponent": {
                "billingItem": "parkingtime",
                "itemPrice": 0.1,
                "stepSize": 0.1
              },
              "tariffRestriction": {
                "regularHours": [
                  {
                    "weekday": 1,
                    "periodBegin": "18:15",
                    "periodEnd": "20:15"
                  }
                ],
                "startDate": "2025-01-01T00:00:00Z",
                "endDate": "2025-01-01T00:00:00Z",
                "minEnergy": 20,
                "maxEnergy": 50,
                "minPower": 0,
                "maxPower": 20,
                "minDuration": 10,
                "maxDuration": 600
              }
            }
          ],
          "recipient": [
            "^A$"
          ]
        }
      ]
    }
  ]
}
```

<h3 id="get__tariff-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of the tariff Information. (GetTariffUpdatest.conf).|[TariffResponseModel](#schematariffresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__tariff-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-cpo-charge-point-information-exchange-api">CPO: Charge Point Information Exchange API</h1>

Exchange of Charge Point Information between CPO & eCHS

## put__ChargePointList

> Code samples

`PUT /ChargePointList`

The CPO uploads own charge point information to the CHS. Each CPO has to upload its own Charge point information to the Clearing House. (SetChargePointList.req)

> Body parameter

```json
{
  "chargePointInfoArray": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}
```

<h3 id="put__chargepointlist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[chargePointRequestModel](#schemachargepointrequestmodel)|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="put__chargepointlist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successfully uploaded the Charge Point Information Records by the CPO into the CHS (SetChargePointList.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful upload of Charge Point Information Records by CPO into the CHS (SetChargePointList.conf).|[refusedChargePointInfoResponse](#schemarefusedchargepointinforesponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="put__chargepointlist-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## patch__ChargePointList

> Code samples

`PATCH /ChargePointList`

The CPO makes an update on the existing list of Charge Point information records.

> Body parameter

```json
{
  "chargePointInfoArray": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}
```

<h3 id="patch__chargepointlist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[chargePointRequestModel](#schemachargepointrequestmodel)|true|none|

> Example responses

> 201 Response

```json
{
  "result": null
}
```

<h3 id="patch__chargepointlist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The response from CHS. Successful update of charge point information records by the CPO into the CHS (UpdateChargePointList.conf).|Inline|
|206|[Partial Content](https://tools.ietf.org/html/rfc7233#section-4.1)|Partially-successful update of Charge Point Information records by the CPO into the CHS (UpdateChargePointList.conf).|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="patch__chargepointlist-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» result|any|true|none|none|

Status Code **206**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[refusedChargePointInfoResponse](#schemarefusedchargepointinforesponse)]|false|none|[The response send by CHS to the CPO after uploading the Charge Point Information Records. This response is sent when not all but only part of the records were only uploaded. The CHS also sends these refused charge point information records along with the response, 'partly']|
|» result|any|true|none|none|
|» refusedChargePointInfo|[[ChargePointInfo](#schemachargepointinfo)]|true|none|[Contains information about the charge points. Static POI data regarding a charge point / EVSE.]|
|»» evseId|any|true|none|none|
|»» evseDescription|string|true|none|Human readable description of an EVSE|
|»» locationId|string|true|none|Alphanumeric. Identifies a location/pool of EVSEs. Unique within one EVSE Operator. All EVSEs of one locationId have to have the same address and Geocoordinates. Characters:- [A-Z], [0-9]|
|»» timeStamp|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|»» locationName|string|true|none|Official name; should be unique in the geographical area.|
|»» locationNameLang|string|true|none|Alpha, three characters. ISO-639-3 language code defining the language of the location name.|
|»» images|[[evseImageUrlType](#schemaevseimageurltype)]|false|none|Links to images related to the EVSE such as photos or logos.|
|»»» uri|string|true|none|uri from where the image data can be fetched. Must begin with a protocol of the list:- http, https, file,ftp.|
|»»» thumbUri|string|false|none|uri from where a thumbnail of the image can be fetched. Must begin with a protocol of the list:- http, https, file, ftp.|
|»»» class|[ImageClass](#schemaimageclass)|true|none|The class of a EVSE image to obtain the correct usage in a user presentation. Has to be set accordingly to the image content in order to guaranty the right usage. * 'networkLogo' -  logo of an associated roaming network to be displayed with the EVSE for example in lists, maps and detailed information view * 'operatorLogo'-  logo of the charge points operator, for example a municipal, to be displayed with the EVSEs detailed information view or in lists and maps, if no networkLogo is present * 'ownerLogo' -  logo of the charge points owner, for example a local store, to be displayed with the EVSEs detailed information view * 'stationPhoto' -  full view photo of the station in field. Should show the station only * 'locationPhoto' -  location overview photo. Should indicate the location of the station on the site or street. * 'entrancePhoto' -  location entrance photo. Should show the car entrance to the location from street side * 'otherPhoto' -  other related photo to be displayed with the stations detailed information view * 'otherLogo' -  other related logo to be displayed with the stations detailed information view * 'otherGraphic' -  other related graphic to be displayed with the stations detailed information view|
|»»» type|string|true|none|Image type like:- gif, jpeg, png, svg|
|»»» width|integer|false|none|Width of the full scale image|
|»»» height|integer|false|none|Height of the full scale image|
|»» relatedResource|[[RelatedResourceType](#schemarelatedresourcetype)]|false|none|Links to be visited by the user, related to the charge point or charging station.|
|»»» uri|string|true|none|Referencing uri to the resource. Must begin with a protocol of the list:- http, https.|
|»»» class|[RelatedResourceClass](#schemarelatedresourceclass)|true|none|The class of referenced related resource. * 'operatorMap' -  direct link to this charge point on a map of the operator * 'operatorPayment' -  link to a payment page of the operator for contractless direct payment * 'stationInfo' -  further information on the charging station * 'surroundingInfo' -  further information on the surroundings of the charging station e.g. further POIs * 'ownerHomepage' -   website of the station owner (not operator) in case of hotels, restaurants, etc. * 'feedbackForm'-  form for user feedback on the charging station service * 'openingTimes' -  link to a calendar or info page containing opening times (only if no other way of defining these is possible).|
|»» chargePointAddress|any|true|none|none|
|»» chargePointLocation|[GeoPointType](#schemageopointtype)|true|none|Defines a geo location. The geodetic system to be used is WGS 84.|
|»»» lat|[latitude](#schemalatitude)|true|none|Latitude of the point in decimal degree.  Decimal separator:- "."|
|»»» lon|[longitude](#schemalongitude)|true|none|Longitude of the point in decimal degree.  Decimal separator:- "."|
|»» relatedLocation|[AdditionalGeoPointType](#schemaadditionalgeopointtype)|false|none|Class defines a geo location. The geodetic system to be used is WGS 84.|
|»»» lat|[latitude](#schemalatitude)|true|none|Latitude of the point in decimal degree.  Decimal separator:- "."|
|»»» lon|[longitude](#schemalongitude)|true|none|Longitude of the point in decimal degree.  Decimal separator:- "."|
|»»» name|string|false|none|Name of the point in local language or as written at the location. For example the street name of a parking lot entrance or it's number.|
|»»» type|[GeoClass](#schemageoclass)|true|none|The class of this geo point for categorization and right usage. * 'entrance' -  For larger sites entrances may be specified for navigation. * 'exit' -  For larger sites exits may be specified for navigation purpose. * 'access'-  Two directional entrance and exit. * 'ui' -  Geographical location of the user interface for authorisation and payment means. If not specified the user interface is assumed to be at the location of the charge point. * 'other' -   Other relevant point. Name recommended.|
|»» timeZone|string|false|none|One of IANA tzdata's TZ-values representing the time zone of the location.|
|»» openingTimes|[HoursType](#schemahourstype)|true|none|Opening hours for the charge point.|
|»»» regularHours|[[RegularHoursType](#schemaregularhourstype)]|false|none|Regular hours, weekday based. Should not be set for representing 24/7 as this is the most common case.|
|»»»» weekday|integer|true|none|Number of day in the week, beginning with Monday (1), ending with Sunday (7).|
|»»»» periodBegin|string|true|none|begin of the regular period given in hours:minutes. Must be in 24h format with leading zeros. Example:- '18:15'. Hour/Minute separator:- ":" Regex:- $[$0-2$]$$[$0-9$]$:$[$0-5$]$$[$0-9$]$|
|»»»» periodEnd|string|true|none|End of the regular period, syntax as for periodBegin. Must be later than periodBegin.|
|»»» twentyfourseven|boolean|true|none|True to represent 24 hours per day and 7 days per week, except the given exceptions. May be set to false if opening hours are defined only by exceptionalOpenings.|
|»»» closedCharging|boolean|true|none|hould be set to true in case an EV can be charged when plugged in during off-times (i.e. when the location is closed according to the specified hours).|
|»»» exceptionalOpenings|[[ExceptionalPeriodType](#schemaexceptionalperiodtype)]|false|none|Exceptions for specified calendar dates, time-range based. Periods the station is operating/accessible. For irregular hours or as addition to regular hours. May overlap regular rules.|
|»»»» periodBegin|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|»»»» peridoEnd|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|»»» exceptionalClosings|[[ExceptionalPeriodType](#schemaexceptionalperiodtype)]|false|none|Exceptions for specified calendar dates, time-range based. Periods the station is not operating/accessible. Overwriting regularHours and twentyfourseven. Should not overlap exceptionalOpenings.|
|»» status|[ChargePointStatusType](#schemachargepointstatustype)|false|none|This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon|
|»» statusSchedule|[[ChargePointScheduleType](#schemachargepointscheduletype)]|false|none|Planned status changes in the future. If a time span matches with the current or displayed date, the corresponding value overwrites status|
|»»» startDate|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|»»» endDate|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|»»» status|[ChargePointStatusType](#schemachargepointstatustype)|true|none|This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon|
|»» telephoneNumber|string|false|none|Numeric. Service hotline for charging station to be displayed to the EV user. Separators recommended. Recommended to be in international format including leading + and country code. (e.g. +49).|
|»» location|[GeneralLocationType](#schemagenerallocationtype)|true|none|Reflects the general type of the charge points location. May be used for user information. * 'on-street' - parking in public space * 'parking-garage' - multistorey car park * 'underground-garage' - multistorey car park, mainly underground * 'parking-lot' - a cleared area that is intended for parking vehicles, i.e. at super markets, bars, etc. * 'private' - located in private or corporate grounds, may not be accessible to the public * 'other' - none of the given possibilities * 'unknown' - parking location type is not known by the operator|
|»» parkingSpot|[[ParkingSpotInfo](#schemaparkingspotinfo)]|false|none|Information about one or more parking spots associated with the EVSE.|
|»»» parkingId|[ParkingId](#schemaparkingid)|true|none|The parking-ID follows a similar syntax to that of contract- and EVSE-IDs. The PSO-ID is followed by a 'P' that signifies a tariff and a unique instance of up to 30 characters.|
|»»» restriction|[[RestrictionType](#schemarestrictiontype)]|false|none|Restrictions applying to the usage of the parking spot. If set, should include the restrictions to EVSE-usage as well.|
|»»» floorlevel|string|false|none|Alphanumeric. Level on which the charge station is located (in garage buildings) in the locally displayed numbering scheme.|
|»»» parkingSpotNumber|string|false|none|Alphanumeric. Locally displayed parking slot number.|
|»» restriction|[[RestrictionType](#schemarestrictiontype)]|false|none|Restrictions applying to the usage of the charging station.|
|»» authMethods|[[AuthMethodType](#schemaauthmethodtype)]|true|none|List of available payment or access methods on site.|
|»» connectors|[[ConnectorType](#schemaconnectortype)]|true|none|Which receptacle type is/are present for a power outlet.|
|»»» connectorStandard|[ConnectorStandardType](#schemaconnectorstandardtype)|true|none|The socket or plug standard of the charging point * 'Chademo'- The connector type is CHAdeMO, DC * 'IEC_62196_T1'-   IEC 62196 Type 1 "SAE J1772" * 'IEC_62196_T1_COMBO'- Combo Type 1 based, DC * 'IEC_62196_T2'-   IEC 62196 Type 2 "Mennekes" * 'IEC_62196_T2_COMBO' - Combo Type 2 based, DC * 'IEC_62196_T3A' IEC 62196 Type 3A * 'IEC_62196_T3C'  IEC 62196 Type 3C "Scame" * 'DOMESTIC_A' Standard/Domestic household, type "A", NEMA 1-15, 2 pins * 'DOMESTIC_B' Standard/Domestic household, type "B", NEMA 5-15, 3 pins * 'DOMESTIC_C' Standard/Domestic household, type "C", CEE 7/17, 2 pins * 'DOMESTIC_D' Standard/Domestic household, type "D", 3 pin * 'DOMESTIC_E' Standard/Domestic household, type "E", CEE 7/5 3 pins * 'DOMESTIC_F' Standard/Domestic household, type "F", CEE 7/4, Schuko, 3 pins * 'DOMESTIC_G' Standard/Domestic household, type "G", BS 1363, Commonwealth, 3 pins * 'DOMESTIC_H' Standard/Domestic household, type "H", SI-32, 3 pins * 'DOMESTIC_I' Standard/Domestic household, type "I", AS 3112, 3 pins * 'DOMESTIC_J'  Standard/Domestic household, type "J", SEV 1011, 3 pins * 'DOMESTIC_K' Standard/Domestic household, type "K", DS 60884-2-D1, 3 pins * 'DOMESTIC_L'  Standard/Domestic household, type "L", CEI 23-16-VII, 3 pins * 'TESLA_R' Tesla Connector "Roadster"-type (round, 4 pin) * 'TESLA_S' Tesla Connector "Model-S"-type (oval, 5 pin) * 'IEC_60309_2_single_16'IEC 60309-2 Industrial Connector single phase 16 Amperes (usually blue) * 'IEC_60309_2_three_16'   IEC 60309-2 Industrial Connector three phase 16 Amperes (usually red) * 'IEC_60309_2_three_32' IEC 60309-2 Industrial Connector three phase 32 Amperes (usually red) * 'IEC_60309_2_three_64' IEC 60309-2 Industrial Connector three phase 64 Amperes (usually red) * 'LPG  ' ACME, DISH, Bajonett, Euronozzle * 'LNG' Universal * 'CNG' NGV1, NGV2 * 'H2' SAE J2601 * 'SUPER_95' Universal * 'SUPER_PLUS' Universal * 'SUPER_E10' Universal * 'DIESEL'  Universal * 'ETHANOL'  Universal * 'ADBLUE' Universal|
|»»» connectorFormat|[ConnectorFormatType](#schemaconnectorformattype)|true|none|The format of the connector, whether it is a socket or a plug. * 'Socket' - The connector is a socket; the EV user needs to bring a fitting plug/cable. * 'Cable'- The connector is an attached cable; the EV users car needs to have a corresponding   inlet. * 'Nozzle'- The connector is a nozzle; used normally at conventional fuel stations. * 'Other'- The connector is of another type, like a nozzle with an attached hose.|
|»»» tariffId|[TariffId](#schematariffid)|false|none|The tariff-ID follows a similar syntax to that of contract- and EVSE-IDs. The The Operator-ID is followed by a 'T' that signifies a tariff and a unique instance of up to 30 characters. The max. length allowed it string(36). Alphanumeric. Identifies a tariff. Unique within one EVSE Operator. Must begin with the Operator-ID, without separators.|
|»» chargePointType|[chargePointType](#schemachargepointtype)|true|none|The chargePointType is extended from AC and DC to the options mentioned below. The enhancement enables the CPOs to define the CPTs more precisely and offer diversified services. * 'AC' - Alternating current * 'DC' - Direct current * 'Super_95' - Premium unleaded petrol having octance rating of 95 * 'Super_Plus' - High octane rating fuel containing 5-10% of ethanol * 'Super_E10' - Petrol fuel with an ethanol content of up to 10 percent and an octane rating of at least 95 * 'Diesel' - Liquid fuel used in diesel engines, whose ignition takes place without any spark * 'LPG' - Liquefied petroleum gas * 'CNG' - Compressed natural gas * 'LNG' - Liquified natural gas * 'H2' - Hydrogen fuel * 'Ethanol' - Ethyl alcohol as fuel * 'AdBlue' - Diesel exhaust fluid used in vehicles with Selective Catalytic Reduction (SCR) * 'Other' - Other chargepoint types|
|»» ratings|any|false|none|none|
|»» userInterfaceLang|[[userInterfaceLang](#schemauserinterfacelang)]|false|none|Alpha, three characters. Language(s) of the user interface or printed on-site instructions. ISO-639-3 language code|
|»» maxReservation|number(float)|false|none|If a reservation of this charge point is possible, this is the maximum duration the CPO will allow a reservation for (in minutes). Recommendation:- 30 minutes.|
|»» meteringInfo|any|false|none|none|
|»» truckParking|[TruckParkingType](#schematruckparkingtype)|false|none|If trucks can be parked at this location. This value if provided can be used to inform which category of trucks and how many trucks can be parked at this location.|
|»»» lightTruck|integer|true|none|Number of light-duty trucks parking spots.|
|»»» mediumTruck|integer|true|none|Number of medium-duty trucks parking spots|
|»»» heavyTruck|integer|true|none|Number of heavy-duty trucks parking spots.|

#### Enumerated Values

|Property|Value|
|---|---|
|class|networkLogo|
|class|operatorLogo|
|class|ownerLogo|
|class|stationPhoto|
|class|locationPhoto|
|class|entrancePhoto|
|class|otherPhoto|
|class|otherLogo|
|class|otherGraphic|
|class|operatorMap|
|class|operatorPayment|
|class|stationInfo|
|class|surroundingInfo|
|class|ownerHomepage|
|class|feedbackForm|
|class|openingTimes|
|type|entrance|
|type|exit|
|type|access|
|type|ui|
|type|other|
|status|Unknown|
|status|Operative|
|status|Inoperative|
|status|Planned|
|status|Closed|
|status|Unknown|
|status|Operative|
|status|Inoperative|
|status|Planned|
|status|Closed|
|location|on-street|
|location|parking-garage|
|location|underground-garage|
|location|parking-lot|
|location|private|
|location|other|
|location|unknown|
|connectorStandard|Chademo|
|connectorStandard|IEC_62196_T1|
|connectorStandard|IEC_62196_T1_COMBO|
|connectorStandard|IEC_62196_T2|
|connectorStandard|IEC_62196_T2_COMBO|
|connectorStandard|IEC_62196_T3A|
|connectorStandard|IEC_62196_T3C|
|connectorStandard|DOMESTIC_A|
|connectorStandard|DOMESTIC_B|
|connectorStandard|DOMESTIC_C|
|connectorStandard|DOMESTIC_D|
|connectorStandard|DOMESTIC_E|
|connectorStandard|DOMESTIC_F|
|connectorStandard|DOMESTIC_G|
|connectorStandard|DOMESTIC_H|
|connectorStandard|DOMESTIC_I|
|connectorStandard|DOMESTIC_J|
|connectorStandard|DOMESTIC_K|
|connectorStandard|DOMESTIC_L|
|connectorStandard|TESLA_R|
|connectorStandard|TESLA_S|
|connectorStandard|IEC_60309_2_single_16|
|connectorStandard|IEC_60309_2_three_16|
|connectorStandard|IEC_60309_2_three_32|
|connectorStandard|IEC_60309_2_three_64|
|connectorStandard|LPG|
|connectorStandard|LNG|
|connectorStandard|CNG|
|connectorStandard|H2|
|connectorStandard|SUPER_95|
|connectorStandard|SUPER_PLUS|
|connectorStandard|SUPER_E10|
|connectorStandard|DIESEL|
|connectorStandard|ETHANOL|
|connectorStandard|ADBLUE|
|connectorFormat|Socket|
|connectorFormat|Cable|
|connectorFormat|Nozzle|
|connectorFormat|Other|
|chargePointType|AC|
|chargePointType|DC|
|chargePointType|Super_95|
|chargePointType|Super_Plus|
|chargePointType|Super_E10|
|chargePointType|Diesel|
|chargePointType|LPG|
|chargePointType|CNG|
|chargePointType|LNG|
|chargePointType|H2|
|chargePointType|Ethanol|
|chargePointType|AdBlue|
|chargePointType|Other|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="ochp-1-5-json-nsp-charge-point-information-exchange-api">NSP: Charge Point Information Exchange API</h1>

Exchange of Charge Point Information between eCHS & NSP

## get__ChargePointList

> Code samples

`GET /ChargePointList`

Allows an NSP to download the charge Point Information from eCHS. (GetChargePointList.req)

<h3 id="get__chargepointlist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pagination|query|[Pagination](#schemapagination)|false|Filter the results updated, starting from the mentioned date and time.|
|CPO-ID|query|[PartnerID](#schemapartnerid)|false|tThe ID of the CPO/CPOs whose ChargePoint information is requested by the NSP. To get ChargePoints from selected partner(s) i.e. CPOs|

> Example responses

> 200 Response

```json
{
  "result": null,
  "chargePointItemInfo": {
    "objectCount": 569,
    "objectSize": "20kB",
    "limit": 100
  },
  "chargePointInfoArray": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}
```

<h3 id="get__chargepointlist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The response from CHS. Successful download of the Roaming Authorisation Lists (GetChargePointList.conf).|[chargePointResponseModel](#schemachargepointresponsemodel)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Data/request has technical errors or One or more ID (EVSE/Contract) were not valid for this user.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Not-authorised to set the data. Wrong username and/password.|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden. No roaming connections set; No own partners connected to this user; Roaming partners have no data.|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None|

<h3 id="get__chargepointlist-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_Pagination">Pagination</h2>
<!-- backwards compatibility -->
<a id="schemapagination"></a>
<a id="schema_Pagination"></a>
<a id="tocSpagination"></a>
<a id="tocspagination"></a>

```json
{
  "dateFrom": "2025-01-01T00:00:00Z",
  "dateTo": "2025-01-01T00:00:00Z",
  "offset": 150,
  "limit": 50
}

```

Allows the users to provide criteria in supported requests to filter the results.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|dateFrom|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|dateTo|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|offset|integer|true|none|The offset of a first object, that the request will return. Default is always zero.|
|limit|integer|true|none|The maximum number of objects that a Get request will return.|

<h2 id="tocS_PartnerID">PartnerID</h2>
<!-- backwards compatibility -->
<a id="schemapartnerid"></a>
<a id="schema_PartnerID"></a>
<a id="tocSpartnerid"></a>
<a id="tocspartnerid"></a>

```json
{
  "partnerID": [
    "DELND"
  ]
}

```

to get data for/from selected partner(s)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|partnerID|[string]|false|none|none|

<h2 id="tocS_ResponseModel">ResponseModel</h2>
<!-- backwards compatibility -->
<a id="schemaresponsemodel"></a>
<a id="schema_ResponseModel"></a>
<a id="tocSresponsemodel"></a>
<a id="tocsresponsemodel"></a>

```json
{
  "result": null,
  "roamingAuthorisationItemInfo": {
    "objectCount": 569,
    "objectSize": "20kB",
    "limit": 100
  },
  "roamingAuthorisationInfoArray": [
    {
      "emtId": {
        "instance": 43,
        "representation": "plain",
        "type": "rfid",
        "subType": "mifareCls"
      },
      "contractId": null,
      "permissions": "AC",
      "printedNumber": 4424,
      "expiryDate": "2025-01-01T00:00:00Z"
    }
  ]
}

```

The response send by CHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|roamingAuthorisationItemInfo|[ItemInfo](#schemaiteminfo)|true|none|This contains the roaming authorisation item info.|
|roamingAuthorisationInfoArray|[[RoamingAuthorisationInfo](#schemaroamingauthorisationinfo)]|true|none|[Contains information about a roaming authorisation card/token.]|

<h2 id="tocS_RequestModel">RequestModel</h2>
<!-- backwards compatibility -->
<a id="schemarequestmodel"></a>
<a id="schema_RequestModel"></a>
<a id="tocSrequestmodel"></a>
<a id="tocsrequestmodel"></a>

```json
{
  "roamingAuthorisationInfoArray": {
    "emtId": {
      "instance": 43,
      "representation": "plain",
      "type": "rfid",
      "subType": "mifareCls"
    },
    "contractId": null,
    "permissions": "AC",
    "printedNumber": 4424,
    "expiryDate": "2025-01-01T00:00:00Z"
  }
}

```

The request send by EMSP for posting Roaming Authorisation Lists.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|roamingAuthorisationInfoArray|[RoamingAuthorisationInfo](#schemaroamingauthorisationinfo)|true|none|Contains information about a roaming authorisation card/token.|

<h2 id="tocS_SingleRoamingResponseModel">SingleRoamingResponseModel</h2>
<!-- backwards compatibility -->
<a id="schemasingleroamingresponsemodel"></a>
<a id="schema_SingleRoamingResponseModel"></a>
<a id="tocSsingleroamingresponsemodel"></a>
<a id="tocssingleroamingresponsemodel"></a>

```json
{
  "result": null,
  "roamingAuthorisationInfo": {
    "emtId": {
      "instance": 43,
      "representation": "plain",
      "type": "rfid",
      "subType": "mifareCls"
    },
    "contractId": null,
    "permissions": "AC",
    "printedNumber": 4424,
    "expiryDate": "2025-01-01T00:00:00Z"
  }
}

```

The response send by CHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|roamingAuthorisationInfo|[RoamingAuthorisationInfo](#schemaroamingauthorisationinfo)|true|none|Contains information about a roaming authorisation card/token.|

<h2 id="tocS_PartialSuccessResponseModel">PartialSuccessResponseModel</h2>
<!-- backwards compatibility -->
<a id="schemapartialsuccessresponsemodel"></a>
<a id="schema_PartialSuccessResponseModel"></a>
<a id="tocSpartialsuccessresponsemodel"></a>
<a id="tocspartialsuccessresponsemodel"></a>

```json
{
  "result": null,
  "refusedRoamingAuthorisationInfo": [
    {
      "emtId": {
        "instance": 43,
        "representation": "plain",
        "type": "rfid",
        "subType": "mifareCls"
      },
      "contractId": null,
      "permissions": "AC",
      "printedNumber": 4424,
      "expiryDate": "2025-01-01T00:00:00Z"
    }
  ]
}

```

The response send by CHS to the EMSP after setting/updating Roaming Authorisation Lists. This response is sent when not all but only part of the lists were only uploaded. The CHS also sends these refused Roaming Authorisation Lists along with the response.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|refusedRoamingAuthorisationInfo|[[RoamingAuthorisationInfo](#schemaroamingauthorisationinfo)]|true|none|[Contains information about a roaming authorisation card/token.]|

<h2 id="tocS_AddCdrRequestModel">AddCdrRequestModel</h2>
<!-- backwards compatibility -->
<a id="schemaaddcdrrequestmodel"></a>
<a id="schema_AddCdrRequestModel"></a>
<a id="tocSaddcdrrequestmodel"></a>
<a id="tocsaddcdrrequestmodel"></a>

```json
{
  "cdrInfoArray": []
}

```

The CDR Info that is send by the CPO to the CHS with the POST CDRs request.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cdrInfoArray|[[./schemas/cdr.yaml#/CDRInfo](#schema./schemas/cdr.yaml#/cdrinfo)]|true|none|none|

<h2 id="tocS_ImplausibleCDRsResponseModel">ImplausibleCDRsResponseModel</h2>
<!-- backwards compatibility -->
<a id="schemaimplausiblecdrsresponsemodel"></a>
<a id="schema_ImplausibleCDRsResponseModel"></a>
<a id="tocSimplausiblecdrsresponsemodel"></a>
<a id="tocsimplausiblecdrsresponsemodel"></a>

```json
{
  "result": null,
  "implausibleCdrsArray": []
}

```

The response send by CHS to the CPO after uploading the Charge detail records. This response is sent when not all CDRs could be successfully added to the Clearing house system. The CHS also sends the list of Implausible/refused CDRs along with the response 'partly'.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|implausibleCdrsArray|[[./schemas/cdr.yaml#/CdrId](#schema./schemas/cdr.yaml#/cdrid)]|true|none|none|

<h2 id="tocS_ConfirmCDRs">ConfirmCDRs</h2>
<!-- backwards compatibility -->
<a id="schemaconfirmcdrs"></a>
<a id="schema_ConfirmCDRs"></a>
<a id="tocSconfirmcdrs"></a>
<a id="tocsconfirmcdrs"></a>

```json
{
  "approved": [
    {
      "cdrId": null,
      "EvseId": null
    }
  ],
  "declined": [
    {
      "cdrId": null,
      "EvseId": null
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|approved|[[Approved](#schemaapproved)]|false|none|[Contains the CdrId and EvseId for CDRs that have been approved by the EMSP.]|
|declined|[[Declined](#schemadeclined)]|false|none|[Contains the CdrId and EvseId for CDRs that have been declined by the EMSP.]|

<h2 id="tocS_refusedIDs">refusedIDs</h2>
<!-- backwards compatibility -->
<a id="schemarefusedids"></a>
<a id="schema_refusedIDs"></a>
<a id="tocSrefusedids"></a>
<a id="tocsrefusedids"></a>

```json
{
  "result": null,
  "refusedcdrIds": []
}

```

This response is sent by the CHS when the EMSP tries to send the list of Approved and/declined CDRs, however not all were  successful due to some reason. The CHS sends the Result value 'partly' and also sends the cdr Ids, whose status could not be uploaded in the CHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|refusedcdrIds|[[./schemas/cdr.yaml#/CdrId](#schema./schemas/cdr.yaml#/cdrid)]|true|none|none|

<h2 id="tocS_ItemInfo">ItemInfo</h2>
<!-- backwards compatibility -->
<a id="schemaiteminfo"></a>
<a id="schema_ItemInfo"></a>
<a id="tocSiteminfo"></a>
<a id="tocsiteminfo"></a>

```json
{
  "objectCount": 569,
  "objectSize": "20kB",
  "limit": 100
}

```

This contains the roaming authorisation item info.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|objectCount|integer|true|none|Total number of objects available in the server system.|
|objectSize|integer|true|none|Object size receive from the server response|
|limit|integer|true|none|Number of objects that are returned.|

<h2 id="tocS_TariffRequestModel">TariffRequestModel</h2>
<!-- backwards compatibility -->
<a id="schematariffrequestmodel"></a>
<a id="schema_TariffRequestModel"></a>
<a id="tocStariffrequestmodel"></a>
<a id="tocstariffrequestmodel"></a>

```json
{
  "tariffInfoArray": [
    {
      "tariffId": "YYABCT01",
      "individualTariff": [
        {
          "currency": null,
          "tariffElement": [
            {
              "priceComponent": {
                "billingItem": "parkingtime",
                "itemPrice": 0.1,
                "stepSize": 0.1
              },
              "tariffRestriction": {
                "regularHours": [
                  {
                    "weekday": 1,
                    "periodBegin": "18:15",
                    "periodEnd": "20:15"
                  }
                ],
                "startDate": "2025-01-01T00:00:00Z",
                "endDate": "2025-01-01T00:00:00Z",
                "minEnergy": 20,
                "maxEnergy": 50,
                "minPower": 0,
                "maxPower": 20,
                "minDuration": 10,
                "maxDuration": 600
              }
            }
          ],
          "recipient": [
            "^A$"
          ]
        }
      ]
    }
  ]
}

```

This contains the tariff information to be updated or added.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tariffInfoArray|[[TariffInfo](#schematariffinfo)]|true|none|[The information on tariff that needs to be added or updated.]|

<h2 id="tocS_TariffResponseModel">TariffResponseModel</h2>
<!-- backwards compatibility -->
<a id="schematariffresponsemodel"></a>
<a id="schema_TariffResponseModel"></a>
<a id="tocStariffresponsemodel"></a>
<a id="tocstariffresponsemodel"></a>

```json
{
  "result": null,
  "TariffInfoArray": [
    {
      "tariffId": "YYABCT01",
      "individualTariff": [
        {
          "currency": null,
          "tariffElement": [
            {
              "priceComponent": {
                "billingItem": "parkingtime",
                "itemPrice": 0.1,
                "stepSize": 0.1
              },
              "tariffRestriction": {
                "regularHours": [
                  {
                    "weekday": 1,
                    "periodBegin": "18:15",
                    "periodEnd": "20:15"
                  }
                ],
                "startDate": "2025-01-01T00:00:00Z",
                "endDate": "2025-01-01T00:00:00Z",
                "minEnergy": 20,
                "maxEnergy": 50,
                "minPower": 0,
                "maxPower": 20,
                "minDuration": 10,
                "maxDuration": 600
              }
            }
          ],
          "recipient": [
            "^A$"
          ]
        }
      ]
    }
  ]
}

```

The response send by CHS to the EMSP for get tariff information request. The CHS sends the tariff information records along with the response 'ok'.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|TariffInfoArray|[[TariffInfo](#schematariffinfo)]|true|none|[The information on tariff that needs to be added or updated.]|

<h2 id="tocS_refusedTariffInfoModel">refusedTariffInfoModel</h2>
<!-- backwards compatibility -->
<a id="schemarefusedtariffinfomodel"></a>
<a id="schema_refusedTariffInfoModel"></a>
<a id="tocSrefusedtariffinfomodel"></a>
<a id="tocsrefusedtariffinfomodel"></a>

```json
{
  "result": null,
  "refusedTariffInfo": [
    {
      "tariffId": "YYABCT01",
      "individualTariff": [
        {
          "currency": null,
          "tariffElement": [
            {
              "priceComponent": {
                "billingItem": "parkingtime",
                "itemPrice": 0.1,
                "stepSize": 0.1
              },
              "tariffRestriction": {
                "regularHours": [
                  {
                    "weekday": 1,
                    "periodBegin": "18:15",
                    "periodEnd": "20:15"
                  }
                ],
                "startDate": "2025-01-01T00:00:00Z",
                "endDate": "2025-01-01T00:00:00Z",
                "minEnergy": 20,
                "maxEnergy": 50,
                "minPower": 0,
                "maxPower": 20,
                "minDuration": 10,
                "maxDuration": 600
              }
            }
          ],
          "recipient": [
            "^A$"
          ]
        }
      ]
    }
  ]
}

```

The response send by CHS to the CPO after uploading/updating the tariff information. This response is sent when not all but only part of the information could only be uploaded/updated. The CHS also sends these refused tariff information records along with the response 'partly'.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|refusedTariffInfo|[[TariffInfo](#schematariffinfo)]|true|none|[The information on tariff that needs to be added or updated.]|

<h2 id="tocS_Approved">Approved</h2>
<!-- backwards compatibility -->
<a id="schemaapproved"></a>
<a id="schema_Approved"></a>
<a id="tocSapproved"></a>
<a id="tocsapproved"></a>

```json
{
  "cdrId": null,
  "EvseId": null
}

```

Contains the CdrId and EvseId for CDRs that have been approved by the EMSP.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cdrId|[./schemas/cdr.yaml#/CdrId](#schema./schemas/cdr.yaml#/cdrid)|false|none|none|
|EvseId|[./schemas/cdr.yaml#/EvseId](#schema./schemas/cdr.yaml#/evseid)|false|none|none|

<h2 id="tocS_Declined">Declined</h2>
<!-- backwards compatibility -->
<a id="schemadeclined"></a>
<a id="schema_Declined"></a>
<a id="tocSdeclined"></a>
<a id="tocsdeclined"></a>

```json
{
  "cdrId": null,
  "EvseId": null
}

```

Contains the CdrId and EvseId for CDRs that have been declined by the EMSP.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cdrId|[./schemas/cdr.yaml#/CdrId](#schema./schemas/cdr.yaml#/cdrid)|false|none|none|
|EvseId|[./schemas/cdr.yaml#/EvseId](#schema./schemas/cdr.yaml#/evseid)|false|none|none|

<h2 id="tocS_TariffInfo">TariffInfo</h2>
<!-- backwards compatibility -->
<a id="schematariffinfo"></a>
<a id="schema_TariffInfo"></a>
<a id="tocStariffinfo"></a>
<a id="tocstariffinfo"></a>

```json
{
  "tariffId": "YYABCT01",
  "individualTariff": [
    {
      "currency": null,
      "tariffElement": [
        {
          "priceComponent": {
            "billingItem": "parkingtime",
            "itemPrice": 0.1,
            "stepSize": 0.1
          },
          "tariffRestriction": {
            "regularHours": [
              {
                "weekday": 1,
                "periodBegin": "18:15",
                "periodEnd": "20:15"
              }
            ],
            "startDate": "2025-01-01T00:00:00Z",
            "endDate": "2025-01-01T00:00:00Z",
            "minEnergy": 20,
            "maxEnergy": 50,
            "minPower": 0,
            "maxPower": 20,
            "minDuration": 10,
            "maxDuration": 600
          }
        }
      ],
      "recipient": [
        "^A$"
      ]
    }
  ]
}

```

The information on tariff that needs to be added or updated.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tariffId|[TariffId](#schematariffid)|true|none|The tariff-ID follows a similar syntax to that of contract- and EVSE-IDs. The The Operator-ID is followed by a 'T' that signifies a tariff and a unique instance of up to 30 characters. The max. length allowed it string(36). Alphanumeric. Identifies a tariff. Unique within one EVSE Operator. Must begin with the Operator-ID, without separators.|
|individualTariff|[[IndividualTariffType](#schemaindividualtarifftype)]|false|none|[Contains multiple individual tariffs dependant on intended recipient. Element describing an individual tariff for a specific recipient. One default tariff without recipients must be provided. When there are more than 1 element, the first tariff element to match the condition is used.]|

<h2 id="tocS_RoamingAuthorisationInfo">RoamingAuthorisationInfo</h2>
<!-- backwards compatibility -->
<a id="schemaroamingauthorisationinfo"></a>
<a id="schema_RoamingAuthorisationInfo"></a>
<a id="tocSroamingauthorisationinfo"></a>
<a id="tocsroamingauthorisationinfo"></a>

```json
{
  "emtId": {
    "instance": 43,
    "representation": "plain",
    "type": "rfid",
    "subType": "mifareCls"
  },
  "contractId": null,
  "permissions": "AC",
  "printedNumber": 4424,
  "expiryDate": "2025-01-01T00:00:00Z"
}

```

Contains information about a roaming authorisation card/token.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|emtId|[EmtId](#schemaemtid)|true|none|The authorisation tokens are defined according to the specification of the EMT-ID (Token ID). Each token consists of a token instance which holds the payload and at least the token type. The sub-type is for further specification of the general token type.|
|contractId|[./schemas/cdr.yaml#/ContractId](#schema./schemas/cdr.yaml#/contractid)|true|none|none|
|permissions|[PermissionsType](#schemapermissionstype)|true|none|RoamingAuthorisationInfo class is extended by the attribute permissions. The PermissionsType (enum) can be set to multiple options. Feature will help EMPs to have better structured and organized customer portfolio. * 'AC' - Alternating current * 'DC' - Direct current * 'CNG' -  Compressed natural gas * 'LNG' - Liquified natural gas * 'Fuel' - Fuel * 'H2' - Hydrogen * 'Ethanol' - Ethyl alcohol as fuel * 'Other' - Other fuel types|
|printedNumber|string|false|none|Might be used for manual authorisation|
|expiryDate|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_EmtId">EmtId</h2>
<!-- backwards compatibility -->
<a id="schemaemtid"></a>
<a id="schema_EmtId"></a>
<a id="tocSemtid"></a>
<a id="tocsemtid"></a>

```json
{
  "instance": 43,
  "representation": "plain",
  "type": "rfid",
  "subType": "mifareCls"
}

```

The authorisation tokens are defined according to the specification of the EMT-ID (Token ID). Each token consists of a token instance which holds the payload and at least the token type. The sub-type is for further specification of the general token type.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|instance|string|true|none|Specification according to the token type|
|representation|[tokenRepresentation](#schematokenrepresentation)|true|none|The token instance may be represented by its hash value (hexadecimal representation of the hash value). This specifies in which representation the token instance is set. * 'plain' - The token instance is represented in plain text. (default) * 'sha-160' - The token instance is represented in its 160bit SHA1 hash in 40 hexadecimal digits. * 'sha-256' - The token instance is represented in its 256bit SHA2 hash in 64 hexadecimal digits.|
|type|[tokenType](#schematokentype)|true|none|The type of the supplied instance for basic filtering. The remote token type is only being used in the CDR of a remotely started charging process. Tokens with type remote shall not be included in a whitelist. * 'rfid' - All kinds of RFID-Cards. Field tokenInstance holds the hexadecimal representation of the card's UID, Byte order- big endian, no zero-filling. * 'remote' - All means of remote authentication through the backend. Field tokenInstance holds a reference to the remote authorization or session. In case of a OCHPdirect authorization the directId. * '15118' - All authentication means defined by ISO/IEC 15118 except RFID-cards. * 'other' - To accommodate the other energy sources incorporated into the protocol.|
|subType|[tokenSubType](#schematokensubtype)|false|none|The exact type of the supplied instance for referencing purpose. * 'mifareCls' - Mifare Classic Card * 'mifareDes' - Mifare Desfire Card * 'calypso' - Calypso Card|

<h2 id="tocS_PermissionsType">PermissionsType</h2>
<!-- backwards compatibility -->
<a id="schemapermissionstype"></a>
<a id="schema_PermissionsType"></a>
<a id="tocSpermissionstype"></a>
<a id="tocspermissionstype"></a>

```json
"AC"

```

RoamingAuthorisationInfo class is extended by the attribute permissions. The PermissionsType (enum) can be set to multiple options. Feature will help EMPs to have better structured and organized customer portfolio. * 'AC' - Alternating current * 'DC' - Direct current * 'CNG' -  Compressed natural gas * 'LNG' - Liquified natural gas * 'Fuel' - Fuel * 'H2' - Hydrogen * 'Ethanol' - Ethyl alcohol as fuel * 'Other' - Other fuel types

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|RoamingAuthorisationInfo class is extended by the attribute permissions. The PermissionsType (enum) can be set to multiple options. Feature will help EMPs to have better structured and organized customer portfolio. * 'AC' - Alternating current * 'DC' - Direct current * 'CNG' -  Compressed natural gas * 'LNG' - Liquified natural gas * 'Fuel' - Fuel * 'H2' - Hydrogen * 'Ethanol' - Ethyl alcohol as fuel * 'Other' - Other fuel types|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AC|
|*anonymous*|DC|
|*anonymous*|CNG|
|*anonymous*|LNG|
|*anonymous*|Fuel|
|*anonymous*|H2|
|*anonymous*|Ethanol|
|*anonymous*|Other|

<h2 id="tocS_DateTimeType">DateTimeType</h2>
<!-- backwards compatibility -->
<a id="schemadatetimetype"></a>
<a id="schema_DateTimeType"></a>
<a id="tocSdatetimetype"></a>
<a id="tocsdatetimetype"></a>

```json
"2025-01-01T00:00:00Z"

```

Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_tokenRepresentation">tokenRepresentation</h2>
<!-- backwards compatibility -->
<a id="schematokenrepresentation"></a>
<a id="schema_tokenRepresentation"></a>
<a id="tocStokenrepresentation"></a>
<a id="tocstokenrepresentation"></a>

```json
"plain"

```

The token instance may be represented by its hash value (hexadecimal representation of the hash value). This specifies in which representation the token instance is set. * 'plain' - The token instance is represented in plain text. (default) * 'sha-160' - The token instance is represented in its 160bit SHA1 hash in 40 hexadecimal digits. * 'sha-256' - The token instance is represented in its 256bit SHA2 hash in 64 hexadecimal digits.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The token instance may be represented by its hash value (hexadecimal representation of the hash value). This specifies in which representation the token instance is set. * 'plain' - The token instance is represented in plain text. (default) * 'sha-160' - The token instance is represented in its 160bit SHA1 hash in 40 hexadecimal digits. * 'sha-256' - The token instance is represented in its 256bit SHA2 hash in 64 hexadecimal digits.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|plain|
|*anonymous*|sha-160|
|*anonymous*|sha-256|

<h2 id="tocS_tokenType">tokenType</h2>
<!-- backwards compatibility -->
<a id="schematokentype"></a>
<a id="schema_tokenType"></a>
<a id="tocStokentype"></a>
<a id="tocstokentype"></a>

```json
"rfid"

```

The type of the supplied instance for basic filtering. The remote token type is only being used in the CDR of a remotely started charging process. Tokens with type remote shall not be included in a whitelist. * 'rfid' - All kinds of RFID-Cards. Field tokenInstance holds the hexadecimal representation of the card's UID, Byte order- big endian, no zero-filling. * 'remote' - All means of remote authentication through the backend. Field tokenInstance holds a reference to the remote authorization or session. In case of a OCHPdirect authorization the directId. * '15118' - All authentication means defined by ISO/IEC 15118 except RFID-cards. * 'other' - To accommodate the other energy sources incorporated into the protocol.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The type of the supplied instance for basic filtering. The remote token type is only being used in the CDR of a remotely started charging process. Tokens with type remote shall not be included in a whitelist. * 'rfid' - All kinds of RFID-Cards. Field tokenInstance holds the hexadecimal representation of the card's UID, Byte order- big endian, no zero-filling. * 'remote' - All means of remote authentication through the backend. Field tokenInstance holds a reference to the remote authorization or session. In case of a OCHPdirect authorization the directId. * '15118' - All authentication means defined by ISO/IEC 15118 except RFID-cards. * 'other' - To accommodate the other energy sources incorporated into the protocol.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|rfid|
|*anonymous*|remote|
|*anonymous*|15118|
|*anonymous*|other|

<h2 id="tocS_tokenSubType">tokenSubType</h2>
<!-- backwards compatibility -->
<a id="schematokensubtype"></a>
<a id="schema_tokenSubType"></a>
<a id="tocStokensubtype"></a>
<a id="tocstokensubtype"></a>

```json
"mifareCls"

```

The exact type of the supplied instance for referencing purpose. * 'mifareCls' - Mifare Classic Card * 'mifareDes' - Mifare Desfire Card * 'calypso' - Calypso Card

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The exact type of the supplied instance for referencing purpose. * 'mifareCls' - Mifare Classic Card * 'mifareDes' - Mifare Desfire Card * 'calypso' - Calypso Card|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|mifareCls|
|*anonymous*|mifareDes|
|*anonymous*|calypso|

<h2 id="tocS_CDRsConfirmation">CDRsConfirmation</h2>
<!-- backwards compatibility -->
<a id="schemacdrsconfirmation"></a>
<a id="schema_CDRsConfirmation"></a>
<a id="tocScdrsconfirmation"></a>
<a id="tocscdrsconfirmation"></a>

```json
{
  "result": null,
  "cdrsItemInfo": {
    "objectCount": 569,
    "objectSize": "20kB",
    "limit": 100
  },
  "cdrInfoArray": []
}

```

The response send by CHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|cdrsItemInfo|[ItemInfo](#schemaiteminfo)|true|none|This contains the roaming authorisation item info.|
|cdrInfoArray|[[./schemas/cdr.yaml#/CDRInfo](#schema./schemas/cdr.yaml#/cdrinfo)]|true|none|none|

<h2 id="tocS_CDRCheck">CDRCheck</h2>
<!-- backwards compatibility -->
<a id="schemacdrcheck"></a>
<a id="schema_CDRCheck"></a>
<a id="tocScdrcheck"></a>
<a id="tocscdrcheck"></a>

```json
{
  "result": null,
  "cdrInfoArray": []
}

```

The response send by CHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|cdrInfoArray|[[./schemas/cdr.yaml#/CDRInfo](#schema./schemas/cdr.yaml#/cdrinfo)]|true|none|none|

<h2 id="tocS_chargePointType">chargePointType</h2>
<!-- backwards compatibility -->
<a id="schemachargepointtype"></a>
<a id="schema_chargePointType"></a>
<a id="tocSchargepointtype"></a>
<a id="tocschargepointtype"></a>

```json
"AC"

```

The chargePointType is extended from AC and DC to the options mentioned below. The enhancement enables the CPOs to define the CPTs more precisely and offer diversified services. * 'AC' - Alternating current * 'DC' - Direct current * 'Super_95' - Premium unleaded petrol having octance rating of 95 * 'Super_Plus' - High octane rating fuel containing 5-10% of ethanol * 'Super_E10' - Petrol fuel with an ethanol content of up to 10 percent and an octane rating of at least 95 * 'Diesel' - Liquid fuel used in diesel engines, whose ignition takes place without any spark * 'LPG' - Liquefied petroleum gas * 'CNG' - Compressed natural gas * 'LNG' - Liquified natural gas * 'H2' - Hydrogen fuel * 'Ethanol' - Ethyl alcohol as fuel * 'AdBlue' - Diesel exhaust fluid used in vehicles with Selective Catalytic Reduction (SCR) * 'Other' - Other chargepoint types

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The chargePointType is extended from AC and DC to the options mentioned below. The enhancement enables the CPOs to define the CPTs more precisely and offer diversified services. * 'AC' - Alternating current * 'DC' - Direct current * 'Super_95' - Premium unleaded petrol having octance rating of 95 * 'Super_Plus' - High octane rating fuel containing 5-10% of ethanol * 'Super_E10' - Petrol fuel with an ethanol content of up to 10 percent and an octane rating of at least 95 * 'Diesel' - Liquid fuel used in diesel engines, whose ignition takes place without any spark * 'LPG' - Liquefied petroleum gas * 'CNG' - Compressed natural gas * 'LNG' - Liquified natural gas * 'H2' - Hydrogen fuel * 'Ethanol' - Ethyl alcohol as fuel * 'AdBlue' - Diesel exhaust fluid used in vehicles with Selective Catalytic Reduction (SCR) * 'Other' - Other chargepoint types|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|AC|
|*anonymous*|DC|
|*anonymous*|Super_95|
|*anonymous*|Super_Plus|
|*anonymous*|Super_E10|
|*anonymous*|Diesel|
|*anonymous*|LPG|
|*anonymous*|CNG|
|*anonymous*|LNG|
|*anonymous*|H2|
|*anonymous*|Ethanol|
|*anonymous*|AdBlue|
|*anonymous*|Other|

<h2 id="tocS_ConnectorType">ConnectorType</h2>
<!-- backwards compatibility -->
<a id="schemaconnectortype"></a>
<a id="schema_ConnectorType"></a>
<a id="tocSconnectortype"></a>
<a id="tocsconnectortype"></a>

```json
{
  "connectorStandard": "Chademo",
  "connectorFormat": "Socket",
  "tariffId": "YYABCT01"
}

```

Defines a power outlet at an EVSE in terms of its connector standard and format (socket/cable)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|connectorStandard|[ConnectorStandardType](#schemaconnectorstandardtype)|true|none|The socket or plug standard of the charging point * 'Chademo'- The connector type is CHAdeMO, DC * 'IEC_62196_T1'-   IEC 62196 Type 1 "SAE J1772" * 'IEC_62196_T1_COMBO'- Combo Type 1 based, DC * 'IEC_62196_T2'-   IEC 62196 Type 2 "Mennekes" * 'IEC_62196_T2_COMBO' - Combo Type 2 based, DC * 'IEC_62196_T3A' IEC 62196 Type 3A * 'IEC_62196_T3C'  IEC 62196 Type 3C "Scame" * 'DOMESTIC_A' Standard/Domestic household, type "A", NEMA 1-15, 2 pins * 'DOMESTIC_B' Standard/Domestic household, type "B", NEMA 5-15, 3 pins * 'DOMESTIC_C' Standard/Domestic household, type "C", CEE 7/17, 2 pins * 'DOMESTIC_D' Standard/Domestic household, type "D", 3 pin * 'DOMESTIC_E' Standard/Domestic household, type "E", CEE 7/5 3 pins * 'DOMESTIC_F' Standard/Domestic household, type "F", CEE 7/4, Schuko, 3 pins * 'DOMESTIC_G' Standard/Domestic household, type "G", BS 1363, Commonwealth, 3 pins * 'DOMESTIC_H' Standard/Domestic household, type "H", SI-32, 3 pins * 'DOMESTIC_I' Standard/Domestic household, type "I", AS 3112, 3 pins * 'DOMESTIC_J'  Standard/Domestic household, type "J", SEV 1011, 3 pins * 'DOMESTIC_K' Standard/Domestic household, type "K", DS 60884-2-D1, 3 pins * 'DOMESTIC_L'  Standard/Domestic household, type "L", CEI 23-16-VII, 3 pins * 'TESLA_R' Tesla Connector "Roadster"-type (round, 4 pin) * 'TESLA_S' Tesla Connector "Model-S"-type (oval, 5 pin) * 'IEC_60309_2_single_16'IEC 60309-2 Industrial Connector single phase 16 Amperes (usually blue) * 'IEC_60309_2_three_16'   IEC 60309-2 Industrial Connector three phase 16 Amperes (usually red) * 'IEC_60309_2_three_32' IEC 60309-2 Industrial Connector three phase 32 Amperes (usually red) * 'IEC_60309_2_three_64' IEC 60309-2 Industrial Connector three phase 64 Amperes (usually red) * 'LPG  ' ACME, DISH, Bajonett, Euronozzle * 'LNG' Universal * 'CNG' NGV1, NGV2 * 'H2' SAE J2601 * 'SUPER_95' Universal * 'SUPER_PLUS' Universal * 'SUPER_E10' Universal * 'DIESEL'  Universal * 'ETHANOL'  Universal * 'ADBLUE' Universal|
|connectorFormat|[ConnectorFormatType](#schemaconnectorformattype)|true|none|The format of the connector, whether it is a socket or a plug. * 'Socket' - The connector is a socket; the EV user needs to bring a fitting plug/cable. * 'Cable'- The connector is an attached cable; the EV users car needs to have a corresponding   inlet. * 'Nozzle'- The connector is a nozzle; used normally at conventional fuel stations. * 'Other'- The connector is of another type, like a nozzle with an attached hose.|
|tariffId|[TariffId](#schematariffid)|false|none|The tariff-ID follows a similar syntax to that of contract- and EVSE-IDs. The The Operator-ID is followed by a 'T' that signifies a tariff and a unique instance of up to 30 characters. The max. length allowed it string(36). Alphanumeric. Identifies a tariff. Unique within one EVSE Operator. Must begin with the Operator-ID, without separators.|

<h2 id="tocS_ConnectorStandardType">ConnectorStandardType</h2>
<!-- backwards compatibility -->
<a id="schemaconnectorstandardtype"></a>
<a id="schema_ConnectorStandardType"></a>
<a id="tocSconnectorstandardtype"></a>
<a id="tocsconnectorstandardtype"></a>

```json
"Chademo"

```

The socket or plug standard of the charging point * 'Chademo'- The connector type is CHAdeMO, DC * 'IEC_62196_T1'-   IEC 62196 Type 1 "SAE J1772" * 'IEC_62196_T1_COMBO'- Combo Type 1 based, DC * 'IEC_62196_T2'-   IEC 62196 Type 2 "Mennekes" * 'IEC_62196_T2_COMBO' - Combo Type 2 based, DC * 'IEC_62196_T3A' IEC 62196 Type 3A * 'IEC_62196_T3C'  IEC 62196 Type 3C "Scame" * 'DOMESTIC_A' Standard/Domestic household, type "A", NEMA 1-15, 2 pins * 'DOMESTIC_B' Standard/Domestic household, type "B", NEMA 5-15, 3 pins * 'DOMESTIC_C' Standard/Domestic household, type "C", CEE 7/17, 2 pins * 'DOMESTIC_D' Standard/Domestic household, type "D", 3 pin * 'DOMESTIC_E' Standard/Domestic household, type "E", CEE 7/5 3 pins * 'DOMESTIC_F' Standard/Domestic household, type "F", CEE 7/4, Schuko, 3 pins * 'DOMESTIC_G' Standard/Domestic household, type "G", BS 1363, Commonwealth, 3 pins * 'DOMESTIC_H' Standard/Domestic household, type "H", SI-32, 3 pins * 'DOMESTIC_I' Standard/Domestic household, type "I", AS 3112, 3 pins * 'DOMESTIC_J'  Standard/Domestic household, type "J", SEV 1011, 3 pins * 'DOMESTIC_K' Standard/Domestic household, type "K", DS 60884-2-D1, 3 pins * 'DOMESTIC_L'  Standard/Domestic household, type "L", CEI 23-16-VII, 3 pins * 'TESLA_R' Tesla Connector "Roadster"-type (round, 4 pin) * 'TESLA_S' Tesla Connector "Model-S"-type (oval, 5 pin) * 'IEC_60309_2_single_16'IEC 60309-2 Industrial Connector single phase 16 Amperes (usually blue) * 'IEC_60309_2_three_16'   IEC 60309-2 Industrial Connector three phase 16 Amperes (usually red) * 'IEC_60309_2_three_32' IEC 60309-2 Industrial Connector three phase 32 Amperes (usually red) * 'IEC_60309_2_three_64' IEC 60309-2 Industrial Connector three phase 64 Amperes (usually red) * 'LPG  ' ACME, DISH, Bajonett, Euronozzle * 'LNG' Universal * 'CNG' NGV1, NGV2 * 'H2' SAE J2601 * 'SUPER_95' Universal * 'SUPER_PLUS' Universal * 'SUPER_E10' Universal * 'DIESEL'  Universal * 'ETHANOL'  Universal * 'ADBLUE' Universal

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The socket or plug standard of the charging point * 'Chademo'- The connector type is CHAdeMO, DC * 'IEC_62196_T1'-   IEC 62196 Type 1 "SAE J1772" * 'IEC_62196_T1_COMBO'- Combo Type 1 based, DC * 'IEC_62196_T2'-   IEC 62196 Type 2 "Mennekes" * 'IEC_62196_T2_COMBO' - Combo Type 2 based, DC * 'IEC_62196_T3A' IEC 62196 Type 3A * 'IEC_62196_T3C'  IEC 62196 Type 3C "Scame" * 'DOMESTIC_A' Standard/Domestic household, type "A", NEMA 1-15, 2 pins * 'DOMESTIC_B' Standard/Domestic household, type "B", NEMA 5-15, 3 pins * 'DOMESTIC_C' Standard/Domestic household, type "C", CEE 7/17, 2 pins * 'DOMESTIC_D' Standard/Domestic household, type "D", 3 pin * 'DOMESTIC_E' Standard/Domestic household, type "E", CEE 7/5 3 pins * 'DOMESTIC_F' Standard/Domestic household, type "F", CEE 7/4, Schuko, 3 pins * 'DOMESTIC_G' Standard/Domestic household, type "G", BS 1363, Commonwealth, 3 pins * 'DOMESTIC_H' Standard/Domestic household, type "H", SI-32, 3 pins * 'DOMESTIC_I' Standard/Domestic household, type "I", AS 3112, 3 pins * 'DOMESTIC_J'  Standard/Domestic household, type "J", SEV 1011, 3 pins * 'DOMESTIC_K' Standard/Domestic household, type "K", DS 60884-2-D1, 3 pins * 'DOMESTIC_L'  Standard/Domestic household, type "L", CEI 23-16-VII, 3 pins * 'TESLA_R' Tesla Connector "Roadster"-type (round, 4 pin) * 'TESLA_S' Tesla Connector "Model-S"-type (oval, 5 pin) * 'IEC_60309_2_single_16'IEC 60309-2 Industrial Connector single phase 16 Amperes (usually blue) * 'IEC_60309_2_three_16'   IEC 60309-2 Industrial Connector three phase 16 Amperes (usually red) * 'IEC_60309_2_three_32' IEC 60309-2 Industrial Connector three phase 32 Amperes (usually red) * 'IEC_60309_2_three_64' IEC 60309-2 Industrial Connector three phase 64 Amperes (usually red) * 'LPG  ' ACME, DISH, Bajonett, Euronozzle * 'LNG' Universal * 'CNG' NGV1, NGV2 * 'H2' SAE J2601 * 'SUPER_95' Universal * 'SUPER_PLUS' Universal * 'SUPER_E10' Universal * 'DIESEL'  Universal * 'ETHANOL'  Universal * 'ADBLUE' Universal|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Chademo|
|*anonymous*|IEC_62196_T1|
|*anonymous*|IEC_62196_T1_COMBO|
|*anonymous*|IEC_62196_T2|
|*anonymous*|IEC_62196_T2_COMBO|
|*anonymous*|IEC_62196_T3A|
|*anonymous*|IEC_62196_T3C|
|*anonymous*|DOMESTIC_A|
|*anonymous*|DOMESTIC_B|
|*anonymous*|DOMESTIC_C|
|*anonymous*|DOMESTIC_D|
|*anonymous*|DOMESTIC_E|
|*anonymous*|DOMESTIC_F|
|*anonymous*|DOMESTIC_G|
|*anonymous*|DOMESTIC_H|
|*anonymous*|DOMESTIC_I|
|*anonymous*|DOMESTIC_J|
|*anonymous*|DOMESTIC_K|
|*anonymous*|DOMESTIC_L|
|*anonymous*|TESLA_R|
|*anonymous*|TESLA_S|
|*anonymous*|IEC_60309_2_single_16|
|*anonymous*|IEC_60309_2_three_16|
|*anonymous*|IEC_60309_2_three_32|
|*anonymous*|IEC_60309_2_three_64|
|*anonymous*|LPG|
|*anonymous*|LNG|
|*anonymous*|CNG|
|*anonymous*|H2|
|*anonymous*|SUPER_95|
|*anonymous*|SUPER_PLUS|
|*anonymous*|SUPER_E10|
|*anonymous*|DIESEL|
|*anonymous*|ETHANOL|
|*anonymous*|ADBLUE|

<h2 id="tocS_ConnectorFormatType">ConnectorFormatType</h2>
<!-- backwards compatibility -->
<a id="schemaconnectorformattype"></a>
<a id="schema_ConnectorFormatType"></a>
<a id="tocSconnectorformattype"></a>
<a id="tocsconnectorformattype"></a>

```json
"Socket"

```

The format of the connector, whether it is a socket or a plug. * 'Socket' - The connector is a socket; the EV user needs to bring a fitting plug/cable. * 'Cable'- The connector is an attached cable; the EV users car needs to have a corresponding   inlet. * 'Nozzle'- The connector is a nozzle; used normally at conventional fuel stations. * 'Other'- The connector is of another type, like a nozzle with an attached hose.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The format of the connector, whether it is a socket or a plug. * 'Socket' - The connector is a socket; the EV user needs to bring a fitting plug/cable. * 'Cable'- The connector is an attached cable; the EV users car needs to have a corresponding   inlet. * 'Nozzle'- The connector is a nozzle; used normally at conventional fuel stations. * 'Other'- The connector is of another type, like a nozzle with an attached hose.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Socket|
|*anonymous*|Cable|
|*anonymous*|Nozzle|
|*anonymous*|Other|

<h2 id="tocS_TariffId">TariffId</h2>
<!-- backwards compatibility -->
<a id="schematariffid"></a>
<a id="schema_TariffId"></a>
<a id="tocStariffid"></a>
<a id="tocstariffid"></a>

```json
"YYABCT01"

```

The tariff-ID follows a similar syntax to that of contract- and EVSE-IDs. The The Operator-ID is followed by a 'T' that signifies a tariff and a unique instance of up to 30 characters. The max. length allowed it string(36). Alphanumeric. Identifies a tariff. Unique within one EVSE Operator. Must begin with the Operator-ID, without separators.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The tariff-ID follows a similar syntax to that of contract- and EVSE-IDs. The The Operator-ID is followed by a 'T' that signifies a tariff and a unique instance of up to 30 characters. The max. length allowed it string(36). Alphanumeric. Identifies a tariff. Unique within one EVSE Operator. Must begin with the Operator-ID, without separators.|

<h2 id="tocS_BillingItemType">BillingItemType</h2>
<!-- backwards compatibility -->
<a id="schemabillingitemtype"></a>
<a id="schema_BillingItemType"></a>
<a id="tocSbillingitemtype"></a>
<a id="tocsbillingitemtype"></a>

```json
"parkingtime"

```

The billing items for charging periods and tariffs. * 'parkingtime'-  Price for the time of parking. The billingValue represents the time in hours. * 'usagetime'-  Price for the time of EVSE usage. The billingValue represents the time in hours. * 'energy'-  Price for the consumed energy. The billingValue represents the energy in kilowatt-hours. * 'power'-  Price for the used power level. The billingValue represents the maximum power in kilowatts. * 'serviceFee'  General service fee per charging process. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservation'-  One time fee for a reservation of the EVSE. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservationtime'-  Price for the duration of a reservation. The billingValue represents the time in hours. * 'volume' - Price for the quantity used in liter. * 'mass' - Price for the quantity used in kilogram (kg).

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The billing items for charging periods and tariffs. * 'parkingtime'-  Price for the time of parking. The billingValue represents the time in hours. * 'usagetime'-  Price for the time of EVSE usage. The billingValue represents the time in hours. * 'energy'-  Price for the consumed energy. The billingValue represents the energy in kilowatt-hours. * 'power'-  Price for the used power level. The billingValue represents the maximum power in kilowatts. * 'serviceFee'  General service fee per charging process. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservation'-  One time fee for a reservation of the EVSE. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservationtime'-  Price for the duration of a reservation. The billingValue represents the time in hours. * 'volume' - Price for the quantity used in liter. * 'mass' - Price for the quantity used in kilogram (kg).|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|parkingtime|
|*anonymous*|usagetime|
|*anonymous*|energy|
|*anonymous*|power|
|*anonymous*|serviceFee|
|*anonymous*|reservation|
|*anonymous*|reservationtime|
|*anonymous*|volume|
|*anonymous*|mass|

<h2 id="tocS_UpdateStatus">UpdateStatus</h2>
<!-- backwards compatibility -->
<a id="schemaupdatestatus"></a>
<a id="schema_UpdateStatus"></a>
<a id="tocSupdatestatus"></a>
<a id="tocsupdatestatus"></a>

```json
{
  "evse": [
    {
      "evseId": null,
      "major": "available",
      "minor": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "parkingspot": [
    {
      "parkingId": "DELNDP12",
      "status": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "ttl": "2025-01-01T00:00:00Z"
}

```

Update the live status of individual charging stations/individual parking spots in the eCHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|evse|[[EvseStatusType](#schemaevsestatustype)]|false|none|[Specifies the major and minor status of a EVSE.]|
|parkingspot|[[ParkingStatusType](#schemaparkingstatustype)]|false|none|[Specifies the live status of a parking spot.]|
|ttl|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_EvseStatusType">EvseStatusType</h2>
<!-- backwards compatibility -->
<a id="schemaevsestatustype"></a>
<a id="schema_EvseStatusType"></a>
<a id="tocSevsestatustype"></a>
<a id="tocsevsestatustype"></a>

```json
{
  "evseId": null,
  "major": "available",
  "minor": "available",
  "ttl": "2025-01-01T00:00:00Z"
}

```

Specifies the major and minor status of a EVSE.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|evseId|[./schemas/cdr.yaml#/EvseId](#schema./schemas/cdr.yaml#/evseid)|true|none|none|
|major|[MajorType](#schemamajortype)|true|none|The major status type reflects the overall status of the EVSE. * 'available' -  the EVSE is able to start a new charging process * 'not-available' -  at the moment no new charging process may be started * 'unknown' -  the current status of the EVSE is not known|
|minor|[MinorType](#schemaminortype)|false|none|The optional minor status type reflects the detailed status of the EVSE in addition to the major status. For each minor status value a proposed ttl value is given. However, the ttl should only be set to a value other than default if the expected status change is known or can be predicted. * 'available' -  the EVSE is able to start a new charging process * 'reserved' -   the EVSE is able to start a new charging process for limited duration as a future reservation is   present. ttl to be set on the start of the reservation when in future or to the end of the reservation else * 'charging' - the EVSE is in use. ttl to be set on the expected end of the charging process * 'blocked' -  the EVSE not accessible because of a physical barrier, i.e. a car * 'outoforder' - the EVSE is currently out of order. ttl to be set to the expected re-enabling|
|ttl|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_ParkingStatusType">ParkingStatusType</h2>
<!-- backwards compatibility -->
<a id="schemaparkingstatustype"></a>
<a id="schema_ParkingStatusType"></a>
<a id="tocSparkingstatustype"></a>
<a id="tocsparkingstatustype"></a>

```json
{
  "parkingId": "DELNDP12",
  "status": "available",
  "ttl": "2025-01-01T00:00:00Z"
}

```

Specifies the live status of a parking spot.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|parkingId|[ParkingId](#schemaparkingid)|true|none|The parking-ID follows a similar syntax to that of contract- and EVSE-IDs. The PSO-ID is followed by a 'P' that signifies a tariff and a unique instance of up to 30 characters.|
|status|[MajorType](#schemamajortype)|true|none|The major status type reflects the overall status of the EVSE. * 'available' -  the EVSE is able to start a new charging process * 'not-available' -  at the moment no new charging process may be started * 'unknown' -  the current status of the EVSE is not known|
|ttl|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_MajorType">MajorType</h2>
<!-- backwards compatibility -->
<a id="schemamajortype"></a>
<a id="schema_MajorType"></a>
<a id="tocSmajortype"></a>
<a id="tocsmajortype"></a>

```json
"available"

```

The major status type reflects the overall status of the EVSE. * 'available' -  the EVSE is able to start a new charging process * 'not-available' -  at the moment no new charging process may be started * 'unknown' -  the current status of the EVSE is not known

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The major status type reflects the overall status of the EVSE. * 'available' -  the EVSE is able to start a new charging process * 'not-available' -  at the moment no new charging process may be started * 'unknown' -  the current status of the EVSE is not known|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|available|
|*anonymous*|not-available|
|*anonymous*|unknown|

<h2 id="tocS_MinorType">MinorType</h2>
<!-- backwards compatibility -->
<a id="schemaminortype"></a>
<a id="schema_MinorType"></a>
<a id="tocSminortype"></a>
<a id="tocsminortype"></a>

```json
"available"

```

The optional minor status type reflects the detailed status of the EVSE in addition to the major status. For each minor status value a proposed ttl value is given. However, the ttl should only be set to a value other than default if the expected status change is known or can be predicted. * 'available' -  the EVSE is able to start a new charging process * 'reserved' -   the EVSE is able to start a new charging process for limited duration as a future reservation is   present. ttl to be set on the start of the reservation when in future or to the end of the reservation else * 'charging' - the EVSE is in use. ttl to be set on the expected end of the charging process * 'blocked' -  the EVSE not accessible because of a physical barrier, i.e. a car * 'outoforder' - the EVSE is currently out of order. ttl to be set to the expected re-enabling

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The optional minor status type reflects the detailed status of the EVSE in addition to the major status. For each minor status value a proposed ttl value is given. However, the ttl should only be set to a value other than default if the expected status change is known or can be predicted. * 'available' -  the EVSE is able to start a new charging process * 'reserved' -   the EVSE is able to start a new charging process for limited duration as a future reservation is   present. ttl to be set on the start of the reservation when in future or to the end of the reservation else * 'charging' - the EVSE is in use. ttl to be set on the expected end of the charging process * 'blocked' -  the EVSE not accessible because of a physical barrier, i.e. a car * 'outoforder' - the EVSE is currently out of order. ttl to be set to the expected re-enabling|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|available|
|*anonymous*|reserved|
|*anonymous*|charging|
|*anonymous*|blocked|
|*anonymous*|outoforder|

<h2 id="tocS_statusType">statusType</h2>
<!-- backwards compatibility -->
<a id="schemastatustype"></a>
<a id="schema_statusType"></a>
<a id="tocSstatustype"></a>
<a id="tocsstatustype"></a>

```json
"evse"

```

When the statusType is defined as combined, the CHS will return values for all EVSEs of all EVSE Operators there is a valid roaming connection to, regardless of whether there is additional parking status information for all of them.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|When the statusType is defined as combined, the CHS will return values for all EVSEs of all EVSE Operators there is a valid roaming connection to, regardless of whether there is additional parking status information for all of them.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|evse|
|*anonymous*|parking|
|*anonymous*|combined|

<h2 id="tocS_StatusConfirmation">StatusConfirmation</h2>
<!-- backwards compatibility -->
<a id="schemastatusconfirmation"></a>
<a id="schema_StatusConfirmation"></a>
<a id="tocSstatusconfirmation"></a>
<a id="tocsstatusconfirmation"></a>

```json
{
  "evse": [
    {
      "evseId": null,
      "major": "available",
      "minor": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "parking": [
    {
      "parkingId": "DELNDP12",
      "status": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ],
  "combined": [
    {
      "evseId": null,
      "major": "available",
      "minor": "available",
      "ttl": "2025-01-01T00:00:00Z"
    }
  ]
}

```

eCHS response to the Get Status request from NSP.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|evse|[[EvseStatusType](#schemaevsestatustype)]|false|none|This contains one EVSE ID with the current status represented in a major part and a minor part.Status values for all EVSE as sent to the eCHS by the EVSE operator.|
|parking|[[ParkingStatusType](#schemaparkingstatustype)]|false|none|This contains one parking spot ID with the current status. Status values for all parking spots as sent to the eCHS by the parking spot operator.|
|combined|[[EvseStatusType](#schemaevsestatustype)]|false|none|This contains one EVSE ID status including the parking spot status (if applicable). Status values for all EVSE that have been combined with parking status values according to static POI data.|

<h2 id="tocS_IndividualTariffType">IndividualTariffType</h2>
<!-- backwards compatibility -->
<a id="schemaindividualtarifftype"></a>
<a id="schema_IndividualTariffType"></a>
<a id="tocSindividualtarifftype"></a>
<a id="tocsindividualtarifftype"></a>

```json
{
  "currency": null,
  "tariffElement": [
    {
      "priceComponent": {
        "billingItem": "parkingtime",
        "itemPrice": 0.1,
        "stepSize": 0.1
      },
      "tariffRestriction": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "startDate": "2025-01-01T00:00:00Z",
        "endDate": "2025-01-01T00:00:00Z",
        "minEnergy": 20,
        "maxEnergy": 50,
        "minPower": 0,
        "maxPower": 20,
        "minDuration": 10,
        "maxDuration": 600
      }
    }
  ],
  "recipient": [
    "^A$"
  ]
}

```

Contains multiple individual tariffs dependant on intended recipient. Element describing an individual tariff for a specific recipient. One default tariff without recipients must be provided. When there are more than 1 element, the first tariff element to match the condition is used.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|currency|[./schemas/generic.yaml#/Currency](#schema./schemas/generic.yaml#/currency)|true|none|none|
|tariffElement|[[TariffElementType](#schematariffelementtype)]|true|none|List of tariff elements. Contains information about the pricing structure of the tariff element.|
|recipient|[[recipient](#schemarecipient)]|false|none|Provider-IDs of the intended recipients for this tariff. If no recipient is provided, this individual tariff is considered the default tariff.|

<h2 id="tocS_TariffElementType">TariffElementType</h2>
<!-- backwards compatibility -->
<a id="schematariffelementtype"></a>
<a id="schema_TariffElementType"></a>
<a id="tocStariffelementtype"></a>
<a id="tocstariffelementtype"></a>

```json
{
  "priceComponent": {
    "billingItem": "parkingtime",
    "itemPrice": 0.1,
    "stepSize": 0.1
  },
  "tariffRestriction": {
    "regularHours": [
      {
        "weekday": 1,
        "periodBegin": "18:15",
        "periodEnd": "20:15"
      }
    ],
    "startDate": "2025-01-01T00:00:00Z",
    "endDate": "2025-01-01T00:00:00Z",
    "minEnergy": 20,
    "maxEnergy": 50,
    "minPower": 0,
    "maxPower": 20,
    "minDuration": 10,
    "maxDuration": 600
  }
}

```

List of tariff elements

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|priceComponent|[PriceComponentType](#schemapricecomponenttype)|true|none|Price component defining this TariffElement.|
|tariffRestriction|[TariffRestrictionType](#schematariffrestrictiontype)|true|none|List of tariff restrictions applicable for this TariffElement / PriceComponent.|

<h2 id="tocS_recipient">recipient</h2>
<!-- backwards compatibility -->
<a id="schemarecipient"></a>
<a id="schema_recipient"></a>
<a id="tocSrecipient"></a>
<a id="tocsrecipient"></a>

```json
"^A$"

```

Alphanumeric. Identifies a recipient EMSP according to EMSP-ID without separators. If not provided, tariff element is considered the default tariff for this tariffId. Should never be returned by the CHS (i.e. only part of upload, not download).

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Alphanumeric. Identifies a recipient EMSP according to EMSP-ID without separators. If not provided, tariff element is considered the default tariff for this tariffId. Should never be returned by the CHS (i.e. only part of upload, not download).|

<h2 id="tocS_PriceComponentType">PriceComponentType</h2>
<!-- backwards compatibility -->
<a id="schemapricecomponenttype"></a>
<a id="schema_PriceComponentType"></a>
<a id="tocSpricecomponenttype"></a>
<a id="tocspricecomponenttype"></a>

```json
{
  "billingItem": "parkingtime",
  "itemPrice": 0.1,
  "stepSize": 0.1
}

```

Price component defining this TariffElement.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|billingItem|[BillingItemType](#schemabillingitemtype)|true|none|The billing items for charging periods and tariffs. * 'parkingtime'-  Price for the time of parking. The billingValue represents the time in hours. * 'usagetime'-  Price for the time of EVSE usage. The billingValue represents the time in hours. * 'energy'-  Price for the consumed energy. The billingValue represents the energy in kilowatt-hours. * 'power'-  Price for the used power level. The billingValue represents the maximum power in kilowatts. * 'serviceFee'  General service fee per charging process. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservation'-  One time fee for a reservation of the EVSE. The billingValue represents a multiplier and thus has to be set to "1.0". * 'reservationtime'-  Price for the duration of a reservation. The billingValue represents the time in hours. * 'volume' - Price for the quantity used in liter. * 'mass' - Price for the quantity used in kilogram (kg).|
|itemPrice|number(float)|true|none|price per unit for this tariff dimension (unit according to dimension)|
|stepSize|number(float)|true|none|Minimum amount to be billed. This unit will be billed in this stepSize blocks. For example:- if billingItem is usagetime and stepSize is 0.1, then time will be billed in blocks of 6 minutes, so if 8 minutes is used, 12 minutes (2 blocks of stepSize) will be billed. In case of one-time payments, this is to be set to 1.0.|

<h2 id="tocS_TariffRestrictionType">TariffRestrictionType</h2>
<!-- backwards compatibility -->
<a id="schematariffrestrictiontype"></a>
<a id="schema_TariffRestrictionType"></a>
<a id="tocStariffrestrictiontype"></a>
<a id="tocstariffrestrictiontype"></a>

```json
{
  "regularHours": [
    {
      "weekday": 1,
      "periodBegin": "18:15",
      "periodEnd": "20:15"
    }
  ],
  "startDate": "2025-01-01T00:00:00Z",
  "endDate": "2025-01-01T00:00:00Z",
  "minEnergy": 20,
  "maxEnergy": 50,
  "minPower": 0,
  "maxPower": 20,
  "minDuration": 10,
  "maxDuration": 600
}

```

List of tariff restrictions applicable for this TariffElement / PriceComponent.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|regularHours|[[RegularHoursType](#schemaregularhourstype)]|false|none|Regular hours that this tariff element should be valid for (maximum of 14 entries). If always valid (24/7), don't set (as this is a tariff restriction).|
|startDate|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|endDate|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|minEnergy|number(float)|false|none|Minimum used energy in kWh, for example 20.0, valid from this amount of energy is used|
|maxEnergy|number(float)|false|none|Maximum used energy in kWh, for example 50.0, valid until this amount of energy is used|
|minPower|number(float)|false|none|Minimum power in kW, for example 0.0, valid from this charging speed|
|maxPower|number(float)|false|none|Maximum power in kW, for example 20.0, valid up to this charging speed|
|minDuration|integer|false|none|Minimum duration in seconds, valid for a duration from x seconds|
|maxDuration|integer|false|none|Maximum duration in seconds, valid for a duration from x seconds|

<h2 id="tocS_RegularHoursType">RegularHoursType</h2>
<!-- backwards compatibility -->
<a id="schemaregularhourstype"></a>
<a id="schema_RegularHoursType"></a>
<a id="tocSregularhourstype"></a>
<a id="tocsregularhourstype"></a>

```json
{
  "weekday": 1,
  "periodBegin": "18:15",
  "periodEnd": "20:15"
}

```

Regular recurring operation or access hours. Consecutive days can be combined using weekdayTo, single days can be defined using only weekdayFrom.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|weekday|integer|true|none|Number of day in the week, beginning with Monday (1), ending with Sunday (7).|
|periodBegin|string|true|none|begin of the regular period given in hours:minutes. Must be in 24h format with leading zeros. Example:- '18:15'. Hour/Minute separator:- ":" Regex:- $[$0-2$]$$[$0-9$]$:$[$0-5$]$$[$0-9$]$|
|periodEnd|string|true|none|End of the regular period, syntax as for periodBegin. Must be later than periodBegin.|

<h2 id="tocS_chargePointRequestModel">chargePointRequestModel</h2>
<!-- backwards compatibility -->
<a id="schemachargepointrequestmodel"></a>
<a id="schema_chargePointRequestModel"></a>
<a id="tocSchargepointrequestmodel"></a>
<a id="tocschargepointrequestmodel"></a>

```json
{
  "chargePointInfoArray": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}

```

The request send by CPO to upload Charge Point Information records.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|chargePointInfoArray|[[ChargePointInfo](#schemachargepointinfo)]|true|none|[Contains information about the charge points. Static POI data regarding a charge point / EVSE.]|

<h2 id="tocS_refusedChargePointInfoResponse">refusedChargePointInfoResponse</h2>
<!-- backwards compatibility -->
<a id="schemarefusedchargepointinforesponse"></a>
<a id="schema_refusedChargePointInfoResponse"></a>
<a id="tocSrefusedchargepointinforesponse"></a>
<a id="tocsrefusedchargepointinforesponse"></a>

```json
{
  "result": null,
  "refusedChargePointInfo": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}

```

The response send by CHS to the CPO after uploading the Charge Point Information Records. This response is sent when not all but only part of the records were only uploaded. The CHS also sends these refused charge point information records along with the response, 'partly'

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|refusedChargePointInfo|[[ChargePointInfo](#schemachargepointinfo)]|true|none|[Contains information about the charge points. Static POI data regarding a charge point / EVSE.]|

<h2 id="tocS_chargePointResponseModel">chargePointResponseModel</h2>
<!-- backwards compatibility -->
<a id="schemachargepointresponsemodel"></a>
<a id="schema_chargePointResponseModel"></a>
<a id="tocSchargepointresponsemodel"></a>
<a id="tocschargepointresponsemodel"></a>

```json
{
  "result": null,
  "chargePointItemInfo": {
    "objectCount": 569,
    "objectSize": "20kB",
    "limit": 100
  },
  "chargePointInfoArray": [
    {
      "evseId": null,
      "evseDescription": "string",
      "locationId": "^A$",
      "timeStamp": "2025-01-01T00:00:00Z",
      "locationName": "string",
      "locationNameLang": "^AAA$",
      "images": [
        {
          "uri": "^(http|https|ftp|file):\\/\\/.$",
          "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
          "class": "networkLogo",
          "type": "stri",
          "width": 0,
          "height": 0
        }
      ],
      "relatedResource": [
        {
          "uri": "^(http|https):\\/\\/.$",
          "class": "operatorMap"
        }
      ],
      "chargePointAddress": null,
      "chargePointLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965."
      },
      "relatedLocation": {
        "lat": "50.770774.",
        "lon": "-126.104965.",
        "name": "string",
        "type": "entrance"
      },
      "timeZone": "Europe/Zurich",
      "openingTimes": {
        "regularHours": [
          {
            "weekday": 1,
            "periodBegin": "18:15",
            "periodEnd": "20:15"
          }
        ],
        "twentyfourseven": true,
        "closedCharging": true,
        "exceptionalOpenings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ],
        "exceptionalClosings": [
          {
            "periodBegin": "2025-01-01T00:00:00Z",
            "peridoEnd": "2025-01-01T00:00:00Z"
          }
        ]
      },
      "status": "Unknown",
      "statusSchedule": [
        {
          "startDate": "2025-01-01T00:00:00Z",
          "endDate": "2025-01-01T00:00:00Z",
          "status": "Unknown"
        }
      ],
      "telephoneNumber": "^0$",
      "location": "on-street",
      "parkingSpot": [
        {
          "parkingId": "DELNDP12",
          "restriction": [
            "evonly"
          ],
          "floorlevel": -2,
          "parkingSpotNumber": 10
        }
      ],
      "restriction": [
        "evonly"
      ],
      "authMethods": [
        "Public"
      ],
      "connectors": [
        {
          "connectorStandard": "Chademo",
          "connectorFormat": "Socket",
          "tariffId": "YYABCT01"
        }
      ],
      "chargePointType": "AC",
      "ratings": null,
      "userInterfaceLang": [
        "^AAA$"
      ],
      "maxReservation": 0,
      "meteringInfo": null,
      "truckParking": {
        "lightTruck": 0,
        "mediumTruck": 0,
        "heavyTruck": 0
      }
    }
  ]
}

```

The response send by the eCHS.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|result|[./schemas/result.yaml#/Result](#schema./schemas/result.yaml#/result)|true|none|none|
|chargePointItemInfo|[ItemInfo](#schemaiteminfo)|true|none|This contains the roaming authorisation item info.|
|chargePointInfoArray|[[ChargePointInfo](#schemachargepointinfo)]|true|none|[Contains information about the charge points. Static POI data regarding a charge point / EVSE.]|

<h2 id="tocS_ChargePointInfo">ChargePointInfo</h2>
<!-- backwards compatibility -->
<a id="schemachargepointinfo"></a>
<a id="schema_ChargePointInfo"></a>
<a id="tocSchargepointinfo"></a>
<a id="tocschargepointinfo"></a>

```json
{
  "evseId": null,
  "evseDescription": "string",
  "locationId": "^A$",
  "timeStamp": "2025-01-01T00:00:00Z",
  "locationName": "string",
  "locationNameLang": "^AAA$",
  "images": [
    {
      "uri": "^(http|https|ftp|file):\\/\\/.$",
      "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
      "class": "networkLogo",
      "type": "stri",
      "width": 0,
      "height": 0
    }
  ],
  "relatedResource": [
    {
      "uri": "^(http|https):\\/\\/.$",
      "class": "operatorMap"
    }
  ],
  "chargePointAddress": null,
  "chargePointLocation": {
    "lat": "50.770774.",
    "lon": "-126.104965."
  },
  "relatedLocation": {
    "lat": "50.770774.",
    "lon": "-126.104965.",
    "name": "string",
    "type": "entrance"
  },
  "timeZone": "Europe/Zurich",
  "openingTimes": {
    "regularHours": [
      {
        "weekday": 1,
        "periodBegin": "18:15",
        "periodEnd": "20:15"
      }
    ],
    "twentyfourseven": true,
    "closedCharging": true,
    "exceptionalOpenings": [
      {
        "periodBegin": "2025-01-01T00:00:00Z",
        "peridoEnd": "2025-01-01T00:00:00Z"
      }
    ],
    "exceptionalClosings": [
      {
        "periodBegin": "2025-01-01T00:00:00Z",
        "peridoEnd": "2025-01-01T00:00:00Z"
      }
    ]
  },
  "status": "Unknown",
  "statusSchedule": [
    {
      "startDate": "2025-01-01T00:00:00Z",
      "endDate": "2025-01-01T00:00:00Z",
      "status": "Unknown"
    }
  ],
  "telephoneNumber": "^0$",
  "location": "on-street",
  "parkingSpot": [
    {
      "parkingId": "DELNDP12",
      "restriction": [
        "evonly"
      ],
      "floorlevel": -2,
      "parkingSpotNumber": 10
    }
  ],
  "restriction": [
    "evonly"
  ],
  "authMethods": [
    "Public"
  ],
  "connectors": [
    {
      "connectorStandard": "Chademo",
      "connectorFormat": "Socket",
      "tariffId": "YYABCT01"
    }
  ],
  "chargePointType": "AC",
  "ratings": null,
  "userInterfaceLang": [
    "^AAA$"
  ],
  "maxReservation": 0,
  "meteringInfo": null,
  "truckParking": {
    "lightTruck": 0,
    "mediumTruck": 0,
    "heavyTruck": 0
  }
}

```

Contains information about the charge points. Static POI data regarding a charge point / EVSE.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|evseId|[./schemas/cdr.yaml#/EvseId](#schema./schemas/cdr.yaml#/evseid)|true|none|none|
|evseDescription|string|true|none|Human readable description of an EVSE|
|locationId|string|true|none|Alphanumeric. Identifies a location/pool of EVSEs. Unique within one EVSE Operator. All EVSEs of one locationId have to have the same address and Geocoordinates. Characters:- [A-Z], [0-9]|
|timeStamp|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|locationName|string|true|none|Official name; should be unique in the geographical area.|
|locationNameLang|string|true|none|Alpha, three characters. ISO-639-3 language code defining the language of the location name.|
|images|[[evseImageUrlType](#schemaevseimageurltype)]|false|none|Links to images related to the EVSE such as photos or logos.|
|relatedResource|[[RelatedResourceType](#schemarelatedresourcetype)]|false|none|Links to be visited by the user, related to the charge point or charging station.|
|chargePointAddress|[./schemas/generic.yaml#/AddressType](#schema./schemas/generic.yaml#/addresstype)|true|none|none|
|chargePointLocation|[GeoPointType](#schemageopointtype)|true|none|Defines a geo location. The geodetic system to be used is WGS 84.|
|relatedLocation|[AdditionalGeoPointType](#schemaadditionalgeopointtype)|false|none|Class defines a geo location. The geodetic system to be used is WGS 84.|
|timeZone|string|false|none|One of IANA tzdata's TZ-values representing the time zone of the location.|
|openingTimes|[HoursType](#schemahourstype)|true|none|Opening hours for the charge point.|
|status|[ChargePointStatusType](#schemachargepointstatustype)|false|none|This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon|
|statusSchedule|[[ChargePointScheduleType](#schemachargepointscheduletype)]|false|none|Planned status changes in the future. If a time span matches with the current or displayed date, the corresponding value overwrites status|
|telephoneNumber|string|false|none|Numeric. Service hotline for charging station to be displayed to the EV user. Separators recommended. Recommended to be in international format including leading + and country code. (e.g. +49).|
|location|[GeneralLocationType](#schemagenerallocationtype)|true|none|Reflects the general type of the charge points location. May be used for user information. * 'on-street' - parking in public space * 'parking-garage' - multistorey car park * 'underground-garage' - multistorey car park, mainly underground * 'parking-lot' - a cleared area that is intended for parking vehicles, i.e. at super markets, bars, etc. * 'private' - located in private or corporate grounds, may not be accessible to the public * 'other' - none of the given possibilities * 'unknown' - parking location type is not known by the operator|
|parkingSpot|[[ParkingSpotInfo](#schemaparkingspotinfo)]|false|none|Information about one or more parking spots associated with the EVSE.|
|restriction|[[RestrictionType](#schemarestrictiontype)]|false|none|Restrictions applying to the usage of the charging station.|
|authMethods|[[AuthMethodType](#schemaauthmethodtype)]|true|none|List of available payment or access methods on site.|
|connectors|[[ConnectorType](#schemaconnectortype)]|true|none|Which receptacle type is/are present for a power outlet.|
|chargePointType|[chargePointType](#schemachargepointtype)|true|none|The chargePointType is extended from AC and DC to the options mentioned below. The enhancement enables the CPOs to define the CPTs more precisely and offer diversified services. * 'AC' - Alternating current * 'DC' - Direct current * 'Super_95' - Premium unleaded petrol having octance rating of 95 * 'Super_Plus' - High octane rating fuel containing 5-10% of ethanol * 'Super_E10' - Petrol fuel with an ethanol content of up to 10 percent and an octane rating of at least 95 * 'Diesel' - Liquid fuel used in diesel engines, whose ignition takes place without any spark * 'LPG' - Liquefied petroleum gas * 'CNG' - Compressed natural gas * 'LNG' - Liquified natural gas * 'H2' - Hydrogen fuel * 'Ethanol' - Ethyl alcohol as fuel * 'AdBlue' - Diesel exhaust fluid used in vehicles with Selective Catalytic Reduction (SCR) * 'Other' - Other chargepoint types|
|ratings|[./schemas/cdr.yaml#/RatingsType](#schema./schemas/cdr.yaml#/ratingstype)|false|none|none|
|userInterfaceLang|[[userInterfaceLang](#schemauserinterfacelang)]|false|none|Alpha, three characters. Language(s) of the user interface or printed on-site instructions. ISO-639-3 language code|
|maxReservation|number(float)|false|none|If a reservation of this charge point is possible, this is the maximum duration the CPO will allow a reservation for (in minutes). Recommendation:- 30 minutes.|
|meteringInfo|[./schemas/cdr.yaml#/MeteringInfoType](#schema./schemas/cdr.yaml#/meteringinfotype)|false|none|none|
|truckParking|[TruckParkingType](#schematruckparkingtype)|false|none|If trucks can be parked at this location. This value if provided can be used to inform which category of trucks and how many trucks can be parked at this location.|

<h2 id="tocS_evseImageUrlType">evseImageUrlType</h2>
<!-- backwards compatibility -->
<a id="schemaevseimageurltype"></a>
<a id="schema_evseImageUrlType"></a>
<a id="tocSevseimageurltype"></a>
<a id="tocsevseimageurltype"></a>

```json
{
  "uri": "^(http|https|ftp|file):\\/\\/.$",
  "thumbUri": "^(http|https|ftp|file):\\/\\/.$",
  "class": "networkLogo",
  "type": "stri",
  "width": 0,
  "height": 0
}

```

This class references images related to a EVSE in terms of a file name or uri.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|uri|string|true|none|uri from where the image data can be fetched. Must begin with a protocol of the list:- http, https, file,ftp.|
|thumbUri|string|false|none|uri from where a thumbnail of the image can be fetched. Must begin with a protocol of the list:- http, https, file, ftp.|
|class|[ImageClass](#schemaimageclass)|true|none|The class of a EVSE image to obtain the correct usage in a user presentation. Has to be set accordingly to the image content in order to guaranty the right usage. * 'networkLogo' -  logo of an associated roaming network to be displayed with the EVSE for example in lists, maps and detailed information view * 'operatorLogo'-  logo of the charge points operator, for example a municipal, to be displayed with the EVSEs detailed information view or in lists and maps, if no networkLogo is present * 'ownerLogo' -  logo of the charge points owner, for example a local store, to be displayed with the EVSEs detailed information view * 'stationPhoto' -  full view photo of the station in field. Should show the station only * 'locationPhoto' -  location overview photo. Should indicate the location of the station on the site or street. * 'entrancePhoto' -  location entrance photo. Should show the car entrance to the location from street side * 'otherPhoto' -  other related photo to be displayed with the stations detailed information view * 'otherLogo' -  other related logo to be displayed with the stations detailed information view * 'otherGraphic' -  other related graphic to be displayed with the stations detailed information view|
|type|string|true|none|Image type like:- gif, jpeg, png, svg|
|width|integer|false|none|Width of the full scale image|
|height|integer|false|none|Height of the full scale image|

<h2 id="tocS_TruckParkingType">TruckParkingType</h2>
<!-- backwards compatibility -->
<a id="schematruckparkingtype"></a>
<a id="schema_TruckParkingType"></a>
<a id="tocStruckparkingtype"></a>
<a id="tocstruckparkingtype"></a>

```json
{
  "lightTruck": 0,
  "mediumTruck": 0,
  "heavyTruck": 0
}

```

If trucks can be parked at this location. This value if provided can be used to inform which category of trucks and how many trucks can be parked at this location.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|lightTruck|integer|true|none|Number of light-duty trucks parking spots.|
|mediumTruck|integer|true|none|Number of medium-duty trucks parking spots|
|heavyTruck|integer|true|none|Number of heavy-duty trucks parking spots.|

<h2 id="tocS_RelatedResourceType">RelatedResourceType</h2>
<!-- backwards compatibility -->
<a id="schemarelatedresourcetype"></a>
<a id="schema_RelatedResourceType"></a>
<a id="tocSrelatedresourcetype"></a>
<a id="tocsrelatedresourcetype"></a>

```json
{
  "uri": "^(http|https):\\/\\/.$",
  "class": "operatorMap"
}

```

This class defines a resource related to the charge point or charging station.A resource can have multiple classes to indicate a combination of resources on one web site.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|uri|string|true|none|Referencing uri to the resource. Must begin with a protocol of the list:- http, https.|
|class|[RelatedResourceClass](#schemarelatedresourceclass)|true|none|The class of referenced related resource. * 'operatorMap' -  direct link to this charge point on a map of the operator * 'operatorPayment' -  link to a payment page of the operator for contractless direct payment * 'stationInfo' -  further information on the charging station * 'surroundingInfo' -  further information on the surroundings of the charging station e.g. further POIs * 'ownerHomepage' -   website of the station owner (not operator) in case of hotels, restaurants, etc. * 'feedbackForm'-  form for user feedback on the charging station service * 'openingTimes' -  link to a calendar or info page containing opening times (only if no other way of defining these is possible).|

<h2 id="tocS_ImageClass">ImageClass</h2>
<!-- backwards compatibility -->
<a id="schemaimageclass"></a>
<a id="schema_ImageClass"></a>
<a id="tocSimageclass"></a>
<a id="tocsimageclass"></a>

```json
"networkLogo"

```

The class of a EVSE image to obtain the correct usage in a user presentation. Has to be set accordingly to the image content in order to guaranty the right usage. * 'networkLogo' -  logo of an associated roaming network to be displayed with the EVSE for example in lists, maps and detailed information view * 'operatorLogo'-  logo of the charge points operator, for example a municipal, to be displayed with the EVSEs detailed information view or in lists and maps, if no networkLogo is present * 'ownerLogo' -  logo of the charge points owner, for example a local store, to be displayed with the EVSEs detailed information view * 'stationPhoto' -  full view photo of the station in field. Should show the station only * 'locationPhoto' -  location overview photo. Should indicate the location of the station on the site or street. * 'entrancePhoto' -  location entrance photo. Should show the car entrance to the location from street side * 'otherPhoto' -  other related photo to be displayed with the stations detailed information view * 'otherLogo' -  other related logo to be displayed with the stations detailed information view * 'otherGraphic' -  other related graphic to be displayed with the stations detailed information view

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The class of a EVSE image to obtain the correct usage in a user presentation. Has to be set accordingly to the image content in order to guaranty the right usage. * 'networkLogo' -  logo of an associated roaming network to be displayed with the EVSE for example in lists, maps and detailed information view * 'operatorLogo'-  logo of the charge points operator, for example a municipal, to be displayed with the EVSEs detailed information view or in lists and maps, if no networkLogo is present * 'ownerLogo' -  logo of the charge points owner, for example a local store, to be displayed with the EVSEs detailed information view * 'stationPhoto' -  full view photo of the station in field. Should show the station only * 'locationPhoto' -  location overview photo. Should indicate the location of the station on the site or street. * 'entrancePhoto' -  location entrance photo. Should show the car entrance to the location from street side * 'otherPhoto' -  other related photo to be displayed with the stations detailed information view * 'otherLogo' -  other related logo to be displayed with the stations detailed information view * 'otherGraphic' -  other related graphic to be displayed with the stations detailed information view|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|networkLogo|
|*anonymous*|operatorLogo|
|*anonymous*|ownerLogo|
|*anonymous*|stationPhoto|
|*anonymous*|locationPhoto|
|*anonymous*|entrancePhoto|
|*anonymous*|otherPhoto|
|*anonymous*|otherLogo|
|*anonymous*|otherGraphic|

<h2 id="tocS_RelatedResourceClass">RelatedResourceClass</h2>
<!-- backwards compatibility -->
<a id="schemarelatedresourceclass"></a>
<a id="schema_RelatedResourceClass"></a>
<a id="tocSrelatedresourceclass"></a>
<a id="tocsrelatedresourceclass"></a>

```json
"operatorMap"

```

The class of referenced related resource. * 'operatorMap' -  direct link to this charge point on a map of the operator * 'operatorPayment' -  link to a payment page of the operator for contractless direct payment * 'stationInfo' -  further information on the charging station * 'surroundingInfo' -  further information on the surroundings of the charging station e.g. further POIs * 'ownerHomepage' -   website of the station owner (not operator) in case of hotels, restaurants, etc. * 'feedbackForm'-  form for user feedback on the charging station service * 'openingTimes' -  link to a calendar or info page containing opening times (only if no other way of defining these is possible).

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The class of referenced related resource. * 'operatorMap' -  direct link to this charge point on a map of the operator * 'operatorPayment' -  link to a payment page of the operator for contractless direct payment * 'stationInfo' -  further information on the charging station * 'surroundingInfo' -  further information on the surroundings of the charging station e.g. further POIs * 'ownerHomepage' -   website of the station owner (not operator) in case of hotels, restaurants, etc. * 'feedbackForm'-  form for user feedback on the charging station service * 'openingTimes' -  link to a calendar or info page containing opening times (only if no other way of defining these is possible).|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|operatorMap|
|*anonymous*|operatorPayment|
|*anonymous*|stationInfo|
|*anonymous*|surroundingInfo|
|*anonymous*|ownerHomepage|
|*anonymous*|feedbackForm|
|*anonymous*|openingTimes|

<h2 id="tocS_GeoPointType">GeoPointType</h2>
<!-- backwards compatibility -->
<a id="schemageopointtype"></a>
<a id="schema_GeoPointType"></a>
<a id="tocSgeopointtype"></a>
<a id="tocsgeopointtype"></a>

```json
{
  "lat": "50.770774.",
  "lon": "-126.104965."
}

```

Defines a geo location. The geodetic system to be used is WGS 84.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|lat|[latitude](#schemalatitude)|true|none|Latitude of the point in decimal degree.  Decimal separator:- "."|
|lon|[longitude](#schemalongitude)|true|none|Longitude of the point in decimal degree.  Decimal separator:- "."|

<h2 id="tocS_AdditionalGeoPointType">AdditionalGeoPointType</h2>
<!-- backwards compatibility -->
<a id="schemaadditionalgeopointtype"></a>
<a id="schema_AdditionalGeoPointType"></a>
<a id="tocSadditionalgeopointtype"></a>
<a id="tocsadditionalgeopointtype"></a>

```json
{
  "lat": "50.770774.",
  "lon": "-126.104965.",
  "name": "string",
  "type": "entrance"
}

```

Class defines a geo location. The geodetic system to be used is WGS 84.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|lat|[latitude](#schemalatitude)|true|none|Latitude of the point in decimal degree.  Decimal separator:- "."|
|lon|[longitude](#schemalongitude)|true|none|Longitude of the point in decimal degree.  Decimal separator:- "."|
|name|string|false|none|Name of the point in local language or as written at the location. For example the street name of a parking lot entrance or it's number.|
|type|[GeoClass](#schemageoclass)|true|none|The class of this geo point for categorization and right usage. * 'entrance' -  For larger sites entrances may be specified for navigation. * 'exit' -  For larger sites exits may be specified for navigation purpose. * 'access'-  Two directional entrance and exit. * 'ui' -  Geographical location of the user interface for authorisation and payment means. If not specified the user interface is assumed to be at the location of the charge point. * 'other' -   Other relevant point. Name recommended.|

<h2 id="tocS_latitude">latitude</h2>
<!-- backwards compatibility -->
<a id="schemalatitude"></a>
<a id="schema_latitude"></a>
<a id="tocSlatitude"></a>
<a id="tocslatitude"></a>

```json
"50.770774."

```

Latitude of the point in decimal degree.  Decimal separator:- "."

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Latitude of the point in decimal degree.  Decimal separator:- "."|

<h2 id="tocS_longitude">longitude</h2>
<!-- backwards compatibility -->
<a id="schemalongitude"></a>
<a id="schema_longitude"></a>
<a id="tocSlongitude"></a>
<a id="tocslongitude"></a>

```json
"-126.104965."

```

Longitude of the point in decimal degree.  Decimal separator:- "."

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Longitude of the point in decimal degree.  Decimal separator:- "."|

<h2 id="tocS_GeoClass">GeoClass</h2>
<!-- backwards compatibility -->
<a id="schemageoclass"></a>
<a id="schema_GeoClass"></a>
<a id="tocSgeoclass"></a>
<a id="tocsgeoclass"></a>

```json
"entrance"

```

The class of this geo point for categorization and right usage. * 'entrance' -  For larger sites entrances may be specified for navigation. * 'exit' -  For larger sites exits may be specified for navigation purpose. * 'access'-  Two directional entrance and exit. * 'ui' -  Geographical location of the user interface for authorisation and payment means. If not specified the user interface is assumed to be at the location of the charge point. * 'other' -   Other relevant point. Name recommended.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The class of this geo point for categorization and right usage. * 'entrance' -  For larger sites entrances may be specified for navigation. * 'exit' -  For larger sites exits may be specified for navigation purpose. * 'access'-  Two directional entrance and exit. * 'ui' -  Geographical location of the user interface for authorisation and payment means. If not specified the user interface is assumed to be at the location of the charge point. * 'other' -   Other relevant point. Name recommended.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|entrance|
|*anonymous*|exit|
|*anonymous*|access|
|*anonymous*|ui|
|*anonymous*|other|

<h2 id="tocS_HoursType">HoursType</h2>
<!-- backwards compatibility -->
<a id="schemahourstype"></a>
<a id="schema_HoursType"></a>
<a id="tocShourstype"></a>
<a id="tocshourstype"></a>

```json
{
  "regularHours": [
    {
      "weekday": 1,
      "periodBegin": "18:15",
      "periodEnd": "20:15"
    }
  ],
  "twentyfourseven": true,
  "closedCharging": true,
  "exceptionalOpenings": [
    {
      "periodBegin": "2025-01-01T00:00:00Z",
      "peridoEnd": "2025-01-01T00:00:00Z"
    }
  ],
  "exceptionalClosings": [
    {
      "periodBegin": "2025-01-01T00:00:00Z",
      "peridoEnd": "2025-01-01T00:00:00Z"
    }
  ]
}

```

Opening hours for the charge point.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|regularHours|[[RegularHoursType](#schemaregularhourstype)]|false|none|Regular hours, weekday based. Should not be set for representing 24/7 as this is the most common case.|
|twentyfourseven|boolean|true|none|True to represent 24 hours per day and 7 days per week, except the given exceptions. May be set to false if opening hours are defined only by exceptionalOpenings.|
|closedCharging|boolean|true|none|hould be set to true in case an EV can be charged when plugged in during off-times (i.e. when the location is closed according to the specified hours).|
|exceptionalOpenings|[[ExceptionalPeriodType](#schemaexceptionalperiodtype)]|false|none|Exceptions for specified calendar dates, time-range based. Periods the station is operating/accessible. For irregular hours or as addition to regular hours. May overlap regular rules.|
|exceptionalClosings|[[ExceptionalPeriodType](#schemaexceptionalperiodtype)]|false|none|Exceptions for specified calendar dates, time-range based. Periods the station is not operating/accessible. Overwriting regularHours and twentyfourseven. Should not overlap exceptionalOpenings.|

<h2 id="tocS_ExceptionalPeriodType">ExceptionalPeriodType</h2>
<!-- backwards compatibility -->
<a id="schemaexceptionalperiodtype"></a>
<a id="schema_ExceptionalPeriodType"></a>
<a id="tocSexceptionalperiodtype"></a>
<a id="tocsexceptionalperiodtype"></a>

```json
{
  "periodBegin": "2025-01-01T00:00:00Z",
  "peridoEnd": "2025-01-01T00:00:00Z"
}

```

Specifies one exceptional period for opening or access hours.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|periodBegin|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|peridoEnd|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|

<h2 id="tocS_ChargePointStatusType">ChargePointStatusType</h2>
<!-- backwards compatibility -->
<a id="schemachargepointstatustype"></a>
<a id="schema_ChargePointStatusType"></a>
<a id="tocSchargepointstatustype"></a>
<a id="tocschargepointstatustype"></a>

```json
"Unknown"

```

This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Unknown|
|*anonymous*|Operative|
|*anonymous*|Inoperative|
|*anonymous*|Planned|
|*anonymous*|Closed|

<h2 id="tocS_ChargePointScheduleType">ChargePointScheduleType</h2>
<!-- backwards compatibility -->
<a id="schemachargepointscheduletype"></a>
<a id="schema_ChargePointScheduleType"></a>
<a id="tocSchargepointscheduletype"></a>
<a id="tocschargepointscheduletype"></a>

```json
{
  "startDate": "2025-01-01T00:00:00Z",
  "endDate": "2025-01-01T00:00:00Z",
  "status": "Unknown"
}

```

This type is used to schedule status periods in the future. The NSP can provide this information to the EV user for trip planning purpose. A period MAY have no end.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|startDate|[DateTimeType](#schemadatetimetype)|true|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|endDate|[DateTimeType](#schemadatetimetype)|false|none|Format is according to ISO8601 UTC. The field takes 20 alphanumeric characters.|
|status|[ChargePointStatusType](#schemachargepointstatustype)|true|none|This value represents the overall status of a charging point. Not to be confused with a live status (available, reserved, occupied, ... ) This overall status should reflect situations which are valid over several days. The live status indicates shorter valid status. * 'Unknown' -  No status information available * 'Operative' -  charge point is in operation and can be used * 'Inoperative' -  charge point cannot be used due to maintenance, greater downtime, blocking construction works or other access restrictions (temporarily, will be operative in the future). * 'Planned' -  planned charge point, will be operating soon * 'Closed' -  discontinued charge point, will be deleted soon|

<h2 id="tocS_GeneralLocationType">GeneralLocationType</h2>
<!-- backwards compatibility -->
<a id="schemagenerallocationtype"></a>
<a id="schema_GeneralLocationType"></a>
<a id="tocSgenerallocationtype"></a>
<a id="tocsgenerallocationtype"></a>

```json
"on-street"

```

Reflects the general type of the charge points location. May be used for user information. * 'on-street' - parking in public space * 'parking-garage' - multistorey car park * 'underground-garage' - multistorey car park, mainly underground * 'parking-lot' - a cleared area that is intended for parking vehicles, i.e. at super markets, bars, etc. * 'private' - located in private or corporate grounds, may not be accessible to the public * 'other' - none of the given possibilities * 'unknown' - parking location type is not known by the operator

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Reflects the general type of the charge points location. May be used for user information. * 'on-street' - parking in public space * 'parking-garage' - multistorey car park * 'underground-garage' - multistorey car park, mainly underground * 'parking-lot' - a cleared area that is intended for parking vehicles, i.e. at super markets, bars, etc. * 'private' - located in private or corporate grounds, may not be accessible to the public * 'other' - none of the given possibilities * 'unknown' - parking location type is not known by the operator|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on-street|
|*anonymous*|parking-garage|
|*anonymous*|underground-garage|
|*anonymous*|parking-lot|
|*anonymous*|private|
|*anonymous*|other|
|*anonymous*|unknown|

<h2 id="tocS_ParkingSpotInfo">ParkingSpotInfo</h2>
<!-- backwards compatibility -->
<a id="schemaparkingspotinfo"></a>
<a id="schema_ParkingSpotInfo"></a>
<a id="tocSparkingspotinfo"></a>
<a id="tocsparkingspotinfo"></a>

```json
{
  "parkingId": "DELNDP12",
  "restriction": [
    "evonly"
  ],
  "floorlevel": -2,
  "parkingSpotNumber": 10
}

```

Contains all parking related information. If a parkingId is given, this ID can be used to associate parking spot live information from a PSO with this EVSE. Static POI data regarding a parking spot.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|parkingId|[ParkingId](#schemaparkingid)|true|none|The parking-ID follows a similar syntax to that of contract- and EVSE-IDs. The PSO-ID is followed by a 'P' that signifies a tariff and a unique instance of up to 30 characters.|
|restriction|[[RestrictionType](#schemarestrictiontype)]|false|none|Restrictions applying to the usage of the parking spot. If set, should include the restrictions to EVSE-usage as well.|
|floorlevel|string|false|none|Alphanumeric. Level on which the charge station is located (in garage buildings) in the locally displayed numbering scheme.|
|parkingSpotNumber|string|false|none|Alphanumeric. Locally displayed parking slot number.|

<h2 id="tocS_ParkingId">ParkingId</h2>
<!-- backwards compatibility -->
<a id="schemaparkingid"></a>
<a id="schema_ParkingId"></a>
<a id="tocSparkingid"></a>
<a id="tocsparkingid"></a>

```json
"DELNDP12"

```

The parking-ID follows a similar syntax to that of contract- and EVSE-IDs. The PSO-ID is followed by a 'P' that signifies a tariff and a unique instance of up to 30 characters.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The parking-ID follows a similar syntax to that of contract- and EVSE-IDs. The PSO-ID is followed by a 'P' that signifies a tariff and a unique instance of up to 30 characters.|

<h2 id="tocS_RestrictionType">RestrictionType</h2>
<!-- backwards compatibility -->
<a id="schemarestrictiontype"></a>
<a id="schema_RestrictionType"></a>
<a id="tocSrestrictiontype"></a>
<a id="tocsrestrictiontype"></a>

```json
"evonly"

```

This value, if provided, represents the restrictions to the usage of the charging station or parking spot for different purposes. * 'evonly' - reserved parking spot for electric vehicles * 'plugged' - parking allowed only while plugged in (and charging) * 'disabled' - reserved parking spot for disabled people with valid ID * 'customers' - parking or charging for costumer/guests only, for example in case of a hotel or shop * 'motorcycles' - parking spot only suitable for (electric) motorcycles, scooters or bicycles * 'carsharing'- charging / parking only for carsharing vehicles

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|This value, if provided, represents the restrictions to the usage of the charging station or parking spot for different purposes. * 'evonly' - reserved parking spot for electric vehicles * 'plugged' - parking allowed only while plugged in (and charging) * 'disabled' - reserved parking spot for disabled people with valid ID * 'customers' - parking or charging for costumer/guests only, for example in case of a hotel or shop * 'motorcycles' - parking spot only suitable for (electric) motorcycles, scooters or bicycles * 'carsharing'- charging / parking only for carsharing vehicles|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|evonly|
|*anonymous*|plugged|
|*anonymous*|disabled|
|*anonymous*|customers|
|*anonymous*|motorcycles|
|*anonymous*|carsharing|

<h2 id="tocS_AuthMethodType">AuthMethodType</h2>
<!-- backwards compatibility -->
<a id="schemaauthmethodtype"></a>
<a id="schema_AuthMethodType"></a>
<a id="tocSauthmethodtype"></a>
<a id="tocsauthmethodtype"></a>

```json
"Public"

```

The authorisation and payment methods available at an EVSE for the EV user. * 'Public' - Public accessible, no authorisation required * 'LocalKey'- A key or token can be received at the location.(i.e. at the hotel reception or in the restaurant) * 'DirectCash' - The EVSE can be accessed through direct payment in cash. * 'DirectCreditcard' - The Evse can be accessed through direct payment with credit card * 'RfidMifareCls' - Personal RFID token with roaming relation. (Mifare Classic) * 'RfidMifareDes' - Personal token with roaming relation. (Mifare Desfire) * 'RfidCalypso' - Personal RFID token with roaming relation. (Calypso) * 'Iec15118' - In-car access token as specified in IEC-15118 * 'OchpDirectAuth' - The EVSE can be accessed through a OCHP-direct capable provider app. * 'OperatorAuth' - The EVSE can be accessed through a direct online payment to the operator.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|The authorisation and payment methods available at an EVSE for the EV user. * 'Public' - Public accessible, no authorisation required * 'LocalKey'- A key or token can be received at the location.(i.e. at the hotel reception or in the restaurant) * 'DirectCash' - The EVSE can be accessed through direct payment in cash. * 'DirectCreditcard' - The Evse can be accessed through direct payment with credit card * 'RfidMifareCls' - Personal RFID token with roaming relation. (Mifare Classic) * 'RfidMifareDes' - Personal token with roaming relation. (Mifare Desfire) * 'RfidCalypso' - Personal RFID token with roaming relation. (Calypso) * 'Iec15118' - In-car access token as specified in IEC-15118 * 'OchpDirectAuth' - The EVSE can be accessed through a OCHP-direct capable provider app. * 'OperatorAuth' - The EVSE can be accessed through a direct online payment to the operator.|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Public|
|*anonymous*|LocalKey|
|*anonymous*|DirectCash|
|*anonymous*|DirectCreditcard|
|*anonymous*|DirectDebitcard|
|*anonymous*|RfidMifareCls|
|*anonymous*|RfidMifareDes|
|*anonymous*|RfidCalypso|
|*anonymous*|Iec15118|
|*anonymous*|OchpDirectAuth|
|*anonymous*|OperatorAuth|

<h2 id="tocS_userInterfaceLang">userInterfaceLang</h2>
<!-- backwards compatibility -->
<a id="schemauserinterfacelang"></a>
<a id="schema_userInterfaceLang"></a>
<a id="tocSuserinterfacelang"></a>
<a id="tocsuserinterfacelang"></a>

```json
"^AAA$"

```

Alpha, three characters. Language(s) of the user interface or printed on-site instructions. ISO-639-3 language code

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Alpha, three characters. Language(s) of the user interface or printed on-site instructions. ISO-639-3 language code|

