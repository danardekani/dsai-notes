# Viator API - Payments

## POST /v1/checkoutsessions/{sessionToken}/paymentaccounts

**Operation ID:** `paymentsCreateToken`

**Summary:** /v1/checkoutsessions/{sessionToken}/paymentaccounts

**Description:**
Creates a payment token from raw credit card details for use with the [/bookings/cart/book](#operation/bookingsCartBook) endpoint.

The URL should not be constructed manually, instead use the `paymentDataSubmissionUrl` value returned from the [/bookings/cart/hold](#operation/bookingsCartHold) endpoint.

When using the API payment solution, it is a requirement that you implement our fraud prevention solution. See <a href="https://partnerresources.viator.com/travel-commerce/api-payments/#api" target="_blank">Implementing the API Solution</a> for more details.

**Note**:
- This endpoint utilises a different domain to other endpoints referenced in the API.
- This endpoint is only available to <u>affiliate partners with API access level "Full Access + Booking"</u>.


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| Content-Type | header | string | Yes | Identifies the payload as application/json. |
| x-trip-clientid | header | string | Yes | This is your unique partner identifier, which you can find in the Viator Partner Program: https://pa |
| x-trip-requestid | header | string | Yes | Any client-side generated request identifier, unique per request. |
| User-Agent | header | string | Yes | value should be appropriate to the client you are using, e.g. "curl/8.8.0" |
| sessionToken | path | string | Yes | The `sessionToken` is obtained from calling the [/bookings/cart/hold](#operation/bookingsCartHold) e |

### Request Body

**Content-Type:** `application/json`

**Schema:** `VaultCardRequest`

### Responses

- **200**: Card successfully stored.
- **404**: Checkout session expired or not found.

---

