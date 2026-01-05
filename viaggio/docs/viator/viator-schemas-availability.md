# Viator API Schemas - Availability

## AvailabilityScheduleSummary

Information about the lowest price available for this product

**Note**: The pricing information given here is based on the recommended retail price (RRP). While affiliate partners must sell at this price, merchant partners set their own prices according to their own margins and booking fees; therefore, merchant partners must calculate their own from-price for display, rather than using these values, unless they have elected to sell at the RRP.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| fromPrice | number | Lowest per-person retail price for this product, calculated according to the price for a group of at |
| fromPriceBeforeDiscount | number | If the product is presently discounted, this field shows what the value of `fromPrice` would be if n |

---

## AvailabilityScheduleExtraChargesSummary

Information about the lowest price with extra charges available for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| fromPrice | number | `fromPrice` value including `extraCharges` value to be paid in destination by the traveler based on  |
| fromPriceBeforeDiscount | number | If the product is presently discounted, this field shows what the value of `fromPrice` would be if n |
| extraCharges | number | The highest amount that a traveler could be asked to pay in-destination based on their age, day of t |

---

## CheckAvailabilityRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Retrieve availability details for the product identified by this product code |
| productOptionCode | string | Retrieve availability details for the product option (tour grade) identified by this product option  |
| startTime | string | Retrieve availability details only for items that start at this time. If this parameter is omitted,  |
| travelDate | string | Retrieve availability details for items that operate on this date |
| currency | string | Display pricing in the currency identified by this 3-letter code - **Example**: `"USD"`  |
| paxMix | array of PaxMixItem | Passenger-mix information |

---

## CheckAvailabilityBookableItem

Details of this bookable item

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productOptionCode | string | Product option code for this bookable item  For more information see: [Key concepts: Product options |
| startTime | string | Starting time for this bookable item relative to the time zone in which this product operates - **Ex |
| available | boolean | `true` if this item is available to be booked |
| capacity | CapacityObject |  |
| unavailableReason | string | Machine-interpretable reason code indicating why this bookable item is unavailable (when `available` |
| lineItems | array of PricingLineItem | Components of total price, each consisting of passenger(s) from a single age band.  **Note**: This e |
| totalPrice |  |  |
| extraChargesSummary | ExtraChargesSummary |  |
| translationInfo | TranslationDetails |  |

---

## CheckAvailabilityResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| currency | string | Currency in which pricing is expressed in this response (as specified in the request) |
| productCode | string | Product code of the product that this availability response pertains to |
| travelDate | string | Date of travel for all bookable items returned in this response (relative to the time zone in which  |
| bookableItems | array of CheckAvailabilityBookableItem | Bookable items for this product |

---

## BulkAvailabilityScheduleRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCodes | array of string | List of product codes for which to retrieve availability schedules |

---

## BulkAvailabilityScheduleResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| availabilitySchedules | array of ProductAvailabilitySchedule | Array of availability schedule objects |

---

## AvailabilitySchedulesResponse

---

