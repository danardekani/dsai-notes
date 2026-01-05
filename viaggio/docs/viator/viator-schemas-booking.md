# Viator API Schemas - Booking

## TicketsPerBooking

Machine-interpretable value indicating whether each traveler needs their own ticket; one of: 

  - `"ONE_PER_BOOKING"`  
  - `"ONE_PER_TRAVELER"`


---

## BookingCutoffType

Machine-interpretable value encoding the type of booking cutoff; one of:

  - `"OPENING_TIME"`
  - `"CLOSING_TIME"`
  - `"START_TIME"`
  - `"FIXED_TIME"`


---

## BookingConfirmationSettings

How this product's bookings are confirmed

For more information, see [Booking concepts – Booking cutoff
times](#section/Booking-concepts/Booking-cutoff-times)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingCutoffType | BookingCutoffType |  |
| bookingCutoffInMinutes | integer | Period in minutes before the start time, opening time, closing time, or a fixed time (respectively,  |
| confirmationType | ConfirmationType |  |
| manualConfirmationPeriod | integer | When the `confirmationType` is `"INSTANT_THEN_MANUAL"`, the value of this field indicates the length |
| bookingCutoffFixedTime | string | Time of day before which this product can be booked (ISO-8601 time stamp, no time zone)    - Example |

---

## BookingRequirements

Passenger type and number requirements for booking

### Properties

| Property | Type | Description |
|----------|------|-------------|
| minTravelersPerBooking | integer | Minimum number of travelers required to book this product |
| maxTravelersPerBooking | integer | Maximum number of travelers required to book this product |
| requiresAdultForBooking | boolean | **True** if at least one passenger from the `"ADULT"` or `"SENIOR"` age band type must be included t |

---

## BookingQuestionFormatType

Machine-interpretable value encoding the required unit type for the answer to the booking question; one of:

  - `"STRING"`
  - `"NUMBER_AND_UNIT"`
  - `"DATE"`
  - `"TIME"`
  - `"LOCATION_REF_OR_FREE_TEXT"`


---

## BookingQuestionGrouping

Machine-interpretable value specifying whether the booking question must be answered individually for each traveler or once per group of travelers in each booking; one of:

  - `"PER_TRAVELER"`
  - `"PER_BOOKING"`


---

## BookingQuestion

A single booking question

### Properties

| Property | Type | Description |
|----------|------|-------------|
| legacyBookingQuestionId | integer | Unique identifier of this booking question <mark>for use with legacy (V1) booking endpoint only</mar |
| id | string | Machine-interpretable value that identifies this booking question; one of: Possible values:    - `"D |
| type | BookingQuestionFormatType |  |
| group | BookingQuestionGrouping |  |
| label | string | Title of this booking question     - **Example**: "Traveler height in feet or centimeters"    - **No |
| hint | string | Hint (tooltip) for this booking question;    - **Example**: "E.g. 14 July 2024, 25 May 2026"    - ** |
| units | array of string | Units that may be used when answering this booking question |
| allowedAnswers | array of string | List of allowed answers for this booking question if the answer represents a selection from a set of |
| required | string | Key string indicating whether an answer must be provided to this question if it is included in the p |
| maxLength | integer | Maximum allowable input length for the answer, measured in characters (UTF-8) |

---

## BookingQuestionsResponse

Information about this product's booking questions

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingQuestions | array of BookingQuestion | Booking questions for this product |

---

## PartnerCartReference

Partner-generated unique cart reference for this group of bookable items.

---

## PartnerBookingReference

Partner-generated unique booking reference for this bookable item.

---

## BookingsCartHoldRequestItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| partnerBookingRef | PartnerBookingReference |  |
| productCode | ProductCode |  |
| productOptionCode | ProductOptionCode |  |
| startTime | StartTime |  |
| travelDate | TravelDate |  |
| paxMix | array of PaxMixItem-2 | Passenger details. |

---

## BookingsCartHoldRequest

---

## CartReference

**Viator-generated** unique reference for this cart of bookable items, e.g.`CR-44e4a3f8b65d11edafa10242ac120002`


---

## BookingReference

Unique Viator-generated booking reference for this bookable item.

---

## BookingHoldStatus

The status of this bookable item; one of:

- `BOOKABLE` – This item can currently be booked. Check `bookingHoldInfo` for availability and pricing hold statuses.
- `REJECTED` – This item is unavailable to be booked.


---

## BookingsCartHoldResponseItemBase

### Properties

| Property | Type | Description |
|----------|------|-------------|
| partnerBookingRef | PartnerBookingReference |  |
| bookingRef | BookingReference |  |
| status | BookingHoldStatus |  |

---

## CartPrice

### Properties

| Property | Type | Description |
|----------|------|-------------|
| recommendedRetailPrice | RecommendedRetailPrice-2 |  |
| partnerNetPrice | PartnerNetPrice-2 |  |
| bookingFee | number | The booking fee component of the amount that Viator will invoice the merchant for the sale of this i |
| commission | number | The amount the merchant or affiliate  will receive as a commission for the sale of this item.   **No |
| partnerTotalPrice | number | The total amount that Viator will invoice the merchant for the sale of this item.   For affiliate pa |

---

## CartLineItemPrice

### Properties

| Property | Type | Description |
|----------|------|-------------|
| price |  | The current price. |
| priceBeforeDiscount |  | Non-discounted price if `price` has a discount applied to it. |

---

## BookingsCartResponseItemPrice

### Properties

| Property | Type | Description |
|----------|------|-------------|
| lineItems | array of PricingLineItem-2 | List of pricing details for each age band in this bookable item. |
| itemTotalPrice |  | Details about the total price of this item. |

---

## BookingHoldInfo

Availability and pricing hold information.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| availability |  | Availability hold information. |
| pricing |  | Pricing hold information. |

---

## BookingsCartHoldResponseBookableItem

---

## BookingsCartHoldResponseRejectedItem

---

## BookingsCartHoldResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cartRef | CartReference |  |
| partnerCartRef | PartnerCartReference |  |
| currency | Currency |  |
| items | array of object | List of bookable items. |
| totalHeldPrice |  | The total price of all bookable items. |
| paymentDataSubmissionUrl | string | The API URL to provide payment details to the Viator payment gateway. Only returned if `paymentDataS |
| paymentSessionToken | string | The payment session token, if `paymentDataSubmissionMode` is set, used to facilitate fraud preventio |
| extraChargesSummary | object | Total amount of Extra Charges considering all cart bookable items. |
| translationInfo | TranslationDetails |  |

---

## CartBookCommunicationInfo

Details for correspondence regarding this booking.

**See**: [Booking concepts – Supplier communications](#section/Booking-concepts/Supplier-communications) for information about closed-loop communication.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| phone | string | Telephone number to be used for correspondence from the supplier regarding the booking. This can be  |
| email | string | Email address of the customer to be used for correspondence from the supplier regarding the booking. |

---

## AdditionalBookingDetails

### Properties

| Property | Type | Description |
|----------|------|-------------|
| voucherDetails | VoucherDetails |  |
| fraudPreventionDetails | FraudPreventionDetails |  |
| loyaltyProgramDetails | LoyaltyProgramDetails |  |

---

## BookingQuestionAnswers

### Properties

| Property | Type | Description |
|----------|------|-------------|
| question | string | Booking question identifier - `id` field in response from [/products/booking-questions](#operation/p |
| answer | string | Answer to the booking question.  **Note**: Emojis are not supported in this field; therefore, please |
| unit | string | Unit in which the answer is provided; one of `units` in response from [/products/booking-questions]( |
| travelerNum | integer | Number of the traveler to which this booking question answer pertains. |

---

## BookingQuestionAnswers-2

Answers to booking questions required for this booking.

**See:** [Booking concepts – Booking questions](#section/Booking-concepts/Booking-questions) for more information.


---

## BookingsCartBookRequestItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | BookingReference |  |
| languageGuide | LanguageGuide |  |
| bookingQuestionAnswers | BookingQuestionAnswers-2 |  |

---

## BookingsCartBookRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cartRef | CartReference |  |
| bookerInfo | BookerInfo |  |
| communication | CartBookCommunicationInfo |  |
| additionalBookingDetails |  | Optional extra details to include with the booking. |
| items | array of BookingsCartBookRequestItem | List of bookable items. |
| paymentToken | string | The payment token obtained from the payments endpoint or from the iframe Javascript library. |

---

## BookingBookStatus

One of: `CONFIRMED`, `PENDING`, `REJECTED`

Note: For `"PENDING"` poll [/booking/status](#tag/Bookings/operation/bookingsStatus) for further booking status updates
            


---

## BookingsCartBookResponseItemBase

### Properties

| Property | Type | Description |
|----------|------|-------------|
| partnerBookingRef | PartnerBookingReference |  |
| bookingRef | BookingReference |  |
| status | BookingBookStatus |  |

---

## BookingsCartBookResponseConfirmedItem

---

## BookingsCartBookResponsePendingItem

---

## CartBookRejectionReasonCode

In the case that `status` is `REJECTED`, this field provides a code as to the reason for the rejection; one of:

  - `"BOOKABLE_ITEM_IS_NO_LONGER_AVAILABLE"` – this bookable item is no longer available
  - `"DUPLICATE_BOOKING"` – this is a duplicate booking
  - `"ISSUE_WITH_PAYMENT"` – the customer’s payment was declined due to an issue trying to process the payment. This could be caused by generic errors, suspected fraud, or incomplete billing information.
  - `"INSUFFICIENT_FUNDS"` - the customer's payment was declined due to insufficient funds
  - `"INVALID_PAYMENT_DETAILS"` - the customer's payment was declined due to invalid payment details
  - `"SUSPECTED_FRAUD"` - the customer payment was declined due to security measures flagging it as potentially fraudulent
  - `"SOFT_DECLINE"` - the customer’s payment was declined due to fixable issues (eg insufficient funds)
  - `"HARD_DECLINE"` - the customer’s payment was declined due to an error or issue which can't be resolved immediately. Action such a new payment method or the customer contacting their bank will need to be taken to resolve the issue before the transaction can be retried.
  - `"THREE_D_SECURE_REQUIRED"` - the customer’s payment was declined due to unsuccessful authentication through 3DS
  - `"INTERNAL_ERROR"` - the customer’s payment was declined due to an internal error in our system
  - `"PROCESSOR_UNAVAILABLE"` - the customer’s payment was declined due to temporary unavailability on the processor’s end
  - `"PROCESSOR_ISSUE_WITH_PAYMENT"` - the customer’s payment was declined due to an issue on the processor’s end
  - `"OTHER"` – other/unlisted reason


---

## BookingsCartBookResponseRejectedItem

---

## VoucherInfoCart

Voucher information for this booking.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| url | string | URL from which this voucher can be retrieved. |
| format | string | File format of the voucher; one of:   - `HTML`  **Note:** Only `HTML` is currently supported at the  |
| type | string | Whether all Viator standard vouchers, supplier provided vouchers or a mix of both Viator standard an |
| isVoucherRestrictionRequired | boolean | Indicates if the transaction was flagged as potentially fraudulent. If set to `true`, partners must  |

---

## BookingsCartBookResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cartRef | CartReference |  |
| partnerCartRef | PartnerCartReference |  |
| currency | Currency |  |
| items | array of object | List of bookable items. |
| voucherInfo |  |  |
| totalConfirmedPrice |  | The total price of all confirmed bookable items. |
| totalPendingPrice |  | The total price of all pending bookable items. |

---

## BookingRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Unique identifier for the product |
| productOptionCode | string | Product option identifier.  For more information see: [Key concepts: Product options](#section/Key-c |
| startTime | string | Starting time for the item in the case that the product/product option has multiple start times.  ** |
| currency | string | Three-letter currency code for the currency in which to return pricing information; one of:    - `"U |
| travelDate | string | Date of travel (according to the time zone in which the product operates) |
| paxMix | array of PaxMixItem | Passenger details |

---

## BookingHoldRequest

---

## BookingHoldResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | string | **Viator-generated** booking reference for this booked item in format `BR-123456789`   This value ca |
| bookingHoldInfo | BookingHoldInfo |  |
| currency | string | Three-letter currency code for the currency in which pricing information is displayed; one of:    -  |
| lineItems | array of PricingLineItem | Array of pricing details for each traveler in this booking |
| totalPrice |  | Details about the total price of this booking |
| extraChargesSummary | ExtraChargesSummary |  |
| translationInfo | TranslationDetails |  |

---

## AdditionalBookingDetails-2

Optional extra details to include with booking

### Properties

| Property | Type | Description |
|----------|------|-------------|
| voucherDetails | VoucherDetails |  |

---

## BookingBookRequest

---

## BookingBookResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| status | string | Indicates the outcome of the booking request; one of:    - `"CONFIRMED"` – the booking has been conf |
| rejectionReasonCode | string | In the case that `status` is `"REJECTED"`, this field provides a code as to the reason for the rejec |
| bookingRef | string | Viator-generated booking reference number |
| partnerBookingRef | string | Partner-generated booking reference number (if sent in the request) |
| currency | string | One of the available billing currencies:    - `"USD"`   - `"CAD"`   - `"GBP"`   - `"AUD"`   - `"EUR" |
| lineItems | array of PricingLineItem | Array of pricing details for each traveler in this booking |
| totalPrice |  | Total price of this booking |
| cancellationPolicy | CancellationPolicy |  |
| voucherInfo | VoucherInfo |  |

---

## BookingStatusRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | string | The booking reference code (in format `BR-123456789`, which is generated by Viator and returned in t |
| partnerBookingRef | string | The booking reference code generated by you (the partner) that was provided in in the request to [/b |
| voucherFormat | string | File format of the voucher; one of: - `PDF` - `HTML`  Default is `HTML` if not specified.  |

---

## BookingStatusResponseCommon

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | string | Viator-generated booking reference number |
| partnerBookingRef | string | Partner-generated booking reference number (if sent in the request) |
| status | string | Indicates the outcome of the booking request; one of:    - `"CONFIRMED"` – the booking has been conf |

---

## BookingStatusResponseConfirmed

---

## BookingStatusResponseTransient

---

## BookingStatusResponseRejected

---

## BookingStatusResponseOther

---

## BookingStatusResponse

---

## CancellationQuoteBookingStatus

Machine-interpretable string indicating the cancellation status of this itinerary item:

  - `"CANCELLABLE"` - this booking is available to be cancelled
  - `"CANCELLED"` - this booking has already been cancelled
  - `"NOT_CANCELLABLE"` - this booking cannot be cancelled (because the product's start time was in the past)


---

## CancelBookingQuoteResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingId | string | Booking reference number for this booking - **Note**: For bookings made with v1 of this API, this co |
| refundDetails | RefundDetails |  |
| status | CancellationQuoteBookingStatus |  |

---

## CancellationBookingStatus

Machine-interpretable string indicating the outcome of the booking cancellation request. One of: 

  - `"ACCEPTED"`: The cancellation was successful
  - `"DECLINED"`: The cancellation failed


---

## CancelBookingResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingId | string | Booking reference code for this booking    - **Note**: For bookings made with v1 of this API, this c |
| reason | CancellationResultItemReason |  |
| status | CancellationBookingStatus |  |

---

## BookingEventItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Unique identification code for the product to which this booking event pertains  |
| productOptionCode | string | Identification code for the product option of the product identified by `productCode` to which this  |
| travelDate | string | The **date** on which the booked item was scheduled to operate  **Example**: `2020-05-29`  |
| travelTime | string | The **time of day** at which the booked item was scheduled to commence  **Example**: `09:30`  |

---

## BookingEventCancellation

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cancellationReasonCode | string | Identification code for the reason that the booking was canceled by the supplier.  This code can be  |
| refundDetails |  |  |

---

## BookingEvent

### Properties

| Property | Type | Description |
|----------|------|-------------|
| transactionRef | string | A unique reference code for this booking event notification.   Example: `"PBE-e60bb92c-f1fc-11ec-b93 |
| campaignValue | string | **Affiliate partners only:** Specifies the campaign tracking identifier that was appended to the URL |
| eventType | string | The type of this booking notification event  One of:    - `"CONFIRMATION"` - The booking was confirm |
| bookingRef | string | The Viator-generated-booking-reference code for the booking to which this event notification pertain |
| partnerBookingRef | string | The partner-nominated-booking-reference code for the booking to which this event notification pertai |
| lastUpdated | string | Timestamp indicating when this booking event occurred. This can be used for the value of the `modifi |
| acknowledgeBy | string | Timestamp for the point in time before which this event notification must be acknowledged by the mer |
| bookedItem |  |  |
| cancellation |  |  |

---

## BookingsModifiedSinceResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookings | array of BookingEvent | List of booking event notifications |
| nextCursor | string | The cursor to use to fetch the next page of booking notification events.  **Example**: `MTU3NDA0NDcz |

---

## BookingRef

The booking reference code (in format `BR-123456789`), generated by Viator and returned in the `bookingRef` element in the response from [/bookings/book](#operation/bookingsBook) and [/bookings/cart/book](#operation/bookingsCartBook)


---

## BookingQuestionTraveler

Booking question identifier - `id` field in response from [/products/booking-questions](#operation/productsBookingQuestions) endpoint. Possible values:
  - `DATE_OF_BIRTH`
  - `HEIGHT`
  - `PASSPORT_EXPIRY`
  - `PASSPORT_NATIONALITY`
  - `PASSPORT_PASSPORT_NO`
  - `WEIGHT`
  - `FULL_NAMES_FIRST`
  - `FULL_NAMES_LAST`

**Note**: only the Booking questions on the list provided are eligible to be amended


---

## BookingQuestionUnit

Unit in which the answer is provided; one of `units` in response from [/products/booking-questions](#operation/productsBookingQuestions) endpoint.


---

## AmendBookingDetails

---

## AmendPerBookingQuestions

---

