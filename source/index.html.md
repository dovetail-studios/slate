---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

includes:
  - errors

search: true
---

# Introduction

This API is for the integration of TIPU with NZTE's Customer Management Portal.

The API provides read-only access for the CMP to pull out customer exposed information about grants.

The response are based on the JSON API standard

https://jsonapi.org/

<aside class="notice">
The example requests use a sample domain of Tipu, please replace them with a valid domain before using. 
</aside>

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "http://tipu.com/api/v1/grants/:grant-id"
  -H "Authorization: Bearer jwt-token"
```

> Make sure to replace `jwt-token` with the generated JWT containing the organisation id.

TIPU's API expects a JWT to be passed along in the header with every request. This JWT will be used for
both authentication and authorization.

The JWT will be encoded with the organisation id.

`Authorization: Bearer jwt-token`

<aside class="notice">
You must replace <code>jwt-token</code> with the generated JWT containing claims such as organisation id.
</aside>

# Grants

## Get Active Grant of an Organisation 

### Required JWT claim:

`
{
  "data": { 
    "organisationDynamicsId": "<Dynamics CRM ID>"
  }
}
`

```shell
curl "http://tipu.com/api/v1/active_grant"
  -H "Authorization: Bearer jwt-token"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "41",
    "type": "grant",
    "attributes": {
      "grant_type_name": "IGF 2.0 - Full",
      "details": "Tru Test is testing out a new product in the South American market.",
      "amount_approved": 600000,
      "claimed_percentage": 0.2,
      "balance_remaining": 540000,
      "months_allocated": 12,
      "days_remaining": 320,
      "days_passed": 45,
      "consent_to_proceed_date": "2019-02-08",
      "contract_expiry": "2019-10-08",
      "contract_closed": "2019-03-08",
      "close_out_report_due": "2019-03-08",
      "contract_end_date": "2019-03-08",
      "final_claim": "2019-03-08",
      "fund_administrator": "573e8c5d-a257-e711-810d-c4346bc540c4",
      "primary_contact": "583e8c5d-a257-e711-810d-c4346bc540c4"
    }
  }
}
```

This endpoint retrieves the active IGF of the organisation.
 
### HTTP Request

`GET http://tipu.com/api/v1/active_grant`

## Get a Specific Grant
### Required JWT claim:
`
{
  "data": { 
    "organisationId": "<Tipu organisation ID>"
  }
}
`

```shell
curl "http://tipu.com/api/v1/grants/:grant-id"
  -H "Authorization: Bearer jwt-token"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "41",
    "type": "grant",
    "attributes": {
      "grant_type_name": "IGF 2.0 - Full",
      "details": "Tru Test is testing out a new product in the South American market.",
      "amount_approved": 600000,
      "claimed_percentage": 0.2,
      "balance_remaining": 540000,
      "months_allocated": 12,
      "days_remaining": 320,
      "days_passed": 45,
      "consent_to_proceed_date": "2019-02-08",
      "contract_expiry": "2019-10-08",
      "contract_closed": "2019-03-08",
      "close_out_report_due": "2019-03-08",
      "contract_end_date": "2019-03-08",
      "final_claim": "2019-03-08",
      "fund_administrator": "573e8c5d-a257-e711-810d-c4346bc540c4",
      "primary_contact": "583e8c5d-a257-e711-810d-c4346bc540c4"
    }
  }
}
```

This endpoint retrieves a specific grant under the organisation.

### HTTP Request

`GET http://tipu.com/api/v1/grants/grant-id`

### URL Parameters

| Parameter | Description                     |
| --------- | ------------------------------- |
| ID        | The ID of the grant to retrieve |
