# Viator API Schemas - Product

## Product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| status | ProductStatus |  |
| productCode | string | Code that is the unique identifier for this product.    - Example: `"5657BRIDGECLIMB"`  |
| language | string | Code indicating the language into which the natural-language fields in this response will be transla |
| createdAt | string | Timestamp (UTC) indicating when this product was originally created    - Example: `"2019-04-03T02:54 |
| lastUpdatedAt | string | Timestamp (UTC) indicating the most recent occasion of this product's details being modified    - Ex |

---

## ProductOption

Detail about a single product option for this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productOptionCode | string | Identification code for this product option     - **Example**: `"BCLM"`   For more information see:  |
| description | string | Description of this product option  **Note**:  - Please note that whether this field contains the ph |
| title | string | Title of this product option    - **Note**: This field contains natural language suitable for displa |
| languageGuides | array of LanguageGuide | Language guides available for this product option |

---

## ProductReviewCount

Breakdown of number of reviews for each rating of this product

### Properties

| Property | Type | Description |
|----------|------|-------------|
| rating | number | Rating given in the review for this product |
| count | integer | How many reviews of this product have this rating |

---

## ProductReviewSource

### Properties

| Property | Type | Description |
|----------|------|-------------|
| provider | string | Source of the review; one of:   - `"VIATOR"`   - `"TRIPADVISOR"`  |
| reviewCounts | array of ProductReviewCount | Breakdown of ratings and counts for reviews from this source for this product |
| totalCount | integer | Total number of reviews for all ratings of this product |
| averageRating | number | Average rating across all reviews from this source for this product  This average is equal to the su |

---

## ProductReviews

Summary of reviews and ratings for this product

**Note**: 

  - Review data is updated daily; i.e., all reviews received on a day will be added and averages re-calculated in a single event.
  - Viator performs checks on reviews - for more information, see [Key concepts - Review authenticity](#section/Key-concepts/Review-authenticity)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| sources | array of ProductReviewSource | Breakdown of ratings, counts and the sources of the reviews of this product |
| reviewCountTotals | array of ProductReviewCount | Combined total number of reviews per rating across all sources for this product |
| totalReviews | integer | Total number of reviews from all sources for this product |
| combinedAverageRating | number | Average rating for all reviews from all sources for this product |

---

## ActiveProduct

---

## InactiveProduct

---

## ProductStatus

Machine-interpretable value indicating this product's current availablility; one of:

  - `"ACTIVE"` - product is available for sale
  - `"INACTIVE"` - product is not available for sale (remainder of object will be empty)


---

## ProductsResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| products | array of Product | Products that fall within the search/filter criteria |
| nextCursor | string | Pagination cursor pointing to the next page of results - Example: `"MTU3NDA0NDczOQ=="`  |

---

## BulkProductRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCodes | array of string | List of product codes for which to retrieve full product details |

---

## ProductSearchFlag

One of:

  - `"NEW_ON_VIATOR"` – products that have been added to Viator's catalogue within the past 270 days
  - `"SKIP_THE_LINE"` – products that allow participants to attend a location without having to obtain a separate ticket on the occasion itself (`itinerary.skipTheLine` is `true`)
  - `"PRIVATE_TOUR"` – products where only the travelers who have booked the product will be present (`itinerary.privateTour` is `true`)
  - `"SPECIAL_OFFER"` – products that have a pricing discount available (i.e., `summary.fromPriceBeforeDiscount` will be present in the response from [/availability/schedules/{product-code}](#operation/availabilitySchedules))
  - `"LIKELY_TO_SELL_OUT"` - popular products that routinely sell out (this is equivalent to filtering by tag `20757`).


---

## ProductSearchFiltering

Only return products that match **all** the criteria provided here.


### Properties

| Property | Type | Description |
|----------|------|-------------|
| destination | string | Only return products that include the destination indicated by this numeric destination reference (a |
| tags | array of integer | Only return products that include **all** tag identifiers provided here. Products with child tags of |
| flags | array of ProductSearchFlag | Only return products that include **all** of the given attributes, which may include any of:    - `" |
| confirmationType | string | Only return products with this confirmation type; one of:      - `"INSTANT"` (instant confirmation)  |
| rating | SearchRatingInfo |  |
| durationInMinutes | SearchDurationInfo |  |
| includeAutomaticTranslations | boolean | Specifies whether results with machine translated content should be included or not |
| attractionId | integer | Only return products that are associated with the **attraction** referenced by this unique numeric i |
| lowestPrice | number | Only return products that have a `fromPrice` that is higher than or equal to this price. If a date r |
| highestPrice | number | Only return products that have a `fromPrice` that is lower than or equal to this price. If a date ra |
| startDate | string | Only return products that are available during a period of time starting from this date.  - **Format |
| endDate | string | Only return products that are available during a period of time ending on this date.   - **Format**: |

---

## ProductSearchSorting

How the search results will be sorted

### Properties

| Property | Type | Description |
|----------|------|-------------|
| sort | string | Method by which product search results will be sorted; one of:      - `"DEFAULT"`: the default sort, |
| order | string | Ordering of product search results when `sort` is `"PRICE"`  One of:    - `"ASCENDING"`   - `"DESCEN |

---

## ProductSearchPagination

Pagination details specifying which search results to return based on start position and item count

### Properties

| Property | Type | Description |
|----------|------|-------------|
| start | integer | Position of first filtered and ordered search result to be included in the response (1-based) |
| count | integer | Number of filtered and ordered search results to be returned in the response |

---

## ProductSearchRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| filtering | ProductSearchFiltering |  |
| sorting | ProductSearchSorting |  |
| pagination | ProductSearchPagination |  |
| currency | string | Currency code for all prices provided in the request; and, the currency in which all pricing will be |

---

## ProductSearchPricing

High-level summary of product prices
  
  - **Note**: This price may not be available during the date range specified in the `filtering` section of the request


### Properties

| Property | Type | Description |
|----------|------|-------------|
| summary |  |  |
| currency | string | Currency code for the currency in which the prices in `summary` are denominated |
| partnerNetFromPrice | number | Lowest per-person price for this product expressed as the amount (excluding the booking fee)that mer |
| extraChargesSummary | AvailabilityScheduleExtraChargesSummary |  |

---

## ProductSummary

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Code that is the unique identifier for this product.  - Example: `"5657BRIDGECLIMB"`  |
| title | string | Natural-language title of this product    - **Example**: `"Sydney BridgeClimb"`   - **Note**: This f |
| description | string | Description of this product  - **Example**: "Climb the Sydney Harbour Bridge with an expert guide fo |
| images | array of Image | Images for this product |
| reviews | ProductReviews |  |
| duration | ItineraryDuration |  |
| pricing | ProductSearchPricing |  |
| productUrl | string | URL for this product on the viator.com site, where the customer will complete their booking.  This U |
| destinations | array of Destination | Destinations in which this product operates.  - **Note**: At present, only the primary destination I |
| tags | array of integer | Array of numeric tag identifiers indicating the product categories into which this product falls   T |
| flags | array of ProductSearchFlag | List of product attribute flags specified in the request  May include any of:    - `"NEW_ON_VIATOR"` |
| confirmationType | ConfirmationType |  |
| itineraryType | ItineraryType |  |
| translationInfo | TranslationDetails |  |

---

## ProductSearchResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| products | array of ProductSummary | List of products matching the filtering criteria, sorted and paginated as specified in the request |
| totalCount | integer | Total number of products matching the filtering criteria – these may be accessed via multiple calls  |

---

## BulkProductRecommendationsRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCodes | array of string | The unique identifier of the product(s) for which recommendations are being retrieved. |
| recommendationTypes | array of string | Types of recommendation. One of: - `IS_SIMILAR_TO`: returns products that are deemed similar to the  |

---

## ProductRecommendation

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | The unique identifier of the product for which recommendations are being retrieved. |
| recommendations | object | A map of recommended product lists, categorized by different recommendation types.  The keys being t |

---

## FreetextSearchProductFiltering

Criteria by which to filter product search results (i.e., when `searchTypes` includes `"PRODUCTS"`)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| destination | string | Match results that are assigned this destination. Only Viator destination integer ID is accepted for |
| dateRange | object | Match products that are available to be booked on one or more of the days included in this date rang |
| price | object | Match products which have a 'from price' within the range indicated here  |
| rating | object | Match products that have an average rating within the range indicated here  |
| durationInMinutes | object | Match products that have a duration (length of time the experience lasts) within the range indicated |
| tags | array of integer | Only return products that include **all** tag identifiers provided here. Products with child tags of |
| flags | array of ProductSearchFlag | Match products that have the following attributes:  Any of:    - `"NEW_ON_VIATOR"` – products that h |
| includeAutomaticTranslations | boolean | Specifies whether proucts with automatically machine-translated content (no human oversight) should  |

---

## FreetextSearchProductSorting

Specify the sorting method for product results (i.e., when `searchTypes` includes `"PRODUCTS"`)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| sort | string | The method of sorting product search results. One of: - `"DEFAULT"`: sorts based on search term to r |
| order | string | The direction of sorting search results. One of:  - `"ASCENDING"` - `"DESCENDING"`  |

---

## ProductReviewsSummaryCount

### Properties

| Property | Type | Description |
|----------|------|-------------|
| rating | number | This object refers to reviews with this star-rating |
| count | integer | Number of reviews for this product with a star-rating of `rating` |

---

## ProductReviewsSummarySource

### Properties

| Property | Type | Description |
|----------|------|-------------|
| provider | string | Provider for this set of reviews; one of: - `"VIATOR"` - `"TRIPADVISOR"`  |
| reviewCounts | array of ProductReviewsSummaryCount | Breakdown of number of reviews per rating for reviews sourced from this provider |
| totalCount | integer | Total number of reviews for this product sourced from this provider |

---

## ProductReviewsSummary

Summary of reviews and ratings for this attraction

**Note**:
  - Review data is updated daily; i.e., all reviews received on a day will be added and averages re-calculated in a single event.
  - Viator performs checks on reviews - for more information, see [Review authenticity](#section/Key-concepts/Review-authenticity)


### Properties

| Property | Type | Description |
|----------|------|-------------|
| sources | array of ProductReviewsSummarySource | Breakdown of review summaries for each review source |
| reviewCountTotals | array of ProductReviewsSummaryCount | Breakdown of number of reviews per rating for all reviews of this product |
| totalReviews | integer | Total number of reviews available for this product from all sources |
| combinedAverageRating | number | Combined average rating for this product across all reviews from all sources |

---

## ProductBookableItemSchedule

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productOptionCode | string | Product option code for this bookable item schedule  For more information see: [Key concepts: Produc |
| seasons | array of BookableItemSeason | Descriptions of pricing and availability information as they pertain to periods of time |

---

## ProductAvailabilitySchedule

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Unique identifier for this product |
| bookableItems | array of ProductBookableItemSchedule | Bookable items for this product |
| currency | string | Three letter currency code for all pricing information in this response; based on the supplier's cur |
| summary | AvailabilityScheduleSummary |  |
| extraChargesSummary | AvailabilityScheduleExtraChargesSummary |  |

---

## ProductCode

Unique identifier for this product.

---

## ProductOptionCode

Product option identifier.

For more information see: [Key concepts: Product options](#section/Key-concepts/Product-options)


---

## ProductReviewsRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCode | string | Retrieve reviews for the product identified by this product code |
| count | integer | Number of reviews to be returned in the response; used for pagination |
| start | integer | Position of first review to be returned in the response; used for pagination |
| provider | string | Limit the reviews returned in the response to those associated with this provider; one of:  - `"VIAT |
| sortBy | string | One of:  - `"HIGHEST_RATING_PER_LOCALE"` – sort by rating (descending) *for each locale* - `"MOST_RE |
| reviewsForNonPrimaryLocale | boolean | Set to `true` to include reviews submitted by users from locales that are not the primary locale as  |
| showMachineTranslated | boolean | Set to `true` to include machine-translated reviews. |
| ratings | array of integer | Only include reviews with these ratings  **Example**: `[3,4,5]` to receive reviews with a rating of  |

---

## ProductReview

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reviewReference | string | Unique identification code for this review |
| language | string | Language code for the language in which this review is written |
| avatarUrl | string | URL for the avatar image (if available) for the reviewer that authored this review |
| publishedDate | string | Date-time stamp indicating when this review was published  E.g.: `2021-01-02T11:17:12Z`  |
| userName | string | Username of the reviewer who submitted this review |
| rating | integer | Star-rating for this product given by this reviewer in this review |
| text | string | Main text of this review  - **Note**: This field contains natural language suitable for display to t |
| title | string | Title of this review  - **Note**: This field contains natural language suitable for display to the u |
| machineTranslated | boolean | Indicates whether the natural-language elements of this review have been machine translated |
| provider | string | Provider for this review; one of:    - `"VIATOR"`   - `"TRIPADVISOR"`  |
| ownerResponse | object | Response to this review from the supplier of this product if available |
| helpfulVotes | integer | Number of times this review has been labeled 'helpful' by other users |
| photosInfo | array of ReviewPhotoInfo | Information about any photographs that were submitted with this review |

---

## ProductReviewsResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reviews | array of ProductReview | Reviews and review metadata for this product, from `start` to (`start`+`count`)  |
| totalReviewsSummary | object | Summary of the set of all reviews available for this product |
| filteredReviewsSummary | object | Summary of the set of reviews available for this product filtered by `provider`, `ratings`, `reviews |

---

## BulkSupplierProductRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| productCodes | array of string |  |

---

## SupplierProductInfo

### Properties

| Property | Type | Description |
|----------|------|-------------|
| reference | string | Unique reference code for this supplier |
| name | string | Name of this supplier |
| supplierInfoVerified | boolean | Supplier has passed Viator's 'know your business customer' checks required by the DSA. |
| supplierAgreedToLegalCompliance | boolean | The operator has self-certified that they are committed to only offer services that comply with appl |
| registrationCountry | string | Country where the supplier is registered (if supplier operates through a registered business entity) |
| tradeRegisterName | string | Name of business register (if supplier operates through a registered business entity) |
| registeredBusinessNumber | string | A unique identifier assigned to a business entity by a government authority for the purpose of regul |
| type | string | Whether this supplier is a business or an individual  One of:   - `"BUSINESS"`   - `"INDIVIDUAL"`  N |
| logo | string | Supplier logo / trademark |
| productCode | string | Product code to which this supplier search result pertains |
| contact | ContactDetails |  |

---

## SupplierProductResponse

Supplier details for the given product code

### Properties

| Property | Type | Description |
|----------|------|-------------|
| suppliers | array of SupplierProductInfo |  |

---

