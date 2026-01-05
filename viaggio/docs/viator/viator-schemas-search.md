# Viator API Schemas - Search

## SearchRatingInfo

Only return products that have a rating that is in the range defined here


### Properties

| Property | Type | Description |
|----------|------|-------------|
| from | integer | Only return products with a rating greater than this value  |
| to | integer | Only return products with a rating less than this value  |

---

## SearchDurationInfo

Only return products that have a duration that is in the range defined here


### Properties

| Property | Type | Description |
|----------|------|-------------|
| from | integer | Match products with durations longer than this value  |
| to | integer | Match products with durations shorter than this value  |

---

## SearchType

### Properties

| Property | Type | Description |
|----------|------|-------------|
| searchType | string | Specifies a domain within which the search should be performed  One of: - `"ATTRACTIONS"` - `"DESTIN |
| pagination | ProductSearchPagination |  |

---

## FreetextSearchRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| searchTerm | string | Return results that contain this free-text search term  |
| productFiltering | FreetextSearchProductFiltering |  |
| productSorting | FreetextSearchProductSorting |  |
| searchTypes | array of SearchType | Specifies the domain(s) in which to search for the `searchTerm` and the respective pagination detail |
| currency | string | Currency code of price range in request filter and the prices in response.  One of: `"AUD"`, `"BRL"` |

---

## DestinationSearchResult

### Properties

| Property | Type | Description |
|----------|------|-------------|
| id | integer | **unique numeric identifier** of the destination  - use this value as the `destination` input field  |
| name | string | **natural-language name** of the destination  |
| parentDestinationId | integer | **unique numeric identifier** of the destination's parent destination  |
| parentDestinationName | string | **natural-language name** of the destination's parent destination  |
| translationInfo | TranslationDetails |  |
| url | string | URL of destination  |

---

## FreetextSearchResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| destinations | object | Destinations that include the `searchTerm` when `"DESTINATIONS"` results are requested via `searchTy |
| attractions | object | Attractions that include the `searchTerm` when `"ATTRACTIONS"` results are requested via `searchType |
| products | object | Products that include the `searchTerm` when `"PRODUCTS"` results are requested via `searchTypes`  |

---

## AttractionsSearchRequest

### Properties

| Property | Type | Description |
|----------|------|-------------|
| destinationId | integer | Unique numeric identifier of the destination to retrieve attractions for  |
| sorting | object | How the search results will be sorted |
| pagination | object | Pagination details specifying which search results to return based on start position and item count |

---

## AttractionsSearchResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| attractions | array of AttractionDetails |  |
| totalCount | integer | Total number of products matching the filtering criteria – these may be accessed via multiple calls  |

---

