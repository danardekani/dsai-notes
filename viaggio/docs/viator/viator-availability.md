# Viator API - Availability

## POST /availability/check

**Operation ID:** `availabilityCheck`

**Summary:** /availability/check

**Description:**
Check real-time availability and pricing for a product depending on the date, pax-mix, start time and/or product option.

We recommend using the pricing information returned by this endpoint as the source of truth for the amount you will be invoiced by Viator for the sale of the product in question.

The third response example – 265910P1 (commission payment model) – shows the alternative PriceObject for merchants using the commission payment model.

**Note**: This service should only be used to determine the availability of a product immediately prior to booking. Bulk operations pertaining to product availability; e.g., generating a calendar of availability for a product, should use the [availability schedule endpoints](#section/Key-concepts/Content-ingestion-endpoints).

(Response sample generated on: 2021-04-06)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `CheckAvailabilityRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: Not Found
- **429**: 
- **500**: 
- **503**: 

---

## GET /availability/schedules/{product-code}

**Operation ID:** `availabilitySchedules`

**Summary:** /availability/schedules/{product-code}

**Description:**
Get availability and pricing details for all product options of the requested product. The pricing is returned in the supplier's currency. We recommend using the [/exchange-rates](#operation/exchangeRates) endpoint to get the Viator exchange rates and apply them for pricing conversion.

 **Note**: This endpoint **should not** be used for ingesting or updating the availability and pricing details for the entire catalog of Viator products. Instead, please use the [/availability/schedules/modified-since](#operation/availabilitySchedulesModifiedSince) endpoint for that purpose.

(Response sample generated on: 2021-03-12)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
| product-code | path | string | Yes | Retrieve availability details for the product identified by this product code |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **405**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /availability/schedules/bulk

**Operation ID:** `availabilitySchedulesBulk`

**Summary:** /availability/schedules/bulk

**Description:**
Get availability and pricing details for all product options of all requested products. The pricing is returned in the supplier's currency. We recommend using the [/exchange-rates](#operation/exchangeRates) endpoint to get the Viator exchange rates and apply them for pricing conversion.

**Note**: This endpoint **should not** be used for ingesting or updating the availability and pricing details for the entire catalog of Viator products. Instead, please use the [/availability/schedules/modified-since](#operation/availabilitySchedulesModifiedSince) endpoint for that purpose.

(Response sample generated on: 2021-03-12)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BulkAvailabilityScheduleRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **405**: 
- **429**: 
- **500**: 
- **503**: 

---

## GET /availability/schedules/modified-since

**Operation ID:** `availabilitySchedulesModifiedSince`

**Summary:** /availability/schedules/modified-since

**Description:**
Get full future availability details for all products modified since the specified time. The pricing is returned in the supplier's currency. We recommend using the [/exchange-rates](#operation/exchangeRates) endpoint to get the Viator exchange rates and apply them for pricing conversion. Initiate a full ingestion only to establish your local copy; this should be a rare occurrence compared to regular updates. Fetch incremental updates through this endpoint on an hourly basis. You are welcome to poll for updates as frequently as every 15 minutes if desired. Be mindful that excessive frequency beyond these recommendations may trigger rate limits.

(Response sample generated on: 2021-03-12)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| cursor | query | string | No | Pagination cursor received from a previous call to **this** endpoint that
points to the desired star |
| count | query | integer | No | The maximum number of products to be returned in response. 
- Maximum allowed and default value: `50 |
| modified-since | query | string | No | Only retrieve availabilty schedules that have been modified since the date and time (UTC) specified  |
|  |  |  | No |  |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **429**: 
- **500**: 
- **503**: 

---

