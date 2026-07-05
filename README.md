# TableCheck (tablecheck)

TableCheck is a restaurant booking and guest-experience platform (founded 2011, headquartered in Tokyo, Japan) used by thousands of restaurants across 35+ countries - including hundreds of Michelin-starred venues - to consolidate reservations, availability, guest CRM, memberships, and POS integration into one system. TableCheck exposes a production JSON/REST API partitioned into components (Availability, Web Booking, Booking, CRM, POS, and Site Controller) under `https://api.tablecheck.com/api`, with each component publishing its own OpenAPI 3.0 description.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/tablecheck/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/tablecheck/refs/heads/main/apis.yml)

## Access Model

TableCheck's API is **partner-gated**, not self-serve:

- **Production only.** TableCheck provides only a Production API environment (no public sandbox); test reservations are created against live data.
- **Approved keys.** Authentication uses a `secret_key` set in the `Authorization` HTTP header (OpenAPI `securityScheme`: `apiKey`, `in: header`, `name: AUTHORIZATION`). One key per environment is issued by the TableCheck API team (api@tablecheck.com) at the time your access is approved.
- **Some components by special arrangement.** The direct **Booking API** (writing reservations straight into TableCheck's inventory backend) is available only by special arrangement - most integrators use the read-only **Web Booking API** plus TableCheck's hosted web-booking flow instead.
- **Documentation.** The API is documented in TableCheck's public Confluence API space, and each component serves its OpenAPI document at `.../<component>/v1/docs`.

## Tags

- Restaurant
- Reservations
- Booking
- Hospitality
- Availability
- Guest CRM
- Point of Sale
- Japan

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### TableCheck Availability API

Obtain near real-time table availability for online reservation booking. Search availability across all shops for a party size and datetime, fetch a shop's availability timetable and calendar, and list bookable tables for a specific shop.

- **Human URL:** [Availability v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/46301274/Availability+v1)
- **Base URL:** `https://api.tablecheck.com/api/availability/v1`
- **OpenAPI:** [openapi/tablecheck-availability.yml](openapi/tablecheck-availability.yml)

### TableCheck Web Booking API

Read-only API to query reservations that diner users booked via the TableCheck website. List reservations with `created_at` / `updated_at` / `start_at` range filters, and fetch a specific reservation by ID or ref. Bookings themselves are made by linking users into TableCheck's hosted web flow.

- **Human URL:** [Web Booking v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/48595292/Web+Booking+v1)
- **Base URL:** `https://api.tablecheck.com/api/web_booking/v1`
- **OpenAPI:** [openapi/tablecheck-web-booking.yml](openapi/tablecheck-web-booking.yml)

### TableCheck Booking API

Book reservations directly into TableCheck's inventory backend. Create, read, update, and cancel reservations; manage blockages and reservation flags; and list shops. Available by special arrangement with TableCheck - in most cases the Web Booking API is used instead.

- **Human URL:** [Booking v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/160334455/Booking+v1)
- **Base URL:** `https://api.tablecheck.com/api/booking/v1`
- **OpenAPI:** [openapi/tablecheck-booking.yml](openapi/tablecheck-booking.yml)

### TableCheck CRM API

Obtain full customer, reservation, membership, and related guest data for restaurant operators. Manage customers (list, create, amend, delete, bulk search/export), memberships and membership programs, reservations and reservation flags, plus shops and franchises.

- **Human URL:** [CRM v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/44664326/CRM+v1)
- **Base URL:** `https://api.tablecheck.com/api/crm/v1`
- **OpenAPI:** [openapi/tablecheck-crm.yml](openapi/tablecheck-crm.yml)

### TableCheck POS API

Connect Point-of-Sale systems to restaurants on the TableCheck platform. List shops, manage POS journals per shop (create, read, update, delete, void), read and update reservations, list tables, and read and update table status.

- **Human URL:** [POS v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/44958898/POS+v1)
- **Base URL:** `https://api.tablecheck.com/api/pos/v1`
- **OpenAPI:** [openapi/tablecheck-pos.yml](openapi/tablecheck-pos.yml)

### TableCheck Site Controller API

Site-controller component for reading shop inventory across the platform. List shops (filtered by IDs, slugs, or franchise IDs) and fetch a specific shop, for channel-manager and site-integration use cases.

- **Human URL:** [Site Controller v1](https://tablecheck.atlassian.net/wiki/spaces/API/pages/1739194852/Site+Controller+v1)
- **Base URL:** `https://api.tablecheck.com/api/site/v1`
- **OpenAPI:** [openapi/tablecheck-site-controller.yml](openapi/tablecheck-site-controller.yml)

## Collections

- [Postman Collection](collections/tablecheck.postman_collection.json) - all six components (59 requests), API-key auth in the `Authorization` header.
- [Open Collection](collections/tablecheck.opencollection.json) - the same requests in Open Collection 1.0 format.

Both collections are generated from TableCheck's published OpenAPI documents.

## Rate Limits

TableCheck publishes a fixed limit of **10,000 requests per 5-minute period**, applied independently to each API component (limits do not pool across components). Exceeding the limit returns HTTP `429 Too Many Requests` until the next 5-minute window. See [rate-limits/tablecheck-rate-limits.yml](rate-limits/tablecheck-rate-limits.yml).

## Common Properties

- [GitHub Organization](https://github.com/tablecheck)
- [LinkedIn](https://www.linkedin.com/company/tablecheck)
- [Website](https://www.tablecheck.com)
- [Documentation](https://tablecheck.atlassian.net/wiki/spaces/API)
- [Plans](plans/tablecheck-plans-pricing.yml)
- [Rate Limits](rate-limits/tablecheck-rate-limits.yml)
- [Fin Ops](finops/tablecheck-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
