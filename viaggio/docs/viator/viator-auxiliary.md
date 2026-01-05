# Viator API - Auxiliary

## POST /search/freetext

**Operation ID:** `searchFreeText`

**Summary:** /search/freetext

**Description:**
Perform a search for products, attractions and/or destinations that contain a free-text search term. Product results can be filtered and sorted according to various criteria.
This endpoint must not be used to ingest the catalog of products, the [/products/modified-since](#operation/productsModifiedSince) endpoint must be used for that purpose.

**Note**: Only **active** products are returned in the response from this endpoint.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| Accept-Language | header | string | Yes | Specifies the language into which the natural-language fields in the response from this service will |
|  |  |  | No |  |
| target-lander | query | string | No | Target lander page for affiliate productUrl
 |

### Request Body

**Content-Type:** `application/json`

**Schema:** `FreetextSearchRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /locations/bulk

**Operation ID:** `locationsBulk`

**Summary:** /locations/bulk

**Description:**
Get full location details for the requested location references. Locations should be cached and refreshed monthly. Additionally, the [/locations/bulk](#operation/locationsBulk) endpoint should be used on demand for any new location references returned in the product content response.

**Note**: If no response is received for a given location reference, this means  that the location was either removed from our database or replaced by a different one.  If this occurs, please disregard the removed location reference and make sure you update the associated product information.

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BulkLocationReferencesRequest`

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

## POST /exchange-rates

**Operation ID:** `exchangeRates`

**Summary:** /exchange-rates

**Description:**
This endpoint gets the exchange rates for conversions between specified currencies.
Exchange rates should be cached and refreshed based on the expiry timestamp (at the moment daily).

In this API, all pricing is denominated in the currency of the supplier. For example, if a tour operates in Thailand, its prices will be given in Thai Baht (THB). 

Not all supplier currencies are supported, but many are. They comprise:

- AED, ARS, AUD, BRL, CAD, CHF, CLP, CNY, COP, DKK, EUR, FJD, GBP 
- HKD, IDR, ILS, INR, ISK, JPY, KRW, MXN, MYR, NOK, NZD, PEN, PHP, PLN, 
- RUB, SEK, SGD, THB, TRY, TWD, USD, VND, ZAR

While pricing can be in any of the currencies listed above, payments for bookings can only be made using the following four currencies:

- GBP (British Pound)
- EUR (Euros)
- USD (US Dollars)
- AUD (Australian dollars)

In order that you display the correct price to the user and charge accordingly, it is important that you perform the currency conversion based on the exchange rates given in the response from this endpoint and that these conversion rates are valid at the time of conversion (as given in the `expiry` field).

In doing so, you ensure the amount that you, the merchant, will be invoiced by Viator for this product matches your records. Discrepancies are bound to occur if you perform the calculations using expired exchange rates or those from an alternative source.

An additional measure to ensure that you charge your customer accurately is to confirm that the pricing details returned by the [/availability/check](../#operation/availabilityCheck) endpoint (in the billing currency specified in the request) conform to your expectations. The information provided by this service is the definitive source of truth with regard to product pricing.

**Note:** If you attempt to use an unsupported currency when making a booking request, you will receive the following error:

```javascript
Incorrect currency code provided
```

**Note**: In order to reduce the number of cal...

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `ExchangeRatesRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /reviews/product

**Operation ID:** `reviewsProduct`

**Summary:** /reviews/product

**Description:**
Retrieves and filters reviews <u>for a **single** product</u>
Reviews should be cached and refreshed weekly, as well as on-demand when you see that the product content endpoint returns a different review count than saved in your database for the product.

**Non-indexing of reviews**

- Review content is protected proprietary information; therefore, you may not allow review content to be indexed by search engines. In order for your site to be certified, you will need to demonstrate that you have implemented systems to ensure that review content is non-indexed. For more information, see [Key concepts - Protecting unique content](#section/Key-concepts/Protecting-unique-content).

**Availability of reviews**

- Occasionally, reviews are deleted due to inauthenticity, offensive language, etc. Furthermore, we cannot guarantee that non-Viator reviews (i.e., those for which the `provider` is not `"VIATOR"`) will remain available in future (however, you will receive a notification email to inform you should this occurr). As such, we require that you implement a mechanism by which locally-cached reviews are automatically deleted from your records (and are not displayed on your site) if they do not appear in the most recent response from this endpoint.  

**Viator performs checks on reviews**

- For more information, see [Key concepts - Review authenticity](#section/Key-concepts/Review-authenticity)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `ProductReviewsRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /suppliers/search/product-codes

**Operation ID:** `suppliersSearchProductCodes`

**Summary:** /suppliers/search/product-codes

**Description:**
Gets a collection of supplier information objects for the provided products. Limited to 500 products per request.
Supplier details should be cached and refreshed weekly.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BulkSupplierProductRequest`

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

## GET /destinations

**Operation ID:** `destinations`

**Summary:** /destinations

**Description:**
Get details of all destinations supported by the API. Destinations should be refreshed weekly (in addition to on-demand updates when a new destination is returned in the product content response).


**Note**:

 - Returns a complete list of Viator destinations, including destination names and parent identifiers
 - Used to provide navigation through drill down lists or combo boxes
 - Use the data received from this endpoint to resolve the destination identifier(s) in the `destinations[].ref` element in the <a href="https://docs.viator.com/partner-api/technical/#section/Key-concepts/Content-ingestion-endpoints">product content response</a>


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

