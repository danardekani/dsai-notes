# Viator API - Attractions

## POST /attractions/search

**Operation ID:** `attractionsSearch`

**Summary:** /attractions/search

**Description:**
Get a list of attractions associated with a given `destinationId`, along with all relevant information about them, including products mapped.

Attractions should be cached and refreshed weekly.

**Note**:

 - Pages generated using data from this endpoint are subject to a strict no-index policy. 
 You must ensure that your site is configured such that **no Viator Unique Content is indexed by any search engine**. 
 This is a requirement for site certification. For more information, see [Key concepts – Protecting unique content](#section/Key-concepts/Protecting-unique-content). 
 If you are unsure about whether you are correctly following this rule or if you would like to take advantage of our unique content, [please reach out to our support team](#section/Support).


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Request Body

**Content-Type:** `application/json;version=2.0`

**Schema:** `AttractionsSearchRequest`

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **405**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

## GET /attractions/{attraction-id}

**Operation ID:** `attractions`

**Summary:** /attractions/{attraction-id}

**Description:**
Get all relevant information about a specific `attractionId`, including products mapped.
    
**Note**:

 - Pages generated using data from this endpoint are subject to a strict no-index policy. 
 You must ensure that your site is configured such that **no Viator Unique Content is indexed by any search engine**. 
 This is a requirement for site certification. For more information, see [Key concepts – Protecting unique content](#section/Key-concepts/Protecting-unique-content). 
 If you are unsure about whether you are correctly following this rule or if you would like to take advantage of our unique content, [please reach out to our support team](#section/Support).


### Parameters

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

### Responses

- **200**: Success
- **400**: 
- **401**: 
- **403**: 
- **404**: 
- **405**: 
- **406**: 
- **429**: 
- **500**: 
- **503**: 

---

