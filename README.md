# weclapp (weclapp)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
