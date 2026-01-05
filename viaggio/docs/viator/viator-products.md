# Viator API - Products

## GET /products/modified-since

**Operation ID:** `productsModifiedSince`

**Summary:** /products/modified-since

**Description:**
Get full product details for all products modified since a specified time.
Initiate a full ingestion only to establish your local copy; this should be a rare occurrence compared to regular updates. Fetch incremental updates through this endpoint on an hourly basis. You are welcome to poll for updates as frequently as every 15 minutes if desired. Be mindful that excessive frequency beyond these recommendations may trigger rate limits.

**Note**:
  - See [Ingesting and updating the product catalogue](#section/Workflows/Ingesting-and-updating-the-product-catalogue) for instructions on how to use this service to ingest the full product catalogue and ensure that it remains up-to-date.
  - The response object utilizes polymorphism and differs markedly depending on whether the product is active or inactive. Click the drop-down selector in the `status` description to toggle between an `"ACTIVE"` and `"INACTIVE"` product response.

**Examples:**

Get all products in the Viator inventory with 500 products per response
page:

```html
GET https://api.sandbox.viator.com/partner/products/modified-since?count=500

```

Get the next page of results:

```html
GET https://api.sandbox.viator.com/partner/products/modified-since?count=500&cursor=MTU3NDA0MzU1NQ==

```

Alternative pagination method (not recommended); e.g., if you have misplaced the cursor value or if for any other reason you wish to get all products modified since 2019-09-17T03:20:45.737043Z:

```html
GET https://api.sandbox.viator.com/partner/products/modified-since?count=500&modified-since=2020-09-30T00%3A00%3A01.737043Z

```

(Response sample generated on: 2020-10-06)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| cursor | query | string | No | Pagination cursor received from a previous call to **this** endpoint that points to the desired star |
| count | query | integer | Yes | Specifies the maximum number of product detail items to be returned in each response from this endpo |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
| modified-since | query | string | No | Only return products that have been modified since the date and time (UTC) specified by this timesta |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /products/bulk

**Operation ID:** `productsBulk`

**Summary:** /products/bulk

**Description:**
Get full product details for all requested products (limited to 500 products per request)

**Note**: 
  - This endpoint **should not** be used to ingest or update the product catalog. Instead, please use the [/products/modified-since](#operation/productsModifiedSince) endpoint for that purpose.
  - The response object utilizes polymorphism and differs markedly depending on whether the product is active or inactive. Click the drop-down selector in the `status` description to toggle between an `"ACTIVE"` and `"INACTIVE"` product response.

(Response sample generated on: 2020-10-06)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BulkProductRequest`

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

## GET /products/{product-code}

**Operation ID:** `products`

**Summary:** /products/{product-code}

**Description:**
Get full product details for a single product.

**Note**: 
  - This endpoint **should not** be used to ingest or update the product catalog. Instead, please use the [/products/modified-since](#operation/productsModifiedSince) endpoint for that purpose.
  - The response object utilizes polymorphism and differs markedly depending on whether the product is active or inactive. Click the drop-down selector in the `status` description to toggle between an `"ACTIVE"` and `"INACTIVE"` product response.

**Example:** Get details for "Big Bus Sydney and Bondi Hop-on Hop-off Tour"
(product code: 5010SYDNEY):

```html
GET https://api.sandbox.viator.com/partner/products/5010SYDNEY

```

(Response samples generated on: 2021-03-29)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
| product-code | path | string | Yes | Retrieve details of the product identified by this product code |

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

## GET /products/tags

**Operation ID:** `productsTags`

**Summary:** /products/tags

**Description:**
Get details for all tags (includes all languages/localizations)
Tags should be cached and refreshed weekly.

To learn more about tags, see this article: [Viator tags, explained](https://partnerresources.viator.com/travel-commerce/tags?source=specs)

**Note**: If no response is received for a given tag reference, this means
that the tag was removed from our database and the associated product has
not yet been updated with a replacement tag. If this occurs, please
disregard the removed tag.

**Note**: The example response has been truncated to five entries for brevity.

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **429**: 
- **500**: 
- **503**: 

---

## GET /products/booking-questions

**Operation ID:** `productsBookingQuestions`

**Summary:** /products/booking-questions

**Description:**
Get full details of all available preset booking questions.
Booking questions should be cached and refreshed monthly.

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /products/search

**Operation ID:** `productsSearch`

**Summary:** /products/search

**Description:**
Returns a list of filtered, ordered and sorted product summaries for products that match the given search criteria.
This endpoint must not be used to ingest the catalog of products, the [/products/modified-since](#operation/productsModifiedSince) endpoint must be used for that purpose.

If you’re a Basic Access Affiliate Partner, this endpoint provides all the essential functionality that you need to implement in order to use the Viator API. The following article describes how to do this in the most efficient way: [Golden Path – Basic Access Affiliate Partners](https://partnerresources.viator.com/travel-commerce/affiliate/basic-access/golden-path/?source=specs).

**Note**: At present, only active products are returned


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `ProductSearchRequest`

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

## POST /products/recommendations

**Operation ID:** `productsRecommendations`

**Summary:** /products/recommendations

**Description:**
Retrieve a list of sorted product-to-product recommendations that match the given search criteria.

Recommendations are algorithm-generated based on various factors such as shared attributes, category, customer purchase patterns, browsing behavior, and other relevant metrics.

This endpoint can be used to enhance product discovery, suggest alternatives, improve cross-selling by displaying related products to customers, etc...

Notes:
- The `recommendations` object may contain multiple recommendation types based on different algorithms or business logic.
- New recommendation types can be added over time, allowing flexibility for different use cases.
- Clients should handle cases where a recommendation category may be empty if no suitable products are found.
- This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BulkProductRecommendationsRequest`

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

