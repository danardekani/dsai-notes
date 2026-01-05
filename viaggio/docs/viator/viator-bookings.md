# Viator API - Bookings

## POST /bookings/cart/hold

**Operation ID:** `bookingsCartHold`

**Summary:** /bookings/cart/hold

**Description:**
Requests the creation of a hold for each item in the cart.

A hold is a guarantee that either the price or availability (or both) of the product will be retained until a booking
request is made using the [/bookings/cart/book](#operation/bookingsCartBook) endpoint.

A hold consists of two components - **availability** and **pricing**. The response to this service indicates whether one, both or neither has been granted, and until when for each item.

- The length of time for which the availability hold will be granted is determined by the supplier, and therefore varies between products.
- The length of time for the pricing hold is determined by Viator, and is therefore standard across all products.

This endpoint must not be used to check availability of a product. Instead, always use the [/availability/check](#operation/availabilityCheck) endpoint to perform the final availability check.

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BookingsCartHoldRequest`

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

## POST /bookings/cart/book

**Operation ID:** `bookingsCartBook`

**Summary:** /bookings/cart/book

**Description:**
Requests a booking for each item in the cart.

- As some products are booked on external supplier systems, it may take > 90s to receive a response from this endpoint. For this reason, <u>we recommend setting your internal time-out for this service to **120s**</u>.
  In the event that this service does time-out, or you receive a HTTP 500 error, you should check the status of the booking using the [/bookings/status](#operation/bookingsStatus) endpoint to ensure the booking was not created before you attempt to make the booking again.
- The status of each item will indicate if the item booking:
  - is still awaiting confirmation (`PENDING`); or,
  - was `CONFIRMED` if it was eventually successful, or 
  - was `REJECTED` if there are valid reasons why it could not be booked; such as, if it was booked-out or other changes to availability occurred; or,
  - failed for an unknown reason if it did eventually fail. In this scenario, a new booking can be attempted using a new `partnerBookingRef`

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BookingsCartBookRequest`

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

## POST /bookings/hold

**Operation ID:** `bookingsHold`

**Summary:** /bookings/hold

**Description:**
**Note**: This endpoint is only available to <u>merchant partners</u>.

Requests the creation of a booking-hold - a guarantee that either the price
or availability (or both) of the product will be retained until a booking
request is made using the [/bookings/book](#operation/bookingsBook)
endpoint.

The booking-hold consists of two components - **availability** and
**pricing**. The response to this service indicates whether one, both or
neither has been granted, and until when.

- The length of time for which the availability hold will be granted is determined by the supplier, and therefore varies between products. 

- The length of time for the pricing-hold is determined by Viator, and is therefore standard across all products. 

This endpoint must not be used to check availability of a product. Instead, always use the [/availability/check](#operation/availabilityCheck) endpoint to perform the final availability check.

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BookingHoldRequest`

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

## POST /bookings/book

**Operation ID:** `bookingsBook`

**Summary:** /bookings/book

**Description:**
Requests a booking for a product.

**Note**: 
- This endpoint is only available to <u>merchant partners</u>.
- The amount that you will be invoiced for the sale of this tour (in the specified currency) is given in the `totalPrice` element in the response from this endpoint.
- As some products are booked on external supplier systems, it may take > 90s to receive a response from this endpoint. For this reason, <u>we recommend setting your internal time-out for this service to **120s**</u>. In the event that this service does time-out, or you receive a HTTP 500 error, you should check the status of the booking using the [/bookings/status](#operation/bookingsStatus) endpoint to ensure the booking was not created before you attempt to make the booking again.
- The booking status will indicate if the booking:
  - is still awaiting confirmation (`"PENDING"`); or,
  - was `"CONFIRMED"` if it was eventually successful, or 
  - was `"REJECTED"` if there are valid reasons why it could not be booked; such as, if it was booked-out or other changes to availability occurred; or,
  - failed for an unknown reason if it did eventually fail. In this scenario, a new booking can be attempted using a new `"partnerBookingRef"`

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BookingBookRequest`

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

## POST /bookings/status

**Operation ID:** `bookingsStatus`

**Summary:** /bookings/status

**Description:**
**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


Requests the status of an existing booking using either the Viator-generated booking reference (`bookingRef`) or the reference generated by the partner (`partnerBookingRef`). For bookings made through v1 endpoints, only Viator-generated booking reference is supported.


Checking the status of a booking is only necessary to retrieve updates on:

  - manual confirmation products status
  - bookings that were left in `"PENDING"`/`"IN_PROGRESS"` status at time of /booking call for other reasons
  - bookings that timed out at time of /booking call
  - amendments that were left in `"IN_PROGRESS"` status at time of /amend call


The endpoint should only be called intermittently and based on the cadence recommended at nextPollAt. To avoid unnecessary calls, do not poll the endpoint before the next recommended polling time, as no updates will be returned.

(Response sample generated on: 2020-11-10)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `BookingStatusRequest`

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

## GET /bookings/cancel-reasons

**Operation ID:** `bookingsCancelReasons`

**Summary:** /bookings/cancel-reasons

**Description:**
Retrieves a dictionary of unique identification codes (`cancellationReasonCode`) and their associated natural-language descriptions (`cancellationReasonText`). Cancellation reasons should be cached and refreshed monthly.
**Note**: 
  - This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.
  - As the data returned by this endpoint may change from time to time, it is recommended that you retrieve the latest cancellation reasons at a fixed cadence – we recommend monthly. For more information, see: [Update frequency](#section/Workflows/Update-frequency).

(Response sample generated on: 2022-07-22)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
| type | query | string | No | Specifies which set of cancellation reasons to retrieve; one of:

- `"CUSTOMER"` – (default) gets th |

### Responses

- **200**: Success
- **401**: 
- **403**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## GET /bookings/{booking-reference}/cancel-quote

**Operation ID:** `bookingsCancelQuote`

**Summary:** /bookings/{booking-reference}/cancel-quote

**Description:**
Gets the cancellation quote for an existing booking.

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.

For more information about how to perform cancellations using this API, see the [Cancellation API workflow](#section/Booking-concepts/Cancellation-API-workflow) section and our in-depth guide about cancellation policies and how to handle cancellations: [All you need to know about cancellation policies](https://partnerresources.viator.com/travel-commerce/merchant/cancellation-policies?source=specs).

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
| booking-reference | path | string | Yes | The booking reference code (in format `BR-123456789`, which is generated by Viator and returned in t |

### Responses

- **200**: Success
- **401**: 
- **403**: 
- **404**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /bookings/{booking-reference}/cancel

**Operation ID:** `bookingsCancel`

**Summary:** /bookings/{booking-reference}/cancel

**Description:**
Cancels existing booking with given Viator-generated booking-reference

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.

For more information about how to perform cancellations using this API, see the [Cancellation API workflow](#section/Booking-concepts/Cancellation-API-workflow) section and our in-depth guide about cancellation policies and how to handle cancellations: [All you need to know about cancellation policies](https://partnerresources.viator.com/travel-commerce/merchant/cancellation-policies?source=specs).

(Response sample generated on: 2020-08-25)


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| booking-reference | path | string | Yes | The booking reference code (in format `BR-123456789`, which is generated by Viator and returned in t |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `CancellationRequest`

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

## GET /bookings/modified-since

**Operation ID:** `bookingsModifiedSince`

**Summary:** /bookings/modified-since

**Description:**
Gets all booking-event notifications relevant to the partner since a point in time indicated by a timestamp or pagination cursor. This endpoint should be polled hourly, except in supplier cancellation scenarios, in which case polling should occur every 5 minutes.

**Merchant partners only:** In order to stop notification emails sent by Viator for **supplier cancellations of bookings made through the API** you must **poll this endpoint every 5 minutes** and send an acknowledge using
[/bookings/modified-since/acknowledge](#operation/bookingsModifiedSinceAcknowledge) endpoint. See the guide on how to automate the flow for supplier cancellations in this article: [Automating supplier cancellations in V.2 Partner API](https://partnerresources.viator.com/travel-commerce/merchant/automating-supplier-cancellations/).
Viator will not send notification emails to partners for customer-initiated cancellations.

**Affiliate partners only:** affiliate partners with API access level Basic or Full will only have access to events of bookings made past September 2025. Whitelabel affiliate partners will only have access to events of bookings made past December 2025.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
| modified-since | query | string | No | Only retrieve booking events that have occurred since the point in time indicated by this timestamp. |
| cursor | query | string | No | Pagination cursor received from a previous call to **this** endpoint that points to the starting poi |
| count | query | integer | No | Specifies the maximum number of booking events to be included in each page of results returned from  |

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

## POST /bookings/modified-since/acknowledge

**Operation ID:** `bookingsModifiedSinceAcknowledge`

**Summary:** /bookings/modified-since/acknowledge

**Description:**
Acknowledges receipt of one or more booking event notifications returned by the [/bookings/modified-since](#operation/bookingsModifiedSince) endpoint. Merchants who wish to assume control of the customer service workflow surrounding booking change events must carry out this step before the time indicated in the `bookings[].acknowledgeBy` field, otherwise Viator will automatically send a cancellation notification to the email address provided by the partner for cancellation notifications.
This endpoint should be called in order to stop notification emails from being sent by Viator. See the guide on how to automate the flow for supplier cancellations in this article: [Automating supplier cancellations in V.2 Partner API](https://partnerresources.viator.com/travel-commerce/merchant/automating-supplier-cancellations/)

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `EventsAcknowledgementRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: Not Found
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## GET /amendment/check/{booking-reference}

**Operation ID:** `amendmentCheck`

**Summary:** /amendment/check/{booking-reference}

**Description:**
Returns the amendability status of a given `bookingRef`, along with a list of booking components (e.g., booking details, traveller info, pickup location) that can be amended. 

**Notes**:
- Only bookings made after July 2025 are eligible to be amended.
- This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


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
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## POST /amendment/quote

**Operation ID:** `amendmentQuote`

**Summary:** /amendment/quote

**Description:**
Gets the amendment quote for an existing booking.

**Notes**:
  - Only one amendmentType can be updated per request.
  - This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `AmendmentQuoteRequest`

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

## POST /amendment/amend/{quote-reference}

**Operation ID:** `amendmentAmend`

**Summary:** /amendment/amend/{quote-reference}

**Description:**
Amends existing booking with given Viator-generated `quoteRef`

**Note**: This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u> and <u>merchant partners</u>.


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
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

