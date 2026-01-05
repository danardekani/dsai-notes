# Viator API Schemas - Other

## TicketType

---

## TicketInfo

Ticket/voucher details for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ticketTypes | array of TicketType | Array of machine-interpretable values encoding the ticket type for this product; i.e., must be print |
| ticketTypeDescription | string | Description of this ticket type - **Note**: This field contains natural language suitable for displa |
| ticketsPerBooking | TicketsPerBooking |  |
| ticketsPerBookingDescription | string | Description of this product's tickets-per-booking information  - **Note**: This field contains natur |

---

## AgeBandType

Machine-interpretable value that specifies this age band's type; one of:

  - `"ADULT"`
  - `"SENIOR"`
  - `"YOUTH"`
  - `"CHILD"`
  - `"INFANT"`
  - `"TRAVELER"`


---

## AgeBand

Age range categories for this product's ticketing scheme

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | AgeBandType |  |
| startAge | integer | Lower limit (inclusive) of the age range defined by this age band |
| endAge | integer | Upper limit (inclusive) of the age range defined by this age band |
| minTravelersPerBooking | integer | Minimum number of travelers in this age band required to book the product |
| maxTravelersPerBooking | integer | Maximum Number of travelers in this age band allowed to book the product |

---

## ImageSourceType

Machine-interpretable value indicating the source of this image; one of:

  - `"SUPPLIER_PROVIDED"`
  - `"PROFESSIONAL"`


---

## ImageVariant

### Properties

| Property | Type | Description |
|----------|------|-------------|
| height | integer | Height of this image in pixels    - Example: `'480'`  |
| width | integer | Width of this image in pixels - Example `'720'`  |
| url | string | URL from which this image can be retrieved.  |

---

## Image

Image information

### Properties

| Property | Type | Description |
|----------|------|-------------|
| imageSource | ImageSourceType |  |
| caption | string | Description of this photo - **Note**: This field contains natural language suitable for display to t |
| isCover | boolean | `true` if this photo is considered to be the cover (leading) photo for this product from this `image |
| variants | array of ImageVariant | Dimension/resolution variants available for this image |

---

## LocationReference

Details about the location can be retrieved using the [/locations/bulk](#operation/locationsBulk) endpoint


### Properties

| Property | Type | Description |
|----------|------|-------------|
| ref | string | Location identifier code    - **Example**: `"LOC-c7d4f6ba-3633-4419-87d4-e88bb66206fc"`  |

---

## StartEndPoint

### Properties

| Property | Type | Description |
|----------|------|-------------|
| location | LocationReference |  |
| description | string | Description of this location    - **Note**: This field contains natural language suitable for displa |

---

## Redemption

Redemption point details for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| redemptionType | string | Machine-interpretable value specifying the type of redemption; one of:    - `"NONE"` - No redemption |
| locations | array of LocationReference | Locations for this redemption point  Details about the location can be retrieved using the [/locatio |
| specialInstructions | string | Special instructions pertaining to this redemption point    - **Example**: `"Bring photo ID for entr |

---

## PickupOptionType

Machine-interpretable value encoding the type of traveler pickup option; one of:

  - `"PICKUP_EVERYONE"` (the supplier will pick up all customers from their respective locations)
  - `"PICKUP_AND_MEET_AT_START_POINT"` (the supplier will pick up all customers from their respective locations; or, customers can make their own way to the start point)
  - `"MEET_EVERYONE_AT_START_POINT"` (all customers must make their own way to and meet at the start point)

**Note**:
  - This value of this field may affect whether or not some booking questions should be answered. See the section on [conditional booking questions](#section/Booking-concepts/Booking-questions) for more information.


---

## PickupLocation

Pickup or meeting point

### Properties

| Property | Type | Description |
|----------|------|-------------|
| location | LocationReference |  |
| pickupType | string | Type of pickup location; one of:     - `"AIRPORT"` – the item is an airport   - `"HOTEL"` – the item |

---

## TravelerPickup

Traveler pickup details for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| pickupOptionType | PickupOptionType |  |
| allowCustomTravelerPickup | boolean | Specifies whether travelers can choose a custom pickup or meeting location for this product    - **N |
| locations | array of PickupLocation | Pickup and meeting points |
| minutesBeforeDepartureTimeForPickup | integer | How long prior to the product departure time will traveler-pickup occur (in minutes) |
| additionalInfo | string | Description of additional information regarding traveler pickup    - **Note**: This field contains n |

---

## Logistics

Logistics details for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| start | array of StartEndPoint | Starting point locations and descriptions |
| end | array of StartEndPoint | Ending point locations and descriptions |
| redemption | Redemption |  |
| travelerPickup | TravelerPickup |  |

---

## InclusionExclusionItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| category | string | Machine-interpretable value encoding the category of this product feature; one of:    - `"EQUIPMENT" |
| categoryDescription | string | Description of this product feature - **Note**: This field contains natural language suitable for di |
| type | string | Machine-interpretable value encoding the type/category of this product feature; one of:    - `"FUEL_ |
| typeDescription | string | Description of this product feature type  - **Note**: This field contains natural language suitable  |
| otherDescription | string | Description of this product feature when `type` is `"OTHER"` - **Note**: This field contains natural |
| quantity | integer | Quantity of this type of inclusion or exclusion in the case that the product is a multi-day tour or  |
| description | string | Description of the item - **Note**: This field contains natural language suitable for display to the |

---

## AdditionalInfo

An additional information fact to communicate to travelers regarding this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | string | Machine-interpretable value encoding the type/category of additional information fact; one of (but n |
| description | string | Description of this additional information fact - **Example**: "Operates in all weather conditions ( |

---

## CancellationConditionType

Machine-interpretable value encoding the type of cancellation policy for this product; one of:

  - `STANDARD` - Products in this category are cancellable up to 24 hours before the travel date (local supplier time) for a full refund. However, a 100% cancellation penalty applies for cancellations submitted less than 24 hours before the start time. Most products (about 85%) fall into this category.
  - `ALL_SALES_FINAL` - Products in this category cannot be cancelled or amended without incurring a 100% penalty; i.e., the refund amount will be zero. Around 10% of products fall into this category.
  - `CUSTOM` - The refund amount for products in this category varies depending on how long before its start time the product is cancelled. Many products on a custom policy are multi-day tours, which require more sophisticated planning on the supplier’s end. Only a small number of products (around 5%) fall into this category.

For more information, see our in-depth guide about cancellation policies and how to handle cancellations: [All you need to know about cancellation policies](https://partnerresources.viator.com/travel-commerce/merchant/cancellation-policies?source=specs).


---

## CancellationCondition

Structured description of fees pertaining to cancellations during various time windows.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| dayRangeMin | integer | Number of days prior to the product start time (relative to the time zone in which the product opera |
| dayRangeMax | integer | Number of days prior to the tour start time (relative to the time zone in which the product operates |
| percentageRefundable | integer | Percentage of total price refundable if a booking for this product is cancelled within the period de |
| startTimestamp | string | Timestamp (UTC) indicating the **beginning** of the period during which this cancellation policy app |
| endTimestamp | string | Timestamp (UTC) indicating the **end** of the period during which this cancellation policy applies;  |

---

## CancellationPolicy

Cancellation policy details for this product.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | CancellationConditionType |  |
| description | string | Description of this product's cancellation policy.  **Note**: This field contains natural language s |
| cancelIfBadWeather | boolean | **True** if the supplier of this product may cancel on account of weather conditions. |
| cancelIfInsufficientTravelers | boolean | **True** if the supplier of this product can cancel due to too few participants. |
| refundEligibility | array of CancellationCondition | Cancellation policy definitions for this product. |

---

## ConfirmationType

Machine-interpretable value encoding when bookings for this product will be confirmed; one of: 

  - `"INSTANT"` (instantly) 
  - `"MANUAL"` (requires manual action prior to confirmation)
  - `"INSTANT_THEN_MANUAL"` (combination – subject to cutoff time)


---

## LanguageGuide

Specifies which language and what type of language guide to include if language guides are available for this product. 

**Note:** This element must be included in order to book products that offer language guides.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | string | Machine-interpretable value encoding the type of language guide; one of:    - `GUIDE` – human tour g |
| language | string | Language code of the language for this guide; one of:    - `cmn` - Mandarin   - `es` - Spanish   - ` |
| legacyGuide | string | Supply this value in the `languageOptionCode` element when making a booking request. |

---

## Itinerary

Details about the places this product visits

See: [Key concepts – Itineraries](#section/Key-concepts/Itineraries) for more information


### Properties

| Property | Type | Description |
|----------|------|-------------|
| itineraryType | ItineraryType |  |
| skipTheLine | boolean | **True** if a ticket for this product allows the customer to 'skip the line' |
| privateTour | boolean | **True** if this product is a private tour; i.e., customers other than those in this booking will ** |
| maxTravelersInSharedTour | integer | Maximum number of travelers that will be present if this product is not a private tour |
| unstructuredDescription | string | Natural language description of this product's itinerary in the case that `itineraryType` is `"UNSTR |

---

## ItineraryDuration

Duration information for this itinerary

**Note**: Depending on whether this itinerary has a fixed or variable duration, this object will include either the `fixedValueInMinutes` element alone; or, both the `fromMinutes` and `toMinutes` elements, respectively.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| fixedDurationInMinutes | integer | Duration of this itinerary (in minutes) in the case that it takes a fixed amount of time |
| variableDurationFromMinutes | integer | Lower limit of the duration of this itinerary (in minutes) in the case that this product's duration  |
| variableDurationToMinutes | integer | Upper limit of the duration of this itinerary (in minutes) in the case that this product's duration  |
| unstructuredDuration | string |  |

---

## ItineraryPoi

Details about this Point Of Interest (POI)

### Properties

| Property | Type | Description |
|----------|------|-------------|
| location | LocationReference |  |
| attractionId | integer | Unique identifier in the Viator taxonomy of this point of interest if it is regarded as an attractio |

---

## AdmissionInclusionType

Machine-interpretable value encoding whether the admission fee for this place is included; one of:

  - `"YES"`
  - `"NO"`
  - `"NOT_APPLICABLE"`


---

## StandardItineraryItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| pointOfInterestLocation | ItineraryPoi |  |
| duration | ItineraryDuration |  |
| passByWithoutStopping | boolean | **True** if this product only 'passes by' this point of interest (i.e., travelers remain in the vehi |
| admissionIncluded | AdmissionInclusionType |  |
| description | string | Description of this itinerary item    - **Note**: This field contains natural language suitable for  |

---

## StandardItinerary

---

## ActivitiesItineraryItem

Location and description of this activity item

### Properties

| Property | Type | Description |
|----------|------|-------------|
| location | LocationReference |  |
| description | string | Description of this activity item    - **Note**: This field contains natural language suitable for d |

---

## ActivityFoodMenu

Food menu details for this activity

### Properties

| Property | Type | Description |
|----------|------|-------------|
| course | string | Machine-interpretable value encoding the meal course category for this menu item; one of:     - `"ST |
| dishName | string | Name of this dish - **Note**: This field contains natural language suitable for display to the user; |
| dishDescription | string | Description of this dish    - **Note**: This field contains natural language suitable for display to |

---

## ActivitiesItinerary

---

## MultiDayTourAccommodation

Details for this accommodation venue

### Properties

| Property | Type | Description |
|----------|------|-------------|
| description | string | Description of this accommodation venue    - **Note**: This field contains natural language suitable |
| location | LocationReference |  |

---

## MultiDayTourFoodAndDrinks

### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | string | One of:      - `"BREAKFAST"`,   - `"LUNCH"`,   - `"DINNER"`,   - `"SNACKS"`,   - `"BOTTLED_WATER"`,  |
| typeDescription | string | Description of the `type` element in this response - **Note**: This field contains natural language  |
| description | string | Description of the item - **Note**: This field contains natural language suitable for display to the |

---

## MultiDayTourItineraryDay

Details about a single day of a multi-day tour

### Properties

| Property | Type | Description |
|----------|------|-------------|
| title | string | Title of this day of the tour    - **Note**: This field contains natural language suitable for displ |
| dayNumber | integer | Number of this day |
| items | array of StandardItineraryItem | Places that this product visits or passes through on this day |
| accommodations | array of MultiDayTourAccommodation | Accommodation available for this day of this tour |
| foodAndDrinks | array of MultiDayTourFoodAndDrinks | Food and drinks available for this day of this tour |

---

## MultiDayTourItinerary

---

## HopOnHopOffStop

Place at which passengers can board or alight the tour vehicle

### Properties

| Property | Type | Description |
|----------|------|-------------|
| stopLocation | LocationReference |  |
| description | string | Description of this stop    - **Note**: This field contains natural language suitable for display to |

---

## HopOnHopOffItineraryRoute

### Properties

| Property | Type | Description |
|----------|------|-------------|
| operatingSchedule | string | Description of this product's operating schedule    - **Note**: This field contains natural language |
| duration | ItineraryDuration |  |
| name | string | Name of this route    - **Note**: This field contains natural language suitable for display to the u |
| stops | array of HopOnHopOffStop | Stops on this route |
| pointsOfInterest | array of ItineraryPoi | Locations of interest relevant to this route |

---

## HopOnHopOffItinerary

---

## UnstructuredItinerary

---

## ItineraryType

Machine-interpretable value specifying the type of itinerary available for this product; one of:

  - `"STANDARD"`
  - `"ACTIVITY"`
  - `"MULTI_DAY_TOUR"`
  - `"HOP_ON_HOP_OFF"`
  - `"UNSTRUCTURED"`


---

## TranslationDetails

Information about whether the text in this response was machine-translated

### Properties

| Property | Type | Description |
|----------|------|-------------|
| containsMachineTranslatedText | boolean | Indicates whether this product description utilizes text in any of its natural language fields that  |
| translationSource | string | One of: - `"MACHINE"` – The text provided by the supplier is in a **different language** and has bee |
| translationAttribution | string | Value specifying the machine-translation service vendor. At present, translation attribution is not  |

---

## Supplier

Supplier details

### Properties

| Property | Type | Description |
|----------|------|-------------|
| name | string | Name of the supplier of this product |
| reference | string | Unique reference code for this supplier |

---

## ViatorUniqueContent

Product details unique to Viator.com

**Note**: 
  - Access to this information is only available if it is enabled for your account. Please speak to your account manager if you would like to take advantage of our unique content.
  - You must ensure that your site is configured such that **no Viator Unique Content is indexed by any search engine**. This is a requirement for site certification. For more information, see [Key concepts – Protecting unique content](#section/Key-concepts/Protecting-unique-content)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| title | string | Viator-improved title of this product  This replaces the supplier-provided-title (given in the `titl |
| shortDescription | string | Viator-improved description of this product  This replaces the supplier-provided-description (given  |
| longDescription | string | Viator-improved natural-language description of this product's itinerary  This text is used in the ' |
| insiderTips | string | Viator's 'insider-tips' for this product  This text is used in the 'Overview – Why Travelers Chose T |
| highlights | array of string | Viator's 'highlights' for this product  These text items are used to provide additional bullet-point |

---

## ErrorResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| code | string |  |
| message | string |  |
| timestamp | string | Timestamp of the request.   **Example**: `"2019-09-17T03:20:45.737043Z"`  |
| trackingId | string | Tracking identifier for this error response.   **Example**: `"0A871A13:DE2A_0A8712F9:01BB_5DCCC98C_2 |

---

## TagWithAllLocalizations

Category/subcategory tag for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| tagId | integer | Unique identifier for this tag |
| parentTagIds | array of integer | Unique identifiers for parent tags of this tag |
| allNamesByLocale | object | Dictionary of language codes to the description of this tag in that language |

---

## TagsResponse

Numeric product category/subcategory tag identifiers for this product

To retrieve details about which tags these identifiers refer to, please use the [/products/tags](#operation/productsTags) endpoint.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| tags | array of TagWithAllLocalizations |  |

---

## PaxMixItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | string | Machine-interpretable value indicating the age-band that this/these traveler(s) fall into; one of:   |
| numberOfTravelers | integer | Number of travelers/passengers in this age-band |

---

## CapacityObject

Provides capacity information for the selected `bookableItem`.

**Note:** Capacity information is not available for all products. The absence of the capacity object or its fields does not indicate that the product is sold out or unavailable.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| remainingCapacity | integer | Indicates how many spots are available for booking at the time of the request for the specified `boo |

---

## NumberOfTravelers

The number of travelers that this line-item describes the subtotal price for.

---

## ExtraChargesItem

List of extra charges. Partners can use this to build a breakdown list of costs.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| name | string | Extra Charges description. |
| numberOfUnits | number | How many times the Extra Charges applies.  If the Extra Charges value is to be charged per person th |
| amountPerUnit | number | The amount per unique Extra Charges. |
| totalAmount | number | Total amount of all Extra Charges for a given item. |
| inDestination | ExtraChargesItemInDestinationCurrency |  |

---

## ExtraChargesSummary

Information about the Extra Charges applicable to this `bookableItem`.

**Note**:
  - Prices payable to third parties are provided to us by the operator, and may be subject to change.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| price | object | Pricing information applicable to this `bookableItem` including extra charges. |
| priceBeforeDiscount | object | Pricing information applicable to this `bookableItem` including extra charges if no discount had bee |
| mandatory | object | Information about the mandatory Extra Charges applicable to this `bookableItem`. |

---

## UnavailableDate

### Properties

| Property | Type | Description |
|----------|------|-------------|
| date | string | Date on which the product is unavailable |
| reason | string | Machine-interpretable reason code indicating why this bookable item is unavailable on this date; one |

---

## TimedEntry

### Properties

| Property | Type | Description |
|----------|------|-------------|
| startTime | string | Starting time for this timed entry - **Example**: `"09:00:00"`   |
| unavailableDates | array of UnavailableDate | Dates on which this timed entry is unavailable. If no unavailable dates exist, this array will be ab |

---

## Special

---

## OperatingHours

### Properties

| Property | Type | Description |
|----------|------|-------------|
| opensAt | string | Opening time; e.g. `"08:30"` |
| closesAt | string | Closing time; e.g. `"17:30"` |

---

## DayOperatingHours

### Properties

| Property | Type | Description |
|----------|------|-------------|
| dayOfWeek | string | Day of the week that these operating hours pertain to |
| operatingHours | array of OperatingHours | Opening and closing times for this day of the week |

---

## BookableItemSeason

### Properties

| Property | Type | Description |
|----------|------|-------------|
| startDate | string | Starting date for when this pricing and availability information applies - **Example**: `"2019-01-01 |
| endDate | string | Ending date for when this pricing and availability information applies.  - **Note**: if this element |
| pricingRecords | array of PricingRecord | Pricing records for this season |
| operatingHours | array of DayOperatingHours | Details about hours of operation for this season  |

---

## Currency

**Merchant Partners:** One of `USD`, `EUR`, `GBP`, `AUD`, `CAD`

**Affiliate Partners with API access level "Full Access + Booking":** One of `USD`, `EUR`, `GBP`, `AUD`, `CAD`,
`CHF`, `DKK`, `FJD`, `HKD`, `JPY`, `NOK`, `NZD`, `SEK`, `SGD`, `THB`, `ZAR`, `INR`, `BRL`, `TWD`, `MXN`, `CLP`, `IDR`, `ILS`, `KRW`, `PHP`, `PLN`, `TRY`


---

## StartTime

Starting time for the item in the case that the `product`/`product option` has multiple start times.

**Note**: This element must be included for products that have multiple starting times.


---

## TravelDate

Date of travel (according to the time zone in which the product operates).


---

## AgeBand-2

Machine-interpretable value indicating the age-band that this/these
traveler(s) fall into; one of:

  - `ADULT`
  - `SENIOR`
  - `YOUTH`
  - `CHILD`
  - `INFANT`
  - `TRAVELER`

The valid age-band identifiers for the product are provided in the `pricingInfo.ageBands[]` array in the [product content response](#section/Key-concepts/Content-ingestion-endpoints). The `TRAVELER` age-band is to be used when the `pricingInfo.type` is `UNIT`; i.e., unit or group pricing.

To learn more about how to implement age bands, see the following guide: [Implementing age bands & pax mix](https://partnerresources.viator.com/travel-commerce/merchant/agebands-pax-mix?source=specs)


---

## PaxMixItem-2

### Properties

| Property | Type | Description |
|----------|------|-------------|
| ageBand | AgeBand-2 |  |
| numberOfTravelers | integer | Number of travelers/passengers in this age-band. |

---

## HoldInfo

### Properties

| Property | Type | Description |
|----------|------|-------------|
| status | string | Status of the booking hold; one of:    - `HOLD_NOT_PROVIDED`   - `HOLDING`  |
| validUntil | string | Timestamp (UTC) indicating when the booking hold expires. |

---

## HoldRejectionReasonCode

In the case that `status` is `REJECTED`, this field provides a code as to the reason for the rejection; one of:

  - `BOOKABLE_ITEM_IS_NO_LONGER_AVAILABLE` – this bookable item is no longer available
  - `FAILED_TO_CHECK_AVAILABILITY_OR_PRICING` – Unable to retrieve availability or pricing data for this bookable item
  - `OTHER` – other/unlisted reason


---

## BookerInfo

Name details for the person making this booking.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| firstName | string | First name (given name) of the person making this booking.  **Note**: Emojis are not supported in th |
| lastName | string | Surname of the person making this booking.  **Note**: Emojis are not supported in this field. Please |

---

## VoucherDetails

**Merchant partners only**: Additional details to display on the voucher.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| companyName | string | Company name to display on the voucher. |
| email | string | Company / customer support email address to display on the voucher. |
| phone | string | Company / customer support phone number to display on the voucher. |
| voucherText | string | Any additional custom text to display on the voucher; e.g., Customer support URL / instructions on h |
| format | string | File format of the voucher; one of: - `PDF` - `HTML`  Default is `HTML` if not specified.  |

---

## FraudPreventionDetails

Additional booking details used to enhance fraud detection accuracy.

**Note**: Fraud Prevention Details only apply to <u>affiliate partners with API access level "Full Access + Booking"</u>.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| subChannelId | string | For partners that operate multiple channels, a unique identifier of the channel making the booking.  |
| agencyId | string | For partners that operate multiple agencies, a unique identifier representing the agency making the  |
| agentId | string | For partners that have agents making bookings, a unique identifier for the agent making the booking. |
| voucherDeliveryType | string | Method of voucher delivery. One of:    - `EMAIL_TO_CUSTOMER` - The voucher is emailed only to the cu |
| customerMemberSince | string | For partners whose customers have a membership with the partner and the customer is making the booki |

---

## LoyaltyProgramDetails

Additional booking details used to associate partner's Loyalty Program Information with the booking.

**Note**:
  This data will be used only by Viator’s internal teams (eg, by Customer Service in the event the traveler contacts Viator for any reason).


### Properties

| Property | Type | Description |
|----------|------|-------------|
| memberId | string | A unique identifier assigned to the member of partner’s loyalty program. |
| points | integer | The amount of loyalty points redeemed in this booking. |
| totalPriceAfterPoints | number | Actual amount paid for the booking after redeeming loyalty points. |

---

## VoucherFormat

File format of the voucher; one of:
  - `PDF`
  - `HTML`

Default is `HTML` if not specified.


---

## VoucherInfo

Voucher information for this booking.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| url | string | URL from which this voucher can be retrieved. |
| format | VoucherFormat |  |
| type | string | Whether it is a Viator standard voucher or a supplier provided voucher; one of:  - `STANDARD` - `SUP |
| isVoucherRestrictionRequired | boolean | Indicates if the transaction was flagged as potentially fraudulent. If set to `true`, partners must  |

---

## CommunicationInfo

Details for correspondence regarding this booking.

**See**: [Booking concepts – Supplier communications](#section/Booking-concepts/Supplier-communications) for information about closed-loop communication.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| phone | string | Telephone number to be used for correspondence from the supplier regarding the booking. This can be  |
| email | string | Email addresses to be used for correspondence from the supplier regarding the booking.  **Note**: In |

---

## AmendmentStatus

Machine-interpretable string indicating the outcome of the booking amendment request. One of:
  - `AMENDED`: The amendment was successful
  - `REJECTED`: The amendment was rejected
  - `PENDING`: The amendment is pending

**Note**: If booking has been amended multiple times, this field will only reflect the latest amendment request status (ie, if the booking was amended once and a second amendment request is rejected, the amendment status response will be `REJECTED`)


---

## AmendmentRejectionReasonCode

Machine-interpretable reason code indicating why the amendment was `REJECTED`. One of:

  - `"BOOKABLE_ITEM_IS_NO_LONGER_AMENDABLE”` – this bookable item is no longer eligible to be amended due to updated restrictions or conditions.
  - `"BOOKABLE_ITEM_IS_NO_LONGER_AVAILABLE"` – this bookable item is no longer available. The selected bookable item is no longer available for the specified travel date /start time / pax mix combination. Retrieve current availability and generate a new quote before attempting the amendment again.
  - `"PRICE_MISMATCH"` – the quotePriceDifference is no longer valid. The product's price has changed since the quotePriceDifference was generated, re-submit the amendment request to receive an updated quote.
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

**Note**: New values may be added over time, allowing flexibility for different use cases.


---

## NextPollAt

Timestamp (UTC) indicating the recommended time the endpoint should be hit again.

Example: "2025-04-03T02:54:29.082753Z"


---

## CancellationReason

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cancellationReasonText | string | Natural-language description of this cancellation reason |
| cancellationReasonCode | string | Machine-interpretable identification code for this cancellation |

---

## CancellationReasonsResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reasons | array of CancellationReason | Array of cancellation reason codes and their asssociated texts for display to the user |

---

## RefundDetails

Details of the refund.

**Note**: Bookings that have not been confirmed by the supplier and have a status of `"PENDING"` will report an `itemPrice`, `refundAmount` and `refundPercentage` of `0`, as no fees are charged until the booking has been accepted by the supplier and its status is `"CONFIRMED"`.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| itemPrice | number | The merchant total price at the time this product was booked. |
| refundAmount | number | Numeric currency amount that will be refunded. |
| refundPercentage | number | Percentage of the item price that will be refunded. |
| currencyCode | string | Three-letter code indicating the currency in which `itemPrice` and `refundAmount` are displayed. |

---

## CancellationRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reasonCode | string | Machine-interpretable identification code for this cancellation reason, retrieved from [/bookings/ca |

---

## CancellationResultItemReason

Machine-interpretable reason code indicating why the cancellation was not successful

  - `"ALREADY_CANCELLED"`: The booking has already been cancelled
  - `"NOT_CANCELLABLE"`: The booking cannot be canceled because the product start time was in the past


**Note**: This field will not be present in the response if the cancellation was successful


---

## EventsAcknowledgementRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| transactionRefs | array of string | List of booking event notification reference codes for which to acknowledge receipt |

---

## Address

Minimal billing address details for cardholder

### Properties

| Property | Type | Description |
|----------|------|-------------|
| country | string | The country of the registered billing address, in two character ISO_3166-1 alpha-2 format. |
| postalCode | string | The post code of the registered billing address. 4-9 alphanumeric characters, optionally separated s |

---

## CreditCardRequest

PCI sensitive details for a debit or credit card and relevant metadata.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| number | string | The full card number, without spaces. |
| cvv | string | The three or four digit CVV. |
| expMonth | string | Two digit representation of expiry month. |
| expYear | string | Four digit representation of expiry year. |
| name | string | The cardholder's full name. |
| address | Address |  |

---

## PaymentAccountsRequest

Wrapper element around payment data.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| creditCards | array of CreditCardRequest | Array of card data, normal use is single item. |

---

## VaultCardRequest

The card submission payload.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| paymentAccounts | PaymentAccountsRequest |  |

---

## AccountMetaData

### Properties

| Property | Type | Description |
|----------|------|-------------|
| sessionAccountToken | string | Token for the submitted card, to be supplied when payment is requested. |

---

## CreditCard

### Properties

| Property | Type | Description |
|----------|------|-------------|
| cardType | string | The name of card network for the card submitted. |
| expMonth | string | Two digit representation of expiry month. |
| expYear | string | Four digit representation of expiry year. |
| name | string | The cardholder's full name. |
| accountHead | string | The first six numbers of the card, the BIN portion. |
| accountTail | string | The last four numbers of the card. |
| address | Address |  |
| accountMetaData | AccountMetaData |  |

---

## PaymentAccounts

### Properties

| Property | Type | Description |
|----------|------|-------------|
| creditCards | array of CreditCard |  |

---

## VaultPaymentResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| paymentAccounts | PaymentAccounts |  |

---

## BulkLocationReferencesRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| locations | array of string | List of location reference identifiers for which to retrieve full location details.  |

---

## Location

Location detail

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reference | string | Unique identifier for this location as given in the request |
| provider | LocationProvider |  |

---

## LocationAddress

Address details for this location

### Properties

| Property | Type | Description |
|----------|------|-------------|
| street | string | Street address of this location    - **Example**: `"1 George St."`  |
| administrativeArea | string | Administrative area this location falls into    - **Example**: `"Sydney"`  |
| state | string | State or region of this location    - **Example**: `"New South Wales"`  |
| country | string | Country of this location    - **Example**: `"Australia"`  |
| countryCode | string | Two-character Alpha-2 country-code for this location    - **Example**: `"AU"`  |
| postcode | string | Post code of this location    - **Example**: `"2000"`  |

---

## LocationCenter

Geographic coordinates (latitude/longitude) for this location

### Properties

| Property | Type | Description |
|----------|------|-------------|
| latitude | number | Latitude of this location    - **Example**: `-33.870037`  |
| longitude | number | Longitude of this location    - **Example**: `151.20955`  |

---

## ResolvedLocation

---

## ProvidedLocation

---

## LocationProvider

Name of the location services provider, one of:

  - `"TRIPADVISOR"` – location details will be provided in this response
  - `"GOOGLE"` – in order to retrieve details for these locations, you will need to use [Google's Places API](https://cloud.google.com/maps-platform/places).


---

## LocationsResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| locations | array of Location | Locations |

---

## ExchangeRatesRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| sourceCurrencies | array of string | List of three-letter currency codes for the source currencies for which to retrieve exchange rate da |
| targetCurrencies | array of string | List of three-letter currency codes for the target currencies for which to retrieve exchange rate da |

---

## ExchangeRateItem

### Properties

| Property | Type | Description |
|----------|------|-------------|
| sourceCurrency | string | Base currency for this conversion rate |
| targetCurrency | string | Target currency for this conversion rate |
| rate | number | Value of `targetCurrency` per unit of `sourceCurrency` |
| lastUpdated | string | Timestamp (UTC) indicating the last time this currency exchange rate was updated  |
| expiry | string | Timestamp (UTC) indicating until when this rate will apply  |

---

## ExchangeRatesResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| rates | array of ExchangeRateItem | Currency exchange rates |

---

## ReviewPhoto

### Properties

| Property | Type | Description |
|----------|------|-------------|
| height | integer | Height of image in pixels |
| width | integer | Width of image in pixels |
| url | string | URL at which this image is located |

---

## ReviewPhotoInfo

### Properties

| Property | Type | Description |
|----------|------|-------------|
| photoVersions | array of ReviewPhoto | Width and height variants of this review image and associated URLs |

---

## ContactDetails

### Properties

| Property | Type | Description |
|----------|------|-------------|
| email | string | Email address of this supplier (for the office managing this product) |
| address | string | Address of this supplier (for the office managing this product) |
| phone | string | Phone number of this supplier (for the office managing this product) |
| countryCode | string | Country code of this supplier (for the office managing this product) |

---

## AmendmentTypes

List of booking components that can be amended in this booking:
  - `"BOOKING_DETAILS"`
  - `"UPDATE_PAX_MIX"`
  - `"PER_TRAVELER_QUESTIONS"`
  - `"PER_BOOKING_QUESTIONS"`

**Notes**:
 - Only one amendmentType can be updated per request
 - This field will not be present in the response if `isAmendable` is `false`
 - New values may be added over time, allowing flexibility for different use cases.


---

## PaxMixSummary

Summary of the current PAX MIX of the booking.  
It ensures each traveler listed in the PaxMix is assigned a `travelerNum` and informs which Booking Questions have been answered for each at the time of the booking.

**Note**: This field will not be present in the response if `isAmendable` is `false`


---

## AmendmentCheckResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | BookingRef |  |
| isAmendable | boolean | Indicates whether the booking can be amended.   If `false`, the booking cannot be amended.  |
| reason | string | Machine-interpretable reason code indicating why the amendment can not proceed. One of:   - `"UNSUPP |
| amendmentTypes | AmendmentTypes |  |
| paxMixSummary | PaxMixSummary |  |

---

## AmendmentQuoteRequestCommon

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | BookingRef |  |

---

## AmendPaxMix

---

## AmendPerTravelerQuestions

---

## AmendmentQuoteRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| voucherFormat | VoucherFormat |  |

---

## QuoteStatus

Machine-interpretable string indicating the outcome of the quote request. One of:
  - `CONFIRMED`: The quote was successful
  - `REJECTED`: The quote was rejected


---

## AmendmentQuoteResponseCommon

### Properties

| Property | Type | Description |
|----------|------|-------------|
| bookingRef | BookingRef |  |
| status | QuoteStatus |  |

---

## QuoteReference

Unique Viator-generated quote reference for a booking.

---

## QuoteValidUntil

Timestamp (UTC) indicating when the quote expires.

---

## PaymentMethod

Information about the payment method to be used for this transaction.

**Notes:**
  - The transaction will be processed using the payment method already associated with the booking being amended.
  - Payment method is only relevant for transactional affiliates.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| type | string | Payment method type. Possible values:   - `CARD`  **Note:** new values may be added over time, allow |
| identifierType | string | Determines how the value of the identifier should be interpreted. One of the following.   - `CARD_LA |
| identifier | string | Value which should be used to identify the payment method.  |

---

## AmendmentQuoteResponseConfirmed

---

## QuoteRejectionReasonCode

Machine-interpretable reason code indicating why the quote was rejected. One of:
  - `"NO_AVAILABILITY"`: This bookable item is not available for the specified combination of date, time and passenger mix
  - `"BOOKABLE_ITEM_IS_NO_LONGER_AMENDABLE"` – this bookable item is no longer eligible to be amended due to updated restrictions or conditions.
                       


---

## AmendmentQuoteResponseRejected

---

## AmendmentQuoteResponse

---

## AmendmentAmendResponseCommon

### Properties

| Property | Type | Description |
|----------|------|-------------|
| status | AmendmentStatus |  |

---

## AmendmentAmendResponseInProgress

---

## AmendmentAmendResponseAmended

---

## AmendmentAmendResponseRejected

---

## AmendmentAmendResponse

---

