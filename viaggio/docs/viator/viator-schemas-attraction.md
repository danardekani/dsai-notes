# Viator API Schemas - Attraction

## AttractionResult

### Properties

| Property | Type | Description |
|----------|------|-------------|
| id | integer | unique numeric identifier of the attraction |
| name | string | natural-language title of the attraction  **Note**: This field contains natural language suitable fo |
| primaryDestinationId | integer | unique numeric identifier of this attraction's primary destination |
| description | string | natural-language descriptive text for this attraction  **Note**: This field contains natural languag |
| destinationName | string | natural-language name of the primary destination associated with this attraction  **Note**: This fie |
| productsCount | integer | Number of products associated with this attraction |
| translationInfo | TranslationDetails |  |
| reviews | ProductReviewsSummary |  |
| images | array of Image |  |

---

## AttractionDetails

### Properties

| Property | Type | Description |
|----------|------|-------------|
| attractionId | integer | Unique numeric identifier for this attraction |
| name | string | Natural-language title of this attraction  **Note**: This field contains natural language suitable f |
| destinations | array of object | Destinations associated with this attraction |
| attractionUrl | string | **URL** to forward users to in order to complete their purchase on the Viator site  This URL include |
| productCount | integer | Number of products associated with the attraction |
| productCodes | array of string | List of `productCodes` associated with the attraction |
| images | array of ImageVariant | Images for this attraction |
| reviews | ProductReviewsSummary |  |
| freeAttraction | boolean | Identifies if a admission fee is required to access this attraction |
| openingHours | string | This attraction Opening Hours |
| viatorUniqueContent | object | Attraction details unique to Viator.com  **Note**:   - Access to this information is only available  |
| translationInfo | TranslationDetails |  |
| center | LocationCenter |  |
| address | object | Address details for this attraction |

---

