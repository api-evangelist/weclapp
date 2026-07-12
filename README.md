# weclapp (weclapp)

weclapp is a German cloud ERP / CRM / commerce platform for small and mid-sized businesses, combining CRM, sales, order management, accounting, inventory / warehouse management, purchasing, and e-commerce in one SaaS suite.

## Access Model (read this first)

- **Per-tenant host.** There is no single shared API host. Each weclapp customer gets their own subdomain, and the REST API lives under it: `https://<tenant>.weclapp.com/webapp/api/v1/`. Replace `<tenant>` with your weclapp subdomain (the `acme` in `acme.weclapp.com`). In this repo the per-tenant host is represented with a `{tenant}` server variable in the OpenAPI and as `https://{tenant}.weclapp.com/webapp/api/v1` in the base URLs — it is intentionally not a real, callable host.
- **Authentication.** A per-user API token, sent in the `AuthenticationToken` request header (`AuthenticationToken: <your-token>`). Generate it inside weclapp under **My Settings > API**. This is not OAuth and not a `Bearer` token.
- **Required headers.** All requests must send `Accept: application/json`. `POST` and `PUT` requests must also send `Content-Type: application/json`.
- **Live Swagger.** Every tenant serves an interactive Swagger UI for its own API version. The public documentation entry point is [https://www.weclapp.com/api/](https://www.weclapp.com/api/).
- **CRUD conventions.** Each entity follows the same pattern: list at `GET /{entity}`, count at `GET /{entity}/count`, fetch one at `GET /{entity}/id/{id}`, create at `POST /{entity}`, update at `PUT /{entity}/id/{id}`, delete at `DELETE /{entity}/id/{id}`. List endpoints support `page`, `pageSize`, `sort`, `properties`, `additionalProperties`, and per-property filter operators (for example `?articleNumber-eq=SKU-1`).
- **API v2 note.** weclapp is rolling out an API v2 that consolidates `/customer`, `/contact`, `/lead`, and `/supplier` into a single `/party` endpoint. This catalog entry models the stable, widely-used **v1** surface (`/customer`, `/salesOrder`, etc.).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/weclapp/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/weclapp/refs/heads/main/apis.yml)

## Tags

- ERP
- CRM
- Cloud ERP
- Accounting
- Inventory
- Commerce
- Germany
- Order Management
- Business Software
- SaaS

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### weclapp Customer API

Create, read, update, delete, list, and count customer master data. In weclapp's data model a customer is a party in the customer role; the API v1 exposes it at `/customer` with the standard list, `/count`, and `/id/{id}` patterns.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- CRM
- Customers
- Party

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [API Reference](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Article API

Manage catalog articles / products - article number (SKU), name, description, unit, type, and status - with list, count, get, create, update, and delete operations at `/article`.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Articles
- Products
- Catalog

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Sales Order API

Create and manage sales orders with their order items, customer, currency, status, and dates at `/salesOrder`, using the standard list, `/count`, and `/id/{id}` conventions.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Sales Orders
- Order Management
- Sales

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Quotation API

Manage sales quotations / quotes and their line items at `/quotation`, including list, count, get, create, update, and delete.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Quotations
- Quotes
- Sales

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Sales Invoice API

Create and manage sales invoices with their items, customer, currency, status, and invoice date at `/salesInvoice`, using list, `/count`, and `/id/{id}`.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Invoices
- Accounting
- Billing

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Shipment API

Manage outbound shipments / deliveries linked to sales orders and warehouses at `/shipment`, including list, count, get, create, update, and delete.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Shipments
- Fulfillment
- Inventory

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### weclapp Purchase Order API

Create and manage purchase orders to suppliers with their items, supplier, currency, status, and order date at `/purchaseOrder`, using list, `/count`, and `/id/{id}`.

- **Human URL:** [https://www.weclapp.com/api/](https://www.weclapp.com/api/)
- **Base URL:** `https://{tenant}.weclapp.com/webapp/api/v1`

#### Tags

- Purchase Orders
- Purchasing
- Procurement

#### Properties

- [Documentation](https://www.weclapp.com/api/)
- [OpenAPI](openapi/weclapp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/weclapp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/weclapp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/weclapp-domain-security.yml)
- [Authentication](authentication/weclapp-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/weclapp)
- [Website](https://www.weclapp.com/)
- [Documentation](https://www.weclapp.com/api/)
- [Plans](plans/weclapp-plans-pricing.yml)
- [Rate Limits](rate-limits/weclapp-rate-limits.yml)
- [Fin Ops](finops/weclapp-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
