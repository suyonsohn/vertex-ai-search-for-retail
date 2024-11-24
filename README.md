# Implementing Recommendations using Vertex AI Search for Retail

## Overview

This guide outlines the steps for implementing a recommendation system using Vertex AI Search for Retail on Google Cloud.

For detailed information, refer to the [Vertex AI Search for Retail Documentation](https://cloud.google.com/retail/docs/overview).

### Notes on Terminologies:

- Google Cloud has rebranded the term _Retail_ (legacy) to **AI Search for Retail** (new).
- Throughout the Google Cloud documentation, _catalog_ and _product_ appear to be interchangeable.

1. Prepare Product Data

Ensure the product data file includes the minimum required fields: `id`, `categories`, and `title`.

**Example product data:**

```
  {
    "id": "1234",
    "categories": "Apparel & Accessories > Shoes",
    "title": "ABC sneakers"
  }
  {
    "id": "5839",
    "categories": "casual attire > t-shirts",
    "title": "Crew t-shirt"
  }
```

Refer to the [sample catalog](resources/products.json) file for a full example.

2. Import Catalog (Product) Information

   Product data can be imported in 3 ways:

- From Cloud Storage:
  [Code sample](product/import-products-gcs.js)
- From BigQuery
- Inline Catalog Data

3. Prepare User Events Data

   To personalize recommendations, historical user events data need to be imported.

   Refer to the [sample user events](resources/user_events.json) file for a full example.

4. Import Historical User Events

   User events data can be imported in 3 ways:

- From Cloud Storage:
  [Code sample](setup/update-user-events-json.js)
- From BigQuery
- Inline User Events Data

5. Upload User Events to Cloud Storage

   [code sample] (setup/events-create-gcs-bucket.js)

6. Import User Events from Cloud Storage

   Once user events are uploaded, import them into Vertex AI Search for Retail.

   [Code sample](events/import-user-events-gcs.js)

7. Record real-time user events

   To track real-time user events, record them using the Vertex AI Search for Retail API.

   [Code sample](events/write-user-event.js)
