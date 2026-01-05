# Viator API Schemas - Pricing

## PricingType

Machine-interpretable value specifying whether the pricing for this product is calculated per individual or per group (unit); one of:  

  - `"PER_PERSON"`
  - `"UNIT"`


---

## PricingUnitType

Machine-interpretable value specifying the type of unit/group when `type` is `"UNIT"`; one of:

  - `"BIKE"`
  - `"BOAT"`
  - `"GROUP"`
  - `"PACKAGE"`
  - `"ROOM"`
  - `"AIRCRAFT"`
  - `"VEHICLE"`


---

## PricingInfo

Ticket/voucher details for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | PricingType |  |
| ageBands | array of AgeBand | Age bands for this product |
| unitType | PricingUnitType |  |

---

## RecommendedRetailPrice

The recommended retail price for the item and the price at which the product is sold on the Viator.com site

---

## PartnerNetPrice

The non-booking fee component of the total amount that Viator will invoice the merchant for this item

---

## PriceObjectSubtotal

Components of this price

### Properties

| Property | Type | Description |
|----------|------|-------------|
| recommendedRetailPrice | RecommendedRetailPrice |  |
| partnerNetPrice | PartnerNetPrice |  |

---

## LineItemPriceObjectSubtotal

Subtotal pricing for this line item, including discount information if available

### Properties

| Property | Type | Description |
|----------|------|-------------|
| price | PriceObjectSubtotal |  |
| priceBeforeDiscount | PriceObjectSubtotal |  |

---

## PricingLineItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | string | Machine-interpretable value indicating the age-band of the travelers that this line-item describes t |
| numberOfTravelers | NumberOfTravelers |  |
| subtotalPrice | LineItemPriceObjectSubtotal |  |

---

## PriceObject

### Properties

| Property | Type | Description |
|----------|------|-------------|
| recommendedRetailPrice | RecommendedRetailPrice |  |
| partnerNetPrice | PartnerNetPrice |  |
| bookingFee | number | The booking fee component of the total amount that Viator will invoice the merchant for the sale of  |
| commission | number | The amount the merchant will receive as a commission for the sale of this item   **Note**: This elem |
| partnerTotalPrice | number | The total amount that Viator will invoice the merchant for the sale of this item  See the following  |

---

## LineItemPriceObject

### Properties

| Property | Type | Description |
|----------|------|-------------|
| price |  | Current price |
| priceBeforeDiscount |  | Non-discounted price if `price` has a discount applied to it |

---

## BasicPriceWithSpecial

Pricing amount information, including 'special' pricing when available.
- **Note**: As the prices listed here may have changed by the time the booking request is made, **please only use the pricing amounts given in the responses from the [/bookings/hold](#operation/bookingsHold) and [/bookings/book](#operation/bookingsBook) endpoints** when charging customers and for invoicing purposes.


---

## PricingDetails

### Properties

| Property | Type | Description |
|----------|------|-------------|
| pricingPackageType | string | Machine-interpretable value indicating the pricing type; one of:     - `"PER_PERSON"` - pricing is c |
| minTravelers | integer | **Minimum** number of travelers required to book to be eligible for this price |
| maxTravelers | integer | **Maximum** number of travelers required to book to be eligible for this price |
| ageBand | string | Machine-interpretable value indicating the age-band to which this price applies; one of:    - `"ADUL |
| price | BasicPriceWithSpecial |  |

---

## PricingRecord

### Properties

| Property | Type | Description |
|----------|------|-------------|
| daysOfWeek | array of string | Array of machine-interpretable strings representing days of the week on which this pricing and avail |
| timedEntries | array of TimedEntry | Array of starting times and unavailability information for this product option code if timed entry i |
| pricingDetails | array of PricingDetails | Pricing details for this season |
| unavailableDates | array of UnavailableDate | Dates on which this product is unavailable during the season. If no unavailable dates exist, this ar |

---

## RecommendedRetailPrice-2

The recommended retail price for the item and the price at which the product is sold on the Viator.com site.

---

## PartnerNetPrice-2

The non-booking fee component of the amount that Viator will invoice the merchant.


For affiliate partners with API access level "Full Access + Booking" this is the amount Viator charges exclusive of commission.


---

## PriceSubtotal

### Properties

| Property | Type | Description |
|----------|------|-------------|
| recommendedRetailPrice | RecommendedRetailPrice-2 |  |
| partnerNetPrice | PartnerNetPrice-2 |  |

---

## PricingLineItemPriceSubtotal

### Properties

| Property | Type | Description |
|----------|------|-------------|
| price |  | The current price. |
| priceBeforeDiscount |  | Non-discounted price if `price` has a discount applied to it. |

---

## PricingLineItem-2

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | AgeBand-2 |  |
| numberOfTravelers | NumberOfTravelers |  |
| subtotalPrice |  | Subtotal pricing for this line item. |

---

## QuoteInitialPrice

Total price of the booking at the time of purchase.

---

## QuotePriceDifference

The price difference that must be paid (or refunded, if negative) to apply the requested amendment to the booking. This value reflects the cost impact of the proposed changes compared to the original booking.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| recommendedRetailPrice | number | The recommended retail price difference for the booking based at price which the product is sold on  |
| partnerNetPrice | number | The non-booking fee component of the total amount that Viator will invoice the merchant for this ame |
| bookingFee | number | The booking fee component of the total amount that Viator will invoice the merchant for the amendmen |
| commission | number | The amount the merchant will receive as a commission for the amendment of this item.    **Note**: Th |
| partnerTotalPrice | number | The total amount that Viator will invoice the merchant for the amendment of this item.    For <u>aff |

---

## AmendmentPricingLineItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | string | Machine-interpretable value indicating the age-band of the travelers that this line-item describes t |
| numberOfTravelers | NumberOfTravelers |  |
| subtotalPrice | object | Subtotal pricing for this line item. |

---

## AmendmentLineItemPriceObject

### Properties

| Property | Type | Description |
|----------|------|-------------|
| price | object | Current price |

---

## QuoteAmendedPrice

A detailed breakdown of the total booking price after the requested amendment has been applied.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| lineItems | array of AmendmentPricingLineItem | Array of pricing details for each traveler in this booking. |
| totalPrice |  | Total price of this booking. |

---

