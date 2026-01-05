# Viator API Schemas - Destination

## Destination

Reference details about a destination associated with this product


### Properties

| Property | Type | Description |
|----------|------|-------------|
| ref | string | Unique numeric identifier for this destination - **Note**: Full details about the destination associ |
| primary | boolean | **True** if this is the primary destination associated with this product |

---

## ExtraChargesItemInDestinationCurrency

The Extra Charges amount in destination currency.

### Properties

| Property | Type | Description |
|----------|------|-------------|
| amountPerUnit | number | The cost per one Extra Charges in Destination currency.  **Note**:   - Prices payable to third parti |
| totalAmount | number | Total amount of all Extra Charges in Destination currency.  **Note**:   - Prices payable to third pa |
| currency | string | The supplier preferred currency to be paid in Destination. |

---

## DestinationDetails

### Properties

| Property | Type | Description |
|----------|------|-------------|
| destinationId | integer | Unique numeric identifier of the destination  Use this value as the `destinationId` input field for  |
| name | string | Name of the destination |
| type | string | Destination type specifier. One of: - `"AREA"` - `"CITY"` - `"COUNTRY"` - `"COUNTY"` - `"DISTRICT"`  |
| parentDestinationId | integer | Unique numeric identifier of the destination's parent destination |
| lookupId | string | Hierarchy location specifier for the destination that is a concatenation of all parentDestinationId  |
| destinationUrl | string | **URL** to forward users to in order to complete their purchase on the Viator site  This URL include |
| defaultCurrencyCode | string | Main currency used in the destination  - Example: `"EUR"`  |
| timeZone | string | Main time zone of the destination  - Example: `"US/Pacific"`  |
| iataCodes | array of string | IATA airport code(s) for the destination: a three-letter code defined by the International Air Trans |
| countryCallingCode | string | International call prefix used to call phone numbers in this destination.  - Example: `"+351"`  |
| languages | array of string | Official language(s) of this destination.  If more than one languages spoken, they’ll be concatenate |
| center | LocationCenter |  |

---

## DestinationsResponse

### Properties

| Property | Type | Description |
|----------|------|-------------|
| destinations | array of DestinationDetails |  |
| totalCount | integer | Total count of Destinations returned |

---

